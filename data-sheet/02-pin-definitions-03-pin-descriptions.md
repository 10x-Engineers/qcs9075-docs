[← Contents](../README.md)

## 2.3 Pin descriptions

The following tables describe the pin functions, pin pull types, and pin voltages. It also provides a mapping of pin numbers and pin names for all the pins on the device. These include primary pins, GPIO pins, RTSS I/O pins, MD_LPASS pins, power-supply pins, DNC pins, and ground pins.

#### Primary pins

| Pin no. | Pin name | Pad voltage | Pad type | Functional description |
|---|---|---|---|---|
| BG45 | CSI0_NC_CLK_P | – | AI | MIPI CSI 0 (D-PHY), differential clock – plus MIPI CSI 0 (C-PHY), no connect |
| BG43 | CSI0_A0_CLK_M | – | AI | MIPI CSI 0 (D-PHY), differential clock – minus MIPI CSI 0 (C-PHY), trio lane 0 – A |
| BF44 | CSI0_B0_LN0_P | – | AI | MIPI CSI 0 (D-PHY), differential lane 0 – plus MIPI CSI 0 (C-PHY), trio lane 0 – B |
| BF42 | CSI0_C0_LN0_M | – | AI | MIPI CSI 0 (D-PHY), differential lane 0 – minus MIPI CSI 0 (C-PHY), trio lane 0 – C |
| BE43 | CSI0_A1_LN1_P | – | AI | MIPI CSI 0 (D-PHY), differential lane 1 – plus MIPI CSI 0 (C-PHY), trio lane 1 – A |
| BE41 | CSI0_B1_LN1_M | – | AI | MIPI CSI 0 (D-PHY), differential lane 1 – minus MIPI CSI 0 (C-PHY), trio lane 1 – B |
| BF40 | CSI0_C1_LN2_P | – | AI | MIPI CSI 0 (D-PHY), differential lane 2 – plus MIPI CSI 0 (C-PHY), trio lane 1 – C |
| BF38 | CSI0_A2_LN2_M | – | AI | MIPI CSI 0 (D-PHY), differential lane 2 – minus MIPI CSI 0 (C-PHY), trio lane 2 – A |
| BG39 | CSI0_B2_LN3_P | – | AI | MIPI CSI 0 (D-PHY), differential lane 3 – plus MIPI CSI 0 (C-PHY), trio lane 2 – B |
| BG37 | CSI0_C2_LN3_M | – | AI | MIPI CSI 0 (D-PHY), differential lane 3 – minus MIPI CSI 0 (C-PHY), trio lane 2 – C |
| BG55 | CSI1_NC_CLK_P | – | AI | MIPI CSI 1 (D-PHY), differential clock – plus MIPI CSI 1 (C-PHY), no connect |
| BG53 | CSI1_A0_CLK_M | – | AI | MIPI CSI 1 (D-PHY), differential clock – minus MIPI CSI 1 (C-PHY), trio lane 0 – A |
| BF54 | CSI1_B0_LN0_P | – | AI | MIPI CSI 1 (D-PHY), differential lane 0 – plus MIPI CSI 1 (C-PHY), trio lane 0 – B |
| BF52 | CSI1_C0_LN0_M | – | AI | MIPI CSI 1 (D-PHY), differential lane 0 – minus MIPI CSI 1 (C-PHY), trio lane 0 – C |
| BE53 | CSI1_A1_LN1_P | – | AI | MIPI CSI 1 (D-PHY), differential lane 1 – plus MIPI CSI 1 (C-PHY), trio lane 1 – A |
| BE51 | CSI1_B1_LN1_M | – | AI | MIPI CSI 1 (D-PHY), differential lane 1 – minus MIPI CSI 1 (C-PHY), trio lane 1 – B |
| BF50 | CSI1_C1_LN2_P | – | AI | MIPI CSI 1 (D-PHY), differential lane 2 – plus MIPI CSI 1 (C-PHY), trio lane 1 – C |
| BF48 | CSI1_A2_LN2_M | – | AI | MIPI CSI 1 (D-PHY), differential lane 2 – minus MIPI CSI 1 (C-PHY), trio lane 2 – A |
| BG49 | CSI1_B2_LN3_P | – | AI | MIPI CSI 1 (D-PHY), differential lane 3 – plus MIPI CSI 1 (C-PHY), trio lane 2 – B |
| BG47 | CSI1_C2_LN3_M | – | AI | MIPI CSI 1 (D-PHY), differential lane 3 – minus MIPI CSI 1 (C-PHY), trio lane 2 – C |
| BD58 | CSI2_NC_CLK_P | – | AI | MIPI CSI 2 (D-PHY), differential clock – plus MIPI CSI 2 (C-PHY), no connect |
| BD56 | CSI2_A0_CLK_M | – | AI | MIPI CSI 2 (D-PHY), differential clock – minus MIPI CSI 2 (C-PHY), trio lane 0 – A |
| BC57 | CSI2_B0_LN0_P | – | AI | MIPI CSI 2 (D-PHY), differential lane 0 – plus MIPI CSI 2 (C-PHY), trio lane 0 – B |
| BC55 | CSI2_C0_LN0_M | – | AI | MIPI CSI 2 (D-PHY), differential lane 0 – minus MIPI CSI 2 (C-PHY), trio lane 0 – C |
| BB56 | CSI2_A1_LN1_P | – | AI | MIPI CSI 2 (D-PHY), differential lane 1 – plus MIPI CSI 2 (C-PHY), trio lane 1 – A |
| BB54 | CSI2_B1_LN1_M | – | AI | MIPI CSI 2 (D-PHY), differential lane 1 – minus MIPI CSI 2 (C-PHY), trio lane 1 – B |
| BC53 | CSI2_C1_LN2_P | – | AI | MIPI CSI 2 (D-PHY), differential lane 2 – plus MIPI CSI 2 (C-PHY), trio lane 1 – C |
| BC51 | CSI2_A2_LN2_M | – | AI | MIPI CSI 2 (D-PHY), differential lane 2 – minus MIPI CSI 2 (C-PHY), trio lane 2 – A |
| BD52 | CSI2_B2_LN3_P | – | AI | MIPI CSI 2 (D-PHY), differential lane 3 – plus MIPI CSI 2 (C-PHY), trio lane 2 – B |
| BD50 | CSI2_C2_LN3_M | – | AI | MIPI CSI 2 (D-PHY), differential lane 3 – minus MIPI CSI 2 (C-PHY), trio lane 2 – C |
| BG65 | CSI3_NC_CLK_P | – | AI | MIPI CSI 3 (D-PHY), differential clock – plus MIPI CSI 3 (C-PHY), no connect |
| BG63 | CSI3_A0_CLK_M | – | AI | MIPI CSI 3 (D-PHY), differential clock – minus MIPI CSI 3 (C-PHY), trio lane 0 – A |
| BF64 | CSI3_B0_LN0_P | – | AI | MIPI CSI 3 (D-PHY), differential lane 0 – plus MIPI CSI 3 (C-PHY), trio lane 0 – B |
| BF62 | CSI3_C0_LN0_M | – | AI | MIPI CSI 3 (D-PHY), differential lane 0 – minus MIPI CSI 3 (C-PHY), trio lane 0 – C |
| BE63 | CSI3_A1_LN1_P | – | AI | MIPI CSI 3 (D-PHY), differential lane 1 – plus MIPI CSI 3 (C-PHY), trio lane 1 – A |
| BE61 | CSI3_B1_LN1_M | – | AI | MIPI CSI 3 (D-PHY), differential lane 1 – minus MIPI CSI 3 (C-PHY), trio lane 1 – B |
| BF60 | CSI3_C1_LN2_P | – | AI | MIPI CSI 3 (D-PHY), differential lane 2 – plus MIPI CSI 3 (C-PHY), trio lane 1 – C |
| BF58 | CSI3_A2_LN2_M | – | AI | MIPI CSI 3 (D-PHY), differential lane 2 – minus MIPI CSI 3 (C-PHY), trio lane 2 – A |
| BG59 | CSI3_B2_LN3_P | – | AI | MIPI CSI 3 (D-PHY), differential lane 3 – plus MIPI CSI 3 (C-PHY), trio lane 2 – B |
| BG57 | CSI3_C2_LN3_M | – | AI | MIPI CSI 3 (D-PHY), differential lane 3 – minus MIPI CSI 3 (C-PHY), trio lane 2 – C |
| AV76 | CXO_0 | PX_11 | DI | 38.4 MHz clock input to SoC from PMIC LNBBCLK1 output |
| G37 | CXO_1 | PX_11 | DI | 38.4 MHz clock input to SoC from PMIC LNBBCLK2 output |
| AH80 | DDR_RESET_N | PX_1 | DO | LPDDR5 reset shared by all DDR EBI (External Bus Interface). Active-low reset signal for the external DDR memory interface or memory subsystem. |
| BG35 | DSI0_A0_LN0_P | – | AO | MIPI DSI 0 (D-PHY), differential lane 0 – plus MIPI DSI 0 (C-PHY), trio lane 0 – A |
| BG33 | DSI0_B0_LN0_M | – | AO | MIPI DSI 0 (D-PHY), differential lane 0 – minus MIPI DSI 0 (C-PHY), trio lane 0 – B |
| BF34 | DSI0_C0_LN1_P | – | AO | MIPI DSI 0 (D-PHY), differential lane 1 – plus MIPI DSI 0 (C-PHY), trio lane 0 – C |
| BF32 | DSI0_A1_LN1_M | – | AO | MIPI DSI 0 (D-PHY), differential lane 1 – minus MIPI DSI 0 (C-PHY), trio lane 1 – A |
| BE33 | DSI0_B1_CLK_P | – | AO | MIPI DSI 0 (D-PHY), differential clock – P – plus MIPI DSI 0 (C-PHY), trio lane 1 – B |
| BE31 | DSI0_C1_CLK_M | – | AO | MIPI DSI 0 (D-PHY), differential clock – M – minus MIPI DSI 0 (C-PHY), trio lane 1 – C |
| BF30 | DSI0_A2_LN2_P | – | AO | MIPI DSI 0 (D-PHY), differential lane 2 – plus MIPI DSI 0 (C-PHY), trio lane 2 – A |
| BF28 | DSI0_B2_LN2_M | – | AO | MIPI DSI 0 (D-PHY), differential lane 2 – minus MIPI DSI 0 (C-PHY), trio lane 2 – B |
| BG29 | DSI0_C2_LN3_P | – | AO | MIPI DSI 0 (D-PHY), differential lane 3 – plus MIPI DSI 0 (C-PHY), trio lane 2 – C |
| BG27 | DSI0_NC_LN3_M | – | AO | MIPI DSI 0 (D-PHY), differential lane 3 – minus MIPI DSI 0 (C-PHY), no connect |
| BC49 | DSI1_A0_LN0_P | – | AO | MIPI DSI 1 (D-PHY), differential lane 0 – plus MIPI DSI 1 (C-PHY), trio lane 0 – A |
| BC47 | DSI1_B0_LN0_M | – | AO | MIPI DSI 1 (D-PHY), differential lane 0 – minus MIPI DSI 1 (C-PHY), trio lane 0 – B |
| BB48 | DSI1_C0_LN1_P | – | AO | MIPI DSI 1 (D-PHY), differential lane 1 – plus MIPI DSI 1 (C-PHY), trio lane 0 – C |
| BB46 | DSI1_A1_LN1_M | – | AO | MIPI DSI 1 (D-PHY), differential lane 1 – minus MIPI DSI 1 (C-PHY), trio lane 1 – A |
| BA47 | DSI1_B1_CLK_P | – | AO | MIPI DSI 1 (D-PHY), differential clock – P – plus MIPI DSI 1 (C-PHY), trio lane 1 – B |
| BA45 | DSI1_C1_CLK_M | – | AO | MIPI DSI 1 (D-PHY), differential clock – M – minusMIPI DSI 1 (C-PHY), trio lane 1 – C |
| BB44 | DSI1_A2_LN2_P | – | AO | MIPI DSI 1 (D-PHY), differential lane 2 – plus MIPI DSI 1 (C-PHY), trio lane 2 – A |
| BB42 | DSI1_B2_LN2_M | – | AO | MIPI DSI 1 (D-PHY), differential lane 2 – minus MIPI DSI 1 (C-PHY), trio lane 2 – B |
| BC43 | DSI1_C2_LN3_P | – | AO | MIPI DSI 1 (D-PHY), differential lane 3 – plus MIPI DSI 1 (C-PHY), trio lane 2 – C |
| BC41 | DSI1_NC_LN3_M | – | AO | MIPI DSI 1 (D-PHY), differential lane 3 – minus MIPI DSI 1 (C-PHY), no connect |
| AH78 | DS_EN | PX_0 | DI | Deep sleep handshake between PMIC and SoC. Not supported on 4-PMIC design. Future support only. |
| H12 | EBI01_CAL | – | DO | External calibration resistor connection for EBI0 and EBI1. Pull up through 240 Ω ± 1% resistor. |
| C21 | EBI0_CA0 | – | DO | EBI0 LPDDR5 command/address bit 0 |
| B20 | EBI0_CA1 | – | DO | EBI0 LPDDR5 command/address bit 1 |
| D18 | EBI0_CA2 | – | DO | EBI0 LPDDR5 command/address bit 2 |
| D16 | EBI0_CA3 | – | DO | EBI0 LPDDR5 command/address bit 3 |
| B16 | EBI0_CA4 | – | DO | EBI0 LPDDR5 command/address bit 4 |
| A15 | EBI0_CA5 | – | DO | EBI0 LPDDR5 command/address bit 5 |
| C15 | EBI0_CA6 | – | DO | EBI0 LPDDR5 command/address bit 6 |
| A19 | EBI0_CK_C | – | DO | EBI0 LPDDR5 differential clock – minus |
| A17 | EBI0_CK_T | – | DO | EBI0 LPDDR5 differential clock – plus |
| C19 | EBI0_CS0 | – | DO | EBI0 LPDDR5 chip select 0 |
| A21 | EBI0_CS1 | – | DO | EBI0 LPDDR5 chip select 1 |
| C7 | EBI0_DMI0 | – | DO | EBI0 LPDDR5 data mask for byte 0 |
| D28 | EBI0_DMI1 | – | DO | EBI0 LPDDR5 data mask for byte 1 |
| D2 | EBI0_DQ0 | – | B | EBI0 LPDDR5 data bit 0 |
| D4 | EBI0_DQ1 | – | B | EBI0 LPDDR5 data bit 1 |
| B4 | EBI0_DQ2 | – | B | EBI0 LPDDR5 data bit 2 |
| C5 | EBI0_DQ3 | – | B | EBI0 LPDDR5 data bit 3 |
| C11 | EBI0_DQ4 | – | B | EBI0 LPDDR5 data bit 4 |
| C13 | EBI0_DQ5 | – | B | EBI0 LPDDR5 data bit 5 |
| A13 | EBI0_DQ6 | – | B | EBI0 LPDDR5 data bit 6 |
| A11 | EBI0_DQ7 | – | B | EBI0 LPDDR5 data bit 7 |
| C33 | EBI0_DQ8 | – | B | EBI0 LPDDR5 data bit 8 |
| C31 | EBI0_DQ9 | – | B | EBI0 LPDDR5 data bit 9 |
| A33 | EBI0_DQ10 | – | B | EBI0 LPDDR5 data bit 10 |
| D30 | EBI0_DQ11 | – | B | EBI0 LPDDR5 data bit 11 |
| C25 | EBI0_DQ12 | – | B | EBI0 LPDDR5 data bit 12 |
| A23 | EBI0_DQ13 | – | B | EBI0 LPDDR5 data bit 13 |
| C23 | EBI0_DQ14 | – | B | EBI0 LPDDR5 data bit 14 |
| A31 | EBI0_DQ15 | – | B | EBI0 LPDDR5 data bit 15 |
| A7 | EBI0_DQS0_C | – | DI | EBI0 LPDDR5 differential read data strobe for byte 0 – minus |
| A5 | EBI0_DQS0_T | – | DI | EBI0 LPDDR5 differential read data strobe for byte 0 – plus |
| B28 | EBI0_DQS1_C | – | DI | EBI0 LPDDR5 differential read data strobe for byte 1 – minus |
| B30 | EBI0_DQS1_T | – | DI | EBI0 LPDDR5 differential read data strobe for byte 1 – plus |
| B10 | EBI0_WCK0_C | – | DO | EBI0 LPDDR5 differential write clock for byte 0 – minus |
| B8 | EBI0_WCK0_T | – | DO | EBI0 LPDDR5 differential write clock for byte 0 – plus |
| A25 | EBI0_WCK1_C | – | DO | EBI0 LPDDR5 differential write clock for byte 1 – minus |
| A27 | EBI0_WCK1_T | – | DO | EBI0 LPDDR5 differential write clock for byte 1 – plus |
| D14 | EBI1_CA0 | – | DO | EBI1 LPDDR5 command/address bit 0 |
| G13 | EBI1_CA1 | – | DO | EBI1 LPDDR5 command/address bit 1 |
| G15 | EBI1_CA2 | – | DO | EBI1 LPDDR5 command/address bit 2 |
| F20 | EBI1_CA3 | – | DO | EBI1 LPDDR5 command/address bit 3 |
| E19 | EBI1_CA4 | – | DO | EBI1 LPDDR5 command/address bit 4 |
| E21 | EBI1_CA5 | – | DO | EBI1 LPDDR5 command/address bit 5 |
| D20 | EBI1_CA6 | – | DO | EBI1 LPDDR5 command/address bit 6 |
| F18 | EBI1_CK_C | – | DO | EBI1 LPDDR5 differential clock – minus |
| F16 | EBI1_CK_T | – | DO | EBI1 LPDDR5 differential clock – plus |
| G19 | EBI1_CS0 | – | DO | EBI1 LPDDR5 chip select 0 |
| E15 | EBI1_CS1 | – | DO | EBI1 LPDDR5 chip select 1 |
| D10 | EBI1_DMI0 | – | DO | EBI1 LPDDR5 data mask for byte 0 |
| E25 | EBI1_DMI1 | – | DO | EBI1 LPDDR5 data mask for byte 1 |
| G1 | EBI1_DQ0 | – | B | EBI1 LPDDR5 data bit 0 |
| E1 | EBI1_DQ1 | – | B | EBI1 LPDDR5 data bit 1 |
| F2 | EBI1_DQ2 | – | B | EBI1 LPDDR5 data bit 2 |
| G5 | EBI1_DQ3 | – | B | EBI1 LPDDR5 data bit 3 |
| F12 | EBI1_DQ4 | – | B | EBI1 LPDDR5 data bit 4 |
| E13 | EBI1_DQ5 | – | B | EBI1 LPDDR5 data bit 5 |
| F10 | EBI1_DQ6 | – | B | EBI1 LPDDR5 data bit 6 |
| E9 | EBI1_DQ7 | – | B | EBI1 LPDDR5 data bit 7 |
| E33 | EBI1_DQ8 | – | B | EBI1 LPDDR5 data bit 8 |
| G33 | EBI1_DQ9 | – | B | EBI1 LPDDR5 data bit 9 |
| E31 | EBI1_DQ10 | – | B | EBI1 LPDDR5 data bit 10 |
| G31 | EBI1_DQ11 | – | B | EBI1 LPDDR5 data bit 11 |
| F24 | EBI1_DQ12 | – | B | EBI1 LPDDR5 data bit 12 |
| G21 | EBI1_DQ13 | – | B | EBI1 LPDDR5 data bit 13 |
| E23 | EBI1_DQ14 | – | B | EBI1 LPDDR5 data bit 14 |
| D26 | EBI1_DQ15 | – | B | EBI1 LPDDR5 data bit 15 |
| E7 | EBI1_DQS0_C | – | DI | EBI1 LPDDR5 differential read data strobe for byte 0 – minus |
| E5 | EBI1_DQS0_T | – | DI | EBI1 LPDDR5 differential read data strobe for byte 0 – plus |
| F28 | EBI1_DQS1_C | – | DI | EBI1 LPDDR5 differential read data strobe for byte 1 – minus |
| F30 | EBI1_DQS1_T | – | DI | EBI1 LPDDR5 differential read data strobe for byte 1 – plus |
| G9 | EBI1_WCK0_C | – | DO | EBI1 LPDDR5 differential write clock for byte 0 – minus |
| G7 | EBI1_WCK0_T | – | DO | EBI1 LPDDR5 differential write clock for byte 0 – plus |
| G25 | EBI1_WCK1_C | – | DO | EBI1 LPDDR5 differential write clock for byte 1 – minus |
| G27 | EBI1_WCK1_T | – | DO | EBI1 LPDDR5 differential write clock for byte 1 – plus |
| H48 | EBI23_CAL | – | DO | External calibration resistor connection for EBI2 and EBI3. Pull up through 240 Ω ± 1% resistor |
| E55 | EBI2_CA0 | – | DO | EBI2 LPDDR5 command/address bit 0 |
| D56 | EBI2_CA1 | – | DO | EBI2 LPDDR5 command/address bit 1 |
| G57 | EBI2_CA2 | – | DO | EBI2 LPDDR5 command/address bit 2 |
| E61 | EBI2_CA3 | – | DO | EBI2 LPDDR5 command/address bit 3 |
| D60 | EBI2_CA4 | – | DO | EBI2 LPDDR5 command/address bit 4 |
| G63 | EBI2_CA5 | – | DO | EBI2 LPDDR5 command/address bit 5 |
| G61 | EBI2_CA6 | – | DO | EBI2 LPDDR5 command/address bit 6 |
| F60 | EBI2_CK_C | – | DO | EBI2 LPDDR5 differential clock – minus |
| F58 | EBI2_CK_T | – | DO | EBI2 LPDDR5 differential clock – plus |
| E57 | EBI2_CS0 | – | DO | EBI2 LPDDR5 chip select 0 |
| F56 | EBI2_CS1 | – | DO | EBI2 LPDDR5 chip select 1 |
| E51 | EBI2_DMI0 | – | DO | EBI2 LPDDR5 data mask for byte 0 |
| D66 | EBI2_DMI1 | – | DO | EBI2 LPDDR5 data mask for byte 1 |
| E43 | EBI2_DQ0 | – | B | EBI2 LPDDR5 data bit 0 |
| G43 | EBI2_DQ1 | – | B | EBI2 LPDDR5 data bit 1 |
| E45 | EBI2_DQ2 | – | B | EBI2 LPDDR5 data bit 2 |
| G45 | EBI2_DQ3 | – | B | EBI2 LPDDR5 data bit 3 |
| F52 | EBI2_DQ4 | – | B | EBI2 LPDDR5 data bit 4 |
| G55 | EBI2_DQ5 | – | B | EBI2 LPDDR5 data bit 5 |
| E53 | EBI2_DQ6 | – | B | EBI2 LPDDR5 data bit 6 |
| D50 | EBI2_DQ7 | – | B | EBI2 LPDDR5 data bit 7 |
| G73 | EBI2_DQ8 | – | B | EBI2 LPDDR5 data bit 8 |
| F72 | EBI2_DQ9 | – | B | EBI2 LPDDR5 data bit 9 |
| D74 | EBI2_DQ10 | – | B | EBI2 LPDDR5 data bit 10 |
| E73 | EBI2_DQ11 | – | B | EBI2 LPDDR5 data bit 11 |
| F64 | EBI2_DQ12 | – | B | EBI2 LPDDR5 data bit 12 |
| E63 | EBI2_DQ13 | – | B | EBI2 LPDDR5 data bit 13 |
| F66 | EBI2_DQ14 | – | B | EBI2 LPDDR5 data bit 14 |
| E67 | EBI2_DQ15 | – | B | EBI2 LPDDR5 data bit 15 |
| F48 | EBI2_DQS0_C | – | DI | EBI2 LPDDR5 differential read data strobe for byte 0 – minus |
| F46 | EBI2_DQS0_T | – | DI | EBI2 LPDDR5 differential read data strobe for byte 0 – plus |
| E69 | EBI2_DQS1_C | – | DI | EBI2 LPDDR5 differential read data strobe for byte 1 – minus |
| E71 | EBI2_DQS1_T | – | DI | EBI2 LPDDR5 differential read data strobe for byte 1 – plus |
| G51 | EBI2_WCK0_C | – | DO | EBI2 LPDDR5 differential write clock for byte 0 – minus |
| G49 | EBI2_WCK0_T | – | DO | EBI2 LPDDR5 differential write clock for byte 0 – plus |
| G67 | EBI2_WCK1_C | – | DO | EBI2 LPDDR5 differential write clock for byte 1 – minus |
| G69 | EBI2_WCK1_T | – | DO | EBI2 LPDDR5 differential write clock for byte 1 – plus |
| C61 | EBI3_CA0 | – | DO | EBI3 LPDDR5 command/address bit 0 |
| A61 | EBI3_CA1 | – | DO | EBI3 LPDDR5 command/address bit 1 |
| D58 | EBI3_CA2 | – | DO | EBI3 LPDDR5 command/address bit 2 |
| C57 | EBI3_CA3 | – | DO | EBI3 LPDDR5 command/address bit 3 |
| B56 | EBI3_CA4 | – | DO | EBI3 LPDDR5 command/address bit 4 |
| A55 | EBI3_CA5 | – | DO | EBI3 LPDDR5 command/address bit 5 |
| C55 | EBI3_CA6 | – | DO | EBI3 LPDDR5 command/address bit 6 |
| A59 | EBI3_CK_C | – | DO | EBI3 LPDDR5 differential clock – minus |
| A57 | EBI3_CK_T | – | DO | EBI3 LPDDR5 differential clock – plus |
| C59 | EBI3_CS0 | – | DO | EBI3 LPDDR5 chip select 0 |
| B60 | EBI3_CS1 | – | DO | EBI3 LPDDR5 chip select 1 |
| D48 | EBI3_DMI0 | – | DO | EBI3 LPDDR5 data mask for byte 0 |
| C69 | EBI3_DMI1 | – | DO | EBI3 LPDDR5 data mask for byte 1 |
| C43 | EBI3_DQ0 | – | B | EBI3 LPDDR5 data bit 0 |
| C45 | EBI3_DQ1 | – | B | EBI3 LPDDR5 data bit 1 |
| A43 | EBI3_DQ2 | – | B | EBI3 LPDDR5 data bit 2 |
| D46 | EBI3_DQ3 | – | B | EBI3 LPDDR5 data bit 3 |
| C51 | EBI3_DQ4 | – | B | EBI3 LPDDR5 data bit 4 |
| C53 | EBI3_DQ5 | – | B | EBI3 LPDDR5 data bit 5 |
| A53 | EBI3_DQ6 | – | B | EBI3 LPDDR5 data bit 6 |
| A45 | EBI3_DQ7 | – | B | EBI3 LPDDR5 data bit 7 |
| B74 | EBI3_DQ8 | – | B | EBI3 LPDDR5 data bit 8 |
| C73 | EBI3_DQ9 | – | B | EBI3 LPDDR5 data bit 9 |
| A73 | EBI3_DQ10 | – | B | EBI3 LPDDR5 data bit 10 |
| C71 | EBI3_DQ11 | – | B | EBI3 LPDDR5 data bit 11 |
| C65 | EBI3_DQ12 | – | B | EBI3 LPDDR5 data bit 12 |
| A63 | EBI3_DQ13 | – | B | EBI3 LPDDR5 data bit 13 |
| C63 | EBI3_DQ14 | – | B | EBI3 LPDDR5 data bit 14 |
| A65 | EBI3_DQ15 | – | B | EBI3 LPDDR5 data bit 15 |
| B48 | EBI3_DQS0_C | – | DI | EBI3 LPDDR5 differential read data strobe for byte 0 – minus |
| B46 | EBI3_DQS0_T | – | DI | EBI3 LPDDR5 differential read data strobe for byte 0 – plus |
| A69 | EBI3_DQS1_C | – | DI | EBI3 LPDDR5 differential read data strobe for byte 1 – minus |
| A71 | EBI3_DQS1_T | – | DI | EBI3 LPDDR5 differential read data strobe for byte 1 – plus |
| A51 | EBI3_WCK0_C | – | DO | EBI3 LPDDR5 differential write clock for byte 0 – minus |
| A49 | EBI3_WCK0_T | – | DO | EBI3 LPDDR5 differential write for byte 0 – plus |
| B66 | EBI3_WCK1_C | – | DO | EBI3 LPDDR5 differential write clock for byte 1 – minus |
| B68 | EBI3_WCK1_T | – | DO | EBI3 LPDDR5 differential write clock for byte 1 – plus |
| L69 | EBI45_CAL | – | DO | External calibration resistor connection for EBI4 and EBI5. Pull up through 240 Ω ± 1% resistor. |
| T70 | EBI4_CA0 | – | DO | EBI4 LPDDR5 command/address bit 0 |
| T74 | EBI4_CA1 | – | DO | EBI4 LPDDR5 command/address bit 1 |
| V76 | EBI4_CA2 | – | DO | EBI4 LPDDR5 command/address bit 2 |
| Y76 | EBI4_CA3 | – | DO | EBI4 LPDDR5 command/address bit 3 |
| W71 | EBI4_CA4 | – | DO | EBI4 LPDDR5 command/address bit 4 |
| AA71 | EBI4_CA5 | – | DO | EBI4 LPDDR5 command/address bit 5 |
| Y74 | EBI4_CA6 | – | DO | EBI4 LPDDR5 command/address bit 6 |
| W73 | EBI4_CK_C | – | DO | EBI4 LPDDR5 differential clock – minus |
| V74 | EBI4_CK_T | – | DO | EBI4 LPDDR5 differential clock – plus |
| U73 | EBI4_CS0 | – | DO | EBI4 LPDDR5 chip select 0 |
| U71 | EBI4_CS1 | – | DO | EBI4 LPDDR5 chip select 1 |
| N75 | EBI4_DMI0 | – | DO | EBI4 LPDDR5 data mask for byte 0 |
| AC77 | EBI4_DMI1 | – | DO | EBI4 LPDDR5 data mask for byte 1 |
| H72 | EBI4_DQ0 | – | B | EBI4 LPDDR5 data bit 0 |
| J71 | EBI4_DQ1 | – | B | EBI4 LPDDR5 data bit 1 |
| J75 | EBI4_DQ2 | – | B | EBI4 LPDDR5 data bit 2 |
| K72 | EBI4_DQ3 | – | B | EBI4 LPDDR5 data bit 3 |
| P72 | EBI4_DQ4 | – | B | EBI4 LPDDR5 data bit 4 |
| R71 | EBI4_DQ5 | – | B | EBI4 LPDDR5 data bit 5 |
| P74 | EBI4_DQ6 | – | B | EBI4 LPDDR5 data bit 6 |
| N71 | EBI4_DQ7 | – | B | EBI4 LPDDR5 data bit 7 |
| AG71 | EBI4_DQ8 | – | B | EBI4 LPDDR5 data bit 8 |
| AG75 | EBI4_DQ9 | – | B | EBI4 LPDDR5 data bit 9 |
| AG77 | EBI4_DQ10 | – | B | EBI4 LPDDR5 data bit 10 |
| AF70 | EBI4_DQ11 | – | B | EBI4 LPDDR5 data bit 11 |
| AB74 | EBI4_DQ12 | – | B | EBI4 LPDDR5 data bit 12 |
| AA73 | EBI4_DQ13 | – | B | EBI4 LPDDR5 data bit 13 |
| AC73 | EBI4_DQ14 | – | B | EBI4 LPDDR5 data bit 14 |
| AD72 | EBI4_DQ15 | – | B | EBI4 LPDDR5 data bit 15 |
| L75 | EBI4_DQS0_C | – | DI | EBI4 LPDDR5 differential read data strobe for byte 0 – minus |
| K74 | EBI4_DQS0_T | – | DI | EBI4 LPDDR5 differential read data strobe for byte 0 – plus |
| AE73 | EBI4_DQS1_C | – | DI | EBI4 LPDDR5 differential read data strobe for byte 1 – minus |
| AF74 | EBI4_DQS1_T | – | DI | EBI4 LPDDR5 differential read data strobe for byte 1 – plus |
| M72 | EBI4_WCK0_C | – | DO | EBI4 LPDDR5 differential write clock for byte 0 – minus |
| L71 | EBI4_WCK0_T | – | DO | EBI4 LPDDR5 differential write clock for byte 0 – plus |
| AD76 | EBI4_WCK1_C | – | DO | EBI4 LPDDR5 differential write clock for byte 1 – minus |
| AE77 | EBI4_WCK1_T | – | DO | EBI4 LPDDR5 differential write clock for byte 1 – plus |
| U77 | EBI5_CA0 | – | DO | EBI5 LPDDR5 command/address bit 0 |
| T80 | EBI5_CA1 | – | DO | EBI5 LPDDR5 command/address bit 1 |
| R77 | EBI5_CA2 | – | DO | EBI5 LPDDR5 command/address bit 2 |
| N77 | EBI5_CA3 | – | DO | EBI5 LPDDR5 command/address bit 3 |
| M80 | EBI5_CA4 | – | DO | EBI5 LPDDR5 command/address bit 4 |
| M78 | EBI5_CA5 | – | DO | EBI5 LPDDR5 command/address bit 5 |
| L77 | EBI5_CA6 | – | DO | EBI5 LPDDR5 command/address bit 6 |
| P80 | EBI5_CK_C | – | DO | EBI5 LPDDR5 differential clock – minus |
| N81 | EBI5_CK_T | – | DO | EBI5 LPDDR5 differential clock – plus |
| R81 | EBI5_CS0 | – | DO | EBI5 LPDDR5 chip select 0 |
| T78 | EBI5_CS1 | – | DO | EBI5 LPDDR5 chip select 1 |
| H78 | EBI5_DMI0 | – | DO | EBI5 LPDDR5 data mask for byte 0 |
| AA77 | EBI5_DMI1 | – | DO | EBI5 LPDDR5 data mask for byte 1 |
| E77 | EBI5_DQ0 | – | B | EBI5 LPDDR5 data bit 0 |
| F76 | EBI5_DQ1 | – | B | EBI5 LPDDR5 data bit 1 |
| D80 | EBI5_DQ2 | – | B | EBI5 LPDDR5 data bit 2 |
| G77 | EBI5_DQ3 | – | B | EBI5 LPDDR5 data bit 3 |
| J77 | EBI5_DQ4 | – | B | EBI5 LPDDR5 data bit 4 |
| K78 | EBI5_DQ5 | – | B | EBI5 LPDDR5 data bit 5 |
| K80 | EBI5_DQ6 | – | B | EBI5 LPDDR5 data bit 6 |
| E81 | EBI5_DQ7 | – | B | EBI5 LPDDR5 data bit 7 |
| AG81 | EBI5_DQ8 | – | B | EBI5 LPDDR5 data bit 8 |
| AE81 | EBI5_DQ9 | – | B | EBI5 LPDDR5 data bit 9 |
| AF80 | EBI5_DQ10 | – | B | EBI5 LPDDR5 data bit 10 |
| AD80 | EBI5_DQ11 | – | B | EBI5 LPDDR5 data bit 11 |
| W77 | EBI5_DQ12 | – | B | EBI5 LPDDR5 data bit 12 |
| U81 | EBI5_DQ13 | – | B | EBI5 LPDDR5 data bit 13 |
| V80 | EBI5_DQ14 | – | B | EBI5 LPDDR5 data bit 14 |
| W79 | EBI5_DQ15 | – | B | EBI5 LPDDR5 data bit 15 |
| G81 | EBI5_DQS0_C | – | DI | EBI5 LPDDR5 differential read data strobe for byte 0 – minus |
| AB80 | EBI5_DQS1_C | – | DI | EBI5 LPDDR5 differential read data strobe for byte 1 – minus |
| F80 | EBI5_DQS0_T | – | DI | EBI5 LPDDR5 differential read data strobe for byte 0 – plus |
| AC81 | EBI5_DQS1_T | – | DI | EBI5 LPDDR5 differential read data strobe for byte 1 – plus |
| J81 | EBI5_WCK0_C | – | DO | EBI5 LPDDR5 differential write clock for byte 0 – minus |
| Y80 | EBI5_WCK1_C | – | DO | EBI5 LPDDR5 differential write clock for byte 1 – minus |
| H80 | EBI5_WCK0_T | – | DO | EBI5 LPDDR5 differential write clock for byte 0 – plus |
| AA81 | EBI5_WCK1_T | – | DO | EBI5 LPDDR5 differential write clock for byte 1 – plus |
| BE75 | EDP0_AUX_M | – | AI, AO | eDP/DP 0 auxiliary channel – minus |
| BD76 | EDP0_AUX_P | – | AI, AO | eDP/DP 0 auxiliary channel – plus |
| BA73 | EDP0_TX0_M | – | AO | eDP/DP 0 transmit channel 0 – minus |
| AY74 | EDP0_TX0_P | – | AO | eDP/DP 0 transmit channel 0 – plus |
| BB76 | EDP0_TX1_M | – | AO | eDP/DP 0 transmit channel 1 – minus |
| BA75 | EDP0_TX1_P | – | AO | eDP/DP 0 transmit channel 1 – plus |
| BC75 | EDP0_TX2_M | – | AO | eDP/DP 0 transmit channel 2 – minus |
| BB74 | EDP0_TX2_P | – | AO | eDP/DP 0 transmit channel 2 – plus |
| BD74 | EDP0_TX3_M | – | AO | eDP/DP 0 transmit channel 3 – minus |
| BC73 | EDP0_TX3_P | – | AO | eDP/DP 0 transmit channel 3 – plus |
| BF66 | EDP1_AUX_M | – | AI, AO | eDP/DP 1 auxiliary channel – minus |
| BF68 | EDP1_AUX_P | – | AI, AO | eDP/DP 1 auxiliary channel – plus |
| BE71 | EDP1_TX0_M | – | AO | eDP/DP 1 transmit channel 0 – minus |
| BE73 | EDP1_TX0_P | – | AO | eDP/DP 1 transmit channel 0 – plus |
| BG71 | EDP1_TX1_M | – | AO | eDP/DP 1 transmit channel 1 – minus |
| BG73 | EDP1_TX1_P | – | AO | eDP/DP 1 transmit channel 1 – plus |
| BF70 | EDP1_TX2_M | – | AO | eDP/DP 1 transmit channel 2 – minus |
| BF72 | EDP1_TX2_P | – | AO | eDP/DP 1 transmit channel 2 – plus |
| BG67 | EDP1_TX3_M | – | AO | eDP/DP 1 transmit channel 3 – minus |
| BG69 | EDP1_TX3_P | – | AO | eDP/DP 1 transmit channel 3 – plus |
| BC65 | EDP2_AUX_M | – | AI, AO | eDP/DP 2 auxiliary channel – minus |
| BC67 | EDP2_AUX_P | – | AI, AO | eDP/DP 2 auxiliary channel – plus |
| BB70 | EDP2_TX0_M | – | AO | eDP/DP 2 transmit channel 0 – minus |
| BB72 | EDP2_TX0_P | – | AO | eDP/DP 2 transmit channel 0 – plus |
| BD70 | EDP2_TX1_M | – | AO | eDP/DP 2 transmit channel 1 – minus |
| BD72 | EDP2_TX1_P | – | AO | eDP/DP 2 transmit channel 1 – plus |
| BC69 | EDP2_TX2_M | – | AO | eDP/DP 2 transmit channel 2 – minus |
| BC71 | EDP2_TX2_P | – | AO | eDP/DP 2 transmit channel 2 – plus |
| BD66 | EDP2_TX3_M | – | AO | eDP/DP 2 transmit channel 3 – minus |
| BD68 | EDP2_TX3_P | – | AO | eDP/DP 2 transmit channel 3 – plus |
| BA57 | EDP3_AUX_M | – | AI, AO | eDP/DP 3 auxiliary channel – minus |
| BA59 | EDP3_AUX_P | – | AI, AO | eDP/DP 3 auxiliary channel – plus |
| AY62 | EDP3_TX0_M | – | AO | eDP/DP 3 transmit channel 0 – minus |
| AY64 | EDP3_TX0_P | – | AO | eDP/DP 3 transmit channel 0 – plus |
| BB62 | EDP3_TX1_M | – | AO | eDP/DP 3 transmit channel 1 – minus |
| BB64 | EDP3_TX1_P | – | AO | eDP/DP 3 transmit channel 1 – plus |
| BA61 | EDP3_TX2_M | – | AO | eDP/DP 3 transmit channel 2 – minus |
| BA63 | EDP3_TX2_P | – | AO | eDP/DP 3 transmit channel 2 – plus |
| BB58 | EDP3_TX3_M | – | AO | eDP/DP 3 transmit channel 3 – minus |
| BB60 | EDP3_TX3_P | – | AO | eDP/DP 3 transmit channel 3 – plus |
| BA9 | MD_PS_HOLD | RTSS_PX_3_BPP | DI | Main domain PS_HOLD. This is an input signal and must be externally connected to the SoC PS_HOLD. |
| T10 | PCIE0_REFCLK_M | – | AI, AO | PCIe 0 Gen 4 reference clock – minus |
| U9 | PCIE0_REFCLK_P | – | AI, AO | PCIe 0 Gen 4 reference clock – plus |
| W9 | PCIE0_RX0_M | – | AI | PCIe 0 Gen 4 receive – minus |
| Y10 | PCIE0_RX0_P | – | AI | PCIe 0 Gen 4 receive – plus |
| V8 | PCIE0_RX1_M | – | AI | PCIe 0 Gen 4 receive – minus |
| W7 | PCIE0_RX1_P | – | AI | PCIe 0 Gen 4 receive – plus |
| R9 | PCIE0_TX0_M | – | AO | PCIe 0 Gen 4 transmit – minus |
| T8 | PCIE0_TX0_P | – | AO | PCIe 0 Gen 4 transmit – plus |
| P8 | PCIE0_TX1_M | – | AO | PCIe 0 Gen 4 transmit – minus |
| R7 | PCIE0_TX1_P | – | AO | PCIe 0 Gen 4 transmit – plus |
| AE7 | PCIE1_REFCLK_M | – | AI, AO | PCIe 1 Gen 4 reference clock – minus |
| AF6 | PCIE1_REFCLK_P | – | AI, AO | PCIe 1 Gen 4 reference clock – plus |
| AK10 | PCIE1_RX0_M | – | AI | PCIe 1 Gen 4 receive – minus |
| AL9 | PCIE1_RX0_P | – | AI | PCIe 1 Gen 4 receive – plus |
| AJ7 | PCIE1_RX1_M | – | AI | PCIe 1 Gen 4 receive – minus |
| AK6 | PCIE1_RX1_P | – | AI | PCIe 1 Gen 4 receive – plus |
| AH10 | PCIE1_RX2_M | – | AI | PCIe 1 Gen 4 receive – minus |
| AJ9 | PCIE1_RX2_P | – | AI | PCIe 1 Gen 4 receive – plus |
| AG9 | PCIE1_RX3_M | – | AI | PCIe 1 Gen 4 receive – minus |
| AH8 | PCIE1_RX3_P | – | AI | PCIe 1 Gen 4 receive – plus |
| AD10 | PCIE1_TX0_M | – | AO | PCIe 1 Gen 4 transmit – minus |
| AE9 | PCIE1_TX0_P | – | AO | PCIe 1 Gen 4 transmit – plus |
| AC7 | PCIE1_TX1_M | – | AO | PCIe 1 Gen 4 transmit – minus |
| AD6 | PCIE1_TX1_P | – | AO | PCIe 1 Gen 4 transmit – plus |
| AB10 | PCIE1_TX2_M | – | AO | PCIe 1 Gen 4 transmit – minus |
| AC9 | PCIE1_TX2_P | – | AO | PCIe 1 Gen 4 transmit – plus |
| AA7 | PCIE1_TX3_M | – | AO | PCIe 1 Gen 4 transmit – minus |
| AB6 | PCIE1_TX3_P | – | AO | PCIe 1 Gen 4 transmit – plus |
| BC39 | PS_HOLD | PX_3_BPP | DO | Power supply HOLD signal driven by the SoC to the PMIC. Active HIGH. Has an internal pull-down by default.<br>During boot, PS_HOLD is set HIGH (1) to indicate a successful boot and request the PMIC to keep the power supplies enabled.<br>During shutdown, watchdog expiry, thermal trip, or certain error paths, software or hardware clears PS_HOLD to LOW (0) to instruct the PMIC to shut down or reset the system. |
| AA11 | REFGEN_REXT0 | – | AI | External resistor connection for the internal reference generator or bias network. Pull-down through 100 Ω ± 1% resistance. |
| H36 | REFGEN_REXT1 | – | AI | External resistor connection for the internal reference generator or bias network. Pull-down through 100 Ω ± 1% resistance. |
| AJ71 | REFGEN_REXT2 | – | AI | External resistor connection for the internal reference generator or bias network. Pull-down through 100 Ω ± 1% resistance. |
| AY28 | REFGEN_REXT3 | – | AI | External resistor connection for the internal reference generator or bias network. Pull-down through 100 Ω ± 1% resistance. |
| AH72 | RESIN_N | PX_0 | DI | Main domain hardware reset input to the SoC, sourced from the PMIC.<br>It is an active-low reset pin.<br>■ RESIN_N = 0 (LOW): SoC is held in reset.<br>■ RESIN_N = 1 (HIGH): SoC reset is released and boot can proceed. Basic power rails are turned ON.<br>If the SoC does not respond by driving PS_HOLDHIGH within a certain time after RESIN_N goes HIGH, the PMIC will trigger a reset.<br>This pin connects to the PON_RESET_N pin on the PMIC side. |
| BD40 | RESOUT_N | PX_3 | DO | Main domain active‑low reset output that follows RESIN_N with a short delay. It can be used to reset external circuitry. It is asserted or de‑asserted a few clock cycles after a change on RESIN_N or after a watchdog expiry status change. |
| AY12 | RTSS_CXO | RTSS_PX_11 | DI | Core crystal oscillator for RTSS domain from PMIC LNBBCLK3 output |
| M4 | RTSS_JTAG_SRST_N | RTSS_PX_3 | DI-PU | RTSS domain JTAG reset for debug |
| M2 | RTSS_JTAG_TCK | RTSS_PX_3 | DI-PU | RTSS domain JTAG clock input |
| N3 | RTSS_JTAG_TDI | RTSS_PX_3 | DI-PU:nppdkp | RTSS domain JTAG data input |
| N1 | RTSS_JTAG_TDO | RTSS_PX_3 | DO-Z | RTSS domain JTAG data output |
| N5 | RTSS_JTAG_TMS | RTSS_PX_3 | DI-PU:nppdkp | RTSS domain JTAG mode select input |
| L5 | RTSS_JTAG_TRST_N | RTSS_PX_3 | DI-B-PD:nppukp | RTSS domain JTAG reset |
| AW11 | RTSS_MODE_0 | RTSS_PX_3 | DI-S PD | Mode control bits [1:0]<br>00 for mission mode<br>11 for boundary scan mode |
| BA11 | RTSS_MODE_1 | RTSS_PX_3 | DI-S PD |  |
| AV12 | RTSS_PS_HOLD | RTSS_PX_3 | DO | When the RTSS domain is up, this signal will be HIGH. For debugging purposes, a test point can be added to this signal.<br>RTSS temperature fatal events, power sequence watchdog expiration, MD PMIC fault indications, or software faults can cause this signal to go LOW. |
| BA13 | RTSS_RESIN_N | RTSS_PX_0 | DI | RTSS domain hardware reset input to the SoC, sourced from the PMIC.<br>This pin must be connected to the main domain RESIN_N. |
| BC9 | RTSS_RESOUT_N | RTSS_PX_3 | DO | RTSS domain reset output. RTSS domain active‑low reset output that follows RTSS_RESIN_N with a short delay. It can be used to reset external circuitry. It is asserted or de‑asserted a few clock cycles after a change on RTSS_RESIN_N or after a watchdog expiry in the RTSS domain. |
| AL3 | SGMII0_RX_M | – | AI | SGMII interface 0 serial data Rx – minus |
| AM4 | SGMII0_RX_P | – | AI | SGMII interface 0 serial data Rx – plus |
| AM2 | SGMII0_TX_M | – | AO | SGMII interface 0 serial data Tx – minus |
| AN3 | SGMII0_TX_P | – | AO | SGMII interface 0 serial data Tx – plus |
| AP2 | SGMII1_RX_M | – | AI | SGMII interface 1 serial data Rx – minus |
| AR3 | SGMII1_RX_P | – | AI | SGMII interface 1 serial data Rx – plus |
| AR1 | SGMII1_TX_M | – | AO | SGMII interface 1 serial data Tx – minus |
| AT2 | SGMII1_TX_P | – | AO | SGMII interface 1 serial data Tx – plus |
| BB36 | SLEEP_CLK | PX_3 | DI | Sleep clock |
| AJ73 | SPMI_CLK | PX_0_BPP | B | Slave and PBUS interface for PMICs – clock |
| AH74 | SPMI_DATA | PX_0_BPP | B | Slave and PBUS interface for PMICs – data |
| BE79 | UFS0_REFCLK | PX_9 | DO | UFS 0 reference clock |
| BD78 | UFS0_RESET_N | PX_9 | DO | UFS 0 reset |
| BF78 | UFS0_RX0_M | – | AI | UFS 0 receive 0 – minus |
| BE77 | UFS0_RX0_P | – | AI | UFS 0 receive 0 – plus |
| BG77 | UFS0_RX1_M | – | AI | UFS 0 receive 1 – minus |
| BF76 | UFS0_RX1_P | – | AI | UFS 0 receive 1 – plus |
| BC81 | UFS0_TX0_M | – | AO | UFS 0 transmit 0 – minus |
| BD80 | UFS0_TX0_P | – | AO | UFS 0 transmit 0 – plus |
| BB78 | UFS0_TX1_M | – | AO | UFS 0 transmit 1 – minus |
| BC79 | UFS0_TX1_P | – | AO | UFS 0 transmit 1 – plus |
| AW79 | UFS1_REFCLK | PX_10 | DO | UFS 1 reference clock |
| AW81 | UFS1_RESET_N | PX_10 | DO | UFS 1 reset |
| BA81 | UFS1_RX0_M | – | AI | UFS 1 receive 0 – minus |
| AY80 | UFS1_RX0_P | – | AI | UFS 1 receive 0 – plus |
| BB80 | UFS1_RX1_M | – | AI | UFS 1 receive 1 – minus |
| BA79 | UFS1_RX1_P | – | AI | UFS 1 receive 1 – plus |
| AU79 | UFS1_TX0_M | – | AO | UFS 1 transmit 0 – minus |
| AV80 | UFS1_TX0_P | – | AO | UFS 1 transmit 0 – plus |
| AT80 | UFS1_TX1_M | – | AO | UFS 1 transmit 1 – minus |
| AU81 | UFS1_TX1_P | – | AO | UFS 1 transmit 1 – plus |
| C37 | USB0_HS_DM | – | AI, AO | USB 0 high-speed data – minus |
| C35 | USB0_HS_DP | – | AI, AO | USB 0 high-speed data – plus |
| A35 | USB0_SS_RX_M | – | AI | USB 0 super-speed receive – minus |
| A37 | USB0_SS_RX_P | – | AI | USB 0 super-speed receive – plus |
| E35 | USB0_SS_TX_M | – | AO | USB 0 super-speed transmit – minus |
| E37 | USB0_SS_TX_P | – | AO | USB 0 super-speed transmit – plus |
| C41 | USB1_HS_DM | – | AI, AO | USB 1 high-speed data – minus |
| C39 | USB1_HS_DP | – | AI, AO | USB 1 high-speed data – plus |
| A39 | USB1_SS_RX_M | – | AI | USB 1 super-speed receive – minus |
| A41 | USB1_SS_RX_P | – | AI | USB 1 super-speed receive – plus |
| E39 | USB1_SS_TX_M | – | AO | USB 1 super-speed transmit – minus |
| E41 | USB1_SS_TX_P | – | AO | USB 1 super-speed transmit – plus |
| G41 | USB2_HS_DM | – | AI, AO | USB 2 high-speed data – minus |
| G39 | USB2_HS_DP | – | AI, AO | USB 2 high-speed data – plus |
| AM6 | SDC1_CLK | PX_7 | DO-NP:pdpukp | Secure digital controller 1 clock for eMMC |
| AL7 | SDC1_CMD | PX_7 | B-NP:pdpukp | Secure digital controller 1 command for eMMC |
| AM10 | SDC1_DATA0 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 0 for eMMC |
| AN7 | SDC1_DATA1 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 1 for eMMC |
| AN9 | SDC1_DATA2 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 2 for eMMC |
| AP8 | SDC1_DATA3 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 3 for eMMC |
| AP10 | SDC1_DATA4 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 4 for eMMC |
| AR7 | SDC1_DATA5 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 5 for eMMC |
| AR9 | SDC1_DATA6 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 6 for eMMC |
| AT8 | SDC1_DATA7 | PX_7 | B-NP:pdpukp | Secure digital controller 1 DATA bit 7 for eMMC |
| AM8 | SDC1_RCLK | PX_7 | DI-PD:pdpukp | Secure digital controller 1 return clock for eMMC |

