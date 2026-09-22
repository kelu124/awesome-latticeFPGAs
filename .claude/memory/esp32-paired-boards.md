---
name: esp32-paired-boards
description: Lattice FPGA boards paired with an ESP32, and the ESP32 sweep results
metadata:
  type: project
---

Boards that pair a Lattice FPGA with an Espressif ESP32 (a recurring request). Confirmed and
listed in `Readme.md` as of 2026-09-22:

- **ICE-V Wireless** — iCE40UP5K + **ESP32-C3** (QWERTY Embedded Design). Pre-existing.
- **ICEd ESPresso** — iCE40UP5K + **ESP32-S2** (Matt Mets/BlinkinLabs). The ESP32-S2 loads the
  bitstream and updates it over WiFi. (Resolved: it is ESP32, *not* ESP8266.)
- **ESP32JTAG** — iCE40UP5K + **ESP32-S3** (EZ32, Crowd Supply 2025), OSH. Wireless JTAG/logic-
  analyzer tool that doubles as a dev board; ESP32-S3 configures the FPGA over SPI. Added 2026-09-22.
- **ULX3S** (ECP5) — has an on-board **ESP32-WROOM-32** that can flash the ECP5 over JTAG (even
  wirelessly, emard/esp32ecp5); primary path is still the FT231X USB-JTAG.
- **MCH2022 badge** — iCE40UP5K + **ESP32-S3** + RP2040 (Conference badges).

Follow-up (see [[boards-to-follow-up]]): **Latticino** (MachXO2-1200 + ESP32-PICO) — dormant.

**Refuted / not a board** (don't chase again): esp32-rjtag & emard/esp32ecp5 are ESP32-as-programmer
*techniques*, not integrated boards; Fri3d Camp 2024 badge has an ESP32-S3 but **no FPGA**.

**Why:** ESP32-loads-FPGA-over-SPI is the common integration pattern; these are the confirmed ones.
**How to apply:** when asked for Lattice+ESP32 boards, start here before re-searching.
