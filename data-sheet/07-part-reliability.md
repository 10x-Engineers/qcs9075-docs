[← Contents](../README.md)

# 7 Part reliability

## 7.1 Reliability qualifications summary

The QCS9075 device has been qualified to AEC-Q100 Grade 3 specification, supporting operation up to 115°C. The qualification plan is summarized in the following table.

**Table 7-1  Qualification plan and results summary**

| Stress test | ABV | Test no. | Test method | Test conditions/pre and post ATE (identify temp, RH, and Bias) | Requirements – S.S per lot | Requirements – # lots | Results fails/ total S.S | Comments |
|---|---|---|---|---|---|---|---|---|
| ***Test group A – accelerated environment stress tests*** |  |  |  |  |  |  |  |  |
| Preconditioning | PC | A1 | JEDEC-J-STD-020, JESD22-A113 | MSL 3, 3x reflow (pre and post ATE at R) | 77, (77) | 3, (3) | 0F/231, (231) | Pass SPIL, (ATK) |
| Preconditioning + bias HAST | BHAST | A2 | JEDEC-JESD22-A110 | 130°C/85% RH for 96 hours (pre and post ATE at R and H) | 77, (77) | 3, (3) | 0F/231, (231) | Pass SPIL, (ATK) |
| Preconditioning + unbiased HAST/temperature humidity | UHAST | A3 | JEDEC-JESD22-A118 | 130°C/85% RH for 96 hours (pre and post ATE at R) | 77, (77) | 3, (3) | 0F/231, (231) | Pass SPIL, (ATK) |
| Preconditioning + temperature cycle | TC | A4 | JEDEC-JESD22-A104 | Ta = -55°C to +125°C for 500 cycles (pre and post ATE at R and H) | 77, (77) | 3, (3) | 0F/231, (231) | Pass SPIL, (ATK) |
| High temperature storage life | HTSL | A6 | JEDEC-JESD22-A103 | Ta = +150°C for 500 hours (pre and post ATE at R and H) | 77, (77) | 3, (3) | 0F/231, (231) | Pass SPIL, (ATK) |
| ***Test group B – accelerated lifetime simulation tests*** |  |  |  |  |  |  |  |  |
| High temperature operating life | HTOL | B1 | JEDEC-JESD22-A108 | Ta ≥ 85°C for 1000 hours (pre and post ATE at R, C, and H) | 77 | 3 | 0F/231 |  |
| Early life failure rate | ELFR | B2 | AEC Q100-008 | Ta ≥ 85°C for 48 hours (pre and post ATE at R and H) | 800 | 3 | 0F/2400 |  |
| NVM endurance, data retention, and operational life | EDR | B3 |  |  |  |  |  | No NVM memory on device |
| Test group C – package assembly integrity tests |  |  |  |  |  |  |  |  |
| Wire bond shear | WBS | C1 |  |  |  |  |  | Not applicable, not a wirebonded package |
| Wire bond pull strength | WBPS | C2 |  |  |  |  |  | Not Applicable, not a wirebonded package |
| Solderability | S | C3 |  |  |  |  |  | Not a leadframe package |
| Physical dimensions | PD | C4 |  | Package outline drawing | 10, (10) | 3, (3) | 0F/30, (30) | CPK ≥ 1.67 SPIL, (ATK) |
| Solder ball shear | SBS | C5 | JESD22-B117 | 5 balls each from a minimum of 10 devices | 10, (10) | 3, (3) | 0F/30, (30) | CPK ≥ 1.67 SPIL, (ATK) |
| Lead integrity | LI | C6 |  |  |  |  |  | Not a leadframe package |
| Test group D – die fabrication reliability tests |  |  |  |  |  |  |  |  |
| Electromigration | EM | D1 | JP001A |  |  |  |  | Pass |
| Time dependent dielectric breakdown | TDDB | D2 | JP001A |  |  |  |  | Pass |
| Hot carrier injection | HCI | D3 | JP001A |  |  |  |  | Pass |
| Negative bias temperature instability | NBTI | D4 | JP001A |  |  |  |  | Pass |
| Stress migration | SM | D5 | JP001A |  |  |  |  | Pass |
| ***Test group E – electrical verification tests*** |  |  |  |  |  |  |  |  |
| Pre- and post-stress electrical test | TEST | E1 |  |  |  |  |  | Per column H |
| ESD – human body model | HBM | E2 | AEC-Q100-002 | Pass target ±1 kV with margin (pre and post ATE at R and H) | 3 | 1 | 0F/3 | Pass SPIL |
| ESD – charged device model | CDM | E3 | AEC-Q100-011 | Pass target ±150 V with margin (pre and post ATE at R and H) | 3, (3) | 1, (1) | 0F/3, (3) | Pass SPIL, (ATK) |
| Latch up | LU | E4 | AEC-Q100-004 | Ta = 115°C, current injection ±100 mA, over voltage test at 1.5x VDD (pre and post ATE at R and H) | 6 | 1 | 0F/6 | Pass SPIL |
| Electrical distribution | ED | E5 |  |  |  |  |  | Available for review |
| Fault grading | FG | E6 |  |  |  |  |  | Available for review |
| Characterization | CHAR | E7 |  |  |  |  |  | Available for review |
| Electromagnetic compatibility | EMC | E9 |  |  |  |  |  | Not performed. System level test |
| Short circuit characterization | SC | E10 |  |  |  |  |  | Not applicable. Not > 12 V or a power device |
| Soft error rate | SER | E11 |  |  |  |  |  | Leverage foundry data |
| ***Test group F – defect screening tests*** |  |  |  |  |  |  |  |  |
| Process average test | PAT | F1 |  |  |  |  |  | Available for review |
| Statistical bin/yield analysis | SBA | F2 |  |  |  |  |  | Available for review |

## 7.2 Device characteristics

**Table 7-2  Device characteristics**

| Category | Definition |
|---|---|
| Device name | QCS9075 |
| Package type | FCBGA1723+HS |
| Package body size | 25.0 × 25.0 × 2.31 mm |
| Ball count | 1723 |
| Ball composition | SAC405 |
| Fab sites | Samsung |
| Assembly sites | SPIL, Taiwan<br>Amkor Technologies Korea (ATK) |
| Solder ball pitch | 0.6 mm |
