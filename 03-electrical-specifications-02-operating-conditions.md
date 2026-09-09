[← Contents](README.md)

## 3.2 Operating conditions

The QCS9075 meets all performance specifications, when used within the operating conditions, unless otherwise noted in those sections (provided the absolute maximum ratings have never been exceeded).

**Table 3-2  Operating conditions for voltage rails with AVS Type - 1**

| Parameter | Parameter | Min | Max | Unit |
|---|---|---|---|---|
| **Power supply voltages** |  |  |  |  |
| VDD_APC0 | Power for the cluster 0 of Kryo Gold Prime processors<br>Active | 0.576 | 1.030 | V |
| VDD_APC1 | Power for the cluster 1 of Kryo Gold Prime processors<br>Active | 0.576 | 1.030 | V |
| VDD_CX<br>VDD_D_EBI<br>VDD_RTSS_CX | Power for digital core circuits<br>Power for EBI digital circuits<br>Power for RTSS digital core circuits<br>Active<br>Retention ᵃ | 0.560<br>0.352 | 1.030<br>0.480 | V<br>V |
| VDD_CX_LPI | Power for Low-power island digital core circuits<br>Active<br>Retention ᵃ | 0.560<br>0.352 | 1.030<br>0.480 | V<br>V |
| VDD_GFX | Power for graphics<br>Active | 0.560 | 1.030 | V |
| VDD_MM | Power for multimedia subsystem circuits |  |  |  |
|  | Active | 0.560 | 1.030 | V |
| VDD_MX_A<br>VDD_RTSS_MX | Power for always-ON memory circuits<br>Power for RTSS On-chip memory circuits<br>Active<br>Retention ᵃ | 0.716<br>0.504 | 1.030<br>0.680 | V<br>V |
| VDD_MX_C | Power for collapsible memory circuits<br>Active | 0.716 | 1.030 | V |
| VDD_MX_LPI | Power for Low-power island memory circuit<br>Active<br>Retention ᵃ | 0.695<br>0.504 | 1.030<br>0.680 | V<br>V |
| VDD_NSP0 | Power for Hexagon Tensor Processor 0<br>Active | 0.560 | 1.030 | V |
| VDD_NSP1 | Power for Hexagon Tensor Processor 1<br>Active | 0.560 | 1.030 | V |
| VDD_A_EBI_0P9<br>VDD_A_EBI_PLL<br>VDD_A_EBI_23_45_0P9 | Power for EBI PHY 0.9 V circuits<br>Power for EBI PHY PLL circuits<br>Power for EBI2/EBI3/EBI4/EBI5 I/O circuits<br>Active<br>Retention ᵃ | 0.835<br>0.352 | 1.030<br>0.480 | V<br>V |

ᵃ The retention voltage is the PMIC output setting and it is static. There is no scaling.

**Table 3-3  Operating conditions for non AVS voltage rails**

