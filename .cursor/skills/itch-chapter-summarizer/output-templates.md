# Output templates

Use these skeletons when writing chapter outputs. Replace bracketed placeholders. Omit empty optional sections only if they truly do not apply.

Chapter root is always `<output-base>/<chapter-id>/` (e.g. `C3/`).

---

## `summary.md`

```markdown
# Chapter summary: [Chapter title or URL slug]

**Source:** [itch.io URL]
**Summarized:** [YYYY-MM-DD]
**Full text:** [raw/story.md](raw/story.md)

## Overview

[One short paragraph: what this chapter covers as a whole.]

## Key beats

- [Major information or narrative beat 1]
- [Major information or narrative beat 2]
- [Major information or narrative beat 3]

## Key facts and concepts

- [Fact or concept]: [Brief explanation]
- [Fact or concept]: [Brief explanation]

## Themes and takeaways

[What the chapter emphasizes; what the reader should retain.]

## Important terms

| Term | Meaning |
|------|---------|
| [Term] | [Definition from the chapter] |

## Attachments overview

See [raw/attachments.md](raw/attachments.md) for the full index. Notable items:

- [Notable image / link 1]
- [Notable image / link 2]

## Final assignment (pointer)

The chapter ends with an assignment. Approach recommendations are in [assignment-approach.md](assignment-approach.md).
```

---

## `assignment-approach.md`

```markdown
# Assignment approach: [Chapter title or short name]

**Source assignment:** [link or description of where the assignment was found]
**Summarized:** [YYYY-MM-DD]

## Requirements (from the assignment)

- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

## Recommended approach

1. [Step — concrete and ordered]
2. [Step]
3. [Step]
4. [Step]

## Suggested deliverables

- [What to produce / submit]
- [Format or structure if specified or implied]

## Risks and pitfalls

- [Common mistake or ambiguity]
- [Time / scope risk]
- [Missing material to watch for]

## Notes from chapter context

[How earlier chapter content should inform the assignment — key facts, constraints, or resources to reuse.]

## Resources

- Assignment doc/link: [URL]
- Full chapter text: [raw/story.md](raw/story.md)
- Related chapter attachments: see [raw/attachments.md](raw/attachments.md)
```

---

## `raw/story.md`

```markdown
# Full chapter story: [Chapter title]

**Source:** [itch.io URL]
**Captured:** [YYYY-MM-DD]
**Format:** [e.g. Twine passages / linear click-through transcript]. Include all branches when extractable from source so later analysis does not require rescraping.

---

## Passage: [name or section]

[Full narrative / dialogue / instructional text for this section]

> **Choice:** [label] → `destination`   <!-- when applicable -->

![image](url-or-note)   <!-- or **Embedded media:** url -->

---

## Passage: [next]

[Continue for the entire chapter…]
```

---

## `raw/attachments.md`

```markdown
# Attachments index: [Chapter title or short name]

**Source:** [itch.io URL]
**Collected:** [YYYY-MM-DD]

## Story transcript

| Name | Local path | Note |
|------|------------|------|
| story.md | raw/story.md | Full chapter text for later analysis |

## Images (downloaded)

| Name | Source URL | Local path | Note |
|------|------------|------------|------|
| [filename] | [url] | raw/[filename] | [optional context] |

## Videos (link + note)

| Title / label | URL | Note |
|---------------|-----|------|
| [label] | [url] | [what it covers; do not download] |

## Documents and Google Drive (link + note)

| Title / label | Type | URL | Note |
|---------------|------|-----|------|
| [label] | Google Doc / PDF / Drive / other | [url] | [role in chapter or assignment] |

## Other links

| Label | URL | Note |
|-------|-----|------|
| [label] | [url] | [optional] |
```
