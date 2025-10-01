# 📚 MRA Reference Guide

Templates, schemas, formatting standards, and technical implementation details.

---

## Templates

### Summary Template

Initial structure for `/.mra/00-SUMMARY.md`:

```markdown
# 📋 Markdown Review Assistant - Summary

- **Review Date:** YYYY-MM-DD
- **Status:** 🟡 PHASE 1 IN PROGRESS
- **Phase:** 1 - Review & Documentation (Read-Only)
- **Files Completed:** 0/[TOTAL]
- **Issues Found:** 0
- **Issues Fixed:** 0
- **Observations:** 0

## Legend

### Issue Types

- 🔴 **Critical**: Broken links, factual errors, major grammar issues
- 🟡 **Medium**: Minor grammar, inconsistent terminology, style issues
- 🟢 **Low**: Suggestions, optional improvements

### Issue Status

- 📋 **Documented**: Issue found and documented in Phase 1 (not yet fixed)
- ✅ **Fixed**: Issue resolved in Phase 2
- 📝 **Acknowledged**: User reviewed but chose not to fix
- ⏸️ **Deferred**: To be addressed later

### Observations

- 💭 **Observation**: Not an error, but something worth flagging for human consideration
- Potential improvements requiring judgment
- Questions about content/structure/format
- Subjective suggestions beyond mechanical fixes
- These are NOT errors - only documented for user review

## Files Reviewed

_Individual findings are in `.mra/findings/` directory._
_Structure mirrors your repository for intuitive navigation._

**Examples:**

- `README.md` → `.mra/findings/README.md`
- `docs/guide.md` → `.mra/findings/docs/guide.md`
- `src/components/Button.tsx.md` → `.mra/findings/src/components/Button.tsx.md`

## Summary

_Summary statistics and analysis will be generated here after all files are completed._
```

---

### File Entry Template

Initial structure for `.mra/findings/[original-path].md`:

```markdown
# 📄 Review: path/to/file.md

- **Review Date:** YYYY-MM-DD HH:MM
- **Status:** 🟡 REVIEWING
- **Issues Found:** 0
- **Issues Fixed:** 0
- **Observations:** 0

_Review in progress..._
```

After review is complete:

```markdown
# 📄 Review: path/to/file.md

- **Review Date:** YYYY-MM-DD HH:MM
- **Status:** ✅ COMPLETED
- **Issues Found:** [#]
- **Issues Fixed:** 0
- **Observations:** [#]

#### Issues

[IF NO ISSUES:]
✅ **No issues found**

**Review Summary:**

- ✅ Grammar and spelling correct
- ✅ All links working
- ✅ Consistent with repository standards
- ✅ Structure clear and logical

[IF ISSUES FOUND, list each one - see Issue Format below]

#### Observations

[IF NO OBSERVATIONS:]
_No observations - file meets all standards._

[IF OBSERVATIONS EXIST - see Observation Format below]

#### Review Notes

[Optional: overall quality assessment, relation to other files, patterns noticed]

---
```

---

### Issue Format

```markdown
##### Issue #1: [Brief Title]

- **Lines:** [specific line numbers]
- **Severity:** 🔴/🟡/🟢
- **Type:** Grammar | Link | Consistency | Structure | Other
- **Status:** 📋 Documented
- **Category:** [Choose: Can Fix Automatically | Needs Human Judgment | Requires Discussion]

**Description:**
[Clear explanation of the problem]

**Current Content:**
```

[Show the problematic content exactly as it appears]

```

**Suggested Fix:**
[IF "Can Fix Automatically": Show exact replacement]
[IF "Needs Human Judgment": Explain options]
[IF "Requires Discussion": Explain what needs clarification]

**Rationale:**
[Why this is an issue and why the suggested fix is appropriate]

---
```

After fixing in Phase 2, add:

```markdown
- **Resolution Date:** YYYY-MM-DD HH:MM
- **Action Taken:** [Describe exactly what was changed]
- **Files Modified:** [List files that were changed]

**Applied Fix:**
```

[Show the new content that replaced the old content]

```

```

---

### Observation Format

