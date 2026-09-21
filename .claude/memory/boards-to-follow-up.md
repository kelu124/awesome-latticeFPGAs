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
- Low-cost HDMI-to-USB3 capture dongle (no link yet; awaiting teardowns).
- Funnyplaying GBA SP IPS screen clones (FPGA yes, but Lattice unconfirmed).
- @ryzerth's UP5K board (X/Twitter sighting, unverifiable).

Resolved 2026-09-21 (subagent audit):
- SD2SNES → confirmed **ECP5** (samlittlewood/sd2snes_ecp5); moved to commercial ECP5 list.
- $38 K210 AI Accelerator HAT → confirmed a Lattice **iCE40** (article says iCE40, not an
  LP part as originally guessed); note corrected in Readme.md.

**Why:** keeps speculative entries out of the confirmed family sections.
**How to apply:** when a part is confirmed, move the entry and update this note.
