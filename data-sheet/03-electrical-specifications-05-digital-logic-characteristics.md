[← Contents](../README.md)

## 3.5 Digital logic characteristics

A digital I/O’s performance specification depends on its pad type, its usage, and/or its supply voltage.

- Some are dedicated for interconnections between the QCS9075 device and other ICs within the QTI chipset; therefore, specifications are not required.
- Some are defined by existing standards, such as I²C and SPI. QTI devices comply with those standards; therefore, additional specifications are not required.
- All other digital I/Os require performance specifications.
- Back powering protection is not supported in digital pads unless otherwise specified in the following table. All non-bpp digital pads must be kept at less than 50 mV and with a maximum of 1 µA current being injected into the pad to avoid potential back-power scenarios.

**NOTE** Unless otherwise specified, all device characterizations are carried out across the specified operating temperature and voltage ranges.

**Table 3-4  Digital I/Os specified in this section**

| Pad voltage | Usage | Table |
|---|---|---|
| 1.8 V | VDD_PX0, VDD_RTSS_PX0, VDD_PX3, VDD_RTSS_PX3 | Table 3-5 |
| 1.8 V | VDD_RTSS_PX8 | Table 3-7 |
| 1.2 V | VDD_PX9/VDD_PX10 | Table 3-9 |

**Table 3-5  DC specification of 1.8 V I/Os**

| Parameter | Description | Min | Max | Unit |
|---|---|---|---|---|
| V<sub>IH</sub> | High-level input voltage, CMOS/Schmitt (HIHYS_EN = low) | 0.65 × VDD_PXx | VDD_PXx ᵃ + 0.3 | V |
| V<sub>IL</sub> | Low-level input voltage, CMOS/Schmitt (HIHYS_EN = low) | -0.3 | 0.35 × VDD_PXx ᵃ | V |
| V<sub>IH</sub> | High-level input voltage, CMOS/Schmitt (HIHYS_EN = high) | 0.7 × VDD_PXx | VDD_PXx ᵃ +0.3 | V |
| V<sub>IL</sub> | Low-level input voltage, CMOS/Schmitt (HIHYS_EN = high) | -0.3 | 0.3 × VDD_PXx ᵃ | V |
| V<sub>SHYS</sub> | Schmitt hysteresis voltage (HIHYS_EN= low) | 100 | – | mV |
| V<sub>SHYS</sub> | Schmitt hysteresis voltage (HIHYS_EN = high) | 300 | – | mV |
| I<sub>IH</sub> | Input high leakage current | – | 3 | µA |
| I<sub>IL</sub> | Input low leakage current | -1 | – | µA |
| R<sub>PD</sub> | Pull-down resistance | 20k | 60k | Ω |
| R<sub>PU</sub> | Pull-up resistance | 20k | 60k | Ω |
| R<sub>KP</sub> | Bus keeper resistor | 20k | 60k | Ω |
| V<sub>OH</sub> | High-level output voltage, CMOS ᵇ | VDD_PXx ᵃ -0.45 | VDD_PXx ᵃ | V |
| V<sub>OL</sub> | Low-level output voltage, CMOS ᵇ | 0.0 | 0.45 | V |

ᵃ VDD_PXx can be VDD_PX0, VDD_RTSS_PX0, VDD_PX3, VDD_RTSS_PX3 depending on the pad group.

ᵇ V<sub>OL</sub> and V<sub>OH</sub> are measured at I<sub>OL</sub> and I<sub>OH</sub> respectively, with 16 mA current across min and max voltages and operating temperatures. For more information regarding possible drive strength settings, see Table 3-6.

**Table 3-6  Possible drive strength settings**

| BIT configuration | Drive strength (mA) |
|---|---|
| 000 | 2 |
| 001 | 4 |
| 010 | 6 |
| 011 | 8 |
| 100 | 10 |
| 101 | 12 |
| 110 | 14 |
| 111 | 16 |

**Table 3-7  DC specifications for RGMII 1.8 V mode (VDD_RTSS_PX8)**

| Parameter | Description | Min | Max | Unit |
|---|---|---|---|---|
| V<sub>OL</sub> | Low-level output voltage ᵃ | – | 0.45 | V |
| V<sub>OH</sub> | High-level output voltage ᵃ | VDD_PXx - 0.45 | – | V |
| V<sub>IL</sub> | Low-level input voltage | -0.3 | 0.35× VDD_PXx | V |
| V<sub>IH</sub> | High-level input voltage | 0.65× VDD_PXx | VDD_PXx+ 0.3 | V |
| V<sub>HYS</sub> | Input Hysteresis | 100 | – | mV |
| R<sub>PULL-UP</sub> | Pull-up resistance | 20 | 50 | kΩ |
| R<sub>PULL-DOWN</sub> | Pull-down resistance | 20 | 50 | kΩ |
| R<sub>KEEPERUP</sub> | Keeper-up resistance | 20 | 50 | kΩ |
| R<sub>KEEPERDOWN</sub> | Keeper-down resistance | 20 | 50 | kΩ |
| I<sub>IL</sub> | Input low leakage current | – | 5 | μA |
| I<sub>IH</sub> | Input high leakage current | -5 | – | μA |

ᵃ V<sub>OL</sub> and V<sub>OH</sub> are measured at I<sub>OL</sub> and I<sub>OH</sub> respectively, with 12 mA current across min and max voltages and operating temperatures. For more information regarding possible drive strength settings, see Table 3-8

