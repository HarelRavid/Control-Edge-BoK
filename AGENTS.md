# Instructions for AI coding and review agents

## Source of truth

- Editable episode sources: `episodes/*/full.he.md` and `episodes/*/full.en.md`.
- Do not edit files under `archive/`.
- Derived `.txt` files must remain semantically aligned with the Markdown source.

## Review behavior

1. Check factual correctness and internal consistency before improving style.
2. Identify whether each statement is a standard requirement, engineering guidance, common practice, example or vendor-specific implementation.
3. Never invent clause numbers, certifications, test values, product capabilities or market claims.
4. Check Hebrew-English semantic parity.
5. Check the episode boundary: do not duplicate later episodes or omit the bridge from the previous episode.
6. Preserve the two-host dialogue and practical engineering examples.
7. Report proposed changes as file path + exact passage + reason + replacement text.

## Editing behavior

- Prefer small, reviewable changes.
- Keep UTF-8 encoding and LF line endings.
- Use English filenames and stable paths.
- Update `docs/SERIES_INDEX.md` and `manifest.json` when adding an episode.