```markdown
##### Observation #1: [Brief Title]

- **Lines:** [specific line numbers or "General"]
- **Category:** Content | Structure | Format | Tone | Consistency | Other

**What I Noticed:**
[Clear description of what you've observed]

**Context:**
[Provide relevant context: what's there now, why it caught your attention]

**Consideration:**
[Present options or questions for the user to consider]

**Potential Impact:**
[IF changed: what would improve]
[IF unchanged: why current approach might be intentional]

---
```

---

### Summary Structure

After all files reviewed, add to `.mra/00-SUMMARY.md`:

```markdown
## Summary

**Review Completed:** YYYY-MM-DD
**Status:** ✅ PHASE 1 COMPLETE
**Phase:** 1 - Review & Documentation
**Total Files Reviewed:** [#]

### Statistics

| Metric                      | Count |
| --------------------------- | ----: |
| **Total Issues Found**      |   [#] |
| **Issues Fixed**            |     0 |
| **Observations Flagged**    |   [#] |
| **Files With No Issues**    |   [#] |
| **Files With Observations** |   [#] |

### Issue Breakdown by Severity

| Severity    | Count | Can Fix Auto | Needs Judgment | Requires Discussion |
| ----------- | ----: | -----------: | -------------: | ------------------: |
| 🔴 Critical |   [#] |          [#] |            [#] |                 [#] |
| 🟡 Medium   |   [#] |          [#] |            [#] |                 [#] |
| 🟢 Low      |   [#] |          [#] |            [#] |                 [#] |

### Issue Breakdown by Type

| Type                     | Found |
| ------------------------ | ----: |
| Grammar/Spelling         |   [#] |
| Broken Links             |   [#] |
| Inconsistent Terminology |   [#] |
| Structural Issues        |   [#] |
| Other                    |   [#] |

### Repository Cohesion Analysis

**Terminology Consistency:**
[✅ Excellent | ✅ Good | 🟡 Some issues | 🔴 Significant issues]

Details:

- [List key terms and whether they're used consistently]
- [Note any problematic variations]

**Tone & Voice:**
[✅ Unified | 🟡 Mostly consistent | 🔴 Inconsistent]

Details:

- [Describe the overall tone]
- [Note any jarring shifts between documents]

**Structural Consistency:**
[✅ Well-organized | 🟡 Could improve | 🔴 Needs work]

Details:

- [Comment on similar document patterns]
- [Note where structure helps or hinders]

**Cross-Reference Quality:**
[✅ Excellent | ✅ Good | 🟡 Some broken | 🔴 Many broken]

Details:

- [Note navigation between documents]
- [Comment on link accuracy]

**Code Example Consistency:**
[✅ Consistent | 🟡 Mostly consistent | 🔴 Inconsistent]

Details:

- [Comment on code style across examples]
- [Note if examples use same domain/concepts]

### Overall Cohesion Assessment

**Grade:** [A+ | A | B | C | D | F]

[Write 2-3 paragraphs describing how well the repository works as a unified whole]

Key strengths:

- [Strength 1]
- [Strength 2]

Areas for improvement:

- [Area 1]
- [Area 2]

### Recommendations

#### 🔴 Must Fix (Before Release)

[List ONLY issues that block release, or state "None"]

1. [Critical blocker with file reference]
2. [Critical blocker with file reference]

#### 🟡 Should Fix (High Priority)

[List important but non-blocking issues, or state "None"]

1. [Important issue with file reference]
2. [Important issue with file reference]

#### 🟢 Nice to Have (Low Priority)

[List optional improvements, or state "None"]

1. [Optional improvement with file reference]
2. [Optional improvement with file reference]

### Files Requiring Attention

[IF any files have issues:]

| File   | Issues | Priority | Quick Summary      |
| ------ | -----: | -------- | ------------------ |
| [path] |    [#] | 🔴/🟡/🟢 | [What needs doing] |

[IF no files have issues:]
✅ All files reviewed - no issues found!

### Release Readiness

**Status:** [✅ READY NOW | 🟡 READY WITH FIXES | 🔴 NOT READY]

**Assessment:**
[2-3 sentences explaining the status with specific evidence]

**Blocking Issues:** [#]
[List specific blockers with file references, or state "None - ready to release"]

**Recommended Action:**
[Clear next step: "Ship it!" or "Fix X and Y first, then ready" or "Significant work needed"]

---

## Next Steps: Phase 2

**You can now review this report and decide what to fix.**

You can give me instructions like:

- "Fix all automatic issues" (I'll fix everything marked "Can Fix Automatically")
- "Fix only critical issues" (I'll fix all 🔴 Critical issues)
- "Fix issue #2 in README.md" (I'll fix that specific issue)
- "Fix all grammar issues across all files" (I'll fix all grammar issues)
- Or any other specific instructions you prefer

I'll apply the fixes and update this report with what was done.

---

_Editorial Review Phase 1 Completed on YYYY-MM-DD_
```

