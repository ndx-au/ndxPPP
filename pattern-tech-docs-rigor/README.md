# Pattern: ndxGEN Tech-Docs-Rigor

## The Philosophy: Document OS vs. CMS

We are moving beyond the era of the **Content Management System (CMS)**.
The term "Management" implies that content is a burden—a chaotic mess that you must passively cope with, categorize, and store away.

**ndxGEN** introduces the **Document Operating System (DOS)**.
In a Document OS, content is not merely "managed"; it is **maintained with rigor**. It is an active "Source of Truth" that is drafted, reviewed, validated, and published through a repeatable process.

### The Paradigm Shift
| The Old Way (CMS) | The ndxGEN Way (Document OS) |
| :--- | :--- |
| **Database Blobs** | **Git-Backed Files** |
| **WYSIWYG Editors** | **Structured Text (AsciiDoc)** |
| **"Looks Good"** | **"Accurate, Consistent, Releasable"** |
| **Passive Storage** | **Active Expression** |
| **Review by Eye** | **Review by Standards & Checks** |

## The Architecture

This pattern is built for technical writing teams that want repeatability, clear handoffs, and review discipline:

1.  **`tech-writer.md` (The Writer)**: Drafts and revises content to solve a user problem.
2.  **`editor.md` (The Editor)**: Reviews for clarity, correctness, consistency, and adherence to the style guide.
3.  **`system.md` (The Process Rules)**: Defines the workflow signals, file conventions, and how work moves from draft → review → done.
4.  **`constitution.md` (The Style Guide)**: The non-negotiable rules for tone, terminology, formatting, and “what good looks like.”
5.  **`architecture.md` (The Information Architecture)**: The blueprint of what belongs where (and what does not).

## How to Use This Pattern in ndxGEN

If you're using this repository as a pattern library (not the ndxGEN runtime), you can still adopt the structure by copying `pattern-tech-docs-rigor/_work/` into your project root as `_work/` and adapting any tool-specific assumptions to your environment.

### 1. Initialization
Decide where documentation lives in your repo (e.g., `content/`), then place this pattern’s `_work/` folder at the project root so your tools/assistants can find the process and role definitions.

### 2. The Workflow
The user acts as the **Requester / Stakeholder**.
> **User**: "We need a troubleshooting guide for the Database Connection Error 503."

**Step 1: The Writer Drafts**
> **Tech-Writer**: Scans `architecture.md`, selects `content/guides/troubleshoot-db.adoc`, and drafts the content using Sentence-Per-Line formatting.

**Step 2: The Editor Reviews**
> **Editor**: Intercepts the draft.
> *Critique*: "You used future tense in paragraph 3 ('The database will restart'). Change to present tense ('The database restarts'). You also used the word 'simply'. Remove it."

**Step 3: The Writer Refines**
> **Tech-Writer**: Applies fixes and produces a releasable `.adoc` file.

## Why "Sentence-Per-Line"?
We treat prose like source text that benefits from careful change control. By placing every sentence on a new line:
1.  **Diffs are Atomic**: Changing one sentence doesn't show a 10-line diff in Git.
2.  **Reordering is Trivial**: You can move sentences around without rewriting paragraphs.