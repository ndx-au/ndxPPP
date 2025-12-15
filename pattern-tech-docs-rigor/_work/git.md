# PROTOCOL: Git for Documentation

## PHILOSOPHY
In the Document OS, **Content is Code**.
If it is not in Git, it does not exist.
If it is not committed, it is not "saved."

## 1. BRANCHING STRATEGY
We use a **Content-Feature** workflow. Never write directly to `main`.

- **`main`**: The immutable production state. Mirrors the live website.
- **`draft/topic-name`**: Short-lived branches for new content (e.g., `draft/kafka-integration`).
- **`fix/topic-name`**: For errata, typos, and broken links (e.g., `fix/broken-url-billing`).
- **`refactor/topic-name`**: For rewriting existing content without changing the underlying facts (e.g., `refactor/simplify-intro`).

## 2. ATOMIC COMMITS
Writers must not save up a whole day's work into one "Update docs" commit. Commits must be **Atomic** and **Semantic**.

### The Format
`type(scope): subject`

### The Types
- **`feat`**: Adding a new document or section.
- **`fix`**: Correcting a factual error, typo, or broken link.
- **`style`**: Formatting changes (e.g., fixing SPL, indentation) that do not change meaning.
- **`refactor`**: Rewriting for clarity or tone (Voice & Tone updates).
- **`asset`**: Adding or updating images/diagrams.

### Examples
- `feat(billing): add guide for credit card updates`
- `fix(install): correct the curl command flags`
- `style(api): apply sentence-per-line formatting`
- `refactor(intro): switch passive voice to active`

## 3. THE "SENTENCE-PER-LINE" (SPL) CONTRACT
Git operates on lines, not sentences.
To ensure Git diffs are readable during the Editorial Review (`editor.md`), you **MUST** use Sentence-Per-Line.

**Bad (Paragraph Mode):**
```text
To install the CLI, run the command below. After the command finishes, you will need to restart your terminal. This ensures the path is updated.