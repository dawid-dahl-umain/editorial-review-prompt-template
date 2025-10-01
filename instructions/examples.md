# 📖 MRA Examples & Edge Cases

Complete example flows showing Phase 1 and Phase 2 in action, plus edge cases and FAQs.

---

## Complete Example Flow

### Phase 1 Example

**User:** "Review all markdown files in this repository"

**AI Response 1:**

```
I'll perform a comprehensive editorial review of your repository's markdown files.

PHASE 1: REVIEW & DOCUMENTATION (Read-Only)
I will:
1. Create .mra/ directory with organized findings
2. Review each file systematically
3. Document all issues and observations (NO fixes applied)
4. Provide a comprehensive summary report

PHASE 2: RESOLUTION & IMPLEMENTATION (After your review)
You will review the findings and give me instructions on what to fix.

Scanning repository...

Found 22 markdown files:
- README.md
- docs/guide.md
- appendices/appendix-a.md
[...etc...]

Shall I proceed with reviewing all 22 files?
```

**User:** "Yes"

**AI Response 2:**

```
Creating .mra/ directory structure...
✅ Created .mra/00-SUMMARY.md

Starting Phase 1 review (read-only)...

📄 Reviewing README.md...
✅ Completed README.md - Found 2 issues (not fixed), 0 observations
   📄 Review saved to: .mra/findings/README.md

📄 Reviewing docs/guide.md...
✅ Completed docs/guide.md - Found 1 issue (not fixed), 2 observations
   📄 Review saved to: .mra/findings/docs/guide.md

[continues through all 22 files...]

✅ Phase 1 Complete: Review & Documentation

📊 Summary:
- Reviewed: 22 files
- Issues found: 8 (none fixed yet)
- Observations flagged: 5
- Assessment: READY WITH FIXES

📁 Findings directory: .mra/
📄 Summary report: .mra/00-SUMMARY.md
📄 Individual reviews: .mra/findings/ (mirrors repository structure)

📋 Found Issues Breakdown:
- Can fix automatically: 6 issues
- Need human judgment: 2 issues
- Require discussion: 0 issues

💭 Observations: 5 items flagged for your consideration

---

READY FOR PHASE 2: Resolution & Implementation

You can now review the report and give me instructions on what to fix.

What would you like me to do?
```

---

### Phase 2 Example: Broad Scope

**User:** "Fix all automatic issues"

**AI Response:**

```
Interpreting instruction: "Fix all automatic issues"
- Scope: All files
- Filter: Category = "Can Fix Automatically"
- Issues to fix: 6

Applying fixes...

✅ Fixed issue #1 in README.md (grammar)
✅ Fixed issue #2 in README.md (broken link)
✅ Fixed issue #1 in docs/guide.md (spelling)
✅ Fixed issue #3 in docs/guide.md (heading level)
✅ Fixed issue #1 in appendices/appendix-a.md (terminology)
✅ Fixed issue #2 in appendices/appendix-a.md (grammar)

Updating .mra/ reports...
✅ Updated .mra/findings/README.md
✅ Updated .mra/findings/docs/guide.md
✅ Updated .mra/findings/appendices/appendix-a.md
✅ Updated .mra/00-SUMMARY.md

✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: 6
- Files modified: 3
- Failed fixes: 0

📁 Updated findings: .mra/
📄 Updated summary: .mra/00-SUMMARY.md
📄 Updated file reviews:
   - .mra/findings/README.md
   - .mra/findings/docs/guide.md
   - .mra/findings/appendices/appendix-a.md

✅ All fixes applied successfully!

📋 Remaining Issues:
- Total: 2
- Critical: 0
- Medium: 2 (both "Need Human Judgment")
- Low: 0

Would you like me to:
- Fix the remaining 2 issues that need judgment?
- Review specific files?
- Something else?
```

---

### Phase 2 Example: Issues Requiring Judgment

**User:** "Fix remaining issues"

**AI Response:**

```
The 2 remaining issues are marked "Needs Human Judgment":

1. Issue #3 in docs/guide.md (Lines 45-50)
   - Type: Terminology
   - Description: Inconsistent use of "user story" vs "scenario"
   - Options:
     a) Change all to "user story"
     b) Change all to "scenario"
     c) Keep both (they mean different things)

2. Issue #4 in docs/guide.md (Lines 78-82)
   - Type: Structure
   - Description: Section could be split or kept as one
   - Options:
     a) Split into two sections
     b) Keep as one section

Which options would you like me to apply?
(e.g., "1a and 2b" or "1c and 2a")
```

**User:** "1a and 2a"

**AI Response:**

