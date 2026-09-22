---
name: list-conventions
description: How to format and place a new board entry in Readme.md
metadata:
  type: reference
---

Rules for adding a board to `Readme.md` (from `contributing.md`):

- File it under the section for its Lattice part (see [[lattice-families]]), inserted
  **alphabetically** within that section.
- Format: `* [Board Name](https://primary-url) (interface). Short description. [Extra link](url).`
- Interface annotation in parens after the name — common values: `(FTDI)`, `(Serial)`,
  `(GPIO RPi)`; may also note companion MCU / PMOD count / standout feature.
- Description starts with a capital, ends with a period; keep it short.
- Prefer open-source hardware (OSH) boards that stand out.
- Search first to avoid duplicates. The list file is `Readme.md` (capital R only).

The `check-links` skill verifies board URLs before committing.
