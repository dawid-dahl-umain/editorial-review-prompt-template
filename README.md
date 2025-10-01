# Editorial Review Prompt Template

This repository provides a comprehensive prompt template for an AI to systematically review markdown files for grammar, links, consistency, and cohesion.

## Two-Phase Workflow

The prompt uses a two-phase approach that separates review from implementation:

### Phase 1: Review & Documentation (Read-Only)

- AI reviews all markdown files without making any changes
- Documents every issue found with suggested fixes
- Categorizes issues by fixability (Can Fix Auto / Needs Judgment / Requires Discussion)
- Flags observations for subjective improvements
- Provides comprehensive cohesion analysis
- **No file mutations** - only creates/updates the findings report

### Phase 2: Resolution & Implementation (Human-Directed)

- You review the findings document
- Give flexible instructions on what to fix (from "fix all" to "fix issue #3 in file X")
- AI applies fixes according to your instructions
- Updates report with strict business-logic rules
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

Provide the instructions.md file to an AI and request:

```
"Review all markdown files in this repository"
```

The AI will:

1. **Phase 1:** Analyze all files and create a comprehensive findings report (read-only)
2. **Phase 2:** Wait for your instructions on what to fix, then apply changes accordingly

## Best For

- When you want full control over what gets fixed and when
- Precise, human-directed implementation
- Sensitive documentation requiring approval
- Repositories where you want to review all findings before any changes
- Flexible workflows (fix everything, fix selectively, fix incrementally)
