# Markdown Review Assistant (MRA)

This repository provides a comprehensive prompt template for an AI to systematically review markdown files for grammar, links, consistency, and cohesion.

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
└── instructions/
    └── instructions.md
```

## Usage

Provide the `instructions/instructions.md` file to an AI and request:

```
"Review all markdown files in this repository"
```

The AI will create a `.mra/` directory:

```
.mra/
├── 00-SUMMARY.md                    # Overview, stats, cohesion analysis
├── README.md                        # Review of /README.md
├── docs__guide.md                   # Review of /docs/guide.md
└── src__components__Button.tsx.md   # Review of /src/components/Button.tsx.md
```

**Workflow:**

1. **Phase 1:** AI analyzes all files and creates `.mra/` with organized findings (read-only)
2. **Phase 2:** You review findings, give instructions, AI applies fixes accordingly

## Best For

- When you want full control over what gets fixed and when
- Easy navigation of findings (one file per reviewed file)
- Precise, human-directed implementation
- Sensitive documentation requiring approval
- Repositories where you want to review all findings before any changes
- Flexible workflows (fix everything, fix selectively, fix incrementally)
- Scalable to repositories with 100+ markdown files