```
Applying your choices:
- Issue #3: Changing all to "user story" (option a)
- Issue #4: Splitting into two sections (option a)

✅ Fixed issue #3 in docs/guide.md (terminology → "user story")
✅ Fixed issue #4 in docs/guide.md (structure → split sections)

Updating .mra/ reports...
✅ Updated .mra/findings/docs/guide.md
✅ Updated .mra/00-SUMMARY.md

✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: 2 (Total: 8/8)
- Files modified: 1
- Failed fixes: 0

📁 Updated findings: .mra/
📄 Updated summary: .mra/00-SUMMARY.md
📄 Updated file review: .mra/findings/docs/guide.md

✅ All issues resolved!

📋 Remaining Issues: 0

🎉 All issues have been fixed!

💭 There are still 5 observations in the report for your consideration.
These are subjective suggestions, not errors.

Would you like to review the observations or is the review complete?
```

---

### Phase 2 Example: Narrow Scope

**User:** "Fix issue #2 in README.md"

**AI Response:**

```
Fixing issue #2 in README.md...

✅ Fixed issue #2 in README.md (broken link to docs/setup.md)

Updating .mra/ reports...
✅ Updated .mra/findings/README.md
✅ Updated .mra/00-SUMMARY.md

✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: 1
- Files modified: 1
- Failed fixes: 0

📁 Updated findings: .mra/
📄 Updated files:
   - .mra/findings/README.md
   - .mra/00-SUMMARY.md

✅ Fix applied successfully!

📋 Remaining Issues:
- Total: 7
- Critical: 1
- Medium: 4
- Low: 2

Would you like me to fix more issues?
```

---

### Phase 2 Example: Filter by Severity

**User:** "Fix all critical issues"

**AI Response:**

```
Interpreting instruction: "Fix all critical issues"
- Scope: All files
- Filter: Severity = Critical (🔴)
- Issues to fix: 3

Applying fixes...

✅ Fixed issue #1 in README.md (broken link)
✅ Fixed issue #2 in docs/guide.md (major grammar error)
✅ Fixed issue #1 in appendices/appendix-b.md (broken link)

Updating .mra/ reports...
✅ Updated .mra/findings/README.md
✅ Updated .mra/findings/docs/guide.md
✅ Updated .mra/findings/appendices/appendix-b.md
✅ Updated .mra/00-SUMMARY.md

✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: 3
- Files modified: 3
- Failed fixes: 0

✅ All critical issues resolved!

📋 Remaining Issues:
- Total: 5
- Critical: 0
- Medium: 4
- Low: 1

Repository is now in a release-ready state (no blocking issues).

Would you like me to fix the remaining medium/low priority issues?
```

---

### Phase 2 Example: Filter with Exclusion

**User:** "Fix all issues except terminology"

**AI Response:**

```
Interpreting instruction: "Fix all issues except terminology"
- Scope: All files
- Filter: Exclude Type = Terminology
- Issues to fix: 6 (excluding 2 terminology issues)

Applying fixes...

✅ Fixed issue #1 in README.md (grammar)
✅ Fixed issue #2 in README.md (broken link)
✅ Fixed issue #1 in docs/guide.md (spelling)
✅ Fixed issue #4 in docs/guide.md (structure)
✅ Fixed issue #1 in appendices/appendix-a.md (grammar)
✅ Fixed issue #3 in appendices/appendix-a.md (heading level)

Skipped 2 terminology issues as instructed.

Updating .mra/ reports...
✅ Updated .mra/findings/README.md
✅ Updated .mra/findings/docs/guide.md
✅ Updated .mra/findings/appendices/appendix-a.md
✅ Updated .mra/00-SUMMARY.md

✅ Phase 2: Fixes Applied

📊 Summary:
- Issues fixed: 6
- Files modified: 3
- Issues skipped: 2 (terminology)
- Failed fixes: 0

📋 Remaining Issues:
- Total: 2
- Type: Terminology (2)

The 2 remaining terminology issues may need discussion about
consistent naming conventions across the repository.

Would you like me to address the terminology issues?
```

---

## Example: Failed Fix

**User:** "Fix issue #5 in docs/advanced.md"

**AI Response:**

```
Attempting to fix issue #5 in docs/advanced.md...

⚠️ Cannot apply fix for issue #5 in docs/advanced.md

**Reason:** The content at line 142 has changed since the review.

**Expected content:**
```

The configuration file should be placed in the root directory.

```

**Actual content:**
```

The config file must be in the project root.

```

It appears the file was modified after the Phase 1 review.

**Options:**
1. Re-run Phase 1 review for this file only
2. Provide updated fix instructions for current content
3. Skip this issue

What would you like me to do?
```

---

## Edge Cases & FAQs

### Phase 1 (Review & Documentation)

**Q: What if the repository is huge (100+ files)?**

A: Pause after every 10 files:

