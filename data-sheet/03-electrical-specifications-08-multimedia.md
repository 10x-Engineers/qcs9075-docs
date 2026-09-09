[← Contents](../README.md)

## 3.8 Multimedia

Multimedia parameters requiring performance specifications are addressed in this section.

### 3.8.1 Camera interfaces

The QCS9075 device supports up to four D-PHY or C-PHY camera interfaces.

**Table 3-12  Supported MIPI-CSI standards and exceptions**

| Applicable standard | Feature exceptions |
|---|---|
| MIPI Alliance Specification for CSI-2 v3.0 | RAW7 is not supported; DPCM predictor 2 is not supported. |
| MIPI Alliance Specification for D-PHY v1.2 | Efficient Packet Delimiter (EPD) for D-PHY is not supported. |
| MIPI Alliance Specification for C-PHY v1.2 | None |

The following tables summarize the electrical and timing characteristics for CSI C‑PHY and D‑PHY interfaces at the SoC pin level.

**Table 3-13  CSI C‑PHY electrical characteristics**

| Parameter | Condition | Min | Typ | Max | Unit |
|---|---|---|---|---|---|
| Symbol rate per trio | – | – | 4.5 | – | Gsps/trio |
| Equivalent data rate | Per trio | – | 10.26 | – | Gb/s |
| Supported trios | – | 1 | – | 3 | trios |
| Single-ended signal swing | HS mode | TBD | 450 | 535 | mVpp |
| Common-mode voltage | HS mode | 95 | 225 | 390 | mV |
| Intra-trio skew | HS mode | – | – | 5 | ps |
| Inter-trio skew | HS mode | – | – | 30 | ps |
| HS jitter (total) | At max rate | – | – | 0.55 | UI |
| LP input low (VIL) | LP mode | – | – | 550 | mV |
| LP input high (VIH) | LP mode | 740 | – | – | mV |

**Table 3-14  CSI D‑PHY electrical characteristics**

| Parameter | Condition | Min | Typ | Max | Unit |
|---|---|---|---|---|---|
| Data rate per lane | HS mode | – | 2.5 | – | Gb/s |
| Supported data lanes | – | 1 | – | 4 | lanes |
| HS differential swing | HS mode | 140 | 200 | 270 | mVpp |
| HS common-mode voltage | HS mode | 70 | – | 330 | mV |
| Receiver sensitivity | HS mode | 40 | – | – | mVpp |
| Intra-pair skew (P–N) | HS mode | – | – | 5 | ps |
| Lane-to-lane skew | HS mode | – | – | 15 | ps |
| HS clock frequency | Dedicated lane | – | 1.25 | – | GHz |
| HS clock jitter (total) | At max rate | – | – | 0.5 | UI |
| HS eye height | HS mode | 140 | – | – | mV |
| LP input high (VIH) | LP mode | – | – | 740 | mV |
| LP input low (VIL) | LP mode | 550 | – | – | mV |
| Hold time | – | 0.3 | – | 0.5 | UI |
| Setup time | – | –0.5 | – | –0.3 | UI |

### 3.8.2 Audio support

The audio-related interfaces supported with QCS9075 include:

- 2 I S interfaces
- PCM/TDM interfaces

### 3.8.3 Display support

The QCS9075 device supports one D-PHY or C-PHY display.

**Table 3-15  Supported MIPI-DSI standards and exceptions**

| Applicable standard | Feature exceptions |
|---|---|
| MIPI Alliance Specification for Display Serial Interface 2, v2.1 | None |
| MIPI Alliance Specification for D-PHY v1.2 | None |
| MIPI Alliance Specification for C-PHY v1.1 | None |

The following tables summarize the electrical and timing characteristics for DSI C‑PHY and D‑PHY interfaces at the SoC pin level.

**Table 3-16  DSI C‑PHY electrical characteristics**

| Parameter | Condition | Min | Typ | Max | Unit |
|---|---|---|---|---|---|
| Symbol rate per trio | – | – | 2.5 | – | Gsym/s per trio |
| Equivalent data rate | Per trio | – | 5.7 | – | Gb/s |
| Supported trios | – | 1 | – | 3 | trios |
| Static common point voltage | HS mode | 175 | – | 310 | mV |
| Intra-trio skew ᵃ | HS mode | – | – | 5 | ps |
| Inter-trio skew ᵃ | HS mode | – | – | 30 | ps |
| HS jitter (total) ᵃ | at max rate | – | – | 0.3 | UI |
| HS eye height ᵃ | HS mode | 80 | – | – | mV |
| HS eye width ᵃ | HS mode | 0.5 | – | – | UI |
| LP output high (VOH) | LP mode | 0.95 | – | – | V |
| LP output low (VOL) | LP mode | -0.05 | – | 0.05 | V |

ᵃ Not characterized; guaranteed by design

**Table 3-17  DSI D‑PHY electrical characteristics**

| Parameter | Condition | Min | Typ | Max | Unit |
|---|---|---|---|---|---|
| Supported data rates | 2.5, 2.1, 1.312 |  |  |  | Gb/s per lane |
| Data rate per lane | HS mode | – | – | 2.5 | Gb/s |
| Supported data lanes | – | 1 | – | 4 | lanes |
| HS differential swing | HS mode | 140 | 200 | 270 | mVpp |
| HS common-mode voltage | HS mode | 0.15 | 0.2 | 0.25 | V |
| Intra-pair skew (P–N) ᵃ | HS mode | – | – | 5 | ps |
| Lane-to-lane skew ᵃ | HS mode | – | – | 15 | ps |
| HS jitter (total) ᵃ | at max rate | – | – | 0.3 | UI |
| HS eye height ᵃ | HS mode | 80 | – | – | mV |
| HS data rise time | HS mode | – | – | 160 | ps |
| HS data fall time | HS mode | – | – | 160 | ps |
| HS clock rise time | HS mode | – | – | 160 | ps |
| HS clock fall time | HS mode | – | – | 160 | ps |
| LP output high (VOH) | LP mode | 0.95 | – | 1.3 | V |
| LP output low (VOL) | LP mode | -0.05 | – | 0.05 | V |
| LP input high (VIH) | LP mode | 740 | – | – | mV |
| LP input low (VIL) | LP mode | – | – | 550 | mV |
| LP Tx rise time | LP mode | – | – | 25 | ns |
| LP Tx fall time | LP mode | – | – | 25 | ns |

ᵃ Not characterized; guaranteed by design

### 3.8.4 DisplayPort

**Table 3-18  Supported DisplayPort standards and exceptions**

| Applicable standard | Feature exceptions |
|---|---|
| VESA DisplayPort v1.4 | None |

The following table summarizes the key electrical and link characteristics for the DisplayPort and embedded DisplayPort (eDP) interface.

**Table 3-19  DP/eDP electrical and link characteristics**

| Parameter | Min | Typ | Max | Unit |
|---|---|---|---|---|
| Main link lane count | 1 | 2 | 4 | lanes |
| Main link per-lane rate (DP 1.4) | 1.612 | – | 8.1 | Gbps/lane |
| Encoding/clocking | – | 8b/10b | – | – |
| Total raw bandwidth (4 lanes) | – | – | 32.4 | Gbps |
| AUX channel data rate | – | 1 | – | Mbps |
| AUX differential peak-to-peak voltage (DP) | 0.29 | – | 1.38 | Vpp (diff) |
| AUX differential peak-to-peak voltage (eDP) | 0.14 | – | 1.36 | Vpp (diff) |
| AUX AC-coupling capacitance | 75 | 100 | 200 | nF |
