# ACME Flux: Project Constitution

## Article I: The Go Philosophy (Code Style)
1.  **Standard Library First:** Do not introduce external dependencies (e.g., `gorilla/mux`, `gin`) unless the standard library is objectively insufficient. We use `net/http` and Go 1.22+ routing.
2.  **Explicit Error Handling:** Never ignore errors. Never use `panic` in production code. Bubble errors up with context using `fmt.Errorf("doing action: %w", err)`.
3.  **Concurrency Safety:** All shared state must be protected by `sync.RWMutex` or confined to channels. Global state is forbidden.

## Article II: The ACME Architecture (System Design)
1.  **Hexagonal Architecture:**
    * `internal/core`: Pure business logic. No SQL, no HTTP imports.
    * `internal/adapter`: Database (SQLite) and Web (Handlers).
    * `cmd/server`: dependency injection and wiring only.
2.  **HTML over JSON:** This is an HTMX app. Handlers return HTML fragments, not JSON, unless the endpoint starts with `/api/v1`.
3.  **Data Integrity:** We use SQLite with strict foreign keys. Schema changes must be additive.

## Article III: The Workflow Protocol (Process)
1.  **Immutable History:** You are forbidden from modifying any file inside a `_work/_NNNN...` folder. Those are past iterations.
2.  **The "Plan" is Binding:** You must not write code until `plan.md` in the current iteration folder is generated and (implicitly) approved.
3.  **Test-Driven Regressions:** If you modify existing logic, you must run `go test ./...` and include the output in your completion summary.

## Article IV: User Experience (The "ACME Standard")
1.  **Speed is a Feature:** Any operation taking >100ms must provide immediate UI feedback (loader/optimistic UI).
2.  **Mobile First:** All CSS generation must prioritize mobile viewports before desktop.