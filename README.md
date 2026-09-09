# QCS9075 data sheet — compute-relevant extract

A Markdown conversion of the sections of the **QCS9075 Data Sheet**
(Qualcomm document 80-73417-1 Rev. AL, 31 August 2026) that carry
compute-architecture information, for Hexagon HTP kernel work.

This is a **subset**. The full 111-page data sheet also covers the 1723-ball
pin map and GPIO muxing, I/O electrical characteristics and interface timing
(USB, PCIe, UFS, SDC, RGMII, I²S, SPI, JTAG), carrier and handling, PCB
mounting, part reliability and sample testing. None of that bears on kernel
development, so it is not reproduced here.

## Contents

| File | Why it is here |
|---|---|
| [1 Introduction](01-introduction.md) | **The one that matters.** §1.2 / Table 1-1 with the Processor and Memory sub-tables: dual HTP up to 1.420 GHz, quad HVX + dual HMX (one integer, one float) per HTP, 8 MB vTCM + 1 MB L2 per HTP, 256 kB IMEM, 1.5 MB GMEM, 6 × 16-bit LPDDR5 @ 3200 MHz, 3 MB system cache, up to 36 GB with inline ECC, and the per-SKU 50 / 100 dense TOPS split. Also §1.1, the functional block diagram. |
| [4 Mechanical information](04-mechanical-information.md) | §4.4 Table 4-4 maps the variant code (`000-AA` / `000-AC`) and `FEATURE_ID` to the actual part, and is the only place giving a **per-variant HTP clock** — 1.487 GHz for AA (100 TOPS) and 0.768 GHz for AC (50 TOPS). Note this disagrees with the "up to 1.420 GHz" in the Processor table. Also package outline and part marking. |
| [3.2 Operating conditions](03-electrical-specifications-02-operating-conditions.md) | Supply rails, and the thermal limits Ta −40…85 °C / Tj max 115 °C — the headroom that governs whether a high DCVS corner is sustainable. |
| [3.7 Memory support](03-electrical-specifications-07-memory-support.md) | One sentence, but the only place naming the LPDDR5 standard (JESD209-5C). |
| [Front matter](00-front-matter.md) | Cover: device description, key-features list, high-level block diagram. A condensed duplicate of chapter 1, useful as a cross-check. |

Figures are 300 dpi renders in [`images/`](images). Section and table numbering
follows the source document, so cross-references into the omitted chapters
(“see Table 3-5”, “see Chapter 4”) will not resolve within this repository.

## Conversion notes

Converted from the vendor PDF; text, tables and footnotes are reproduced in
full for the sections included. Conventions:

- Each figure is followed by a transcription of the text printed inside it —
  most figures in the source are bitmaps with no text layer.
- A table that continues over several PDF pages is joined into one Markdown
  table; the repeated header rows and “(cont.)” captions are dropped.
- A blank table cell means the cell was merged with the one above it in the
  PDF. Where a value was printed as one cell spanning two columns it is
  repeated in both; a cell spanning three or more columns (a section-divider
  row) is left in the first column only.
- Running headers, running footers and page numbers are omitted.

The data sheet is Qualcomm copyright material and carries its own terms of
use, set out on the last page of the source PDF (not reproduced here).