#### GPIO pins

GPIO pins can support multiple functions. To assign GPIOs to particular functions (such as the options listed in the preceding table), designers must identify all their application’s requirements and map each GPIO to its function–carefully avoiding conflicts in GPIO assignments. See GPIO pins for a list of all supported functions for each GPIO.

**Note** Board designers must examine each GPIO’s external connection and programmed configuration, and take steps necessary to avoid excessive leakage current. Combinations of the following factors must be controlled properly:

- GPIO configuration
  - Input vs. output
  - Pull-up or pull-down
- External connections
  - Unused inputs
  - Connections to high-impedance (tri-state) outputs
  - Connections to external devices that may not be attached

To help designers define their products’ GPIO assignments, QTI provides an Excel spreadsheet that lists all QCS9075 GPIOs (in numeric order), pad numbers, pad voltages, pull states, and available configurations.

**Note** See the [QCS9075 + PMM8650AU Pin Assignment and GPIO Configuration Spreadsheet (80-73417-1A)](https://docs.qualcomm.com/bundle/80-73417-1A/resource/80-73417-1A.xlsm) from the Qualcomm website.

After successfully logging on, the document is downloaded.

| Pin no. | Pin name and/or function | Alternate function | Pad characteristics – Voltage | Pad characteristics – Type | Functional description | Wakeup function |
|---|---|---|---|---|---|---|
| BF4 | GPIO_0 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BE5 | GPIO_1 |  | PX_3 | PU:nppdkp | Configurable I/O | Y |
|  |  | PCIE0_CLKREQ_N |  |  | PCIe0 clock request |  |
| BF6 | GPIO_2 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BE7 | GPIO_3 |  | PX_3 | PU:nppdkp | Configurable I/O | Y |
|  |  | PCIE1_CLKREQ_N |  |  | PCIe1 clock request |  |
| BG7 | GPIO_4 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BF8 | GPIO_5 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BD8 | GPIO_6 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | EMAC0_PTP_AUX_TS_I_0 |  |  | EMAC0 trigger 0 A for Auxiliary snapshot |  |
|  |  | EMAC0_PTP_PPS_O_0 |  |  | EMAC0 configurable PPS output 0 |  |
|  |  | EMAC1_PTP_AUX_TS_I_0 |  |  | EMAC1 trigger 0 A for Auxiliary snapshot |  |
|  |  | EMAC1_PTP_PPS_O_0 |  |  | EMAC1 configurable PPS output 0 |  |
| BE9 | GPIO_7 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | SGMII_PHY_INTR0_N |  |  | SGMII0 PHY interrupt |  |
| BG9 | GPIO_8 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC0_MDC |  |  | EMAC0 management interface clock |  |
| BF10 | GPIO_9 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC0_MDIO |  |  | EMAC0 management interface I/O |  |
|  |  | GP_PDM_MIRA[2] |  |  | General-purpose PDM output 2 A |  |
| BD2 | GPIO_10 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | USB2PHY_AC_EN0 |  |  | USB AC coupling control for USB0 port |  |
|  |  | EMAC0_PTP_AUX_TS_I_1 |  |  | EMAC0 trigger 1 A for Auxiliary snapshot |  |
|  |  | EMAC0_PTP_PPS_O_1 |  |  | EMAC0 configurable PPS output 1 |  |
|  |  | EMAC1_PTP_AUX_TS_I_1 |  |  | EMAC1 trigger 1 A for Auxiliary snapshot |  |
|  |  | EMAC1_PTP_PPS_O_1 |  |  | EMAC1 configurable PPS output 1 |  |
|  |  | GP_PDM_MIRB[2] |  |  | General-purpose PDM output 2 B |  |
|  |  | BOOT_CONFIG[12] |  |  | Boot configuration bit 12 |  |
| BD4 | GPIO_11 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | USB2PHY_AC_EN1 |  |  | USB AC coupling control for USB 1 port |  |
|  |  | EMAC0_PTP_AUX_TS_I_2 |  |  | EMAC0 trigger 2 A for Auxiliary snapshot |  |
|  |  | EMAC0_PTP_PPS_O_2 |  |  | EMAC0 configurable PPS output 2 |  |
|  |  | EMAC1_PTP_AUX_TS_I_2 |  |  | EMAC1 trigger 2 A for Auxiliary snapshot |  |
|  |  | EMAC1_PTP_PPS_O_2 |  |  | EMAC1 configurable PPS output 2 |  |
|  |  | GP_PDM_MIRA[1] |  |  | General-purpose PDM output 1 A |  |
|  |  | BOOT_CONFIG[13] |  |  | Boot configuration bit 13 |  |
| BE3 | GPIO_12 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | USB2PHY_AC_EN2 |  |  | USB AC coupling control for USB 2 port |  |
|  |  | EMAC0_PTP_AUX_TS_I_3 |  |  | EMAC0 trigger 3 A for Auxiliary snapshot |  |
|  |  | EMAC0_PTP_PPS_O_3 |  |  | EMAC0 configurable PPS output 3 |  |
|  |  | EMAC1_PTP_AUX_TS_I_3 |  |  | EMAC1 trigger 3 A for Auxiliary snapshot |  |
|  |  | EMAC1_PTP_PPS_O_3 |  |  | EMAC1 configurable PPS output 3 |  |
|  |  | EMAC0_MCG_PST_TRIG_LW[0] |  |  | EMAC0 trigger input 0 for Media clock generation |  |
|  |  | GP_PDM_MIRB[1] |  |  | General-purpose PDM output 1 B |  |
|  |  | BOOT_CONFIG[14] |  |  | Boot configuration bit 14 |  |
| J1 | GPIO_13 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC0_MCG_PST_TRIG_LW[1] |  |  | EMAC0 trigger input 1 for Media clock generation |  |
| J3 | GPIO_14 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC0_MCG_PST_TRIG_LW[2] |  |  | EMAC0 trigger input 2 for Media clock generation |  |
| J5 | GPIO_15 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC0_MCG_PST_TRIG_LW[3] |  |  | EMAC0 trigger input 3 for Media clock generation |  |
| K2 | GPIO_16 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | EMAC1_MCG_PST_TRIG_LW[3] |  |  | EMAC1 trigger input 0 for Media clock generation |  |
| K4 | GPIO_17 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC1_MCG_PST_TRIG_LW[1] |  |  | EMAC1 trigger input 1 for Media clock generation |  |
| L1 | GPIO_18 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EMAC1_MCG_PST_TRIG_LW[2] |  |  | EMAC1 trigger input 2 for Media clock generation |  |
| L3 | GPIO_19 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | EMAC1_MCG_PST_TRIG_LW[3] |  |  | EMAC1 trigger input 3 for Media clock generation |  |
| BG21 | GPIO_20 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE0_L0 |  |  | QUP0 SE0 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | EMAC1_MDC |  |  | EMAC1 management interface clock |  |
| BG19 | GPIO_21 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE0_L1 |  |  | QUP0 SE0 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | EMAC1_MDIO |  |  | EMAC1 management interface I/O |  |
| BE21 | GPIO_22 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE0_L2 |  |  | QUP0 SE0 lane 2: UART_TX/SPI-M_SCLK |  |
| BF20 | GPIO_23 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE0_L3 |  |  | QUP0 SE0 lane 3: UART_RX/SPI-M_CS0 |  |
| BD20 | GPIO_24 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE1_L0 |  |  | QUP0 SE1 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BE19 | GPIO_25 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE1_L1 |  |  | QUP0 SE1 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| BF18 | GPIO_26 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | SGMII_PHY_INTR1_N |  |  | SGMII1 PHY interrupt |  |
|  |  | QUP0_SE1_L2 |  |  | QUP0 SE1 lane 2: UART_TX/SPI-M_SCLK |  |
| BD18 | GPIO_27 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE1_L3 |  |  | QUP0 SE1 lane 3: UART_RX/SPI-M_CS0 |  |
| BG15 | GPIO_28 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE3_L0 |  |  | QUP0 SE3 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BE17 | GPIO_29 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE3_L1 |  |  | QUP0 SE3 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| BF16 | GPIO_30 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE3_L2 |  |  | QUP0 SE3 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
| BD16 | GPIO_31 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE3_L3 |  |  | QUP0 SE3 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
| BG13 | GPIO_32 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE4_L0 |  |  | QUP0 SE4 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
| BE15 | GPIO_33 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE4_L1 |  |  | QUP0 SE4 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
|  |  | GCC_GP4_CLK_MIRA |  |  | General-purpose Clock 4 A |  |
| BF14 | GPIO_34 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE4_L2 |  |  | QUP0 SE4 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | GCC_GP5_CLK_MIRA |  |  | General-purpose Clock 5 A |  |
| BE13 | GPIO_35 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE4_L3 |  |  | QUP0 SE4 lane 3: UART_RX/SPI-M_CS0/SPI-M_CS |  |
|  |  | GP_MN |  |  | General-purpose M/N:D counter output |  |
| BF12 | GPIO_36 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE2_L0 |  |  | QUP0 SE2 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | QUP0_SE5_L0 |  |  | QUP0 SE5 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
| BD12 | GPIO_37 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE2_L1 |  |  | QUP0 SE2 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | QUP0_SE5_L1 |  |  | QUP0 SE5 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
| BE11 | GPIO_38 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP0_SE5_L2 |  |  | QUP0 SE5 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | QUP0_SE2_L2 |  |  | QUP0 SE2 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
|  |  | BOOT_CONFIG[1] |  |  | Boot configuration bit 1 |  |
| BD10 | GPIO_39 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP0_SE5_L3 |  |  | QUP0 SE5 lane 3: UART_RX/SPI-M_CS0/SPI-S_CS |  |
|  |  | QUP0_SE2_L3 |  |  | QUP0 SE2 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
| BD30 | GPIO_40 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE0_L0 |  |  | QUP1 SE0 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | QUP1_SE1_L2 |  |  | QUP1 SE1 lane 2: UART_TX/SPI-M_SCLK |  |
| BE27 | GPIO_41 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE0_L1 |  |  | QUP1 SE0 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | QUP1_SE1_L3 |  |  | QUP1 SE1 lane 3: UART_RX/SPI-M_CS0 |  |
| BD38 | GPIO_42 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE1_L0 |  |  | QUP1 SE1 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | QUP1_SE0_L2 |  |  | QUP1 SE0 lane 2: UART_TX/SPI-M_SCLK |  |
|  |  | GCC_GP5_CLK_MIRB |  |  | General-purpose Clock 5 B |  |
| BE37 | GPIO_43 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE1_L1 |  |  | QUP1 SE1 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | QUP1_SE0_L3 |  |  | QUP1 SE0 lane 3: UART_RX/SPI-M_CS0 |  |
| BD36 | GPIO_44 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE2_L2 |  |  | QUP1 SE2 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
|  |  | QUP1_SE3_L0 |  |  | QUP1 SE3 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BC37 | GPIO_45 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE2_L3 |  |  | QUP1 SE2 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
|  |  | QUP1_SE3_L1 |  |  | QUP1 SE3 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| BE35 | GPIO_46 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE3_L2 |  |  | QUP1 SE3 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
|  |  | QUP1_SE2_L0 |  |  | QUP1 SE2 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BD34 | GPIO_47 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE3_L3 |  |  | QUP1 SE3 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
|  |  | QUP1_SE2_L1 |  |  | QUP1 SE2 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| BE29 | GPIO_48 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE4_L0 |  |  | QUP1 SE4 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
|  |  | BOOT_CONFIG[0] |  |  | Boot configuration bit 0 |  |
| BD32 | GPIO_49 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE4_L1 |  |  | QUP1 SE4 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
| BF26 | GPIO_50 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE4_L2 |  |  | QUP1 SE4 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | CCI_ASYNC_IN4 |  |  | Camera control interface async 4 |  |
|  |  | FORCED_USB_BOOT |  |  | Boot strap to enter USB0 emergency download mode. See QCS9075 Technical Reference Manual (80-73417-5) for details. |  |
| BD26 | GPIO_51 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE4_L3 |  |  | QUP1 SE4 lane 3: UART_RX/SPI-M_CS0/SPI-S_CS |  |
|  |  | GCC_GP1_CLK_MIRB |  |  | General-purpose Clock 1 B |  |
| BE25 | GPIO_52 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE5_L0 |  |  | QUP1 SE5 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
|  |  | CCI_TIMER4 |  |  | Camera 4 control interface timer |  |
|  |  | CCI_I2C_SDA1 |  |  | Camera 1 I²C Data |  |
|  |  | GCC_GP2_CLK_MIRB |  |  | General-purpose Clock 2 B |  |
| BG25 | GPIO_53 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE5_L1 |  |  | QUP1 SE5 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
|  |  | CCI_TIMER5 |  |  | Camera 5 control interface timer |  |
|  |  | CCI_I2C_SCL1 |  |  | Camera 1 I²C clock |  |
|  |  | GCC_GP3_CLK_MIRB |  |  | General-purpose Clock 3 B |  |
| BF24 | GPIO_54 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP1_SE5_L2 |  |  | QUP1 SE5 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | CCI_TIMER6 |  |  | Camera 6 control interface timer |  |
|  |  | CCI_I2C_SDA3 |  |  | Camera 3 I²C Data |  |
| BD24 | GPIO_55 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE5_L3 |  |  | QUP1 SE5 lane 3: UART_RX/SPI-M_CS0/SPI-M_CS |  |
|  |  | CCI_TIMER7 |  |  | Camera 7 control interface timer |  |
|  |  | CCI_I2C_SCL3 |  |  | Camera 3 I²C clock |  |
|  |  | GCC_GP4_CLK_MIRB |  |  | General-purpose Clock 4 B |  |
| BE23 | GPIO_56 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE6_L0 |  |  | QUP1 SE6 lane 0: UART_CTS/I2C_SDA |  |
|  |  | QUP1_SE6_L2 |  |  | QUP1 SE6 lane 2: UART_TX |  |
|  |  | CCI_TIMER8 |  |  | Camera 8 control interface timer |  |
|  |  | CCI_I2C_SDA5 |  |  | Camera 5 I²C Data |  |
| BF22 | GPIO_57 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP1_SE6_L1 |  |  | QUP1 SE6 lane 1: UART_RFR/I2C_SCL |  |
|  |  | QUP1_SE6_L3 |  |  | QUP1 SE6 lane 3: UART_RX |  |
|  |  | CCI_TIMER9 |  |  | Camera 9 control interface timer |  |
|  |  | CCI_I2C_SCL5 |  |  | Camera 5 I²C Clock |  |
| BB10 | GPIO_58 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CCI_I2C_SDA7 |  |  | Camera 7 I²C Data |  |
|  |  | BOOT_CONFIG[11] |  |  | Boot configuration bit 11 |  |
| BC11 | GPIO_59 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CCI_I2C_SCL7 |  |  | Camera 7 I²C clock |  |
| BB12 | GPIO_60 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SDA0 |  |  | Camera 0 I²C Data |  |
| BC13 | GPIO_61 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SCL0 |  |  | Camera 0 I²C clock |  |
| BB14 | GPIO_62 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SDA2 |  |  | Camera 2 I²C Data |  |
| AY14 | GPIO_63 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SCL2 |  |  | Camera 2 I²C clock |  |
| BA15 | GPIO_64 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SDA4 |  |  | Camera 4 I²C Data |  |
| BC15 | GPIO_65 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SCL4 |  |  | Camera 4 I²C clock |  |
| BB16 | GPIO_66 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SDA6 |  |  | Camera 6 I²C Data |  |
|  |  | CCI_ASYNC_IN5 |  |  | Camera control interface async 5 |  |
| AY16 | GPIO_67 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_I2C_SCL6 |  |  | Camera 6 I²C clock |  |
| BC33 | GPIO_68 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_TIMER0 |  |  | Camera 0 control interface timer |  |
|  |  | CCI_ASYNC_IN0 |  |  | Camera control interface async 0 |  |
| BA35 | GPIO_69 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_TIMER1 |  |  | Camera 1 control interface timer |  |
|  |  | CCI_ASYNC_IN1 |  |  | Camera control interface async 1 |  |
| AY36 | GPIO_70 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_TIMER2 |  |  | Camera 2 control interface timer |  |
|  |  | CCI_ASYNC_IN2 |  |  | Camera control interface async 2 |  |
| BB34 | GPIO_71 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | CCI_TIMER3 |  |  | Camera 3 control interface timer |  |
|  |  | CCI_ASYNC_IN3 |  |  | Camera control interface async 3 |  |
| BB32 | GPIO_72 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CAM_MCLK0 |  |  | Camera 0 MCLK |  |
| BA33 | GPIO_73 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CAM_MCLK1 |  |  | Camera 1 MCLK |  |
| AY34 | GPIO_74 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CAM_MCLK2 |  |  | Camera 2 MCLK |  |
| BA31 | GPIO_75 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | CAM_MCLK3 |  |  | Camera 3 MCLK |  |
| BC29 | GPIO_76 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BB30 | GPIO_77 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| AY32 | GPIO_78 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| AY30 | GPIO_79 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
| BC27 | GPIO_80 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE0_L0 |  |  | QUP2 SE0 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | GP_PDM_MIRA[0] |  |  | General-purpose PDM output 0 A |  |
| BA27 | GPIO_81 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE0_L1 |  |  | QUP2 SE0 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | GP_PDM_MIRB[0] |  |  | General-purpose PDM output 0 B |  |
| AY26 | GPIO_82 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE0_L2 |  |  | QUP2 SE0 lane 2: UART_TX/SPI-M_SCLK |  |
|  |  | MDP_VSYNC_S |  |  | MDP vertical sync |  |
|  |  | GCC_GP1_CLK_MIRA |  |  | General-purpose Clock 1 A |  |
| BB26 | GPIO_83 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE0_L3 |  |  | QUP2 SE0 lane 3: UART_RX/SPI-M_CS0 |  |
|  |  | MDP_VSYNC_E |  |  | MDP vertical sync – external |  |
|  |  | GCC_GP2_CLK_MIRA |  |  | General-purpose Clock 2 A |  |
| BC25 | GPIO_84 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE1_L0 |  |  | QUP2 SE1 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | QUP2_SE5_L2 |  |  | QUP2 SE5 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | MDP_VSYNC_P |  |  | MDP vertical sync – Primary |  |
|  |  | GCC_GP3_CLK_MIRA |  |  | General-purpose Clock 3 A |  |
| BA25 | GPIO_85 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE1_L1 |  |  | QUP2 SE1 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | QUP2_SE5_L3 |  |  | QUP2 SE5 lane 3: UART_RX/SPI-M_CS0/SPI-M_CS |  |
| AY24 | GPIO_86 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE2_L0 |  |  | QUP2 SE2 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BC23 | GPIO_87 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE2_L1 |  |  | QUP2 SE2 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| AY22 | GPIO_88 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE2_L2 |  |  | QUP2 SE2 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
| BA23 | GPIO_89 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE2_L3 |  |  | QUP2 SE2 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
| BB22 | GPIO_90 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE2_L4 |  |  | QUP2 SE2 lane 4: SPI-M_CS1 |  |
| BC21 | GPIO_91 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE3_L0 |  |  | QUP2 SE3 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| BA21 | GPIO_92 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE3_L1 |  |  | QUP2 SE3 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/SPI-M_MOSI |  |
| AY20 | GPIO_93 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | QUP2_SE3_L2 |  |  | QUP2 SE3 lane 2: UART_TX/HS-UART_TX/SPI-M_SCLK |  |
| BB20 | GPIO_94 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE3_L3 |  |  | QUP2 SE3 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
| BC19 | GPIO_95 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE4_L0 |  |  | QUP2 SE4 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
|  |  | QUP2_SE6_L2 |  |  | QUP2 SE6 lane 2: UART_TX/SPI-M_SCLK |  |
| BA19 | GPIO_96 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE4_L1 |  |  | QUP2 SE4 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
|  |  | QUP2_SE6_L3 |  |  | QUP2 SE6 lane 3: UART_RX/SPI-M_CS0 |  |
| AY18 | GPIO_97 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE6_L0 |  |  | QUP2 SE6 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | QUP2_SE4_L2 |  |  | QUP2 SE4 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
| BB18 | GPIO_98 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE6_L1 |  |  | QUP2 SE6 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI |  |
|  |  | QUP2_SE4_L3 |  |  | QUP2 SE4 lane 3: UART_RX/SPI-M_CS0/SPI-M_CS |  |
| BA17 | GPIO_99 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE5_L0 |  |  | QUP2 SE5 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
|  |  | QUP2_SE1_L2 |  |  | QUP2 SE1 lane 2: UART_TX/SPI-M_SCLK |  |
| BC17 | GPIO_100 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | QUP2_SE5_L1 |  |  | QUP2 SE5 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
|  |  | QUP2_SE1_L3 |  |  | QUP2 SE1 lane 3: UART_RX/SPI-M_CS0 |  |
| BA37 | GPIO_101 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EDP0_HOT_PLUG_DETECT |  |  | Embedded DisplayPort 0 hot plug detect |  |
| BB38 | GPIO_102 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EDP1_HOT_PLUG_DETECT |  |  | Embedded DisplayPort 1 hot plug detect |  |
| AY40 | GPIO_103 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EDP3_HOT_PLUG_DETECT |  |  | Embedded DisplayPort 3 hot plug detect |  |
| AY38 | GPIO_104 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | EDP2_HOT_PLUG_DETECT |  |  | Embedded DisplayPort 2 hot plug detect |  |
| AP78 | GPIO_105 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | MI2S_MCLK0 |  |  | MI2S master clock 0 |  |
|  |  | BOOT_CONFIG[2] |  |  | Boot configuration bit 2 |  |
| AP80 | GPIO_106 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | MI2S1_SCK_OR_HS3_MI2S_SCK |  |  | MI2S 1 clock or high-speed 3 MI2S clock |  |
|  |  | BOOT_CONFIG[3] |  |  | Boot configuration bit 3 |  |
| AR71 | GPIO_107 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | MI2S1_WS_OR_HS3_MI2S_WS |  |  | MI2S 1 word select or high-speed 3 MI2S word select and synchronization |  |
|  |  | RESERVED |  |  | Reserved boot configuration pin. See QCS9075 Technical Reference Manual (80-73417-5) for details. |  |
| AR73 | GPIO_108 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | MI2S1_DATA0_OR_HS3_MI2S_DATA0 |  |  | MI2S 1 serial data channel 0 or high speed 3 MI2S serial data channel 0 |  |
| AR75 | GPIO_109 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | MI2S1_DATA1_OR_HS3_MI2S_DATA1 |  |  | MI2S 1 serial data channel 1 or high speed 3 MI2S serial data channel 1 |  |
| AR77 | GPIO_110 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | MI2S2_SCK_OR_HS4_MI2S_SCK |  |  | MI2S 2 clock or High-speed 4 MI2S clock |  |
|  |  | BOOT_CONFIG[4] |  |  | Boot configuration bit 4 |  |
| AR81 | GPIO_111 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | MI2S2_WS_OR_HS4_MI2S_WS |  |  | MI2S 2 serial data word select or high-speed 4 MI2S 2 serial data word select and synchronization |  |
| AT70 | GPIO_112 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | MI2S2_DATA0_OR_HS4_MI2S_DATA0 |  |  | MI2S 2 serial data channel 0 or high speed 4 MI2S serial data channel 0 |  |
| AT72 | GPIO_113 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | MI2S2_DATA1_OR_HS4_MI2S_DATA1 |  |  | MI2S 2 serial data channel 1 or high speed 4 MI2S serial data channel 1 |  |
|  |  | AUDIO_REF_CLK |  |  | Audio reference clock |  |
| AT76 | GPIO_114 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S0_SCK |  |  | High-speed 0 MI2S clock |  |
| AT78 | GPIO_115 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S0_WS |  |  | High-speed 0 MI2S word select |  |
| AU71 | GPIO_116 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S0_DATA0 |  |  | High-speed 0 MI2S data 0 |  |
| AU73 | GPIO_117 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S0_DATA1 |  |  | High-speed 0 MI2S data 1 |  |
|  |  | MI2S_MCLK1 |  |  | MI2S master clock 1 |  |
| AU75 | GPIO_118 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S1_WS |  |  | High-speed 1 MI2S word select |  |
| AU77 | GPIO_119 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S1_SCK |  |  | High-speed 1 MI2S clock |  |
| AV70 | GPIO_120 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S1_DATA0 |  |  | High-speed 1 MI2S data 0 |  |
| AV72 | GPIO_121 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S1_DATA1 |  |  | High-speed 1 MI2S data 1 |  |
| AW71 | GPIO_122 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S2_SCK |  |  | High-speed 2 MI2S clock |  |
| AW73 | GPIO_123 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S2_WS |  |  | High-speed 2 MI2S word select |  |
| AW75 | GPIO_124 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S2_DATA0 |  |  | High-speed 2 MI2S data 0 |  |
| AW77 | GPIO_125 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | HS_I2S2_DATA1 |  |  | High-speed 2 MI2S data 1 |  |
| AJ77 | GPIO_126 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_0 |  |  | See MD_LPASS pins for details |  |
| AK72 | GPIO_127 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_1 |  |  | See MD_LPASS pins for details |  |
| AK76 | GPIO_128 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_2 |  |  | See MD_LPASS pins for details |  |
| AK78 | GPIO_129 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_3 |  |  | See MD_LPASS pins for details |  |
| AK80 | GPIO_130 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_4 |  |  | See MD_LPASS pins for details |  |
| AL71 | GPIO_131 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_5 |  |  | See MD_LPASS pins for details |  |
| AL73 | GPIO_132 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_6 |  |  | See MD_LPASS pins for details |  |
| AL75 | GPIO_133 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_7 |  |  | See MD_LPASS pins for details |  |
| AL77 | GPIO_134 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_8 |  |  | See MD_LPASS pins for details |  |
| AL81 | GPIO_135 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_9 |  |  | See MD_LPASS pins for details |  |
| AM70 | GPIO_136 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_10 |  |  | See MD_LPASS pins for details |  |
| AM72 | GPIO_137 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_11 |  |  | See MD_LPASS pins for details |  |
| AM76 | GPIO_138 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_15 |  |  | See MD_LPASS pins for details |  |
| AM78 | GPIO_139 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_16 |  |  | See MD_LPASS pins for details |  |
| AM80 | GPIO_140 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_14 |  |  | See MD_LPASS pins for details |  |
| AN71 | GPIO_141 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_12 |  |  | See MD_LPASS pins for details |  |
| AN73 | GPIO_142 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_13 |  |  | See MD_LPASS pins for details |  |
| AN75 | GPIO_143 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_17 |  |  | See MD_LPASS pins for details |  |
| AN77 | GPIO_144 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_18 |  |  | See MD_LPASS pins for details |  |
| AN81 | GPIO_145 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | LPASS_19 |  |  | See MD_LPASS pins for details |  |
| AP70 | GPIO_146 |  | PX_3 | PD:nppukp | Configurable I/O | Y |
|  |  | LPASS_20 |  |  | See MD_LPASS pins for details |  |
| AP72 | GPIO_147 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_21 |  |  | See MD_LPASS pins for details |  |
| AP76 | GPIO_148 |  | PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | LPASS_22 |  |  | See MD_LPASS pins for details |  |

#### RTSS I/O pins

| Pin number | RTSS I/O | Alternate functions | Pad voltage | Pad type | Functional description | Wakeup function |
|---|---|---|---|---|---|---|
| P4 | RTSS_IO_0 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE0_L0 |  |  | RTSS QUP0 SE0 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
| P2 | RTSS_IO_1 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE0_L1 |  |  | RTSS QUP0 SE0 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
| R3 | RTSS_IO_2 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_QUP0_SE1_L0 |  |  | RTSS QUP0 SE1 lane 0: UART_CTS/I2C_SDA/SPI-M_MISO/SPI-S_MISO |  |
| R5 | RTSS_IO_3 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE1_L1 |  |  | RTSS QUP0 SE1 lane 1: UART_RFR/I2C_SCL/SPI-M_MOSI/SPI-S_MOSI |  |
| T2 | RTSS_IO_4 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE1_L2 |  |  | RTSS QUP0 SE1 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | RTSS_QUP0_SE3_L2 |  |  | RTSS QUP0 SE3 lane 2: UART_TX/HSUART_TX/SPI-M_SCLK |  |
| T4 | RTSS_IO_5 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE1_L3 |  |  | RTSS QUP0 SE1 lane 3: UART_RX/SPI-M_CS0/SPI-S_CS |  |
|  |  | RTSS_QUP0_SE3_L3 |  |  | RTSS QUP0 SE3 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
| U1 | RTSS_IO_6 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE2_L2 |  |  | RTSS QUP0 SE2 lane 2: UART_TX/HSUART_TX/SPI-M_SCLK |  |
|  |  | RTSS_QUP0_SE0_L2 |  |  | RTSS QUP0 SE0 lane 2: UART_TX/SPI-M_SCLK/SPI-S_SCLK |  |
|  |  | RTSS_BOOT_CONFIG[13] |  |  | RTSS Boot configuration bit 13 |  |
| U3 | RTSS_IO_7 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_QUP0_SE2_L3 |  |  | RTSS QUP0 SE2 lane 3: UART_RX/HS-UART_RX/SPI-M_CS0 |  |
|  |  | RTSS_QUP0_SE0_L3 |  |  | RTSS QUP0 SE0 lane 3: UART_RX/SPI-M_CS0/SPI-S_CS |  |
|  |  | RTSS_BOOT_CONFIG[14] |  |  | RTSS Boot configuration bit 14 |  |
| U5 | RTSS_IO_8 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE3_L0 |  |  | RTSS QUP0 SE3 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
|  |  | RTSS_QUP0_SE2_L0 |  |  | RTSS QUP0 SE2 lane 0: UART_CTS/HS-UART_CTS/I2C_SDA/SPI-M_MISO |  |
| V2 | RTSS_IO_9 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE3_L1 |  |  | RTSS QUP0 SE3 lane 1: UART_RFR/HS-UART_RFR/I2C_SCL/ SPI-M_MOSI |  |
|  |  | RTSS_QUP0_SE2_L1 |  |  | RTSS QUP0 SE2 lane 1: UART_RFR/HS-UART_RFR /I2C_SCL/SPI-M_MOSI |  |
| V4 | RTSS_IO_10 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_QUP0_SE4_L0 |  |  | RTSS QUP0 SE4 lane 0: UART_CTS/I2C_SDA/ SPI-M_MISO |  |
| W3 | RTSS_IO_11 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE4_L1 |  |  | RTSS QUP0 SE4 lane 1: UART_RFR/ / I2C_SCL/ SPI-M_MOSI |  |
| W5 | RTSS_IO_12 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE4_L2 |  |  | RTSS QUP0 SE4 lane 2: UART_TX/SPI-M_SCLK |  |
| Y2 | RTSS_IO_13 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE4_L3 |  |  | RTSS QUP0 SE4 lane 3: UART_RX/SPI-M_CS0 |  |
| Y4 | RTSS_IO_14 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_QUP0_SE4_L4 |  |  | RTSS QUP0 SE4 lane 4: SPI-M_CS1 |  |
|  |  | RTSS_BOOT_CONFIG[6] |  |  | RTSS Boot configuration bit 6 |  |
| AA5 | RTSS_IO_15 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_FORCED_USB_BOOT |  |  | Bootstrap to enter USB0 emergency download mode for RTSS domain. See QCS9075 Technical Reference Manual (80-73417-5) for details. |  |
| AA3 | RTSS_IO_16 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_RGMII_VOL_SEL |  |  | Voltage selection pin for RTSS RGMII interface |  |
| AA1 | RTSS_IO_17 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_BOOT_CONFIG[11] |  |  | RTSS Boot configuration bit 11 |  |
| T6 | RTSS_IO_18 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_BOOT_CONFIG[12] |  |  | RTSS Boot configuration bit 12 |  |
| AV6 | RTSS_IO_19 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_ERR1 |  |  | RTSS error 1 (default output LOW) |  |
| AU5 | RTSS_IO_20 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_ERR2 |  |  | RTSS SS error 1 (default output HIGH) |  |
| BB8 | RTSS_IO_21 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_PHY_INTR_N |  |  | RTSS Ethernet interrupt 0 |  |
| BB6 | RTSS_IO_22 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_MDC |  |  | RTSS RGMII 0 management interface clock |  |
| BC7 | RTSS_IO_23 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_MDIO |  |  | RTSS RGMII 0 management interface clock |  |
| BA3 | RTSS_IO_24 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RXC |  |  | RTSS RGMII 0 receive clock signal |  |
| AY4 | RTSS_IO_25 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RX_CTL |  |  | RTSS RGMII 0 receive control |  |
| AY2 | RTSS_IO_26 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RXD0 |  |  | RTSS RGMII 0 receive data 0 |  |
| AW5 | RTSS_IO_27 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RXD1 |  |  | RTSS RGMII 0 receive data 1 |  |
| AW3 | RTSS_IO_28 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RXD2 |  |  | RTSS RGMII 0 receive data 2 |  |
| AW1 | RTSS_IO_29 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_RXD3 |  |  | RTSS RGMII 0 receive data 3 |  |
| BC1 | RTSS_IO_30 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TXC |  |  | RTSS RGMII 0 transmit clock signal |  |
| BC3 | RTSS_IO_31 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TX_CTL |  |  | RTSS RGMII 0 transmit control |  |
| BC5 | RTSS_IO_32 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TXD0 |  |  | RTSS RGMII 0 transmit data 0 |  |
| BB4 | RTSS_IO_33 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TXD1 |  |  | RTSS RGMII 0 transmit data 1 |  |
| BA5 | RTSS_IO_34 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TXD2 |  |  | RTSS RGMII 0 transmit data 2 |  |
| BB2 | RTSS_IO_35 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_RGMII0_TXD3 |  |  | RTSS RGMII 0 transmit data 3 |  |
| BA7 | RTSS_IO_36 |  | RTSS_PX_8 | PD:nppukp | RTSS domain configurable I/O | N |
| AB2 | RTSS_IO_37 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN0_TX |  |  | RTSS CAN 0 transmit |  |
|  |  | RTSS_BOOT_CONFIG[0] |  |  | RTSS Boot configuration bit 0 |  |
| AB4 | RTSS_IO_38 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN0_RX |  |  | RTSS CAN 0 receive |  |
|  |  | RTSS_CC_GP2_CLK_MIRA |  |  | RTSS Global general-purpose clock 2 A |  |
| AD4 | RTSS_IO_39 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN1_TX |  |  | RTSS CAN 1 transmit |  |
|  |  | RTSS_BOOT_CONFIG[1] |  |  | RTSS Boot configuration bit 1 |  |
| AC3 | RTSS_IO_40 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN1_RX |  |  | RTSS CAN 1 receive |  |
|  |  | RTSS_CC_GP2_CLK_MIRB |  |  | RTSS Global general-purpose clock 2 B |  |
| AD2 | RTSS_IO_41 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN2_TX |  |  | RTSS CAN 2 transmit |  |
| AE5 | RTSS_IO_42 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN2_RX |  |  | RTSS CAN 2 receive |  |
|  |  | RTSS_CC_GP3_CLK_MIRA |  |  | RTSS Global general-purpose clock 3 A |  |
| AE3 | RTSS_IO_43 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN3_TX |  |  | RTSS CAN 3 transmit |  |
|  |  | RTSS_BOOT_CONFIG[2] |  |  | RTSS Boot configuration bit 2 |  |
| AE1 | RTSS_IO_44 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN3_RX |  |  | RTSS CAN 3 receive |  |
|  |  | RTSS_CC_GP3_CLK_MIRB |  |  | RTSS Global general-purpose clock 3 B |  |
| AF4 | RTSS_IO_45 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN4_TX |  |  | RTSS CAN 4 transmit |  |
|  |  | RTSS_BOOT_CONFIG[3] |  |  | RTSS Boot configuration bit 3 |  |
| AF2 | RTSS_IO_46 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN4_RX |  |  | RTSS CAN 4 receive |  |
|  |  | RTSS_CC_GP4_CLK_MIRA |  |  | RTSS Global general-purpose clock 4 A |  |
| AG5 | RTSS_IO_47 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN5_TX |  |  | RTSS CAN 5 transmit |  |
| AG3 | RTSS_IO_48 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN5_RX |  |  | RTSS CAN 5 receive |  |
|  |  | RTSS_EMAC0_PTP_PPS_O_1_MIRA |  |  | RTSS EMAC0 configurable PPS output 1 A |  |
|  |  | RTSS_EMAC0_PTP_AUX_TS_I_0_MIRA |  |  | RTSS EMAC0 trigger 0 A for Auxiliary snapshot |  |
|  |  | RTSS_CC_GP4_CLK_MIRB |  |  | RTSS Global general-purpose clock 4 B |  |
| AH4 | RTSS_IO_49 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN6_TX |  |  | RTSS CAN 6 transmit |  |
|  |  | RTSS_EMAC0_PTP_PPS_O_0_MIRA |  |  | RTSS EMAC0 configurable PPS output 0 A |  |
| AH2 | RTSS_IO_50 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN6_RX |  |  | RTSS CAN 6 receive |  |
|  |  | RTSS_EMAC0_PTP_PPS_O_0_MIRB |  |  | RTSS EMAC0 configurable PPS output 0 B |  |
|  |  | RTSS_CC_GP5_CLK_MIRA |  |  | RTSS Global general-purpose clock 5 A |  |
| AJ5 | RTSS_IO_51 |  | RTSS_PX_3 | PU:nppdkp | RTSS domain configurable I/O | N |
|  |  | RTSS_CAN7_TX |  |  | RTSS CAN 7 transmit |  |
|  |  | RTSS_EMAC0_PTP_PPS_O_1_MIRB |  |  | RTSS EMAC0 configurable PPS output 1 B |  |
| AJ3 | RTSS_IO_52 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_CAN7_RX |  |  | RTSS CAN 7 receive |  |
|  |  | RTSS_CC_GP5_CLK_MIRB |  |  | RTSS Global general-purpose clock 5 B |  |
| AV4 | RTSS_IO_53 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
| AJ1 | RTSS_IO_54 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
| AK4 | RTSS_IO_55 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_PTP_PPS_O_2 |  |  | RTSS EMAC0 configurable PPS output 2 |  |
| AK2 | RTSS_IO_56 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_PTP_AUX_TS_I_0_MIRB |  |  | RTSS EMAC0 trigger 0 B for Auxiliary snapshot |  |
|  |  | RTSS_EMAC0_PTP_PPS_O_3 |  |  | RTSS EMAC0 configurable PPS output 3 |  |
| AT6 | RTSS_IO_57 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_MCG_PST_TRIG_LW[0] |  |  | RTSS EMAC0 trigger input 0 for Media clock generation |  |
| AT4 | RTSS_IO_58 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_MCG_PST_TRIG_LW[1] |  |  | RTSS EMAC0 trigger input 1 for Media clock generation |  |
| AU3 | RTSS_IO_59 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_MCG_PST_TRIG_LW[2] |  |  | RTSS EMAC0 trigger input 2 for Media clock generation |  |
|  |  | RTSS_CC_GP1_CLK_MIRA |  |  | RTSS Global general-purpose clock 1 A |  |
| AV2 | RTSS_IO_60 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_EMAC0_MCG_PST_TRIG_LW[3] |  |  | RTSS EMAC0 trigger input 3 for Media clock generation |  |
|  |  | RTSS_CC_GP1_CLK_MIRB |  |  | RTSS Global general-purpose clock 1 B |  |
| AU1 | RTSS_IO_61 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
| AY8 | RTSS_IO_62 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
| AW9 | RTSS_IO_63 |  | RTSS_PX_3 | PD:nppukp | Configurable I/O | N |
|  |  | PRTSS_ERR_N |  |  | PMIC RTSS domain error signal active low (internally pulled up to 1.8 V). Indicates PMIC error and resulting PMIC shutdown. |  |
| AV10 | RTSS_IO_64 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
| AW7 | RTSS_IO_65 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | Y |
|  |  | RTSS_PWR_READY |  |  | RTSS power ready |  |
| AV8 | RTSS_IO_66 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_SLP_EN |  |  | RTSS sleep enable |  |
| J7 | RTSS_IO_67 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_CS_N_0 |  |  | RTSS OSPI0 chip select 0 |  |
| K6 | RTSS_IO_68 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DQS |  |  | RTSS OSPI0 differential data strobe |  |
| K8 | RTSS_IO_69 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
| K10 | RTSS_IO_70 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_CLK |  |  | RTSS OSPI0 clock |  |
| L7 | RTSS_IO_71 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[0] |  |  | RTSS OSPI0 data 0 |  |
| L9 | RTSS_IO_72 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[1] |  |  | RTSS OSPI0 data 1 |  |
| M6 | RTSS_IO_73 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[2] |  |  | RTSS OSPI0 data 2 |  |
| M8 | RTSS_IO_74 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[3] |  |  | RTSS OSPI0 data 3 |  |
| M10 | RTSS_IO_75 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[4] |  |  | RTSS OSPI0 data 4 |  |
| N7 | RTSS_IO_76 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[5] |  |  | RTSS OSPI0 data 5 |  |
| N9 | RTSS_IO_77 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[6] |  |  | RTSS OSPI0 data 6 |  |
| P10 | RTSS_IO_78 |  | RTSS_PX_3 | PD:nppukp | RTSS domain configurable I/O | N |
|  |  | RTSS_OSPI0_DATA[7] |  |  | RTSS OSPI0 data 7 |  |

#### MD_LPASS pins

| LPASS I/O | Alternate function | Functional description |
|---|---|---|
| LPASS_0 |  | (GPIO_126) |
|  | LPI_QUA_MI2S_SCK | LPI quad I²S clock |
| LPASS_1 |  | (GPIO_127) |
|  | LPI_QUA_MI2S_WS | LPI quad I²S word select |
| LPASS_2 |  | (GPIO_128) |
|  | LPI_QUA_MI2S_DATA0 | LPI quad I²S serial channel 0 |
| LPASS_3 |  | (GPIO_129) |
|  | LPI_QUA_MI2S_DATA1 | LPI quad I²S serial channel 1 |
| LPASS_4 |  | (GPIO_130) |
|  | LPI_QUA_MI2S_DATA2 | LPI quad I²S serial channel 2 |
| LPASS_5 |  | (GPIO_131) |
|  | LPI_QUA_MI2S_DATA3 | LPI quad I²S serial channel 3 |
|  | EXT_MCLK1_C | MI2S external MCLK1 C |
| LPASS_6 |  | (GPIO_132) |
|  | LPI_I2S1_CLK | LPI I2S 1 clock |
| LPASS_7 |  | (GPIO_133) |
|  | LPI_I2S1_WS | LPI I2S 1 word select |
| LPASS_8 |  | (GPIO_134) |
|  | LPI_I2S1_DATA0 | LPI I2S 1 serial channel 0 |
| LPASS_9 |  | (GPIO_135) |
|  | LPI_I2S1_DATA1 | LPI I2S 1 serial channel 1 |
|  | EXT_MCLK1_B | MI2S external MCLK1 B |
| LPASS_10 |  | (GPIO_136) |
|  | LPI_I2S2_CLK | LPI I2S 2 clock |
| LPASS_11 |  | (GPIO_137) |
|  | LPI_I2S2_WS | LPI I2S 2 word select |
| LPASS_12 |  | (GPIO_141) |
|  | LPI_I2S4_CLK | LPI I2S 4 clock |
| LPASS_13 |  | (GPIO_142) |
|  | LPI_I2S4_WS | LPI I2S 4 word select |
|  | EXT_MCLK1_A | MI2S external MCLK1 A |
| LPASS_14 |  | (GPIO_140) |
|  | EXT_MCLK1_D | MI2S external MCLK1 D |
| LPASS_15 |  | (GPIO_138) |
|  | LPI_I2S2_DATA0 | LPI I2S 2 serial channel 0 |
| LPASS_16 |  | (GPIO_139) |
|  | LPI_I2S2_DATA1 | LPI I2S 2 serial channel 1 |
| LPASS_17 |  | (GPIO_143) |
|  | LPI_I2S4_DATA0 | LPI I2S 4 serial channel 0 |
| LPASS_18 |  | (GPIO_144) |
|  | LPI_I2S4_DATA1 | LPI I2S 4 serial channel 1 |
| LPASS_19 |  | (GPIO_145) |
|  | LPI_I2S3_CLK | LPI I2S 3 clock |
| LPASS_20 |  | (GPIO_146) |
|  | LPI_I2S3_WS | LPI I2S 3 word select |
| LPASS_21 |  | (GPIO_147) |
|  | LPI_I2S3_DATA0 | LPI I2S 3 serial channel 0 |
| LPASS_22 |  | (GPIO_148) |
|  | LPI_I2S3_DATA1 | LPI I2S 3 serial channel 1 |
|  | EXT_MCLK1_E | MI2S external MCLK1 E |

#### Power-supply pins

| Pin number | Pin name | Functional description |
|---|---|---|
| AA53, AA57, N49, N51, N55, N57, P58, R49, R57, R59, T48, U49, U57, U59, V48, W57, W59, Y58 | VDD_APC0 | Power for the cluster 0 of Kryo Gold Prime processors |
| AA37, AA41, AA43, M38, M42, M46, N37, N47, P38, P46, R37, R47, T38, V38, V44, W37, W45, Y38 | VDD_APC1 | Power for the cluster 1 of Kryo Gold Prime processors |
| U47 | VDD_A_APC_CS_1P2 | Power for application processor current sensor 1.2 V analog circuits |
| AV50 | VDD_A_CSI_0_1P2 | Power for MIPI CSI0 1.2 V analog circuits |
| AT50 | VDD_A_CSI_0_1_0P9 | Power for MIPI CSI0/CSI1 0.9 V analog circuits |
| AV52 | VDD_A_CSI_1_1P2 | Power for MIPI CSI1 1.2 V analog circuits |
| AV54 | VDD_A_CSI_2_1P2 | Power for MIPI CSI2 1.2 V analog circuits |
| AT54 | VDD_A_CSI_2_3_0P9 | Power for MIPI CSI2/CSI3 0.9 V analog circuits |
| AV56 | VDD_A_CSI_3_1P2 | Power for MIPI CSI3 1.2 V analog circuits |
| AU45 | VDD_A_DSI_0_0P9 | Power for MIPI DSI0 0.9 V analog circuits |
| AV46, AV48 | VDD_A_DSI_0_1_1P2 | Power for MIPI DSI0/DSI1 1.2 V analog circuits |
| AT46 | VDD_A_DSI_0_PLL_0P9 | Power for MIPI DSI0 PLL 0.9 V |
| AU49 | VDD_A_DSI_1_0P9 | Power for MIPI DSI1 0.9 V analog circuits |
| AT48 | VDD_A_DSI_1_PLL_0P9 | Power for MIPI DSI1 PLL 0.9 V |
| M26, M28, M32, M34 | VDD_A_EBI_01_0P9 | Power for EBI0/EBI1 PHY 0.9 V circuits |
| M52, M54, M58, M60, R63, U63, V60, W63 | VDD_A_EBI_23_45_0P9 | Power for EBI2/EBI3/EBI4/EBI5 PHY 0.9 V circuits |
| K24, K34, K50, K58, N65, V66 | VDD_A_EBI_PLL | Power for EBI PHY PLL circuits |
| AJ59 | VDD_A_EDP_0_0P9 | Power for EDP 0 0.9 V circuits |
| AH64 | VDD_A_EDP_0_1P2 | Power for EDP 0 1.2 V circuits |
| AK60 | VDD_A_EDP_1_0P9 | Power for EDP 1 0.9 V circuits |
| AK64 | VDD_A_EDP_1_1P2 | Power for EDP 1 1.2 V circuits |
| AK62 | VDD_A_EDP_2_0P9 | Power for EDP 2 0.9 V circuits |
| AL63 | VDD_A_EDP_2_1P2 | Power for EDP 2 1.2 V circuits |
| AM62 | VDD_A_EDP_3_0P9 | Power for EDP 3 0.9 V circuits |
| AL61 | VDD_A_EDP_3_1P2 | Power for EDP 3 1.2 V circuits |
| AK58 | VDD_A_NSP0_CS_1P2 | Power for HTP0 current sensor 1.2 V circuits |
| V32 | VDD_A_NSP1_CS_1P2 | Power for HTP1 current sensor 1.2V circuits |
| T18, T20, U21 | VDD_A_PCIE_0_0P9 | Power for PCIe 0 0.9 V circuits |
| V20, V22, W21, W23 | VDD_A_PCIE_1_0P9 | Power for PCIe 1 0.9V circuits |
| T16 | VDD_A_PCIE_0_PLL_1P2 | Power for PCIe 0 PLL 1.2 V circuits |
| U13 | VDD_A_PCIE_1_PLL_1P2 | Power for PCIe 1 PLL 1.2 V circuits |
| AC65 | VDD_A_REFGEN_0P875 | Power for high-speed interface reference generation circuits – 0.875 V |
| AD66 | VDD_A_REFGEN_1P2 | Power for high-speed interface reference generation circuits – 1.2 V |
| Y22 | VDD_A_SGMII_0_0P9 | Power for serial gigabit media-independent interface 0<br>0.9 V |
| AA19 | VDD_A_SGMII_0_1P2 | Power for serial gigabit media-independent interface 0<br>1.2 V |
| AA21 | VDD_A_SGMII_1_0P9 | Power for serial gigabit media-independent interface 1<br>0.9 V |
| AB20 | VDD_A_SGMII_1_1P2 | Power for serial gigabit media-independent interface 1<br>1.2 V |
| AH60, AF60 | VDD_A_UFS_0_0P9 | Power for the UFS 0.9 V analog circuits |
| AG63, AG61 | VDD_A_UFS_0_1P2 | Power for the UFS 1.2 V analog circuits |
| K36 | VDD_A_USBHS_0_0P9 | Power for USB high-speed 0 0.9 V circuits |
| J37 | VDD_A_USBHS_0_1P8 | Power for USB high-speed 0 1.8 V circuits |
| J39 | VDD_A_USBHS_0_3P1 | Power for USB high-speed 0 3.1 V circuits |
| K40 | VDD_A_USBHS_1_0P9 | Power for USB high-speed 1 0.9 V circuits |
| J41 | VDD_A_USBHS_1_1P8 | Power for USB high-speed 1 1.8 V circuits |
| J43 | VDD_A_USBHS_1_3P1 | Power for USB high-speed 1 3.1 V circuits |
| L45 | VDD_A_USBHS_2_0P9 | Power for USB high-speed 2 0.9 V circuits |
| K46 | VDD_A_USBHS_2_1P8 | Power for USB high-speed 2 1.8 V circuits |
| K48 | VDD_A_USBHS_2_3P1 | Power for USB high-speed 2 3.1 V circuits |
| L39 | VDD_A_USBSS_0_0P9 | Power for USB super-speed 0 0.9 V circuits |
| K38 | VDD_A_USBSS_0_1P2 | Power for USB super-speed 0 1.2 V circuits |
| L43 | VDD_A_USBSS_1_0P9 | Power for USB super-speed 1 0.9 V circuits |
| K42 | VDD_A_USBSS_1_1P2 | Power for USB super-speed 1 1.2 V circuits |
| AA35, AB38, AB40, AB44, AB46, AC35, AD50, AD52, AE49, AG49, AJ49, AK50, T36, U35, V34, W35, Y36, Y46 | VDD_CX | Power for digital core circuits |
| AC55, AC59, AC63, AD54, AD56, AD58, AD60, AD64 | VDD_CX_LPI | Power for Low-power island digital core circuits |
| AA61, L23, L25, L27, L31, L33, L35, L49, L51, L53, L57, L59, L61, N61, P62, T62, V62, Y62 | VDD_D_EBI | Power for EBI digital circuits |
| AH24, AH26, AH30, AJ23, AJ25, AJ33, AK34, AL23, AL25, AM36, AN23, AN25, AN35, AP36, AR23, AR25, AR27, AR29, AR31, AR33, AR35, AT26, AT30, AT34, AU29, AU31, AU35, AV24, AV28, AV34 | VDD_GFX | Power for graphics |
| M22, M24, M30, M36 | VDD_IO_EBI_01 | Power for EBI0/EBI1 I/O circuits |
| AA63, M48, M50, M56, N59, R61, U61, W61 | VDD_IO_EBI_23_45 | Power for EBI2/EBI3/EBI4/EBI5 I/O circuits |
| AE35, AF36, AG35, AG37, AH34, AH46, AJ41, AJ45, AK40, AK44, AL45, AM38, AN45, AP38, AR39, AR41, AR45, AR47, AT38, AT42, AU39, AU43, AV38, AV42 | VDD_MM | Power for multimedia subsystem circuits |
| AA51, AB48, AB50, AC47, AC51, AD46, AK46, AL47, AM46, W47, Y48 | VDD_MX_A | Power for always-ON memory circuits |
| AA33, AB34, AC33, AD34, AE33, ,AF48, AG47, AH38, AH48, AJ37, AK36, AL37 | VDD_MX_C | Power for collapsible memory circuits |
| AB54, AB56, AB58, AB60, AB64 | VDD_MX_LPI | Power for Low-power island memory circuit |
| AE53, AE55, AE57, AF58, AG57, AJ51, AJ53, AJ57, AK54, AK56, AM48, AM58, AM60, AP48, AP58, AP60, AR49, AR51, AR55, AR57, AR61 | VDD_NSP0 | Power for Hexagon Tensor Processor 0 |
| AA25, AB24, AC25, AC29, N21, N25, N27, N31, N33, P22, P24, P34, T22, T24, T34, V24, V28, V30, W25, W29, W31 | VDD_NSP1 | Power for Hexagon Tensor Processor 1 |
| AB68 | VDD_PX0 | Power for pad group 0 |
| K30, K54, T66, Y66 | VDD_PX1 | Power for pad group 1 |
| AG67 | VDD_PX10 | Power for pad group 10 |
| AE63, J35 | VDD_PX11 | Power for pad group 11 |
| AB66, AU21, AV32, AV58, AW45, J33 | VDD_PX3 | Power for pad group 3 |
| AB16 | VDD_PX7 | Power for pad group 7 |
| AF66 | VDD_PX9 | Power for pad group 9 |
| AV60, AA67 | VDD_QFPROM | Power for programming the QFPROM |
| AC21 | VDD_QFPROM_RTSS | Power for programming the QFPROM RTSS |
| AE31, AF24, AF28, AF32, AG23, AG27, AG31, AH32 | VDD_RTSS_CX | Power for RTSS digital core circuits |
| AD26, AD30, AE23, AE27, AE29 | VDD_RTSS_MX | Power for RTSS On-chip memory circuits |
| AT20 | VDD_RTSS_PX0 | Power for RTSS pad group 0 |
| AR19 | VDD_RTSS_PX11 | Power for RTSS pad group 11 |
| AF18, AK20, AP20 | VDD_RTSS_PX3 | Power for RTSS pad group 3 |
| AH20 | VDD_RTSS_PX8 | Power for RTSS pad group 8 |
| AD20 | VBIAS_RTSS_RGMII | Power for RTSS_RGMII reference circuits; 0.85 V |

#### Ground pins

| Pin number | Pin name | Functional description |
|---|---|---|
| A9, A29, A47, A67, A75, A77, AA13, AA15,AA17, AA23, AA39, AA45, AA47, AA49, AA55, AA59, AA65, AA75, AA79, AB8, AB12, AB14, AB18, AB22, AB36, AB42, AB52, AB62, AB70, AB72, AB76, AB78, AC1, AC5, AC11, AC13, AC15, AC17, AC19, AC23, AC27, AC31, AC49, AC53, AC57, AC61, AC67, AC69, AC71, AC75, AC79, AD8, AD12, AD14, AD16, AD18, AD22, AD24, AD28, AD32, AD36, AD48, AD62, AD68, AD70, AD74, AD78, AE11, AE13, AE15, AE17, AE19, AE25, AE47, AE51, AE59, AE61, AE65, AE67, AE69, AE71, AE75, AE79, AF8, AF10, AF12, AF14, AF16, AF22, AF26, AF30, AF34, AF46, AF62, AF64, AF68, AF72, AF76, AF78, AG1, AG7, AG11, AG13, AG15, AG17, AG19, AG25, AG29, AG33, AG59, AG65, AG69, AG73, AG79, AH6, AH12, AH14, AH16, AH18, AH28, AH36, AJ55, AH58, AH62, AH66, AH68, AH70, AH76, AJ11, AJ13, AJ15, AJ17, AJ19, AJ21, AJ35, AJ39, AJ43, AJ47, AJ61, AJ63, AJ65, AJ67, AJ69, AJ75, AJ79, AK8, AK12, AK14, AK16, AK18, AK22, AK24, AK38, AK42, AK48, AK52, AK66, AK68, AK70, AK74, AL1, AL5, AL11, AL13, AL15, AL17, AL19, AL21, AL35, AL39, AL59, AL65, AL67, AL69, AL79, AM12, AM14, AM16, AM18, AM20, AM22, AM24, AM64, AM66, AM68, AM74, AN1, AN5, AN11, AN13, AN15, AN17, AN19, AN21, AN37, AN39, AN47, AN59, AN61, AN63, AN65, AN67, AN69, AN79, AP4, AP6, AP12, AP14, AP16, AP18, AP22, AP24, AP46, AP62, AP64, AP66, AP68, AP74, AR5, AR11, AR13, AR15, AR17, AR37, AR43, AR53, AR59, AR65, AR67, AR69, AR79, AT10, AT12, AT14, AT16, AT18, AT24, AT28, AT32, AT36, AT40, AT44, AT52, AT56, AT58, AT60, AT64, AT66, AT68, AT74, AU7, AU9, AU11, AU13, AU17, AU19, AU27, AU33, AU37, AU41, AU47, AU51, AU53, AU55, AU57, AU59, AU61, AU63, AU65, AU67, AU69, AV14, AV16, AV18, AV20, AV22, AV26, AV30, AV36, AV40, AV44, AV62, AV64, AV66, AV68, AV74, AV78, AW13, AW15, AW17, AW19, AW21, AW23, AW25, AW27, AW29, AW31, AW33, AW35, AW37, AW39, AW41, AW43, AW47, AW49, AW51, AW53, AW55, AW57, AW59, AW61, AW63, AW65, AW67, AW69, AY6, AY42, AY44, AY46, AY48, AY50, AY52, AY54, AY56, AY58, AY60, AY66, AY68, AY70, AY72, AY76, AY78, B6, B12, B14, B18, B22, B24, B26, B32, B34, B36, B38, B40, B42, B44, B50, B52, B54, B58, B62, B64, B70, B72, B76, BA1, BA41, BA43, BA49, BA51, BA53, BA55, BA65, BA67, BA69, BA71, BA77, BB24, BB50, BB52, BB66, BB68, BC31, BC35, BC45, BC59, BC61, BC63, BC77, BD6, BD14, BD22, BD28, BD42, BD44, BD46, BD48, BD54, BD60, BD62, BD64, BE39, BE45, BE47, BE49, BE55, BE57, BE59, BE65, BE67, BE69, BF36, BF46, BF56, BF74, BG5, BG11, BG17, BG23, BG31, BG41, BG51, BG61, BG75, C3, C9, C17, C27, C29, C47, C49, C67, C75, C79, D6, D8, D12, D22, D24, D32, D34, D36, D38, D40, D42, D44, D52, D54, D62, D64, D68, D70, D72, D76, D78, E3, E11, E17, E27, E29, E47, E49, E59, E65, E75, E79, F4, F6, F8, F14, F22, F26, F32, F34, F36, F38, F40, F42, F44, F50, F54, F62, F68, F70, F74, F78, G3, G11, G17, G23, G29, G35, G47, G53, G59, G65, G71, G75, G79, H2, H4, H6, H8, H10, H14, H16, H18, H20, H22, H24, H26, H30, H32, H38, H40, H42, H44, H46, H50, H54, H56, H58, H60, H62, H66, H68, H70, H74, H76, J9, J11, J13, J15, J17, J19, J21, J23, J25, J27, J29, J31, J47, J55, J57, J59, J61, J63, J65, J67, J69, J73, J79, K12, K16, K18, K20, K22, K26, K28, K32, K52, K56, K60, K62, K64, K68, K70, K76, L11, L13, L15, L17, L19, L21, L29, L37, L41, L47, L55, L63, L65, L67, L73, L79, L81, M12, M14, M16, M18, M20, M40, M44, M62, M64, M66, M68, M70, M74, M76, N11, N13, N15, N17, N23, N29, N35, N53, N63, N67, N69, N73, N79, P6, P12, P14, P16, P20, P36, P48, P60, P64, P66, P68, P70, P76, P78, R1, R11, R13, R15, R17, R19, R21, R23, R35, R65, R67, R69, R73, R75, R79, T12, T14, T46, T58, T60, T64, T68, T72, T76, U7, U11, U23, U37, U65, U67, U69, U75, U79, V6, V10, V12, V14, V26, V36, V46, V58, V64, V68, V70, V72, V78, W1, W11, W13, W27, W33, W49, W65, W67, W69, W75, W81, Y6, Y8, Y12, Y14, Y20, Y24, Y34, Y44, Y60, Y64, Y68, Y70, Y72, Y78, | GND | Ground |

#### DNC pins

| Pin number | Pin name | Functional description |
|---|---|---|
| AR21, BB40, BA39, B78, C77, J53, J45, AE21, AG21, AH22, AU23, AT62, P18, H28, H64, AA69, BA29, AA9, H34, H52, J49, AJ81, BB28, AY10, J51, K44, AU25, AR63, N19, AF20, AT22, A1, A3, A79, A81, B2, B80, BE1, BE81, BF2, BF80, BG1, BG3, BG79, BG81, C1, C81 | DNC | Do not connect; do not connect externally. |
