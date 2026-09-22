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
- @ryzerth's UP5K board (X/Twitter sighting, unverifiable).
- Inogeni SDI2USB3 (likely ECP3 LFE3-17EA per Lattice ref design; no teardown yet).
- PixelFX Retro GEM HDMI mod kits (FPGA-based; vendor/part unconfirmed).
- AR smart glasses (Xreal/Rokid/RayNeo) — CrossLink-NX MIPI bridging plausible, unconfirmed.

Confirmed & added 2026-09-21 (commercial teardown sweep):
- SD2SNES → **ECP5** (samlittlewood/sd2snes_ecp5); in commercial ECP5 list.
- Valve Index (iCE40HX8K), Apple iPhone 7 & Vision Pro (iCE5LP4K/iCE40 Ultra),
  Elgato Game Capture 4K60 Pro (MachXO3L), Magewell USB Capture Plus (ECP3+ECP5),
  Schlappi Three Body (ECP5), Siglent SDS1000X (MachXO, part unconfirmed).

Refuted 2026-09-21 (checked, NOT Lattice — don't chase again):
- Funnyplaying FPGA kits & ModRetro Chromatic → **Gowin**.
- Cheap HDMI-to-USB3 dongles → **MacroSilicon** MS2109/MS2130 ASIC.
- Analogue Pocket / Super Nt / Mega Sg → **Altera** Cyclone.
- Linsn/Novastar LED cards → mostly **Xilinx**; only Colorlight is Lattice ECP5.
- $38 K210 HAT → confirmed a Lattice **iCE40** (kept as follow-up; exact part unknown).

**Why:** keeps speculative entries out of the confirmed family sections.
**How to apply:** when a part is confirmed, move the entry and update this note.
