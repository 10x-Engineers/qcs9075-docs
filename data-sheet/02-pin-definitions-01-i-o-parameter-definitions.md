[← Contents](../README.md)

# 2 Pin definitions

## 2.1 I/O parameter definitions

**Table 2-1  I/O description (pin type) parameters**

| Symbol | Description |
|---|---|
| ***Pad type*** |  |
| AI | Analog input (does not include pad circuitry) |
| AO | Analog output (does not include pad circuitry) |
| B | Bidirectional digital with CMOS input |
| DI | Digital input (CMOS) |
| DO | Digital output (CMOS) |
| H | High-voltage tolerant |
| S | Schmitt trigger input |
| Z | High-impedance (Hi-Z) output |
| ***Padpull details for digital I/Os*** |  |
| nppdpukp | Programmable pull resistor. The default pull direction is indicated using capital letters and is a prefix to other programmable options:<br>NP: pdpukp = default no-pull with programmable options following the colon (:)<br>PD: nppukp = default pull-down with programmable options following the colon (:)<br>PU: nppdkp = default pull-up with programmable options following the colon (:)<br>KP: nppdpu = default keeper with programmable options following the colon (:) |
| KP | Contains an internal weak keeper device (keepers cannot drive external buses) |
| NP | Contains no internal pull |
| PU | Contains an internal pull-up device |
| PD | Contains an internal pull-down device |
| ***Pad voltage groupings for baseband circuits*** |  |
| PX_0 | Pad group 0 for main domain (control signals); 1.8 V |
| PX_0_BPP | Pad group 0 _BPP (back power protection); 1.8 V |
| PX_1 | Pad group 1 (EBI I/O); 1.1 V |
| RTSS_PX_0 | Pad group 0 for RTSS domain (control signals); 1.8 V |
| PX_3 | Pad group 3 (most peripherals); 1.8 V |
| PX_3_BPP | Pad group 3_BPP (back power protection I/Os); 1.8 V |
| PX_7 | Pad group 7 (SDC1- eMMC); 1.8 V |
| RTSS_PX_3 | Pad group 3 for RTSS domain (most peripherals); 1.8 V |
| RTSS_PX_3_BPP | Pad group 3_BPP (back power protection I/Os) for RTSS; 1.8 V |
| RTSS_PX_8 | Pad group 8 for RTSS domain (RGMII_0); 1.8 V |
| PX_9 | Pad group 9 (UFS0_REF_CLK and UFS0_RESET); 1.2 V |
| PX_10 | Pad group 10 (UFS1_REF_CLK and UFS1_RESET); 1.2 V |
| PX_11 | Pad group 11 (CXO); 1.8 V |
| RTSS_PX_11 | Pad group 11 for RTSS domain (CXO); 1.8 V |
