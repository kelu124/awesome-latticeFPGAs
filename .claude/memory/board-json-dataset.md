---
name: board-json-dataset
description: Structured per-board JSON metadata lives in .claude/jsons/
metadata:
  type: reference
---

Every board in `Readme.md` has a machine-readable twin at `.claude/jsons/<slug>.json` (one file
per board; slug = board name lowercased, ASCII, punctuation → hyphens). Fields: `name`, `url`,
`fpga` {vendor, family, part}, `section`, `category` (dev-board/commercial/badge/follow-up),
`programming` {interface, details}, `companion_mcu`, `connectivity[]`, `pmod_count`, `osh`,
`maker`, `description`, `links[]`, `tags[]`, `outdated`, `last_updated`.

Spec + JSON Schema: `.claude/jsons/README.md` and `.claude/jsons/schema.json`.
`programming.interface` is a controlled vocabulary documenting how each board is configured
(FTDI / JTAG / USB-bootloader / RP2040 / RP2350 / microcontroller / Pico / GPIO RPi / Serial /
SPI-flash / proprietary / null).

**Why:** `Readme.md` is canonical, but the JSONs make the catalogue queryable and record the
programming method + companion MCU per board. The two must never drift apart.

**How to apply — TWO MANDATORY ACTIONS (keep `Readme.md` and `.claude/jsons/` in sync):**
1. When you **add, edit, or remove a product in `Readme.md`**, you MUST create/update/delete the
   corresponding `.claude/jsons/<slug>.json` in the same change (mirror the name, url, section,
   description, programming annotation, outdated flag; bump `last_updated`).
2. When you **add (or change) a `.claude/jsons/*.json`**, you MUST add/update the matching entry
   in `Readme.md` (correct family section, inserted alphabetically, per [[list-conventions]]).

Watch slug collisions for duplicate names — e.g. `iceboy-up5k` vs `iceboy-breakout`,
`nut2nt` (commercial) vs `nut2nt-plus` (dev), `mtx-bc48-db` (dev) vs `mtx-bc48-db-commercial`.
