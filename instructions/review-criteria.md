# 📝 Editorial Review Criteria

This document defines what to check when reviewing markdown files. These criteria form the domain expertise of the Markdown Review Assistant.

---

## Overview

When reviewing a markdown file, examine six core categories. Each category has specific checks that help identify issues requiring correction or observations worth flagging.

---

## Review Categories

### Grammar & Mechanics

**What to check:**

- **Subject-verb agreement** - "The files is complete" → "The files are complete"
- **Tense consistency** - "Yesterday we create" → "Yesterday we created"
- **Pronoun agreement** - "Each user must set their password" (acceptable) vs "Each user must set his password" (dated)
- **Sentence fragments** - Incomplete sentences that don't express a complete thought
- **Run-on sentences** - Multiple independent clauses without proper punctuation
- **Comma splices** - Two independent clauses joined only by a comma
- **Punctuation** - Missing periods, incorrect comma usage, misused apostrophes
- **Capitalization** - Proper nouns, sentence starts, heading capitalization consistency

**Level of detail:**

Document clear errors that impact clarity or correctness:

✅ **Document as issues:**

- Subject-verb disagreement: "The files is complete"
- Wrong tense: "Yesterday we create the file"
- Missing punctuation affecting meaning

❌ **Don't document:**

- Style preferences: "However," vs "However"
- Oxford comma choices (unless inconsistent within the document)
- Passive vs active voice (unless it impacts clarity)

---

### Spelling

**What to check:**

- **Typos** - "recieve" → "receive", "seperate" → "separate"
- **Misspellings** - Words spelled incorrectly
- **Consistent spelling variants** - Choose one: "behavior" vs "behaviour", "color" vs "colour"
- **Technical terms** - Correct spelling of API names, product names, technical jargon

**Notes:**

- If a document uses British English consistently, that's fine
- Flag inconsistency: mixing "color" and "colour" in the same doc or repository
- Check that brand names and technical terms match official spelling (e.g., "GitHub" not "Github")

---

### Links

**What to check:**

- **Internal anchors** - `#heading-id` - Verify the heading exists
- **Relative paths** - `../other/file.md` - Verify the target file exists
- **External URLs** - `https://example.com` - Check URL structure is valid
- **Images** - Local paths and remote URLs
- **Link text clarity** - "Click here" vs descriptive link text

**How to verify:**

**Internal Anchors** (`#heading-id`):

- Read target file
- Search for heading (convert to lowercase, replace spaces with hyphens)
- Verify heading exists at expected level

**Relative Paths** (`../other/file.md`):

- Calculate absolute path from current file location
- Verify target file exists
- If file doesn't exist → 🔴 Critical broken link

**External URLs** (`https://example.com`):

- Check URL structure looks valid (has protocol, domain)
- Don't test HTTP status (too slow/unreliable)
- Flag if obviously malformed:
  - ✅ Valid: `https://example.com/path`
  - ✅ Valid: `http://localhost:3000`
  - 🟡 Flag: `htps://example.com` (typo in protocol)
  - 🟡 Flag: `www.example.com` (missing protocol)

**Image Links:**

- Same as relative paths if local
- Same as external URLs if remote

---

### Terminology

**What to check:**

- **Key terms used consistently** - "user story" vs "scenario" - pick one
- **Capitalization consistency** - "Todo" vs "TODO" vs "todo"
- **Acronyms defined on first use** - "DDD (Domain-Driven Design)" before using "DDD" alone
- **Product/brand names** - Consistent capitalization and spelling
- **Technical terms** - Consistent naming of concepts, classes, functions

**Cross-file consistency:**

This is where repository-wide analysis matters:

- Track key terminology across ALL files
- Note variations in the cohesion analysis
- Flag in individual file reports when inconsistent with rest of repository

**Example issue:**

```
File A uses "user story", File B uses "scenario", File C uses both.
```

Flag this in all three files with context about the inconsistency.

---

### Structure

**What to check:**

- **Heading hierarchy** - No skipped levels (H1 → H2 → H3, not H1 → H3)
- **Table of contents** - If present, matches actual headings
- **Duplicate headings** - No duplicate headings at the same level in same section
- **Logical flow** - Content organized in a clear progression
- **Section organization** - Related content grouped appropriately

**Heading hierarchy rules:**

✅ **Correct:**

```markdown
# Document Title

## Section

### Subsection

#### Detail
```

❌ **Incorrect (skipped H2):**

```markdown
# Document Title

### Subsection
```

**Notes:**

- One H1 per document (the title)
- Don't skip levels when going deeper
- Can jump up any number of levels (H4 → H2 is fine)

---

### Formatting

**What to check:**

- **List styles consistent** - All unordered lists use same marker (`-` or `*`)
- **Code block language hints** - ` ```javascript ` not just ` ``` `
- **Bold/italic patterns** - Consistent use for emphasis
- **Table formatting** - Proper alignment, consistent spacing
- **Inline code** - Technical terms in backticks
- **Blockquotes** - Consistent usage

**Examples:**

**List consistency:**

```markdown
❌ Mixed:

- Item 1

* Item 2

- Item 3

✅ Consistent:

- Item 1
- Item 2
- Item 3
```

**Code block language hints:**

