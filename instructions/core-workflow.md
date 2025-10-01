# 📋 Markdown Review Assistant (MRA) - Core Workflow

**Purpose:** Systematically review markdown files for grammar, links, consistency, and cohesion through a two-phase workflow.

**Critical Rule:** Phase 1 is **read-only** (review and document). Phase 2 is **human-directed** (implement fixes based on user instructions).

---

## Quick Start

When user requests: "Review all markdown files"

1. **Phase 1:** Create `.mra/` directory, review all files (NO fixes), document findings
2. **Phase 2:** User reviews findings, gives instructions, you apply fixes and update reports

---

## Workflow Overview

For a detailed visual workflow diagram, see: [mra-workflow.mermaid](../mra-workflow.mermaid)

**Key Decision Points:**

- **Phase 1 (Read-Only)**: Document EVERYTHING, fix NOTHING
- **Phase 2 (Human-Directed)**: Fix according to user instructions only

---

## PHASE 1: Review & Documentation (Read-Only)

### Critical Rules

✅ **ALLOWED:** Read files, analyze content, create/update `.mra/` directory with findings

❌ **FORBIDDEN:** Modify any source files, fix issues, change content

---

### Step 1: Confirm and Clarify

**First response to user:**

```
I'll perform a comprehensive editorial review of your repository's markdown files.

PHASE 1: REVIEW & DOCUMENTATION (Read-Only)
I will:
1. Create .mra/ directory with organized findings
2. Review each .md file systematically
3. Document all issues and observations (NO fixes applied)
4. Provide a comprehensive summary report

PHASE 2: RESOLUTION & IMPLEMENTATION (After your review)
You will:
1. Review the findings (easy navigation, one file per reviewed file)
2. Give me instructions on what to fix
3. I'll apply fixes according to your instructions
4. Update the reports with resolutions

Scanning repository for markdown files...
```

