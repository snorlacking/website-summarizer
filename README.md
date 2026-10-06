# Website Summarizer

Cursor skill that walks **linear itch.io visual-novel chapters**, unlocks them with a password, saves the full story transcript, summarizes the chapter, collects attachments, and writes assignment approach recommendations—all as markdown under a chapter folder (e.g. `C3`).

## Skill locations

| Location | Purpose |
|----------|---------|
| [`.cursor/skills/itch-chapter-summarizer/`](.cursor/skills/itch-chapter-summarizer/) | Versioned in this repo (GitHub sync) |
| `~/.cursor/skills/itch-chapter-summarizer/` | Personal copy for use in any project |

## How to invoke

In Cursor chat, ask to run the **itch-chapter-summarizer** skill and provide:

1. **Chapter URL** — the itch.io chapter page  
2. **Unlock password** — for the itch.io password gate (do not commit this)  
3. **Output base directory** — parent folder for the course/game (chapter subfolders live here)  
4. **Chapter id** — short folder name such as `C3`  

Example:

> Use itch-chapter-summarizer on `https://….itch.io/…` with password `…`, chapter id `C3`, and write under `D:\courses\Rome the Game`.

## Outputs

```
<output-base>/<chapter-id>/
  summary.md                 # whole-chapter summary
  assignment-approach.md     # how to approach the final assignment
  raw/
    story.md                 # full chapter text (for later analysis; avoid rescraping)
    attachments.md           # index of story, images, and video/Drive/PDF links
    <downloaded images>
```

**Attachment rules:** download images into `raw/`; for videos, PDFs, and Google Drive docs, record link + note only (read Drive/docs when needed for the assignment). Always write `raw/story.md` with the complete chapter text.

## Navigation assumptions

- Chapters are linear; advance via highlighted “next” text on the page.
- If multiple highlighted options exist, any choice is fine; when Twine/source is available, extract all passages into `story.md`.
- The agent identifies the final assignment near the end and bases `assignment-approach.md` on that document.

## Privacy

Never commit unlock passwords or put them in output markdown files.
