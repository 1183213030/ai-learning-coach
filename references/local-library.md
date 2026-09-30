# Local Library & Textbook Ingestion Protocol

This document specifies how the coach ingests, indexes, and prioritizes local user-supplied textbooks, notes, and documentation stored in `library/`.

---

## 1. Local-First Ingestion Priority

When a user initiates a topic (e.g. `/learn teach software-testing`), the coach follows a strict priority cascade:

```text
Check library/<topic>/
       │
       ├──> Local Textbooks / Notes Found?
       │       ├── YES: Ingest as Primary Ground Truth (S1/S2 equivalent)
       │       └── NO: Fallback to Web Research (S0/S1 official specs)
```

**Guiding Rule**:
If a user provides a local book (e.g. *《软件测试基础教程》* or a directory of markdown files), that resource becomes the **Curriculum Backbone**. The coach must not substitute generic internet opinions for the user's chosen textbook. Web research is permitted only to verify current official standards or clarify missing prerequisites.

---

## 2. Directory Structure of `library/`

The local library is organized by technical domain under the workspace root:

```text
library/
├── frontend/
│   ├── modern-javascript-guide.md
│   └── css-architecture.pdf
├── software-testing/
│   ├── testing-fundamentals.md
│   └── playwright-advanced-handbook/
├── backend/
│   └── nodejs-design-patterns.md
├── security/
│   └── owasp-top-10-deep-dive.md
└── ai/
    └── prompt-engineering-and-agents.md
```

---

## 3. The `/learn import` Protocol

When the user runs `/learn import <path>` (e.g. `/learn import ./library/software-testing/testing-guide.md`):

### Step 1: Structural Decomposition
The coach scans the file and extracts:
- Table of Contents / Heading Hierarchy (H1, H2, H3).
- Conceptual progression (Chapters -> Sections -> Code snippets).
- Explicit learning objectives stated by the author.

### Step 2: Capability & Prerequisite Extraction
For each section in the book, extract:
- Target capabilities (what the author expects the reader to do).
- Implied prerequisites (e.g. Chapter 4 assumes Chapter 2's test runner is understood).

### Step 3: Source Manifest Registration
Record the textbook metadata in `templates/source-manifest.yaml`:
```yaml
sources:
  - id: local-testing-guide
    title: "Software Testing Fundamentals"
    path: "library/software-testing/testing-guide.md"
    type: "local_book"
    format: "markdown"
    role: "primary_curriculum"
    chapters_indexed: 14
```

---

## 4. Teaching from a Local Textbook

When teaching from an ingested book:
1. **Never dump chapter summaries**.
   Do NOT say: *"Chapter 3 is about equivalence partitioning. Here is the summary..."*
2. **Anchor to the Author's Problem Space**.
   State the specific scenario or case study provided in the book:
   > *"In Chapter 3 of your testing handbook, the author presents a flight booking system with age inputs between 0 and 120. Before we write tests, how many equivalence partitions do you identify, and what are their boundary values?"*
3. **Bridge Book to Project**.
   Whenever possible, apply the book's theory directly to the user's active codebase.