```
Completed 10 files. Continue with next batch? (Y/n)
```

This prevents overwhelming output. If no response after 30 seconds, continue automatically.

---

**Q: What if files are in subfolders with complex structure?**

A: Review in alphabetical order by full path. The `.mra/findings/` structure mirrors the repository:

- `acceptance-test/dsl/utils/README.md` → `.mra/findings/acceptance-test/dsl/utils/README.md`

The nested directory structure makes navigation intuitive.

---

**Q: What if I find the same issue in many files?**

A: Document it in each file individually. In the summary, note:

```
**Pattern:** "Todo" vs "TODO" inconsistency found in 15 files.
See individual file reports for specific line numbers.
```

---

**Q: What if a file has dozens of issues?**

A: Document all of them. In Review Notes, add:

```
**Note:** This file requires significant attention. Consider major revision.
```

---

**Q: What if user interrupts the process?**

A: The `.mra/00-SUMMARY.md` shows progress with `**Files Completed:** 12/45`. User can ask you to resume:

```
User: "Continue the review"
AI: "Resuming from file #13 (docs/next-file.md)..."
```

---

**Q: What if there are non-.md files that might need review (like .mdx or .txt)?**

A: Stick to `.md` files unless user specifically requests others. In final summary, note:

```
**Scope Note:** Only `.md` files reviewed. Repository also contains:
- 3 `.mdx` files (docs/components/)
- 2 `.txt` files (notes/)

Consider reviewing these separately if needed.
```

---

**Q: Should I check external URLs for HTTP status?**

A: No. Only flag if URL structure is obviously broken:

- ✅ Valid: `https://example.com/path`
- ✅ Valid: `http://localhost:3000`
- 🟡 Flag: `htps://example.com` (typo in protocol)
- 🟡 Flag: `www.example.com` (missing protocol)

Don't actually test HTTP requests - too slow and unreliable (sites may be temporarily down).

---

**Q: How detailed should grammar checking be?**

A: Catch clear errors that impact clarity or correctness:

**Document as issues:**

- Subject-verb disagreement: "The files is complete"
- Wrong tense: "Yesterday we create the file"
- Typos: "recieve" → "receive"
- Missing punctuation affecting meaning

**Don't document:**

- Style preferences: "However," vs "However"
- Oxford comma choices (unless inconsistent)
- Passive vs active voice (unless it impacts clarity)

---

### Phase 2 (Resolution & Implementation)

**Q: User says "fix all issues" but some are marked "Requires Discussion" - what do I do?**

A: Interpret conservatively:

```
Interpreting "fix all issues" as "fix all issues I can without discussion"

Applying fixes to:
- Can Fix Automatically: 12 issues
- Needs Human Judgment (with clear suggestions): 3 issues

Skipping:
- Requires Discussion: 2 issues

Will report which issues need discussion after fixes complete.
```

Then after fixes:

```
✅ Fixed 15 issues.

⏸️ 2 issues require discussion before fixing:
- Issue #5 in docs/architecture.md: Significant restructure needed
- Issue #2 in README.md: Content may need product owner input

Would you like to discuss these, or should I skip them?
```

---

**Q: A suggested fix in the report doesn't make sense anymore - what do I do?**

A: Stop and report:

```
⚠️ Cannot apply fix for issue #3 in docs/guide.md

**Reason:** Suggested fix is unclear/incomplete

**Issue description:** "Inconsistent terminology: 'user story' vs 'scenario'"
**Suggested fix in report:** "Standardize terminology"
**Problem:** Report doesn't specify which term to use

Please clarify:
1. Change all to "user story"?
2. Change all to "scenario"?
3. Something else?
```

---

**Q: User says "fix issue #3" but multiple files have issue #3 - what do I do?**

A: Ask for clarification:

```
Multiple files have issue #3:
- README.md: Issue #3 (grammar on line 45)
- docs/guide.md: Issue #3 (broken link on line 120)
- appendices/appendix-a.md: Issue #3 (terminology on line 67)

Which file did you mean, or should I fix all of them?
```

---

**Q: I fixed an issue but it created a new problem - what do I do?**

A: Immediately report:

```
⚠️ Fix created new issue

Fixed: Issue #2 in README.md (changed "Todo" to "TODO")
Problem: This created inconsistency with docs/guide.md which uses "Todo"

Should I:
1. Revert the fix in README.md?
2. Apply the same fix to docs/guide.md?
3. Something else?
```

---

**Q: User asks to fix something that wasn't documented in Phase 1 - what do I do?**

A: Ask for guidance:

```
Issue not found in Phase 1 report.

You asked to: "Fix the typo on line 52 of README.md"

This wasn't documented during Phase 1 (possibly added after review,
or I missed it).

Would you like me to:
1. Fix it now and add to report as a new issue?
2. Re-run Phase 1 review for README.md first?
3. Something else?
```

