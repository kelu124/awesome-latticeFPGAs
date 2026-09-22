# Board metadata (`.claude/jsons/`)

One JSON file per board listed in [`../../Readme.md`](../../Readme.md), capturing the same
information in a structured, machine-readable form. The list in `Readme.md` stays the
canonical human-facing deliverable; these files mirror it so the catalogue can be queried,
sorted, or checked programmatically.

## File naming

`.claude/jsons/<slug>.json`, where `<slug>` is the board name lowercased, ASCII, with spaces
and punctuation collapsed to single hyphens (e.g. `iCE-V Wireless` → `ice-v-wireless.json`,
`Colorlight 5A-75B` → `colorlight-5a-75b.json`). Slugs are unique across the whole catalogue.

## Schema

See [`schema.json`](schema.json) (JSON Schema, draft 2020-12). Every field:

| Field | Type | Notes |
|-------|------|-------|
| `name` | string | Board name, exactly as in `Readme.md`. |
| `url` | string | Primary URL (the first link in the entry). |
| `fpga.vendor` | string | Always `"Lattice"`. |
| `fpga.family` | string | Human family name, e.g. `"iCE40 UltraPlus"`, `"ECP5"`, `"CrossLink-NX"`, `"MachXO2"`. |
| `fpga.part` | string\|null | Exact part when known (e.g. `"iCE40UP5K"`, `"LFE5U-25F"`); else the family's default part, or `null` if genuinely unknown. |
| `section` | string | The `Readme.md` section header the entry lives under (e.g. `"UP5K"`, `"ECP5"`, `"Conference badges"`). |
| `category` | string | One of `dev-board`, `commercial`, `badge`, `follow-up`. |
| `programming.interface` | string\|null | Primary configuration/programming method. Controlled vocabulary — see below. |
| `programming.details` | string\|null | Free-text specifics (chip used, how the bitstream is loaded). |
| `companion_mcu` | string\|null | On-board microcontroller paired with the FPGA, if any (e.g. `"RP2040"`, `"ESP32-C3"`, `"STM32G031"`). |
| `connectivity` | string[] | Wireless/interfaces of note, e.g. `["WiFi","BLE"]`, `["USB3"]`. `[]` if none. |
| `pmod_count` | integer\|null | Number of Pmod sockets, if stated. |
| `osh` | boolean\|null | Open-source hardware? `true`/`false`/`null` (unknown). |
| `maker` | string\|null | Designer / vendor / company. |
| `description` | string | Short description, matching or refining the `Readme.md` prose. |
| `links` | array | Extra links: `[{"label": "...", "url": "..."}]`. `[]` if none. |
| `tags` | string[] | Free tags, e.g. `["esp32","sdr","retro","wireless"]`. `[]` if none. |
| `outdated` | boolean | `true` if the `Readme.md` entry is marked **(outdated)**. |
| `last_updated` | string | ISO date (`YYYY-MM-DD`) this record was last updated/verified. |

### `programming.interface` controlled vocabulary

- `FTDI` — FTDI USB chip (FT2232H/FT232H/FT231X) doing JTAG/SPI programming.
- `JTAG` — dedicated JTAG header/programmer (not via FTDI).
- `USB-bootloader` — FPGA/board enumerates as USB and is flashed by a bootloader (e.g. DFU, TinyFPGA/Fomu style).
- `RP2040` / `RP2350` — on-board Raspberry Pi Pico class MCU programs the FPGA.
- `microcontroller` — some other on-board MCU programs the FPGA (name it in `companion_mcu`/`details`).
- `Pico` — external Raspberry Pi Pico used as the programmer.
- `GPIO RPi` — programmed over Raspberry Pi GPIO header (HAT-style).
- `Serial` — serial/UART programming path.
- `SPI-flash` — boots from on-board SPI flash (loaded separately).
- `proprietary` — Lattice/vendor proprietary programmer/tooling.
- `null` — unknown / not documented.

Where a board offers several, pick the most characteristic for `interface` and describe the
rest in `details`.
