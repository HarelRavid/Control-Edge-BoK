# Control Edge - Industrial Control Engineering Podcast Body of Knowledge

A bilingual, text-first repository for a professional podcast series aimed at mechanical and process engineers.

## Why this repository exists

PDF files are useful for presentation but poor as the primary source for AI review, collaborative editing and version control. This repository therefore treats UTF-8 Markdown and plain text as the source of truth. Original PDF and DOCX files are retained only under each episode's `archive/` folder when available.

## Current status

Episodes 1-11 are complete in Hebrew and English. Episode 12 is planned as **Industrial Cybersecurity**.

## Start here

1. Read [`docs/SERIES_INDEX.md`](docs/SERIES_INDEX.md).
2. For editorial or technical review, use [`prompts/CLAUDE_REVIEW_PROMPT.txt`](prompts/CLAUDE_REVIEW_PROMPT.txt).
3. For NotebookLM, upload the relevant `script.<language>.txt`, `notebooklm_prompt.<language>.txt`, and `standards_and_sources.<language>.md` files.
4. For a single-file review, use the files under `exports/`.

## Repository rules

- Edit `full.he.md` and `full.en.md` together with the canonical `script.*.txt` for each episode; regenerate derived exports after changes.
- Maintain semantic parity between Hebrew and English, but do not force literal translation when technical clarity requires different phrasing.
- Never invent a standard clause, certification, vendor capability or numerical design value.
- Separate standards requirements from guidance, common practice and vendor-specific implementation.
- Preserve the two-host format: Yael, a young mechanical engineer, and Amir, a senior process and controls engineer.
- Keep each episode within its declared scope and preserve transitions to adjacent episodes.

## Hebrew

זהו מאגר טקסטואלי דו-לשוני לסדרת הפודקאסט **Control Edge**. קובצי Markdown ו-TXT הם מקור העבודה. קובצי PDF ו-DOCX נשמרים בארכיון בלבד כאשר הם זמינים, כדי לאפשר השוואה לתוצר המקורי.
