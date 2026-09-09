# Qualcomm Hexagon V73 Programmer’s Reference Manual — 80-N2040-53 Rev. AB

Markdown conversion of the full 686-page manual, one file per chapter (chapter 11, the instruction set, is split by section).

## Contents

- [Front matter](00-front-matter.md)
- [Contents](00-contents.md)
- [1 Introduction](01-introduction.md)
- [2 Registers](02-registers.md)
- [3 Instructions](03-instructions.md)
- [4 Data Processing](04-data-processing.md)
- [5 Memory](05-memory.md)
- [6 Conditional Execution](06-conditional-execution.md)
- [7 Software Stack](07-software-stack.md)
- [8 Program Flow](08-program-flow.md)
- [9 PMU Events](09-pmu-events.md)
- [10 Instruction Encoding](10-instruction-encoding.md)
- **11 Instruction Set**
  - [11.1 ALU32](11-instruction-set-01-alu32.md)
  - [11.2 CR](11-instruction-set-02-cr.md)
  - [11.3 JR](11-instruction-set-03-jr.md)
  - [11.4 J](11-instruction-set-04-j.md)
  - [11.5 LD](11-instruction-set-05-ld.md)
  - [11.6 MEMOP](11-instruction-set-06-memop.md)
  - [11.7 NV](11-instruction-set-07-nv.md)
  - [11.8 ST](11-instruction-set-08-st.md)
  - [11.9 SYSTEM](11-instruction-set-09-system.md)
  - [11.10 XTYPE](11-instruction-set-10-xtype.md)
- [Instruction Index](12-instruction-index.md)
- [Intrinsics Index](13-intrinsics-index.md)

## Conversion notes

Converted from the vendor PDF; every character of body text, tables, code, figure and
diagram labels, and both indexes is reproduced. Conventions:

- Instruction syntax, behaviour pseudocode and intrinsic prototypes are set as code.
- Instruction encoding diagrams become 33-column tables, one column per bit; a field
  name is repeated across every bit it covers.
- Figures and the unlabelled inline diagrams are 200 dpi images in `images/`, each
  followed by a plain-text transcription of the labels drawn inside it (they carry no
  reading order in the PDF, so the transcription is in geometric order).
- A table continued across a page break is joined into one Markdown table, so the
  repeated header row is dropped.
- A blank table cell means the cell was merged with the one above it in the PDF.
- Running headers, running footers and page numbers are omitted; the page numbers
  printed in the two indexes refer to the original PDF.

Source: <https://docs.qualcomm.com/bundle/80-N2040-53>.
