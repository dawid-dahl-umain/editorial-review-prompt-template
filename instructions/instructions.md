# 📋 Markdown Review Assistant (MRA) - Instructions

---

## Quick Start

This is the main entry point for the Markdown Review Assistant. The instructions are split into three focused documents:

### 1. **[Core Workflow](core-workflow.md)** ⭐ START HERE

The essential workflow and rules you need to execute MRA:

- Two-phase workflow (Review → Implementation)
- Step-by-step process for Phase 1 and Phase 2
- Critical rules (read-only vs controlled mutations)
- Decision rules (what to document, how to categorize)
- Essential guidelines (DO/DON'T lists)

**Read this first** - it contains everything needed to perform the review.

### 2. **[Reference Guide](reference.md)**

Templates, schemas, and technical details:

- Document templates (summary, file entries, issues, observations)
- Formatting standards (dates, status indicators, file paths, etc.)
- Technical implementation (file discovery, link verification, update patterns)
- Verification checklist

**Use this as needed** - reference when creating documents or implementing technical details.

### 3. **[Examples & Edge Cases](examples.md)**

Complete example flows and FAQs:

- Full Phase 1 example (scan → review → summarize)
- Multiple Phase 2 examples (broad scope, narrow scope, filters, exclusions)
- Edge cases (huge repositories, interrupted reviews, failed fixes, etc.)
- FAQs with specific guidance

**Refer to this for clarity** - see how the workflow operates in practice.

---

## System Overview

**Purpose:** Systematically review markdown files for grammar, links, consistency, and cohesion through a two-phase workflow.

**How it works:**

- **Phase 1 (Read-Only):** Review all files, create `.mra/` directory with findings, document everything, fix nothing
- **Phase 2 (Human-Directed):** User reviews findings, gives instructions, AI applies fixes and updates reports

**Key Features:**

- ✅ Complete separation between review and implementation
- ✅ User has full control over what gets fixed and when
- ✅ One findings file per reviewed file (easy navigation)
- ✅ Flexible instructions (from "fix everything" to "fix issue #3 in file X")
- ✅ Strict report update rules ensure traceability
- ✅ Handles repositories of any size (1 file to 1000+ files)

---

## When User Requests Review

When user says: **"Review all markdown files"** or similar:

1. **Go to [Core Workflow](core-workflow.md)** and follow the process
2. **Reference [Reference Guide](reference.md)** for templates and formatting
3. **Check [Examples](examples.md)** if you encounter edge cases or need clarity

That's it. The modular structure keeps everything organized and accessible.

---

## Document Structure

```
instructions/
├── instructions.md          # This file (entry point)
├── core-workflow.md         # Essential workflow and rules ⭐
├── reference.md             # Templates, schemas, technical details
└── examples.md              # Complete examples and edge cases

.mra/                        # Created during review
├── 00-SUMMARY.md            # Overview, statistics, cohesion analysis
└── findings/                # Mirrors repository structure
    ├── README.md
    ├── docs/
    │   └── guide.md
    └── src/
        └── ...
```

---

## What Makes MRA Effective

### Phase Separation

- **Phase 1:** Read-only analysis creates comprehensive findings without changing anything
- **Phase 2:** Human-directed implementation applies only what user instructs

### Organized Findings

- `.mra/` directory with nested structure mirroring your repository
- Easy navigation: `.mra/findings/docs/guide.md` contains review of `docs/guide.md`
- Summary file: `.mra/00-SUMMARY.md` provides overview and statistics

### Flexible Instructions

Parse and execute instructions from broad to narrow:

- "Fix all automatic issues"
- "Fix only critical issues"
- "Fix grammar in all files"
- "Fix issue #3 in docs/guide.md"
- "Fix everything except terminology"

### Complete Traceability

- Every issue documented with line numbers, severity, type, category
- Every fix tracked with timestamp, action taken, files modified
- Resolution log captures complete history

### Scalable Process

- Works with 1 file or 1000+ files
- Pauses every 10 files to prevent overwhelming output
- Can resume if interrupted
- Handles complex repository structures

---

## For AI Assistants

When executing MRA:

1. **Primary document:** [Core Workflow](core-workflow.md) - contains all essential instructions
2. **Reference as needed:** [Reference Guide](reference.md) - for templates and technical details
3. **Consult for clarity:** [Examples](examples.md) - for edge cases and practical guidance

**Critical rules:**

- ✅ **Phase 1:** Document everything, fix nothing
- ✅ **Phase 2:** Fix only what user instructs
- ✅ **Always:** Update `.mra/` reports after changes
- ✅ **Always:** Follow formatting standards from reference guide

---

## For Users

**To use MRA:**

1. Provide [core-workflow.md](core-workflow.md) to your AI assistant
2. Request: "Review all markdown files in this repository"
3. AI will create `.mra/` directory with findings (Phase 1)
4. Review the findings
5. Give instructions on what to fix (Phase 2)
6. AI applies fixes and updates reports

**The modular structure means:**

- Faster loading (AI reads only what's needed)
- Easier maintenance (update one section without affecting others)
- Better clarity (focused documents vs monolithic instruction set)

---

**Ready to start?** → [Open Core Workflow](core-workflow.md)
