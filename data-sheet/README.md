# QCS9075 Data Sheet — 80-73417-1 Rev. AL

Markdown conversion of the full 111-page data sheet, one file per chapter (chapters 2 and 3 are split by section). Source: <https://docs.qualcomm.com/doc/80-73417-1/topic/device-description.html>.

## Contents

- [Front matter](00-front-matter.md)
- [1 Introduction](01-introduction.md)
- **2 Pin definitions**
  - [2.1 I/O parameter definitions](02-pin-definitions-01-i-o-parameter-definitions.md)
  - [2.2 Pin map](02-pin-definitions-02-pin-map.md)
  - [2.3 Pin descriptions](02-pin-definitions-03-pin-descriptions.md)
- **3 Electrical specifications**
  - [3.1 Absolute maximum ratings](03-electrical-specifications-01-absolute-maximum-ratings.md)
  - [3.2 Operating conditions](03-electrical-specifications-02-operating-conditions.md)
  - [3.3 Average operating current](03-electrical-specifications-03-average-operating-current.md)
  - [3.4 Power-on circuits and power sequence](03-electrical-specifications-04-power-on-circuits-and-power-sequence.md)
  - [3.5 Digital logic characteristics](03-electrical-specifications-05-digital-logic-characteristics.md)
  - [3.6 Timing characteristics](03-electrical-specifications-06-timing-characteristics.md)
  - [3.7 Memory support](03-electrical-specifications-07-memory-support.md)
  - [3.8 Multimedia](03-electrical-specifications-08-multimedia.md)
  - [3.9 Connectivity](03-electrical-specifications-09-connectivity.md)
  - [3.10 Internal functions](03-electrical-specifications-10-internal-functions.md)
- [4 Mechanical information](04-mechanical-information.md)
- [5 Carrier, handling, and storage information](05-carrier-handling-and-storage-information.md)
- [6 PCB mounting guidelines](06-pcb-mounting-guidelines.md)
- [7 Part reliability](07-part-reliability.md)
- [8 Samples and known issues](08-samples-and-known-issues.md)
- [9 Revision history](09-revision-history.md)
- [Legal information](10-legal-information.md)

## Conversion notes

Complete Markdown conversion of the PDF *QCS9075 Data Sheet*,
80-73417-1 Rev. AL, 31 August 2026 (111 pages). All body text, tables, figures, footnotes and
legal text from the PDF are reproduced. Conventions:

- Figures are reproduced as 300 dpi images in `images/`; each figure is followed by a
  transcription of the text printed inside it (most figures are bitmaps with no text layer).
- Figure 2-1 (the ball map) is additionally reproduced as a full row × column table of pin
  names, with the colour legend and the balls belonging to each net class.
- A table that continues over several PDF pages is joined into one Markdown table; the repeated
  header rows and the repeated “(cont.)” captions are therefore dropped.
- A blank table cell means the cell was merged with the one above it in the PDF. Where a value
  was printed as one cell spanning two columns, it is repeated in both columns; a cell spanning
  three or more columns (a section-divider row) is left in the first column only.
- Running headers, running footers and page numbers are omitted.