---

## Formatting Standards (Schema)

### Dates & Times

- **Date:** `YYYY-MM-DD` (e.g., `2025-10-01`)
- **Time:** `HH:MM` 24-hour (e.g., `14:30`)
- **DateTime:** `YYYY-MM-DD HH:MM`

### Status Indicators

Format: `[Emoji] [TEXT IN CAPS]`

- ✅ `🟡 IN PROGRESS`
- ✅ `✅ COMPLETED`
- ✅ `⏸️ DEFERRED`
- ❌ NOT: `In Progress 🟡` or `Completed` or `✅ completed`

**Phase-specific:**

- Phase 1: `🟡 PHASE 1 IN PROGRESS` → `✅ PHASE 1 COMPLETE`
- Phase 2: `🟡 PHASE 2 IN PROGRESS` → `✅ PHASE 2 COMPLETE`

### Issue Status

Format: `[Emoji] [Text in Title Case]`

- Phase 1: `📋 Documented`
- Phase 2: `✅ Fixed` | `📝 Acknowledged` | `⏸️ Deferred`

### Severity Indicators

Format: `[Emoji] [Text in Title Case]`

- ✅ `🔴 Critical`
- ✅ `🟡 Medium`
- ✅ `🟢 Low`
- ❌ NOT: `Critical 🔴` or `🔴 CRITICAL`

### Numbers

- **Zero values:** Use `0` (not empty or `None`)
- **Placeholders:** Use `[#]`
- **Actual values:** Plain numbers (e.g., `42` not `42 issues`)

### File Paths

- **Format:** Relative from repository root, forward slashes
- **Example:** `appendices/appendix-a/file.md`
- ❌ NOT: `./appendices/appendix-a/file.md` or `\appendices\`

### Lists

- **Unordered:** `-` (hyphen), one space after
- **Ordered:** `1.` `2.` etc., one space after
- **Checkboxes:** `[ ]` unchecked, `[x]` checked

### Headings

- **H1:** `#` (document title only)
- **H2:** `##` (major sections)
- **H3:** `###` (file entries)
- **H4:** `####` (subsections within files)
- **H5:** `#####` (individual issues)
- **Format:** One space after `#` symbols

### Code Blocks

- Fenced with triple backticks: ` ``` `
- Language hint when applicable: ` ```markdown `
- No language hint for plain text: ` ``` `

### Tables

- **Header separator:** `|---|---|---|`
- **Alignment:** Left-align text, right-align numbers (using `--:`)
- **Spacing:** One space padding inside each cell

Example:

```markdown
| Column 1 | Column 2 | Count |
| -------- | -------- | ----: |
| Text     | Text     |    42 |
```

### Horizontal Rules

- **Format:** `---` (three hyphens) on its own line
- **Spacing:** One blank line before and after

### Emphasis

- **Bold:** `**text**` (not `__text__`)
- **Italic:** `_text_` (not `*text*`)
- **Inline code:** `` `text` ``

### Issue Numbering

- **Format:** `Issue #1:` `Issue #2:` etc.
- **Sequential:** Start at 1 for each file
- **Persistent:** Don't renumber if issues are fixed

---

## Technical Implementation

### File Discovery

**Option 1 (Preferred):** Use `glob_file_search` tool with pattern `**/*.md`

**Option 2:** Use `list_dir` tool recursively and filter for `.md` files

**Option 3:** Ask user to provide list of markdown files

**Review Order:** Alphabetically by full path (e.g., `README.md` before `docs/guide.md` before `docs/setup.md`)

### Directory Structure for Findings

Create nested directories within `.mra/findings/` that mirror the repository structure:

- `README.md` → `.mra/findings/README.md`
- `docs/guide.md` → `.mra/findings/docs/guide.md` (create `docs/` subdirectory)
- `src/components/Button.tsx.md` → `.mra/findings/src/components/Button.tsx.md` (create `src/components/` subdirectories)

