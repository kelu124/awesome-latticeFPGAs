# CLAUDE.md

## What this repository is

**Awesome Lattice FPGA boards** — a curated [awesome list](https://github.com/sindresorhus/awesome#readme)
of (mostly open-source hardware) boards built around **Lattice Semiconductor FPGAs**.

The single deliverable is [`Readme.md`](Readme.md): a Markdown list. There is no code, build,
or test. Contributions are new board entries or improvements to the categorization.

The core job when maintaining this repo is: **identify the Lattice FPGA a board uses, and file it
under the right family.** Every board lives in the section matching its FPGA part.

## Family taxonomy (the section headers in Readme.md)

Boards are grouped by the exact Lattice part/family. Families already captured:

### iCE40 family (by part)
| Section | Part | Notes |
|---------|------|-------|
| `HX1K` | iCE40HX1K | iCE40 HX, 1K LUTs |
| `HX4K` | iCE40HX4K | often usable as 8K in yosys |
| `HX8K` | iCE40HX8K | |
| `LP384` | iCE40LP384 | smallest LP |
| `LP1K` | iCE40LP1K | |
| `LP4K` | iCE40LP4K | |
| `LP8K` | iCE40LP8K | |
| `UL1K` | iCE40UL1K | UltraLite |
| `UP5K` | iCE40UP5K | UltraPlus — largest section |

### Larger / other families
| Section | Part | Notes |
|---------|------|-------|
| `CrossLink-NX` | LIFCL (e.g. LIFCL-40) | |
| `ECP5` | LFE5U / LFE5UM / LFE5UM5G | |
| `LFE3` | LatticeECP3 | mostly commercial (TV tuner cards) |
| `MachXO2` | MachXO2 | appears under "Others" |

### `Other commercial products`
A separate top-level section for **shipping commercial gear** (not dev boards) that contains a
Lattice FPGA, sub-grouped by family (`UP5K`, `HX8K`, `ECP5`, `LFE3`, `Others`). It also has a
`To follow up` bucket for unconfirmed sightings ("guessing those are Lattice FPGAs").

When a board uses a family **not yet listed**, add a new `## Section` header for that part —
new categories are explicitly welcomed by the contribution guidelines.

## Entry conventions (from `contributing.md` — follow exactly)

- **Alphabetize** the entry within its section.
- Search first — avoid duplicates (some boards legitimately appear twice, e.g. as both a dev board
  and a commercial product).
- Prefer boards that are **beautiful / stand out**, ideally **open-source hardware (OSH)**.
- **Keep descriptions short**, start with a **capital**, end with a **period**.
- Common inline annotations after the name: programming interface in parens — `(FTDI)`, `(Serial)`,
  `(GPIO RPi)` — plus companion MCU, PMOD count, or standout feature.
- Entry format:
  ```markdown
  * [Board Name](https://primary-url) (interface). Short description. [Extra link](url).
  ```
- Check spelling/grammar; strip trailing whitespace.

## Working in this repo

- The list file is `Readme.md` (capital R), not `README.md`.
- One PR per suggestion; keep diffs minimal and scoped to the relevant section.
- The `check-links` skill can verify board URLs are still live before committing edits.
- To place a new board: find its Lattice part → go to that family section → insert alphabetically.

## Structured metadata (`.claude/jsons/`)

Every board in `Readme.md` also has a machine-readable record at `.claude/jsons/<slug>.json`
(one file per board), capturing FPGA part/family (+ part `source`/`confidence`), section,
category, programming method + companion MCU(s), `toolchain` (open/proprietary/both),
`form_factor`, connectivity, OSH status + `repo`, maker, links, tags and `last_updated`. The schema and
field spec live in [`.claude/jsons/schema.json`](.claude/jsons/schema.json) and
[`.claude/jsons/README.md`](.claude/jsons/README.md). `Readme.md` stays the canonical
deliverable; the `programming.interface` vocabulary documents how each board is configured
(FTDI / JTAG / USB-bootloader / RP2040 / microcontroller / GPIO RPi / Serial / SPI-flash / …).

**Two mandatory actions — always keep the list and the JSONs in sync:**

1. **When `Readme.md` updates a product** (add / edit / remove), update the corresponding
   `.claude/jsons/<slug>.json` in the same change (mirror name, url, section, description,
   programming annotation and `outdated`; bump `last_updated`).
2. **When a `.claude/jsons/*.json` is added or changed**, update `Readme.md` to match — place
   the entry in the right family section, alphabetically, following the entry conventions above.

## Memory

Persist durable, non-obvious findings in [`.claude/memory/`](.claude/memory/) — see its
[`MEMORY.md`](.claude/memory/MEMORY.md) index. Good candidates: boards confirmed/refuted as Lattice
(resolving the "To follow up" list), which family a hard-to-identify part belongs to, and dead links
found. Do **not** record what `Readme.md` or git history already show.