```markdown
❌ No hint:
```

const x = 42;

````

✅ With hint:
```javascript
const x = 42;
````

```

---

## Decision Rules

### What to Document as Issue vs Observation

**Document as Issue** (clear errors):

- Clear grammar/spelling error (subject-verb disagreement, wrong tense, typo)
- Broken internal link
- Inconsistent terminology (one doc uses "Todo", another uses "TODO")
- Wrong heading level (skipped levels in hierarchy)
- Missing punctuation that affects meaning

**Document as Observation** (subjective improvements):

- Content could be reorganized but current structure is functional
- Tone shifts between sections but not incorrect
- Potential duplication between documents
- Examples could be clearer but aren't wrong
- Links work but might point to better targets
- Terminology is consistent but might not be ideal choice

**Don't Document** (pure preference):

- Personal preferences with no rationale
- Vague "could be better" statements without specifics
- Stylistic choices that don't impact clarity or consistency

---

## Severity Assignment

| Severity        | Use When                                                                                                          |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| 🔴 **Critical** | Broken links to key navigation, major factual errors, severe grammar obscuring meaning, missing critical sections |
| 🟡 **Medium**   | Minor grammar issues, inconsistent terminology, formatting issues, minor structural problems                      |
| 🟢 **Low**      | Stylistic suggestions, optional improvements, nice-to-have additions, minor polish items                          |

**Examples by severity:**

**🔴 Critical:**
- Broken link to main documentation
- "The users is required to..." (grammar obscures meaning)
- Missing H2 causing confusing jump from H1 to H3
- Factually incorrect information

**🟡 Medium:**
- Minor typo: "teh" → "the"
- Inconsistent terminology within document
- Missing language hint on code block
- Inconsistent list markers

**🟢 Low:**
- Link text could be more descriptive
- Example could be clearer
- Optional section could be added
- Minor formatting polish

---

## Category Assignment

For each issue, assign one of these categories to guide Phase 2 implementation:

| Category                  | When to Use                                                                                                         |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Can Fix Automatically** | Clear errors with obvious corrections (grammar, broken internal links where target is obvious, missing punctuation) |
| **Needs Human Judgment**  | Multiple valid corrections exist, terminology choice impacts other docs, style preferences involved                 |
| **Requires Discussion**   | Significant rewrite needed, affects meaning/intent, cross-file implications, user preference unknown                |

**Examples:**

**Can Fix Automatically:**
- "The files is complete" → "The files are complete" (one correct fix)
- Link to `docs/setup.md` broken, file is at `docs/getting-started.md` (obvious)
- Missing period at end of sentence

**Needs Human Judgment:**
- Should we use "user story" or "scenario"? (both valid, need to pick one)
- This section could be split into two or kept together (tradeoff)
- Tone is formal here, casual elsewhere (which should we standardize on?)

**Requires Discussion:**
- This entire section may be outdated (needs product owner input)
- Major restructure would help, but impacts cross-references from 10+ files
- Content might contradict the API behavior (need to verify with engineering)

---

## Consistency Checking Across Repository

Track these patterns across ALL files and note in both individual entries AND final summary:

1. **Key terminology** - Are main concepts named consistently?
   - Example: "Todo" vs "TODO" vs "to-do" vs "task"

2. **Tone & voice** - Formal? Conversational? Technical? Consistent across files?
   - Example: Some docs use "you", others use "users", others use "one"

3. **Structure patterns** - Do similar docs use similar formats?
   - Example: All API docs start with "Overview → Usage → Examples → Reference"

4. **Example domains** - Do examples reference consistent concepts?
   - Example: Some examples use "blog posts", others use "e-commerce", others use "todo lists"

5. **Emoji usage** - If used, are meanings consistent?
   - Example: ✅ always means "correct/complete", 🔴 always means "critical/error"

6. **Code style** - Indentation, naming, patterns consistent in examples?
   - Example: Some code uses camelCase, some uses snake_case

7. **Link style** - Relative vs absolute, with/without extensions?
   - Example: `./guide.md` vs `guide.md` vs `guide` vs `/docs/guide.md`

**In individual file reports:** Note when file deviates from repository patterns

**In summary report:** Analyze overall consistency and recommend standardization where needed

---

## Customization Guidance

This criteria file is designed to be customized for different documentation types:

**For API Documentation:**
- Add checks for: endpoint format consistency, parameter documentation completeness, response example accuracy
- Increase severity for technical accuracy issues
- Add terminology checks for API-specific terms

**For User Guides:**
- Add checks for: step-by-step clarity, screenshot currency, prerequisite clarity
- Focus on tone consistency (user-facing voice)
- Check that examples match typical user scenarios

**For README Files:**
- Add checks for: installation instructions completeness, badge accuracy, link to other docs
- Focus on "quick start" clarity
- Verify examples are copy-pasteable

**For Technical Specifications:**
- Increase rigor for: terminology precision, structural consistency, technical accuracy
- Add checks for: diagram accuracy, code example correctness
- Require formal tone consistency

---

## See Also

- **[Core Workflow](core-workflow.md)** - How to apply these criteria during review
- **[Reference Guide](reference.md)** - Templates and formatting standards
- **[Examples](examples.md)** - See criteria applied in practice
```