---

**Q: After fixing issues, counters don't match - what do I do?**

A: Stop and audit:

```
⚠️ Counter mismatch detected

Expected: 6 issues fixed
Counted in reports: 5 issues marked "✅ Fixed"

Auditing...

Found discrepancy: Issue #3 in docs/guide.md marked as fixed
but resolution section is missing.

Correcting now...

✅ Audit complete. All counters now match.
```

---

**Q: User gives ambiguous instruction like "make it better" - what do I do?**

A: Ask for specifics:

```
Instruction unclear: "make it better"

Could you specify what you'd like me to do?

Based on the Phase 1 report, here are options:
- Fix all 8 documented issues?
- Fix only automatic issues (6 issues)?
- Fix only critical issues (2 issues)?
- Address specific observations?
- Something else?

Please provide more specific instructions.
```

---

## Example: Large Batch Confirmation

**User:** "Fix everything"

**AI Response:**

```
Interpreting instruction: "Fix everything"
- Scope: All files
- Filter: None
- Issues to fix: 47 issues across 15 files

⚠️ Large batch detected (>20 issues)

Breakdown:
- Can Fix Automatically: 38 issues
- Needs Human Judgment: 7 issues
- Requires Discussion: 2 issues

I can proceed with:
- Fix all 38 automatic issues now
- Present the 7 judgment issues for your decision
- Skip the 2 discussion issues (need clarification first)

Proceed with this plan? (Y/n)

Or specify different approach?
```

---

## Example: File Modified After Review

**User:** "Fix issue #1 in README.md"

**AI Response:**

```
⚠️ Content mismatch

Issue #1 documented at line 23:
**Expected:** "The files is complete"
**Actual:** "The files are complete"

This issue appears to have been fixed already (manually or by another process).

Updating report to reflect current state...
✅ Marked issue #1 as resolved (fixed externally)

Updated .mra/findings/README.md with note:
**Resolution Date:** 2025-10-01 15:45
**Action Taken:** Issue already resolved (fixed outside of MRA process)
**Status:** ✅ Fixed

No changes made to source file (already correct).
```

---

## Validation Example: Before/After

### ❌ WRONG Format (Phase 1)

```markdown
### appendices/file.md

Status: Completed ✅
**Issues Found**: 2
**Issues Fixed**: 1
Date: 10/01/2025 2:30pm

##### Critical Issue

Lines 45
Status: Fixed
```

### ✅ CORRECT Format (Phase 1)

```markdown
# 📄 Review: appendices/file.md

- **Review Date:** 2025-10-01 14:30
- **Status:** ✅ COMPLETED
- **Issues Found:** 2
- **Issues Fixed:** 0
- **Observations:** 1

##### Issue #1: Subject-Verb Disagreement

- **Lines:** 45
- **Severity:** 🔴 Critical
- **Type:** Grammar
- **Status:** 📋 Documented
- **Category:** Can Fix Automatically

**Description:**
Subject-verb disagreement

**Current Content:**
```

The files is complete

```

**Suggested Fix:**
```

The files are complete

```

**Rationale:**
"Files" is plural, requires plural verb "are" not singular "is"

#### Observations

##### Observation #1: Section Structure Differs from Similar Docs

- **Lines:** General
- **Category:** Structure

**What I Noticed:**
This document uses a different heading structure than other appendices.

**Context:**
Appendices A, B, and C all begin content at H3 level. This one starts at H2.

**Consideration:**
Should this be restructured to match the pattern, or is the difference intentional?

**Potential Impact:**
If changed: Better consistency across appendices
If unchanged: May indicate this appendix serves different purpose
```

### ✅ CORRECT Format (Phase 2 - After Fix)

```markdown
# 📄 Review: appendices/file.md

- **Review Date:** 2025-10-01 14:30
- **Status:** ✅ COMPLETED
- **Issues Found:** 2
- **Issues Fixed:** 1
- **Observations:** 1

##### Issue #1: Subject-Verb Disagreement

- **Lines:** 45
- **Severity:** 🔴 Critical
- **Type:** Grammar
- **Status:** ✅ Fixed
- **Category:** Can Fix Automatically

**Description:**
Subject-verb disagreement

**Current Content:**
```

The files is complete

```

**Suggested Fix:**
```

The files are complete

```

**Rationale:**
"Files" is plural, requires plural verb "are" not singular "is"

- **Resolution Date:** 2025-10-01 15:22
- **Action Taken:** Changed "is" to "are" on line 45
- **Files Modified:** appendices/file.md

**Applied Fix:**
```

The files are complete

```

```
