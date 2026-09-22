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
programming method + companion MCU per board.
**How to apply:** when adding or editing a board in `Readme.md`, create/update its JSON too.
Watch slug collisions for duplicate names — e.g. `iceboy-up5k` vs `iceboy-breakout`,
`nut2nt` (commercial) vs `nut2nt-plus` (dev), `mtx-bc48-db` (dev) vs `mtx-bc48-db-commercial`.