**Scan for files** using `glob_file_search` with pattern `**/*.md` (or alternative method - see [Reference: File Discovery](reference.md#file-discovery))

**List files alphabetically:**

```
Found [X] markdown files:
- README.md
- docs/guide.md
- appendices/appendix-a.md
[...etc...]

Shall I proceed with reviewing all [X] files?
```

**User confirms** → Proceed to Step 2

**User specifies subset** → Proceed with only those files

---

### Step 2: Create .mra/ Directory Structure

Create the following structure:

```
.mra/
├── 00-SUMMARY.md           # Overview, statistics, cohesion analysis
└── findings/               # Mirror of repository structure with reviews
```

**Create** `/.mra/00-SUMMARY.md` with initial structure (see [Reference: Summary Template](reference.md#summary-template))

**Create** `/.mra/findings/` directory. Individual review files will be created here during Step 3, mirroring the original repository structure.

**Directory structure examples:**

- `README.md` → `.mra/findings/README.md`
- `docs/guide.md` → `.mra/findings/docs/guide.md`
- `acceptance-test/dsl/utils/README.md` → `.mra/findings/acceptance-test/dsl/utils/README.md`

This nested structure makes navigation intuitive and directly maps to your project organization.

---

### Step 3: Review Files (Read-Only)

**🔒 CRITICAL: NO FIXES ALLOWED IN PHASE 1**

**For EACH file:**

1. **Create findings file** `.mra/findings/[original-path].md` with initial status, creating subdirectories as needed to mirror repository structure (see [Reference: File Entry Template](reference.md#file-entry-template))

2. **Review the file** checking:

   | Category                | What to Check                                                                                                                         |
   | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
   | **Grammar & Mechanics** | Subject-verb agreement, tense consistency, pronoun agreement, sentence fragments, run-ons, comma splices, punctuation, capitalization |
   | **Spelling**            | Typos, misspellings, consistent spelling variants (e.g., "behavior" vs "behaviour")                                                   |
   | **Links**               | Internal anchors, relative paths, external URLs, images (see [Reference: Link Verification](reference.md#link-verification))          |
   | **Terminology**         | Key terms used consistently, capitalization consistency, acronyms defined on first use                                                |
   | **Structure**           | Heading hierarchy (no skipped levels), TOC matches headings, no duplicate headings at same level                                      |
   | **Formatting**          | List styles consistent, code block language hints, bold/italic patterns, table formatting                                             |

3. **🔒 DO NOT FIX ANYTHING** - Only document findings

4. **Categorize each issue:**

   | Category                  | When to Use                                                                                                         |
   | ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
   | **Can Fix Automatically** | Clear errors with obvious corrections (grammar, broken internal links where target is obvious, missing punctuation) |
   | **Needs Human Judgment**  | Multiple valid corrections exist, terminology choice impacts other docs, style preferences involved                 |
   | **Requires Discussion**   | Significant rewrite needed, affects meaning/intent, cross-file implications, user preference unknown                |

5. **Document issues vs observations:**

   **Issues** (clear errors):

   - Grammar/spelling errors
   - Broken links
   - Inconsistent terminology
   - Structural problems (wrong heading levels)

   **Observations** (not errors, need human consideration):

   - Content reorganization suggestions
   - Tone shifts between sections
   - Potential duplication
   - Missing expected content
   - Format differences from similar docs

6. **Update findings file** with complete review (see [Reference: Issue Format](reference.md#issue-format) and [Observation Format](reference.md#observation-format))

7. **Update `.mra/00-SUMMARY.md` header:**

   ```markdown
   **Files Completed:** X/Y
   **Issues Found:** [total]
   **Observations:** [total]
   ```

8. **Report to user:** `✅ Completed [filename] - Found X issues (not fixed), Y observations. See .mra/findings/[original-path].md`

9. **Every 10 files, pause:** "Completed 10 files. Continue with next batch? (Y/n)" (continue automatically after 30 seconds if no response)

10. **Continue to next file**

---

### Step 4: Generate Final Summary

After ALL files reviewed, update `.mra/00-SUMMARY.md` with:

- **Statistics tables** (total issues, breakdown by severity, breakdown by type)
- **Repository Cohesion Analysis** (terminology consistency, tone & voice, structural consistency, cross-reference quality, code example consistency)
- **Overall Cohesion Assessment** with grade and key strengths/areas for improvement
- **Recommendations** (🔴 Must Fix / 🟡 Should Fix / 🟢 Nice to Have)
- **Release Readiness** (✅ READY NOW / 🟡 READY WITH FIXES / 🔴 NOT READY)

See [Reference: Summary Structure](reference.md#summary-structure) for complete template.

---

### Step 5: Present Report to User

```
✅ Phase 1 Complete: Review & Documentation

📊 Summary:
- Reviewed: X files
- Issues found: Y (none fixed yet)
- Observations flagged: Z
- Assessment: [READY/READY WITH FIXES/NOT READY]

📁 Findings directory: .mra/
📄 Summary report: .mra/00-SUMMARY.md
📄 Individual reviews: .mra/findings/ (mirrors repository structure)

[If issues found:]
📋 Found Issues Breakdown:
- Can fix automatically: [#] issues
- Need human judgment: [#] issues
- Require discussion: [#] issues

[If observations exist:]
💭 Observations: [#] items flagged for your consideration

---

READY FOR PHASE 2: Resolution & Implementation

You can now review the report and give me instructions on what to fix.

Examples:
- "Fix all automatic issues"
- "Fix only critical issues"
- "Fix grammar in README.md"
- "Fix issue #3 in docs/guide.md"
- "Fix everything"
- Or any other specific instructions

What would you like me to do?
```

---

## PHASE 2: Resolution & Implementation (Human-Directed)

### Critical Rules

✅ **ALLOWED:** Modify source files according to user instructions, update `.mra/` findings

❌ **FORBIDDEN:** Fix anything not instructed by user, make assumptions about scope

---

### Interpreting User Instructions

**Parse instruction to determine:**

1. **Scope:**

   - "all" or "everything" → ALL_FILES
   - Mentions specific file(s) → SPECIFIED_FILES
   - Mentions specific issue number(s) → SPECIFIC_ISSUES
   - Unclear → Ask user for clarification

2. **Filter:**
   - Contains severity keyword (critical/medium/low) → Filter by severity
   - Contains type keyword (grammar/link/consistency/structure) → Filter by type
   - Contains category keyword (automatic/judgment/discussion) → Filter by category
   - Contains "except" or "skip" → Apply exclusion
   - Otherwise → No filter (all issues in scope)

**Example interpretations:**

| User Instruction                  | Scope         | Filter               | Result                             |
| --------------------------------- | ------------- | -------------------- | ---------------------------------- |
| "Fix all automatic issues"        | ALL_FILES     | Category: automatic  | All "Can Fix Automatically" issues |
| "Fix critical issues"             | ALL_FILES     | Severity: critical   | All 🔴 Critical issues             |
| "Fix issue #2 in README.md"       | README.md     | Issue #2             | Only that specific issue           |
| "Fix grammar in all files"        | ALL_FILES     | Type: grammar        | All grammar issues                 |
| "Fix everything in docs/guide.md" | docs/guide.md | None                 | All issues in that file            |
| "Fix all except terminology"      | ALL_FILES     | Exclude: terminology | All non-terminology issues         |

**Confirm if ambiguous or large (>20 issues)**

---

### Applying Fixes

For each issue to be fixed:

1. Read the source file
2. Locate exact content (using line numbers and "Current Content" from report)
3. Apply the fix (using "Suggested Fix" from report)
4. Verify the fix worked
5. Update the report (see next section)

**If fix fails or is unclear:**

- Stop and report: "Cannot apply fix for issue #X in [file]: [reason]"
- Wait for user guidance
- Do not proceed until resolved

---

### Report Update Rules (STRICT)

After applying each fix, update `.mra/` files in this order:

**Rule 1: Update Issue Status**

In `.mra/findings/[original-path].md`:

```markdown
**Status:** 📋 Documented → ✅ Fixed
```

Add resolution section:

```markdown
**Resolution Date:** YYYY-MM-DD HH:MM
**Action Taken:** [Describe exactly what was changed]
**Files Modified:** [List files]

**Applied Fix:**
```

[Show the new content]

```

```

**Rule 2: Update File Entry Counters**

In `.mra/findings/[original-path].md` header:

```markdown
**Issues Fixed:** 0 → [increment by number of fixes]
```

**Rule 3: Update Summary Header**

In `.mra/00-SUMMARY.md` top:

```markdown
**Issues Fixed:** 0 → [increment]
**Status:** → 🟡 PHASE 2 IN PROGRESS
**Phase:** → 2 - Resolution & Implementation
```

**Rule 4: Update Summary Statistics**

Update statistics tables in `.mra/00-SUMMARY.md` to reflect new counts.

**Rule 5: Add Resolution Log Entry**

Add to end of `.mra/00-SUMMARY.md`:

```markdown
## Resolution Log

### YYYY-MM-DD HH:MM - Batch Fix #1

**User Instruction:** "[exact user instruction]"
**Issues Addressed:** [#]
**Issues Successfully Fixed:** [#]
**Issues Failed:** [#]

**Fixed Issues:**

- Issue #X in [file]: [brief description]
- Issue #Y in [file]: [brief description]

**Failed Issues:** (if any)

- Issue #Z in [file]: [reason] - [what needs to happen]

**Files Modified:**

- [file 1]
- [file 2]

---
```

**Rule 6: NEVER delete or renumber original issues** - preserve complete history.

---

### Report Back to User

After completing fix batch:

```
✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: X
- Files modified: Y
- Failed fixes: Z (if any)

📁 Updated findings: .mra/
📄 Updated files:
   - .mra/00-SUMMARY.md
   - .mra/findings/[affected files].md

[If all succeeded:]
✅ All fixes applied successfully!

[If some failed:]
⚠️ Some fixes need attention:
- [list failed fixes with reasons]

[If issues remain:]
📋 Remaining Issues:
- Total: [#]
- Critical: [#]
- Medium: [#]
- Low: [#]

Would you like me to:
- Fix more issues?
- Review specific files?
- Something else?
```

---

## Decision Rules

### What to Document as Issue vs Observation

**Document as Issue:**

- Clear grammar/spelling error (subject-verb disagreement, wrong tense, typo)
- Broken internal link
- Inconsistent terminology (one doc uses "Todo", another uses "TODO")
- Wrong heading level (skipped levels in hierarchy)
- Missing punctuation

**Document as Observation:**

- Content could be reorganized but current structure is functional
- Tone shifts between sections but not incorrect
- Potential duplication between documents
- Examples could be clearer
- Links work but might point to better targets

**Don't Document:**

- Personal preferences with no rationale
- Vague "could be better" statements without specifics

### Severity Assignment

| Severity        | Use When                                                                                                          |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| 🔴 **Critical** | Broken links to key navigation, major factual errors, severe grammar obscuring meaning, missing critical sections |
| 🟡 **Medium**   | Minor grammar issues, inconsistent terminology, formatting issues, minor structural problems                      |
| 🟢 **Low**      | Stylistic suggestions, optional improvements, nice-to-have additions, minor polish items                          |

### When to Ask User for Clarification (Phase 2)

**Ask when:**

- Instruction scope is ambiguous
- Instruction would fix >50 issues
- Multiple interpretations possible
- Suggested fix in report is unclear
- Fix would affect multiple related issues

**Proceed without asking when:**

- Instruction is clear and specific
- Scope is <20 issues
- Suggested fixes are explicit
- No risk of unintended changes

---

## Essential Guidelines

### Phase 1: DO

✅ Document EVERYTHING you find (even small typos)

✅ Be specific (include line numbers)

✅ Categorize issues correctly (Can Fix Auto / Needs Judgment / Requires Discussion)

✅ Provide clear suggested fixes for automatic issues

✅ Phrase observations as questions, not directives

✅ Update `.mra/` after EACH file

✅ Check links by verifying paths/anchors exist

✅ Look for consistency across entire repository

### Phase 1: DON'T

❌ Fix anything (even obvious errors)

❌ Modify any source files

❌ Report subjective preferences as issues (use observations)

❌ Skip checking links because "they look ok"

❌ Make assumptions about author's intent

### Phase 2: DO

✅ Follow user instructions precisely

✅ Ask for clarification when ambiguous

✅ Apply fixes exactly as documented in report

✅ Update report after every fix batch

✅ Track all changes in Resolution Log

✅ Report failures immediately

✅ Preserve all original information in report

### Phase 2: DON'T

❌ Fix anything not instructed by user

❌ Make assumptions about scope

❌ Apply fixes that differ from report suggestions

❌ Delete or modify original issue entries

❌ Renumber issues after fixing

❌ Skip report updates

❌ Continue if a fix fails

---

## Consistency Checking

Track these patterns across ALL files and note in individual entries AND final summary:

1. **Key terminology** - Are main concepts named consistently?
2. **Tone** - Formal? Conversational? Technical? Consistent across files?
3. **Structure patterns** - Do similar docs use similar formats?
4. **Example domains** - Do examples reference consistent concepts?
5. **Emoji usage** - If used, are meanings consistent?
6. **Code style** - Indentation, naming, patterns consistent in examples?
7. **Link style** - Relative vs absolute, with/without extensions?

---

## See Also

- **[Reference Guide](reference.md)** - Templates, schemas, formatting standards, technical implementation
- **[Examples](examples.md)** - Complete Phase 1 and Phase 2 example flows, edge cases, FAQs
