# System Architecture: ACME Flux

## 1. The "North Star" (Definition of Done)
*The system is considered "Complete" when it meets the following state:*

* **Artifact:** A single, self-contained executable binary (`flux`) with zero runtime dependencies (no external dlls, assets embedded via `embed`).
* **Performance:** * Cold boot time < 500ms.
    * API/Page latency < 50ms (p95).
    * Handles 5,000 concurrent SSE (Server-Sent Events) connections on a $5 VPS.
* **Distribution:** The binary is capable of replicating its data across nodes using LiteFS without application-level clustering logic.
* **UX State:** A user can open the dashboard on a mobile phone on 3G, disconnect, reconnect, and see the graph "catch up" without a page refresh.

---

## 2. High-Level Design Pattern
**"The Majestic Monolith" (Hexagonal/Ports & Adapters)**

We reject microservices. The application is a single process that handles:
1.  Serving static assets (embedded).
2.  Rendering HTML (Server-Side Rendering).
3.  Managing WebSocket/SSE streams.
4.  Direct SQLite database access.

### The Dependency Graph
`CMD` → `SERVER` → `CORE` ← `STORE`

* **CMD:** Wiring and config only.
* **SERVER:** HTTP/HTMX handlers. Transforms Domain Objects into HTML.
* **CORE:** Pure Go business logic. Agnostic of HTTP or SQL.
* **STORE:** Persistence layer. Knows SQL, returns Domain Objects.

---

## 3. Technology Stack

### Core Runtime
* **Language:** Go (Latest Stable).
* **Standard Library:** Heavy usage (`net/http`, `html/template`, `context`).

### Data Layer
* **Database:** SQLite 3 (CGO-free wrapper preferred, e.g., `modernc.org/sqlite` or `wazero` if strictly needed, otherwise standard `mattn/go-sqlite3`).
* **Replication:** LiteFS (Application assumes a file-system based DB, LiteFS handles the replication at the OS/FUSE level).
* **Schema Management:** SQL-based migrations stored in `sql/migrations`.

### Presentation Layer (The "V" in MVC)
* **Hypermedia Client:** HTMX 1.9+.
    * *Role:* Swaps HTML fragments based on user interaction.
    * *Constraint:* No client-side JSON parsing or state management.
* **Styling:** Tailwind CSS (generated at build time, embedded in binary).
* **Real-time:** Server-Sent Events (SSE).
    * *Role:* Pushing metric updates to the browser.
    * *Format:* `data: <div id="metric-1">...</div>` (HTML over the wire).

---

## 4. Component Roles & Responsibilities

### A. The Event Bus (`internal/bus`)
* **Responsibility:** The central nervous system.
* **Mechanism:** In-memory Go channels.
* **Flow:** When `CORE` processes a write (e.g., `IngestMetric`), it emits an event. The `SERVER` subscribes to these events to push updates via SSE.

### B. The Store (`internal/store`)
* **Responsibility:** Data persistence and integrity.
* **Constraint:** Must assume the database file might become read-only (during LiteFS primary failover). All write operations must handle `SQLITE_READONLY` errors gracefully.

### C. The Renderer (`internal/ui`)
* **Responsibility:** Converting data structs into Safe HTML.
* **Technique:** strongly-typed Go templates.
* **Safety:** Context-aware escaping is mandatory.

---

## 5. Data Flow Specifications

### Scenario: Ingesting a New Metric
1.  **Request:** POST `/api/ingest` (API Key Auth).
2.  **Server:** Validates auth, parses payload, calls `core.Ingest()`.
3.  **Core:** Validates business rules (e.g., rate limits).
4.  **Store:** `INSERT INTO metrics ...` (Atomic Transaction).
5.  **Bus:** Emits `MetricUpdated{ID, Value}`.
6.  **Server (Background):** Catches event, renders HTML fragment `<span id="val-1">99%</span>`, pushes to active SSE clients.
7.  **Response:** 202 Accepted.

### Scenario: Dashboard Load
1.  **Request:** GET `/dashboard`.
2.  **Store:** `SELECT * FROM metrics ...`.
3.  **Core:** Aggregates data.
4.  **Server:** Renders full `index.html` template.
5.  **Client:** Browser renders HTML. HTMX immediately opens SSE connection to `/events` for updates.