**Table 3-8  Possible drive strength**

| Drive strength | IOL (mA) | IOH (mA) |
|---|---|---|
| 000 | 1.5 | 1.5 |
| 001 | 3.0 | 3.0 |
| 010 | 4.5 | 4.5 |
| 011 | 6.0 | 6.0 |
| 100 | 7.5 | 7.5 |
| 101 | 9.0 | 9.0 |
| 110 | 10.5 | 10.5 |
| 111 | 12.0 | 12.0 |

**NOTE** There is no industry-standard specification for a 1.8 V RGMII interface. Thus, the above specifications are taken from *JESD8-7A, “1.8 V ± 0.15 V (Normal range) and 1.2 V – 1.95 V (Wide range) Power* *Supply Voltage and Interface Standard for Non terminated Digital Integrated Circuits”*.

**Table 3-9  Digital I/O characteristics for UFS_RESET and UFS_REF_CLK (VDD_PX9/VDD_PX10)**

| Parameter | Description | Min | Max | Unit |
|---|---|---|---|---|
| V<sub>OL</sub> | Low-level output voltage ᵃ | 0 | 0.25 × VDD_PXx | V |
| V<sub>OH</sub> | High-level output voltage ᵃ | VDD_PXx × 0.75 | VDD_PXx | V |
| R<sub>PULL-UP</sub> | Pull-up resistance | 20 | 60 | kΩ |
| R<sub>PULL-DOWN</sub> | Pull-down resistance | 20 | 60 | kΩ |
| I<sub>LEAK</sub> | Standby leakage | -10 | 10 | µA |

ᵃ V<sub>OL</sub> and V<sub>OH</sub> are measured at I<sub>OL</sub> and I<sub>OH</sub> respectively, with 4.8 mA current across min and max voltages and operating temperatures.

**NOTE** VDD_PXx can be either VDD_PX9 or VDD_PX10.

**Table 3-10  DC specifications for SPMI (VDD_PX0)**

| Parameter | Description | Min | Max | Unit |
|---|---|---|---|---|
| V<sub>IH</sub> | High-level input voltage | 0.65 × VDD_PXx | VDD_PXx + 0.3 | V |
| V<sub>IL</sub> | Low-level input voltage | -0.3 | 0.35 × VDD_PXx | V |
| V<sub>SHYS</sub> | Schmitt hysteresis voltage | 100 | – | mV |
| I<sub>IH</sub> | Input high leakage current | – | 30 | μA |
| I<sub>IL</sub> | Input low leakage current | -10 | – | μA |
| R<sub>pullup</sub> | Pull-up resistance | 7.5 K | 20 K | Ω |
| R<sub>pulldown</sub> | Pull-down resistance | 10 K | 50 K | Ω |
| R<sub>keeperup</sub> | Keeper-up resistance | 7.5 K | 20 K | Ω |
| R<sub>keeperdown</sub> | Keeper-down resistance | 10 K | 50 K | Ω |
| V<sub>OH</sub> | High-level output voltage, CMOS ᵃ | VDD_PXx - 0.45 | VDD_PXx | V |
| V<sub>OL</sub> | Low-level output voltage, CMOS ᵃ | 0 | 0.45 | V |

ᵃ V<sub>OL</sub> and V<sub>OH</sub> are measured at I<sub>OL</sub> and I<sub>OH</sub> respectively, with 12 mA current across min and max voltages and operating temperatures.

**Table 3-11  DC specifications for PS_HOLD and MD_PS_HOLD (VDD_PX3)**

| Parameter | Description | Min | Max | Unit |
|---|---|---|---|---|
| V<sub>IH</sub> | High-level input voltage, (hihys_en = LOW) | 0.65 × VDD_PXx | VDD_PXx + 0.3 V | V |
| V<sub>IL</sub> | Low-level input voltage, (hihys_en = LOW) | -0.3 | 0.35 × VDD_PXx | V |
| V<sub>IH</sub> | High-level input voltage, (hihys_en = HIGH) | 0.7 × VDD_PXx | VDD_PXx + 0.3 V | V |
| V<sub>IL</sub> | Low-level input voltage, (hihys_en = HIGH) | -0.3 | 0.3 × VDD_PXx | V |
| V<sub>SHYS</sub> | Schmitt hysteresis, (hihys_en = LOW) | 100 | – | mV |
| V<sub>SHYS</sub> | Schmitt hysteresis, (hihys_en = HIGH) | 300 | – | mV |
| I<sub>IH</sub> | Input high leakage current | – | 20 | μA |
| I<sub>L</sub> | Input low leakage current | -1 | – | μA |
| R<sub>PD</sub> | Pull-down resistance | 10 K | 50 K | Ω |
| R<sub>PU</sub> | Pull-up resistance | 3 K | 20 K | Ω |
| R<sub>KP</sub> | Bus keeper resistor | 3 K | 50 K | Ω |
| V<sub>OH</sub> | High-level output voltage ᵃ | VDD_PXx - 0.45 | VDD_PXx | V |
| V<sub>OL</sub> | Low-level output voltage ᵃ | 0 | 0.45 | V |

ᵃ V<sub>OL</sub> and V<sub>OH</sub> are measured at I<sub>OL</sub> and I<sub>OH</sub> respectively, with 12 mA current across min and max voltages and operating temperatures.
