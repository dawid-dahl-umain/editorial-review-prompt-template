---
description: Quick editorial review of a single markdown file using MRA criteria
---

# Quick File Review Command

Review the current markdown file or user-specified file using the editorial criteria from `instructions/review-criteria.md`.

## Instructions

1. **Read the target file** (current file or user-specified)
2. **Apply review criteria** from the six core categories:

   - Grammar & Mechanics
   - Spelling
   - Links (internal anchors, relative paths, external URLs, images)
   - Terminology
   - Structure (heading hierarchy, logical flow)
   - Formatting (list styles, code blocks, consistency)

3. **Present findings** in a concise inline report:

   ```markdown
   ## Review Results: [filename]

   ### Issues Found: X

   #### 🔴 Critical (count)

   - Line X: [issue description] → Suggested fix: [suggestion]

   #### 🟡 Medium (count)

   - Line X: [issue description] → Suggested fix: [suggestion]

   #### 🟢 Low (count)

   - Line X: [issue description] → Suggested fix: [suggestion]

   ### Observations: Y

   - [Observation with context and question]

   ### Summary

   - Total lines: X
   - Issues by category: Grammar (X), Spelling (X), Links (X), etc.
   - Overall quality: [assessment]
   ```

4. **Do NOT create `.mra/` directory** - this is a quick review, not the full MRA workflow
5. **Do NOT make changes** - only document findings
6. **If user says "fix" after review** - apply the fixes directly to the file

## Severity Levels

- 🔴 **Critical**: Broken links, major grammar obscuring meaning, severe structural issues
- 🟡 **Medium**: Minor grammar, inconsistent terminology, formatting issues
- 🟢 **Low**: Stylistic suggestions, optional improvements, minor polish

## Link Verification

- **Internal anchors**: Verify heading exists in target file
- **Relative paths**: Calculate absolute path and verify file exists
- **External URLs**: Check structure looks valid (don't test HTTP status)
- **Images**: Same as above based on local/remote

## Notes

- Focus on clear errors and actionable improvements
- Include line numbers for all issues
- Provide specific suggested fixes, not vague observations
- If checking links to other files, read those files to verify
- Keep report concise - this is a quick review, not exhaustive documentation

## When to Use This vs Full MRA

- **Use this command** when: Quick review of 1-2 files, immediate feedback needed, ad-hoc quality check
- **Use full MRA workflow** when: Reviewing entire repository, need systematic documentation, want Phase 1/Phase 2 separation, need cohesion analysis across files
