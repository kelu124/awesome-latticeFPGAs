---
name: boards-to-follow-up
description: Unconfirmed Lattice-FPGA sightings awaiting confirmation before listing
metadata:
  type: project
---

The `To follow up` section of `Readme.md` holds boards suspected — but not confirmed — to contain a
Lattice FPGA. Resolving one means confirming the exact part (from a teardown/datasheet), then moving
it into the matching family section per [[list-conventions]], or dropping it if refuted.

Open as of 2026-09-21:
- Low-cost HDMI-to-USB3 capture dongle (awaiting teardowns).
- Funnyplaying GBA SP IPS screen clones (guessed Lattice).
- SD2SNES (via @samlittlewood).
- @ryzerth's UP5K board.
- $38 K210 AI Accelerator HAT (contains a Lattice LP-series part).

**Why:** keeps speculative entries out of the confirmed family sections.
**How to apply:** when a part is confirmed, move the entry and update this note.