| Parameter ᵃ | Parameter ᵃ | Min | Typ ᵇ | Max | Unit |
|---|---|---|---|---|---|
| **Power supply voltages** |  |  |  |  |  |
| VDD_A_APC_CS_1P2<br>VDD_A_NSP0_CS_1P2<br>VDD_A_NSP1_CS_1P2<br>VDD_PX11<br>VDD_RTSS_PX11 | Power for application processor current sensor 1.2 V analog circuits<br>Power for HTP0 current sensor 1.2 V circuits<br>Power for HTP1 current sensor 1.2 V circuits<br>Power for pad group 11<br>Power for RTSS pad group 11 | 1.100 | 1.200 | 1.300 | V |
| VDD_PX0<br>VDD_RTSS_PX0 | Power for pad group 0<br>Power for RTSS pad group 0 | 1.700 | 1.800 | 1.900 | V |
| VDD_PX1 | Power for pad group 1 | 1.010 | 1.100 | 1.120 | V |
| VDD_PX10 | Power for pad group 10 | 1.100 | 1.200 | 1.250 | V |
| VDD_PX3<br>VDD_PX7<br>VDD_QFPROM<br>VDD_RTSS_PX3<br>VDD_QFPROM_RTSS | Power for pad group 3<br>Power for pad group 7<br>Power for programming the QFPROM<br>Power for RTSS pad group 3<br>Power for programming the QFPROM RTSS | 1.700 | 1.800 | 1.900 | V |
| **Power supply voltages** |  |  |  |  |  |
| VDD_PX9 | Power for pad group 9 | 1.100 | 1.200 | 1.250 | V |
| VDD_RTSS_PX8<br>VBIAS_RTSS_RGMII | Power for RTSS pad group 8<br>Power for RTSS_RGMII reference circuits; 0.85 V | 1.700 | 1.800 | 1.900 | V |
|  |  | 0.800 | 0.850 | 0.900 | V |
| VDD_A_CSI_0_1_0P9<br>VDD_A_CSI_2_3_0P9<br>VDD_A_DSI_0_0P9<br>VDD_A_DSI_0_PLL_0P9<br>VDD_A_DSI_1_0P9<br>VDD_A_DSI_1_PLL_0P9<br>VDD_A_EDP_0_0P9<br>VDD_A_EDP_1_0P9<br>VDD_A_EDP_2_0P9<br>VDD_A_EDP_3_0P9<br>VDD_A_REFGEN_0P875<br>VDD_A_SGMII_0_0P9<br>VDD_A_SGMII_1_0P9<br>VDD_A_UFS_0_0P9<br>VDD_A_UFS_1_0P9 | Power for MIPI CSI0/CSI1 0.9 V analog circuits<br>Power for MIPI CSI2/CSI3 0.9 V analog circuits<br>Power for MIPI DSI0 0.9 V analog circuits<br>Power for MIPI DSI0 PLL 0.9 V<br>Power for MIPI DSI1 0.9 V analog circuits<br>Power for MIPI DSI1 PLL 0.9 V<br>Power for EDP 0 0.9 V circuits<br>Power for EDP 1 0.9 V circuits<br>Power for EDP 2 0.9 V circuits<br>Power for EDP 3 0.9 V circuits<br>Power for high-speed interface reference generation circuits – 0.875 V<br>Power for serial giga bit media-independent interface 0 - 0.9 V<br>Power for serial giga bit media-independent interface 1 - 0.9 V<br>Power for the UFS0 0.9 V analog circuits<br>Power for the UFS1 0.9 V analog circuits | 0.830 | 0.880 | 0.920 | V |
| VDD_A_CSI_0_1P2<br>VDD_A_CSI_1_1P2<br>VDD_A_CSI_2_1P2<br>VDD_A_CSI_3_1P2<br>VDD_A_DSI_0_1_1P2<br>VDD_A_EDP_0_1P2<br>VDD_A_EDP_1_1P2<br>VDD_A_EDP_2_1P2<br>VDD_A_EDP_3_1P2<br>VDD_A_PCIE_0_PLL_1P2<br>VDD_A_PCIE_1_PLL_1P2<br>VDD_A_REFGEN_1P2<br>VDD_A_SGMII_0_1P2<br>VDD_A_SGMII_1_1P2<br>VDD_A_UFS_0_1P2<br>VDD_A_UFS_1_1P2<br>VDD_A_USBSS_0_1P2<br>VDD_A_USBSS_1_1P2 | Power for MIPI CSI0 1.2 V analog circuits<br>Power for MIPI CSI1 1.2 V analog circuits<br>Power for MIPI CSI2 1.2 V analog circuits<br>Power for MIPI CSI3 1.2 V analog circuits<br>Power for MIPI DSI0/DSI1 1.2 V analog circuits<br>Power for EDP 0 1.2 V circuits<br>Power for EDP 1 1.2 V circuits<br>Power for EDP 2 1.2 V circuits<br>Power for EDP 3 1.2 V circuits<br>Power for PCIe 0 PLL 1.2 V circuits<br>Power for PCIe 1 PLL 1.2 V circuits<br>Power for high-speed interface reference generation circuits – 1.2 V<br>Power for serial giga bit media-independent interface 0 - 1.2 V<br>Power for serial giga bit media-independent interface 1 - 1.2 V<br>Power for the UFS0 1.2 V analog circuits<br>Power for the UFS1 1.2 V analog circuits<br>Power for USB super-speed 0 1.2 V circuits<br>Power for USB super-speed 1 1.2 V circuits | 1.150 | 1.200 | 1.250 | V |
| VDD_A_USBHS_0_0P9 | Power for USB high-speed 0 0.9 V circuits | 0.830 | 0.880 | 0.920 | V |
| **Power supply voltages** |  |  |  |  |  |
| VDD_A_USBHS_1_0P9<br>VDD_A_USBHS_2_0P9<br>VDD_A_USBSS_0_0P9<br>VDD_A_USBSS_1_0P9 | Power for USB high-speed 1 0.9 V circuits<br>Power for USB high-speed 2 0.9 V circuits<br>Power for USB super-speed 0 0.9 V circuits<br>Power for USB super-speed 1 0.9 V circuits |  |  |  |  |
| VDD_A_USBHS_0_3P1<br>VDD_A_USBHS_1_3P1<br>VDD_A_USBHS_2_3P1 | Power for USB high-speed 0 3.1 V circuits<br>Power for USB high-speed 1 3.1 V circuits<br>Power for USB high-speed 2 3.1 V circuits | 2.970 | 3.072 | 3.200 | V |
| VDD_A_USBHS_0_1P8<br>VDD_A_USBHS_1_1P8<br>VDD_A_USBHS_2_1P8 | Power for USB high-speed 0 1.8 V circuits<br>Power for USB high-speed 1 1.8 V circuits<br>Power for USB high-speed 2 1.8 V circuits | 1.650 | 1.800 | 1.950 | V |
| VDD_A_PCIE_0_0P9<br>VDD_A_PCIE_1_0P9 | Power for PCIe 0.9 V circuits | 0.880 | 0.912 | 0.960 | V |
| VDD_IO_EBI<br>VDD_IO_EBI_23_45 | Power for EBI I/O circuits<br>Power for EBI2/EBI3/EBI4/EBI5 I/O circuits | 0.470 | 0.500 | 0.570 | V |
| **Thermal Conditions** |  |  |  |  |  |
| T<sub>A</sub> | Ambient operating temperature | -40 | – | 85 ᶜ | °C |
| T<sub>J</sub> | Junction operating temperature | – | – | 115 | °C |

ᵃ Parts with voltages outside of the specified ranges are not guaranteed to operate properly.

ᵇ Typical voltages represent the recommended output settings of the companion PMIC device.

ᶜ The T<sub>J</sub>max specification must be met.
