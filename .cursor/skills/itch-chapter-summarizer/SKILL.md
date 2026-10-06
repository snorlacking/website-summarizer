---
name: itch-chapter-summarizer
description: >-
  Walks linear itch.io visual-novel chapters via browser, unlocks with a
  password, writes a full story transcript into raw/, summarizes the chapter,
  collects attachments, and writes assignment approach recommendations under a
  chapter folder (e.g. C3). Use when the user asks to summarize an itch.io
  chapter, process a visual novel chapter URL, unlock an itch.io password page,
  or run itch-chapter-summarizer.
disable-model-invocation: true
---

# Itch.io Chapter Summarizer

Summarize one itch.io visual-novel chapter end-to-end. Produce markdown outputs and a `raw/` folder under a chapter subfolder (e.g. `C3`).

## Required inputs

Ask for any that are missing before starting:

1. **Chapter URL** — itch.io page for the chapter
2. **Unlock password** — for the itch.io password gate
3. **Output base directory** — absolute path for the course/game folder (parent of chapter folders)
4. **Chapter id** — short folder name such as `C3` (ask if not given)

Do not hardcode or commit passwords. Use the password only to unlock the page in the browser.

## Output layout

```
<output-base>/<chapter-id>/
  summary.md
  assignment-approach.md
  raw/
    story.md              # full chapter text for later analysis (do not rescrape)
    attachments.md
    <downloaded images>
```

Example: `...\Rome the Game\C3\raw\story.md`

Use the skeletons in [output-templates.md](output-templates.md).

## Workflow checklist

Copy and track progress:

```
Progress:
- [ ] Inputs confirmed (URL, password, output base, chapter id)
- [ ] <output-base>/<chapter-id>/ and raw/ created
- [ ] itch.io unlocked
- [ ] Chapter traversed (linear next clicks) OR full Twine/source extracted
- [ ] Text and attachment URLs collected
- [ ] raw/story.md written (entire story)
- [ ] Final assignment identified and read
- [ ] Images downloaded to raw/
- [ ] Videos / Drive / PDFs linked in raw/attachments.md
- [ ] summary.md written
- [ ] assignment-approach.md written
- [ ] Folder layout verified
```

### 1. Prepare output folder

Create `<output-base>/<chapter-id>/` and `<output-base>/<chapter-id>/raw/` if they do not exist. Do not overwrite sibling chapter folders (e.g. leave `C1`, `C2` alone).

### 2. Unlock and open the chapter

1. Use Cursor browser tools: `browser_navigate` → `browser_lock` → `browser_snapshot`.
2. Enter the user-provided password on the itch.io unlock gate.
3. Proceed into the chapter content (for itch embeds, open the HTML game iframe URL directly if the outer page blocks interaction).

### 3. Traverse / extract the full story

1. Capture the **entire** chapter narrative for archival — not only a summary.
2. Prefer extracting full Twine/`tw-passagedata` (or equivalent) source when available so all linear branches are preserved without rescraping later.
3. Otherwise click through highlighted next text; if multiple highlighted options exist, pick any (content is linear) but still capture text from all reachable passages if extractable from source.
4. Record image URLs and links to video, Google Drive, PDF, or docs.
5. Stop when there is no further next control, or after the final assignment page is fully captured.

### 4. Write `raw/story.md` (required)

Save the **complete chapter text** to `raw/story.md` before or alongside the summary.

- Markdown (`.md`), suitable for later analysis.
- Include passage/section structure when the source has it (e.g. Twine passage names).
- Preserve choice labels when branches exist.
- Keep embedded media as markdown images or `**Embedded media:** <url>` lines so attachments stay discoverable.
- Do **not** rely on rescraping the site for future analysis — `story.md` is the durable transcript.

### 5. Attachments (`raw/`)

| Type | Action |
|------|--------|
| Images | Download into `raw/`; list in `attachments.md` with local path |
| Videos | Do **not** download; add link + short note in `attachments.md` |
| Google Drive / PDFs / Docs | Do **not** download binaries; add link + note in `attachments.md`. Open/read content when needed for the assignment |

Keep `raw/attachments.md` as the index of every attachment found. List `story.md` under other/working files if useful.

### 6. Final assignment

1. Identify the final assignment near the end (assignment brief, Google Doc, PDF, or clearly labeled assignment page).
2. Read the assignment content (follow the link / open the doc as needed).
3. Write `assignment-approach.md` with concrete approach recommendations.

### 7. Write remaining markdown outputs

1. **`summary.md`** — one holistic chapter summary (not a page-by-page dump): overview, key beats, facts, themes, important terms. Link to `raw/story.md` for the full text.
2. **`assignment-approach.md`** — restate requirements briefly; recommended steps; risks/pitfalls; suggested deliverables.
3. **`raw/attachments.md`** — complete attachment index.

All text outputs must be `.md` markdown.

### 8. Verify

Confirm the output layout matches the tree above, `raw/story.md` exists and is non-empty, and every discovered attachment appears in `attachments.md`.

## Browser notes

- Prefer `browser_snapshot` for structure and clickable refs; use screenshots only when visual confirmation is needed.
- Unlock → lock → interact → unlock when fully done with browser work for the run.
- If login, captcha, or a missing password blocks progress, stop and ask the user.

## Anti-patterns

- Do not dump every page as a separate summary file at the chapter root.
- Do not skip `raw/story.md` — summaries alone are not enough for later analysis.
- Do not write chapter outputs into the base folder without a chapter id subfolder (e.g. `C3`).
- Do not download videos or full Drive/PDF binaries when a link + note is enough.
- Do not invent assignment requirements — base recommendations on the actual assignment text.
- Do not store the unlock password in any output file.