This provides intuitive navigation that directly maps to your project organization.

### Link Verification

**Internal Anchors** (`#heading-id`):

- Read target file
- Search for heading (convert to lowercase, replace spaces with hyphens)
- Verify heading exists

**Relative Paths** (`../other/file.md`):

- Calculate absolute path from current file location
- Verify target file exists (use `read_file` to check)
- If file doesn't exist → 🔴 Critical broken link

**External URLs** (`https://example.com`):

- Check URL structure looks valid (has protocol, domain)
- Don't test HTTP status (slow/unreliable)
- If obviously malformed → 🟡 Medium issue

**Image Links:**

- Same as relative paths if local
- Same as external URLs if remote

### Document Update Pattern

**Phase 1 - After reviewing each file:**

1. Create/update `.mra/findings/[original-path].md` with complete findings (create subdirectories as needed)
2. Update `.mra/00-SUMMARY.md` header: `**Files Completed:** [increment]`
3. Update `.mra/00-SUMMARY.md` header: `**Issues Found:** [add new issues]`
4. Update `.mra/00-SUMMARY.md` header: `**Observations:** [add new observations]`
5. Report to user with path to findings file

**Phase 2 - After applying each fix batch:**

1. Update issue status in `.mra/findings/[original-path].md`: `📋 Documented` → `✅ Fixed`
2. Add resolution section to each issue
3. Update file header in `.mra/findings/[original-path].md`: `**Issues Fixed:** [increment]`
4. Update `.mra/00-SUMMARY.md` header: `**Issues Fixed:** [increment]`
5. Update summary statistics in `.mra/00-SUMMARY.md`
6. Add entry to Resolution Log in `.mra/00-SUMMARY.md`
7. Report to user with paths to updated files

### Progress Reporting

**Phase 1 - After each file:**

```
✅ Completed [filename] - Found X issues (not fixed), Y observations
   📄 Review saved to: .mra/findings/[original-path].md
```

**Every 10 files:**

```
Completed 10 files. Continue with next batch? (Y/n)
```

If user doesn't respond in 30 seconds, continue automatically (they can interrupt if needed).

**Phase 2 - After each fix batch:**

```
✅ Applied fixes to [X] issues in [Y] files
   📄 Updated: .mra/findings/[affected-files].md and .mra/00-SUMMARY.md
```

### Tool Availability Handling

If you lack certain tools, adapt:

- No `glob_file_search` → Ask user for file list
- No `search_replace` → Recreate entire document
- No `read_file` → Ask user if link targets exist
- Limited output tokens → Batch files in groups

Always work within your tool constraints. Don't fail because a tool is missing.

---

## Verification Checklist

Before finalizing any `.mra/` document, verify:

### Schema Compliance

- [ ] All dates use `YYYY-MM-DD` format
- [ ] All times use `HH:MM` 24-hour format
- [ ] Status indicators follow `[Emoji] [CAPS]` format
- [ ] Issue status follows correct format
- [ ] Severity indicators follow `[Emoji] [Title Case]` format
- [ ] File paths are relative, forward slashes, no `./` prefix
- [ ] Lists use correct format
- [ ] Headings have correct level and spacing
- [ ] Tables properly formatted
- [ ] Emphasis uses correct syntax

### Phase 1 Content

- [ ] Document has title and metadata
- [ ] Every issue has all required fields (lines, severity, type, status, category, description, current content, suggested fix, rationale)
- [ ] Every issue is categorized (Can Fix Auto / Needs Judgment / Requires Discussion)
- [ ] Observations have all required fields
- [ ] "Issues Fixed" counter = 0 in Phase 1
- [ ] Summary has statistics, cohesion analysis, recommendations, release readiness

### Phase 2 Content

- [ ] Fixed issues have status "✅ Fixed"
- [ ] Each fixed issue has resolution section (date, action, files modified, applied fix)
- [ ] Document header "Issues Fixed" counter matches actual fixed count
- [ ] Summary statistics updated
- [ ] Resolution Log exists with entries for each fix batch

### Consistency

- [ ] Issue numbering sequential within each file (starts at #1)
- [ ] Counters in header match sum of individual entries
- [ ] Issue numbers NOT renumbered (stay consistent even when fixed)
- [ ] No duplicate file entries
