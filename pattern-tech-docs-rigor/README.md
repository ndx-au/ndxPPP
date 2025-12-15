# Pattern: ndxGEN Tech-Docs-Rigor

## The Philosophy: Document OS vs. CMS

We are moving beyond the era of the **Content Management System (CMS)**.
The term "Management" implies that content is a burden—a chaotic mess that you must passively cope with, categorize, and store away.

**ndxGEN** introduces the **Document Operating System (DOS)**.
In a Document OS, content is not "managed"; it is **engineered**. It is an active "Source of Truth" that is compiled, tested, and deployed just like software.

### The Paradigm Shift
| The Old Way (CMS) | The ndxGEN Way (Document OS) |
| :--- | :--- |
| **Database Blobs** | **Git-Backed Files** |
| **WYSIWYG Editors** | **Structured Text (AsciiDoc)** |
| **"Looks Good"** | **"Compiles Correctly"** |
| **Passive Storage** | **Active Expression** |
| **Review by Eye** | **Review by Linter & Logic** |

## The Architecture

This pattern maps software engineering principles directly to technical writing:

1.  **`tech-writer.md` (The Developer)**: The creative engine. Writes the "code" (AsciiDoc) to solve a user problem.
2.  **`editor.md` (The Code Reviewer)**: The quality gate. Runs the "unit tests" (Style Guide checks) and ensures the architecture is respected.
3.  **`system.md` (The Kernel)**: Defines the immutable laws of the environment (File I/O, compilation rules).
4.  **`constitution.md` (The Linter)**: The strict style guide that defines valid syntax and tone.
5.  **`architecture.md` (The Spec)**: The blueprint of what belongs where.

## How to Use This Pattern in ndxGEN

If you're using this repository as a pattern library (not the ndxGEN runtime), you can still adopt the structure by copying `pattern-tech-docs-rigor/_work/` into your project root as `_work/` and adapting any tool-specific path assumptions (e.g., `/live`, `.instructions/`) to your runner.

### 1. Initialization
Mount your project root to `/live`. Ensure your `.instructions/` folder contains the agent definitions above.

### 2. The Workflow
The user acts as the **Product Owner**.
> **User**: "We need a troubleshooting guide for the Database Connection Error 503."

**Step 1: The Writer Drafts**
> **Tech-Writer**: Scans `architecture.md`, selects `/live/content/guides/troubleshoot-db.adoc`, and drafts the content using Sentence-Per-Line formatting.

**Step 2: The Editor Reviews**
> **Editor**: Intercepts the draft.
> *Critique*: "You used future tense in paragraph 3 ('The database will restart'). Change to present tense ('The database restarts'). You also used the word 'simply'. Remove it."

**Step 3: The Writer Refines**
> **Tech-Writer**: Applies fixes and outputs the final `.adoc` file.

## Why "Sentence-Per-Line"?
We treat prose like code. By placing every sentence on a new line:
1.  **Diffs are Atomic**: Changing one sentence doesn't show a 10-line diff in Git.
2.  **Reordering is Trivial**: You can swap sentence logic by moving lines, just like code statements.