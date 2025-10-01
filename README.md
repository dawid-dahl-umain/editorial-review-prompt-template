# Markdown Review Assistant (MRA)

A comprehensive, modular prompt system for AI assistants to systematically review markdown files for grammar, links, consistency, and cohesion.

## Two-Phase Workflow

The MRA uses a two-phase approach that separates review from implementation:

### Phase 1: Review & Documentation (Read-Only)

- AI reviews all markdown files without making any changes
- Creates `.mra/` directory with organized findings (one file per reviewed file)
- Documents every issue found with suggested fixes
- Categorizes issues by fixability (Can Fix Auto / Needs Judgment / Requires Discussion)
- Flags observations for subjective improvements
- Provides comprehensive cohesion analysis in summary report
- **No file mutations** - only creates `.mra/` directory structure

### Phase 2: Resolution & Implementation (Human-Directed)

- You review the findings (easy navigation, one file per reviewed file)
- Give flexible instructions on what to fix (from "fix all" to "fix issue #3 in file X")
- AI applies fixes according to your instructions
- Updates findings with strict business-logic rules
- Tracks all changes in resolution log
- **Controlled mutations** - only what you instruct

## Repository Structure

```
.
├── README.md
├── mra-workflow.mermaid     # Detailed visual workflow diagram
└── instructions/
    ├── instructions.md      # Entry point and overview
    ├── core-workflow.md     # Essential workflow and rules ⭐
    ├── review-criteria.md   # Editorial standards (domain expertise) 📝
    ├── reference.md         # Templates, schemas, technical details
    └── examples.md          # Complete examples and edge cases
```

**Modular Design Benefits:**

- **Focused documents** - Each file has a clear purpose
- **Customizable** - Adapt review-criteria.md for different doc types
- **Faster loading** - AI reads only what's needed
- **Easier maintenance** - Update sections independently
- **Better clarity** - No overwhelming monolithic file

## Usage

### Option 1: Attach All Files (Recommended)

Copy the `instructions/` folder into your project, then provide all instruction files to your AI:

```
@instructions.md @core-workflow.md @review-criteria.md @reference.md @examples.md

Follow the MRA workflow to review all markdown files in this repository. Start with Phase 1 (read-only review and documentation).
```

The AI will have access to the complete workflow, editorial standards, all templates/schemas, and examples.

### Option 2: Single File (Alternative)

Use a solution like [repo.md](https://repo-md.com/) to convert this repository into one markdown file and provide it to your AI.

**Pros:** Everything in one prompt  
**Cons:** Larger file (~2,500 lines) may reduce context space for your actual files

### Option 3: Core Only (Minimal)

Attach only the core workflow:

```
@core-workflow.md

Follow the workflow in this file to review all markdown files in this repository. Start with Phase 1.
```

**Trade-off:** AI has maximum context for your files but may improvise on editorial standards, formatting details, and edge cases since it won't have review-criteria.md, reference.md, or examples.md.

### What Gets Created

The AI creates a `.mra/` directory with nested structure:

```
.mra/
├── 00-SUMMARY.md            # Overview, stats, cohesion analysis
└── findings/                # Mirrors your repository structure
    ├── README.md            # Review of /README.md
    ├── docs/
    │   └── guide.md         # Review of /docs/guide.md
    └── src/
        └── components/
            └── Button.tsx.md # Review of /src/components/Button.tsx.md
```

The nested structure makes navigation intuitive and directly maps to your project organization.

### Complete Workflow

1. **Phase 1:** AI analyzes all files and creates `.mra/` with organized findings (read-only)
2. **You review** the `.mra/` directory - easy navigation with one file per reviewed file
3. **Phase 2:** You give instructions, AI applies fixes and updates reports

## Instruction Files

- **📘 [instructions.md](instructions/instructions.md)** - Entry point with overview and navigation
- **⭐ [core-workflow.md](instructions/core-workflow.md)** - Essential workflow, rules, and guidelines (primary file)
- **📝 [review-criteria.md](instructions/review-criteria.md)** - Editorial standards and domain expertise (customizable)
- **📚 [reference.md](instructions/reference.md)** - Templates, schemas, and formatting standards
- **📖 [examples.md](instructions/examples.md)** - Complete example flows, edge cases, and FAQs
- **🔀 [mra-workflow.mermaid](mra-workflow.mermaid)** - Visual workflow diagram (for humans)

## Key Features

**Comprehensive Review:** Grammar, spelling, links (internal/external/anchors/images), terminology consistency, structure, and repository-wide cohesion analysis.

**Human Control:** Two-phase workflow ensures you review all findings before any changes. Give flexible instructions from "fix all" to "fix issue #3 in specific file."

**Complete Traceability:** Every issue and fix documented with line numbers, severity, timestamps, and actions taken.

**Scalable:** Works with 1 to 1000+ files. Pauses every 10 files to prevent overwhelming output. Can resume if interrupted.
