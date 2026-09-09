## 6.8 HVX MPY DOUBLE RESOURCE

The HVX MPY DOUBLE RESOURCE instruction subclass includes memory load instructions.

#### 3 × 3 multiply for 2 × 2 tile

Multiply optimized for 3 × 3 filtering for a 2 × 2 tile format of two horizontal by two vertical bytes with three 10-bit coefficients. Byte 4 of the inlane word in the coefficient vector specifies the upper two bits for each coefficient.

Accumulation is not shown to simplify the diagrams, but all multiplies are assumed to reduce and accumulate with the corresponding output.

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.
- The accumulator (Vxx) source of this instruction must generate in the previous packet to avoid a stall. The accumulator cannot come from a .tmp operation.

| Syntax | Behavior |
|---|---|
| `Vdd.w = v6mpy(Vuu.ub, Vvv.b, `<br>`#u2):h` | `for (i = 0; i < VELEM(32); i++) {`<br>`c00=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[0]) << 6) >> 6;`<br>`c01=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[1]) << 6) >> 6;`<br>`c02=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[2]) << 6) >> 6;`<br>`c10=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[0]) << 6) >> 6;`<br>`c11=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[1]) << 6) >> 6;`<br>`c12=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[2]) << 6) >> 6;`<br>`if (#u == 0) {`<br>`Vdd.v[1].w[i] = (Vuu.v[1].uw[i].ub[3] * c10);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c11);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[1].uw[i].ub[2] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c12);`<br>`} else if (#u == 1) {`<br>`Vdd.v[1].w[i] = (Vuu.v[1].uw[i].ub[3] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[1].uw[i].ub[3] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c12);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c00);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c02);`<br>`} else if (#u == 2) {`<br>`Vdd.v[1].w[i] = (Vuu.v[1].uw[i].ub[1] * c10);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] * `<br>`c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[0] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[1].uw[i].ub[0] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * c12);`<br>`} else if (#u == 3) {`<br>`Vdd.v[1].w[i] = (Vuu.v[1].uw[i].ub[1] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[1].uw[i].ub[1] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c12);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c00);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c01); `<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * `<br>`c02);`<br>`} `<br>`}` |
| `Vdd.w = v6mpy(Vuu.ub, Vvv.b, `<br>`#u2):v` | `for (i = 0; i < VELEM(32); i++) {`<br>`c00=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[0]) << 6) >> 6;`<br>`c01=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[1]) << 6) >> 6;`<br>`c02=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[2]) << 6) >> 6;`<br>`c10=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[0]) << 6) >> 6;`<br>`c11=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[1]) << 6) >> 6;`<br>`c12=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[2]) << 6) >> 6;`<br>`if (#u == 0) {`<br>`Vdd.v[1].w[i] = (Vuu.v[0].uw[i].ub[3] * c10);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c11);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[0].uw[i].ub[1] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * `<br>`c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[0].uw[i].ub[3] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[3] * c12);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c00);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c02);`<br>`} else if (#u == 2) {`<br>`Vdd.v[1].w[i] = (Vuu.v[0].uw[i].ub[2] * c10);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[0] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[0].uw[i].ub[0] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c12);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[0].uw[i].ub[0] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c12);`<br>`} else if (#u == 3) {`<br>`Vdd.v[1].w[i] = (Vuu.v[0].uw[i].ub[2] * c00);`<br>`Vdd.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c01);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c02);`<br>`Vdd.v[0].w[i] = (Vuu.v[0].uw[i].ub[2] * c10);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c12);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * c00);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c01);`<br>`Vdd.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c02);`<br>`}`<br>`}` |
| `Vxx.w += v6mpy(Vuu.ub, Vvv.b, `<br>`#u2):h` | `for (i = 0; i < VELEM(32); i++) {`<br>`c00=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[0]) << 6) >> 6;`<br>`c01=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[1]) << 6) >> 6;`<br>`c02=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[2]) << 6) >> 6;`<br>`c10=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[0]) << 6) >> 6;`<br>`c11=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[1]) << 6) >> 6;`<br>`c12=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[2]) << 6) >> 6;`<br>`if (#u == 0) {`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c10);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c11);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c12);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c12);`<br>`} else if (#u == 1) {`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[3] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c12);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c00);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c02);`<br>`} else if (#u == 2) {`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c10);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c12);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] `<br>`*c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[0] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * c12);`<br>`} else if (#u == 3) {`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c12);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c00);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c01);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * `<br>`c02);`<br>`}`<br>`}` |
| `Vxx.w += v6mpy(Vuu.ub, Vvv.b, `<br>`#u2):v` | `for (i = 0; i < VELEM(32); i++) {`<br>`c00=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[0]) << 6) >> 6;`<br>`c01=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[1]) << 6) >> 6;`<br>`c02=(((((Vvv.v[0].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[0].uw[i].ub[2]) << 6) >> 6;`<br>`c10=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 0)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[0]) << 6) >> 6;`<br>`c11=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 1)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[1]) << 6) >> 6;`<br>`c12=(((((Vvv.v[1].uw[i].ub[3] >> (2 * 2)) & 3) << `<br>`8) \| Vvv.v[1].uw[i].ub[2]) << 6) >> 6;`<br>`if (#u == 0) {`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c10);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c11);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c12);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[1] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c12);`<br>`} else if (#u == 1) {`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[3] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[3] * c12);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c00);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c01);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[1] * c02);`<br>`} else if (#u == 2) {`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] * c10);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c12);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[0] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[1] * `<br>`c01);` |

|  |  |
|---|---|
| `Vxx.w += v6mpy(Vuu.ub, Vvv.b, `<br>`#u2):v` | `Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[0] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * c12);`<br>`} else if (#u == 3) {`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[2] * c00);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].uw[i].ub[3] * c01);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].uw[i].ub[2] * c02);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[2] * c10);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[3] * c11);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[2] * c12);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[0] * c00);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].uw[i].ub[1] * c01);`<br>`Vxx.v[0].w[i] += (Vuu.v[1].uw[i].ub[0] * `<br>`c02);`<br>`}}` |

##### Intrinsics

```
Vdd.w=v6mpy(Vuu.ub,Vvv.b,#u2):hHVX_VectorPair Q6_Ww_v6mpy_WubWbI_h(HVX_VectorPair
                                 Vuu, HVX_VectorPair Vvv, Word32 Iu2)
Vdd.w=v6mpy(Vuu.ub,Vvv.b,#u2):vHVX_VectorPair Q6_Ww_v6mpy_WubWbI_v(HVX_VectorPair
                                 Vuu, HVX_VectorPair Vvv, Word32 Iu2)
Vxx.w+=v6mpy(Vuu.ub,Vvv.b,#u2):hHVX_VectorPair Q6_Ww_v6mpyacc_WwWubWbI_h
                                 (HVX_VectorPair Vxx, HVX_VectorPair Vuu,
                                 HVX_VectorPair Vvv, Word32 Iu2)
Vxx.w+=v6mpy(Vuu.ub,Vvv.b,#u2):vHVX_VectorPair Q6_Ww_v6mpyacc_WwWubWbI_v
                                 (HVX_VectorPair Vxx, HVX_VectorPair Vuu,
                                 HVX_VectorPair Vvv, Word32 Iu2)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | i | i | x | x | x | x | x | Vxx.w+=v6mpy(Vuu.ub,Vvv .b,#u2):v |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | i | i | x | x | x | x | x | Vxx.w+=v6mpy(Vuu.ub,Vvv .b,#u2):h |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | i | i | d | d | d | d | d | Vdd.w=v6mpy(Vuu.ub,Vvv. b,#u2):v |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | i | i | d | d | d | d | d | Vdd.w=v6mpy(Vuu.ub,Vvv. b,#u2):h |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Arithmetic widening

Add or subtract the elements of vector registers Vu and Vv. The resulting elements are double the width of the input size to capture data growth in the result. The result is placed in a double vector register.

Supports unsigned byte, and signed and unsigned halfword.

Vdd.w=vadd(Vu.h,Vv.h)

N bits

|  |  |
|---|---|
| [1] | [0] |

Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | [1] |  | [0] |

Vv

<sub>To other slices</sub> +/- +/-

|  |  |
|---|---|
|  | [0] |

Vdd_e

<sub>[0]</sub> Vdd_o

2N bits

| Syntax | Behavior |
|---|---|
| `Vdd.h=vadd(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = Vu.uh[i].ub[0] + Vv.uh[i].ub[0];`<br>`Vdd.v[1].h[i] = Vu.uh[i].ub[1] + Vv.uh[i].ub[1];`<br>`}` |
| `Vdd.h=vsub(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = Vu.uh[i].ub[0] - Vv.uh[i].ub[0];`<br>`Vdd.v[1].h[i] = Vu.uh[i].ub[1] - Vv.uh[i].ub[1];`<br>`}` |
| `Vdd.w=vadd(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = Vu.w[i].h[0] + Vv.w[i].h[0];`<br>`Vdd.v[1].w[i] = Vu.w[i].h[1] + Vv.w[i].h[1];`<br>`}` |
| `Vdd.w=vadd(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = Vu.uw[i].uh[0] + Vv.uw[i].uh[0];`<br>`Vdd.v[1].w[i] = Vu.uw[i].uh[1] + Vv.uw[i].uh[1];`<br>`}` |
| `Vdd.w=vsub(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = Vu.w[i].h[0] - Vv.w[i].h[0];`<br>`Vdd.v[1].w[i] = Vu.w[i].h[1] - Vv.w[i].h[1];`<br>`}` |
| `Vdd.w=vsub(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = Vu.uw[i].uh[0] - Vv.uw[i].uh[0];`<br>`Vdd.v[1].w[i] = Vu.uw[i].uh[1] - Vv.uw[i].uh[1];`<br>`}` |
| `Vxx.h+=vadd(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += Vu.h[i].ub[0] + Vv.h[i].ub[0];`<br>`Vxx.v[1].h[i] += Vu.h[i].ub[1] + Vv.h[i].ub[1];`<br>`}` |
| `Vxx.w+=vadd(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += Vu.w[i].h[0] + Vv.w[i].h[0];`<br>`Vxx.v[1].w[i] += Vu.w[i].h[1] + Vv.w[i].h[1];`<br>`}` |
| `Vxx.w+=vadd(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += Vu.w[i].uh[0] + Vv.w[i].uh[0];`<br>`Vxx.v[1].w[i] += Vu.w[i].uh[1] + Vv.w[i].uh[1];`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vadd(Vu.ub,Vv.ub)` | `HVX_VectorPair Q6_Wh_vadd_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.h=vsub(Vu.ub,Vv.ub)` | `HVX_VectorPair Q6_Wh_vsub_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vadd(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Ww_vadd_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vadd(Vu.uh,Vv.uh)` | `HVX_VectorPair Q6_Ww_vadd_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vsub(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Ww_vsub_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vsub(Vu.uh,Vv.uh)` | `HVX_VectorPair Q6_Ww_vsub_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.h+=vadd(Vu.ub,Vv.ub)` | `HVX_VectorPair Q6_Wh_vaddacc_WhVubVub(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.w+=vadd(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Ww_vaddacc_WwVhVh(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.w+=vadd(Vu.uh,Vv.uh)` | `HVX_VectorPair Q6_Ww_vaddacc_WwVuhVuh(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vxx.w+=vadd(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vxx.w+=vadd(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vxx.h+=vadd(Vu.ub,Vv.ub) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.h=vadd(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.w=vadd(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.w=vadd(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.h=vsub(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.w=vsub(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.w=vsub(Vu.h,Vv.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply with 2-wide reduction

Multiply elements from Vu by the corresponding elements in the scalar register Rt. The products are added in pairs to yield a by-2 reduction. The products can optionally be accumulated with Vx, with optional saturation after summation.

Supports multiplication of unsigned bytes by bytes, halfwords by signed bytes, and halfwords by halfwords. The double-vector version performs a sliding window 2-way reduction, where the odd register output contains the offset computation. Vd.h[+]=vdmpy(Vu.ub, Rt.b) / Vd.w[+]=vdmpy(Vu.h, Rt.b) Vdd.h[+]=vdmpy(Vuu.ub, Rt.b) / Vdd.w[+]=vdmpy(Vuu.h, Rt.b)

|  |  |  |  |
|---|---|---|---|
| ub/h[3] | ub/h[2] | ub/h[1] | ub/h[0] |

Vuu[1]ub/h[3]ub/h[2]ub/h[1]ub/h[0] Vuu[0]

|  |  |  |  |
|---|---|---|---|
| ub/h[3] | ub/h[2] | ub/h[1] | ub/h[0] |

ub/h[3]ub/h[2]ub/h[1]ub/h[0] Vuu[1] Vuu[0]

|  |  |  |  |
|---|---|---|---|
| ub/h[3] | ub/h[2] | ub/h[1] | ub/h[0] |

ub/h[3]ub/h[2]ub/h[1]ub/h[0] Vuu[1]ub/h[3]ub/h[2]ub/h[1]ub/h[0] Vuu[0]

Vu

|  |  |  |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

ub/h[3]ub/h[2]ub/h[1]ub/h[0] Vu

Rt.b[0]

X Rt.b[0] X X

Rt.b[1]

X Rt.b[1] X X

Rt.b[2]

X Rt.b[2] X X

|  |  |
|---|---|
|  |  |
|  |  |

Rt.b[1]

X Rt.b[1] X X

Rt.b[2]

X Rt.b[2] X X

Rt.b[3]

X Rt.b[3] X X

|  |  |
|---|---|
|  |  |
|  |  |

Rt.b[1]

X Rt.b[1] X X

Rt.b[2]

X Rt.b[2] X X

Rt.b[3]

X Rt.b[3] X X

+ +Optional accumulation + +Optional accumulation + +

|  |  |  |
|---|---|---|
| h/w[1] |  | h/w[0] |

Vd h/w[1] h/w[0] Vdd[1] h/w[1] h/w[0] Vdd[0]

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| h/w[1] | h/w[1] |  | h/w[0] | h/w[0] |  |
|  |  |  |  |  |  |

h/w[1] h/w[0] Vd Vdd[1] h/w[1] h/w[0] Vdd[0]

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| h/w[1] | h/w[1] |  | h/w[0] | h/w[0] |  |
|  |  |  |  |  |  |

h/w[1] h/w[0] Vd h/w[1] h/w[0] Vdd[1] Vdd[0]

32/64-bit lane 32/64-bit lane pair

Vd.w[+]=vdmpy(Vu.h, Rt.h):sat Vd.w[+]=vdmpy(Vuu.h, Rt.h):sat

|  |  |
|---|---|
| h[1] | h[0] |

Vu h[1] h[0] Vuu[1] h[1] h[0] Vuu[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vu Vuu[1] h[1] h[0] Vuu[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vu h[1] h[0] Vuu[1] Vuu[0]

X Rt.h[0] Rt.h[0] X

X Rt.h[1]

Rt.h[1] X

+<sub>Optional Accumulation</sub> +Optional Accumulation

Optional Saturation SATOptional Saturation SAT

w[0] Vd w[0] Vdd[0]

32bit Lane 32bit Lane Pair

Multiply halfword elements from vector register Vu by the corresponding halfword elements in the vector register Vv. The products are added in pairs to make a 32-bit wide sum. The sum is optionally accumulated with the vector register destination Vx, and then saturated to 32 bits.

Vd.w[+]=vdmpy(Vu.h, Vv.h):sat

|  |  |
|---|---|
| h[1] | h[0] |

Vv

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
| h[1] |  | h[0] |  |

Vu

X X

+<sub>accumulation</sub><sup>Optional</sup>

sat

|  |  |  |
|---|---|---|
| w0 | w0 |  |
|  |  |  |

Vd

32-bit lane

| Syntax | Behavior |
|---|---|
| `Vd.w=vdmpy(Vuu.h,Rt.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vuu.v[0].w[i].h[1] * Rt.h[0]);`<br>`accum += (Vuu.v[1].w[i].h[0] * Rt.h[1]);`<br>`Vd.w[i] = sat₃₂(accum);`<br>`}` |
| `Vd.w=vdmpy(Vuu.h,Rt.uh,#1):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vuu.v[0].w[i].h[1] * Rt.uh[0]);`<br>`accum += (Vuu.v[1].w[i].h[0] * Rt.uh[1]);`<br>`Vd.w[i] = sat₃₂(accum);`<br>`}` |
| `Vdd.h=vdmpy(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].uh[i].ub[0] * `<br>`Rt.b[(2*i) % 4]);`<br>`Vdd.v[0].h[i] += (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[1].h[i] = (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i) % 4]);`<br>`Vdd.v[1].h[i] += (Vuu.v[1].uh[i].ub[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vdd.w=vdmpy(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vuu.v[0].w[i].h[0] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vdd.v[0].w[i] += (Vuu.v[0].w[i].h[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[1].w[i] = (Vuu.v[0].w[i].h[1] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vdd.v[1].w[i] += (Vuu.v[1].w[i].h[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vx.w+=vdmpy(Vu.h,Vv.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vu.w[i].h[0] * Vv.w[i].h[0]);`<br>`accum += (Vu.w[i].h[1] * Vv.w[i].h[1]);`<br>`Vx.w[i] = sat₃₂(Vx.w[i]+accum) ;`<br>`}` |
| `Vx.w+=vdmpy(Vuu.h,Rt.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = Vx.w[i];`<br>`accum += (Vuu.v[0].w[i].h[1] * Rt.h[0]);`<br>`accum += (Vuu.v[1].w[i].h[0] * Rt.h[1]);`<br>`Vx.w[i] = sat₃₂(accum);`<br>`}` |
| `Vx.w+=vdmpy(Vuu.h,Rt.uh,#1):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum=Vx.w[i];`<br>`accum += (Vuu.v[0].w[i].h[1] * Rt.uh[0]);`<br>`accum += (Vuu.v[1].w[i].h[0] * Rt.uh[1]);`<br>`Vx.w[i] = sat₃₂(accum);`<br>`}` |
| `Vxx.h+=vdmpy(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vuu.v[0].uh[i].ub[0] * `<br>`Rt.b[(2*i) % 4]);`<br>`Vxx.v[0].h[i] += (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[1].h[i] += (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i) % 4]);`<br>`Vxx.v[1].h[i] += (Vuu.v[1].uh[i].ub[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vxx.w+=vdmpy(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vuu.v[0].w[i].h[0] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vxx.v[0].w[i] += (Vuu.v[0].w[i].h[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].w[i].h[1] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vxx.v[1].w[i] += (Vuu.v[1].w[i].h[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vd.w=vdmpy(Vuu.h,Rt.h):sat` | `HVX_Vector Q6_Vw_vdmpy_WhRh_sat(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vd.w=vdmpy(Vuu.h,Rt.uh,#1):sat` | `HVX_Vector Q6_Vw_vdmpy_WhRuh_sat(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.h=vdmpy(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vdmpy_WubRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.w=vdmpy(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vdmpy_WhRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vx.w+=vdmpy(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vw_vdmpyacc_VwVhVh_sat(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vdmpy(Vuu.h,Rt.h):sat` | `HVX_Vector Q6_Vw_vdmpyacc_VwWhRh_sat(HVX_Vector Vx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vx.w+=vdmpy(Vuu.h,Rt.uh,#1):sat` | `HVX_Vector Q6_Vw_vdmpyacc_VwWhRuh_sat(HVX_Vector Vx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.h+=vdmpy(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vdmpyacc_WhWubRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.w+=vdmpy(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vdmpyacc_WwWhRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.h=vdmpy(Vuu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vxx.h+=vdmpy(Vuu.ub,Rt.b ) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.w=vdmpy(Vuu.h,Rt.uh,# 1):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.w=vdmpy(Vuu.h,Rt.h):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.w=vdmpy(Vuu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vx.w+=vdmpy(Vuu.h,Rt.uh, #1):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vx.w+=vdmpy(Vuu.h,Rt.h): sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vxx.w+=vdmpy(Vuu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx.w+=vdmpy(Vu.h,Vv.h):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Lookup table for piecewise from 64-bit scalar

The `vlut4` instruction implements a four entry lookup table, which is specified in scalar register pair Rtt.

| Syntax | Behavior |
|---|---|
| `Vd.h=vlut4(Vu.uh,Rtt.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i]= Rtt.h[((Vu.h[i]>>14)&0x3)];`<br>`}` |

##### Class: COPROC_VX (slots 2)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

```
Vd.h=vlut4(Vu.uh,Rtt.h)HVX_Vector Q6_Vh_vlut4_VuhPh(HVX_Vector Vu,
                             Word64 Rtt)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vlut4(Vu.uh,Rtt.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |

#### Multiply with piecewise addition/subtraction from 64-bit scalar

Instructions to help nonlinear function calculations.

| Syntax | Behavior |
|---|---|
| `Vx.h=vmpa(Vx.h,Vu.h,Rtt.h):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i]= sat₁₆(( ( (Vx.h[i] * Vu.h[i])<<1) `<br>`+ (Rtt.h[( (Vu.h[i] >> 14)&0x3)]<<15))>>16);`<br>`}` |
| `Vx.h=vmpa(Vx.h,Vu.uh,Rtt.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i]= sat₁₆(( (Vx.h[i] * Vu.uh[i]) + `<br>`(Rtt.uh[((Vu.uh[i] >> 14)&0x3)]<<15))>>16);`<br>`}` |
| `Vx.h=vmps(Vx.h,Vu.uh,Rtt.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i]= sat₁₆(( (Vx.h[i] * Vu.uh[i]) - `<br>`(Rtt.uh[((Vu.uh[i] >> 14)&0x3)]<<15))>>16);`<br>`}` |

##### Class: COPROC_VX (slots 2)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vx.h=vmpa(Vx.h,Vu.h,Rtt.h):sat` | `HVX_Vector Q6_Vh_vmpa_VhVhVhPh_sat(HVX_Vector Vx, HVX_Vector Vu, Word64 Rtt)` |
| `Vx.h=vmpa(Vx.h,Vu.uh,Rtt.uh):sat` | `HVX_Vector Q6_Vh_vmpa_VhVhVuhPuh_sat (HVX_Vector Vx, HVX_Vector Vu, Word64 Rtt)` |
| `Vx.h=vmps(Vx.h,Vu.uh,Rtt.uh):sat` | `HVX_Vector Q6_Vh_vmps_VhVhVuhPuh_sat (HVX_Vector Vx, HVX_Vector Vu, Word64 Rtt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vx.h=vmpa(Vx.h,Vu.h,Rtt.h ):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.h=vmpa(Vx.h,Vu.uh,Rtt. uh):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vx.h=vmps(Vx.h,Vu.uh,Rtt. uh):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply add

Compute the sum of two byte multiplies. The two products consist of either unsigned bytes or signed halfwords coming from the vector registers Vuu and Vvv. These are multiplied by a signed byte coming from a scalar register Rt. The result of the summation is a signed halfword or word. Each corresponding pair of elements in Vuu and Vvv is weighted, using Rt.b[0] and Rt.b[1] for the even elements, and Rt.b[2] and Rt.b[3] for the odd elements.

Optionally accumulates the product with the destination vector register Vxx.

For vector by vector, compute the sum of two byte multiplies. The two products consist of an unsigned byte vector operand multiplied by a signed byte scalar. The result of the summation is a signed halfword. Even elements from the input vector register pairs Vuu and Vvv are multiplied together and placed in the even register of Vdd. Odd elements are placed in the odd register of Vdd.

Vdd.h [+]=vmpa(Vuu.ub,Rt.b)

|  |  |
|---|---|
| [1] | [0] |

Vuu.V[1]

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | [1] |  | [0] |

Vuu.V[0]

Rt.b[3] X X Rt.b[1]

Rt.b[2] X X Rt.b[0]

+ +

|  |  |  |  |
|---|---|---|---|
| [0] | [0] |  |  |
|  |  |  |  |

Vdd.V[1]

[0] Vdd.V[0]

Each lane

Vdd.h =vmpa(Vuu.ub,Vvv.b)

|  |  |
|---|---|
| b[1] | b[0] |

Vuu.V[1]

b[1] b[0] Vuu.V[0]

|  |  |
|---|---|
| b[1] | b[0] |

b[1] b[0] Vuu.V[1]

Vuu.V[0]

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | b[1] |  | b[0] |

Vvv.V[1]

b[1] b[0] Vvv.V[0]

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | b[1] |  | b[0] |

b[1] b[0] Vvv.V[1]

Vvv.V[0]

X X

X X

+

+

h[0] Vdd.V[1] h[0] Vdd.V[0]

Each 16-bit lane pair

| Syntax | Behavior |
|---|---|
| `Vdd.h=vmpa(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].uh[i].ub[0] * Rt.b[0]) + `<br>`(Vuu.v[1].uh[i].ub[0] * Rt.b[1]);`<br>`Vdd.v[1].h[i] = (Vuu.v[0].uh[i].ub[1] * Rt.b[2]) + `<br>`(Vuu.v[1].uh[i].ub[1] * Rt.b[3]);`<br>`}` |
| `Vdd.h=vmpa(Vuu.ub,Rt.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = (Vuu.v[0].uh[i].ub[0] * Rt.ub[0]) + `<br>`(Vuu.v[1].uh[i].ub[0] * Rt.ub[1]);`<br>`Vdd.v[1].uh[i] = (Vuu.v[0].uh[i].ub[1] * Rt.ub[2]) + `<br>`(Vuu.v[1].uh[i].ub[1] * Rt.ub[3]);`<br>`}` |
| `Vdd.h=vmpa(Vuu.ub,Vvv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].uh[i].ub[0] * `<br>`Vvv.v[0].uh[i].b[0]) + (Vuu.v[1].uh[i].ub[0] * `<br>`Vvv.v[1].uh[i].b[0]);`<br>`Vdd.v[1].h[i] = (Vuu.v[0].uh[i].ub[1] * `<br>`Vvv.v[0].uh[i].b[1]) + (Vuu.v[1].uh[i].ub[1] * `<br>`Vvv.v[1].uh[i].b[1]);`<br>`}` |
| `Vdd.h=vmpa(Vuu.ub,Vvv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].uh[i].ub[0] * `<br>`Vvv.v[0].uh[i].ub[0]) + (Vuu.v[1].uh[i].ub[0] * `<br>`Vvv.v[1].uh[i].ub[0]);`<br>`Vdd.v[1].h[i] = (Vuu.v[0].uh[i].ub[1] * `<br>`Vvv.v[0].uh[i].ub[1]) + (Vuu.v[1].uh[i].ub[1] * `<br>`Vvv.v[1].uh[i].ub[1]);`<br>`}` |
| `Vdd.w=vmpa(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vuu.v[0].w[i].h[0] * Rt.b[0]) + `<br>`(Vuu.v[1].w[i].h[0] * Rt.b[1]);`<br>`Vdd.v[1].w[i] = (Vuu.v[0].w[i].h[1] * Rt.b[2]) + `<br>`(Vuu.v[1].w[i].h[1] * Rt.b[3]);`<br>`}` |
| `Vdd.w=vmpa(Vuu.uh,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vuu.v[0].w[i].uh[0] * Rt.b[0]) + `<br>`(Vuu.v[1].w[i].uh[0] * Rt.b[1]);`<br>`Vdd.v[1].w[i] = (Vuu.v[0].w[i].uh[1] * Rt.b[2]) + `<br>`(Vuu.v[1].w[i].uh[1] * Rt.b[3]);`<br>`}` |
| `Vxx.h+=vmpa(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vuu.v[0].uh[i].ub[0] * Rt.b[0]) + `<br>`(Vuu.v[1].uh[i].ub[0] * Rt.b[1]);`<br>`Vxx.v[1].h[i] += (Vuu.v[0].uh[i].ub[1] * Rt.b[2]) + `<br>`(Vuu.v[1].uh[i].ub[1] * Rt.b[3]);`<br>`}` |
| `Vxx.h+=vmpa(Vuu.ub,Rt.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].uh[i] += (Vuu.v[0].uh[i].ub[0] * Rt.ub[0]) + `<br>`(Vuu.v[1].uh[i].ub[0] * Rt.ub[1]);`<br>`Vxx.v[1].uh[i] += (Vuu.v[0].uh[i].ub[1] * Rt.ub[2]) + `<br>`(Vuu.v[1].uh[i].ub[1] * Rt.ub[3]);`<br>`}` |
| `Vxx.w+=vmpa(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vuu.v[0].w[i].h[0] * Rt.b[0]) + `<br>`(Vuu.v[1].w[i].h[0] * Rt.b[1]);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].w[i].h[1] * Rt.b[2]) + `<br>`(Vuu.v[1].w[i].h[1] * Rt.b[3]);`<br>`}` |
| `Vxx.w+=vmpa(Vuu.uh,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vuu.v[0].w[i].uh[0] * Rt.b[0]) + `<br>`(Vuu.v[1].w[i].uh[0] * Rt.b[1]);`<br>`Vxx.v[1].w[i] += (Vuu.v[0].w[i].uh[1] * Rt.b[2]) + `<br>`(Vuu.v[1].w[i].uh[1] * Rt.b[3]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vmpa(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vmpa_WubRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.h=vmpa(Vuu.ub,Rt.ub)` | `HVX_VectorPair Q6_Wh_vmpa_WubRub(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.h=vmpa(Vuu.ub,Vvv.b)` | `HVX_VectorPair Q6_Wh_vmpa_WubWb(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.h=vmpa(Vuu.ub,Vvv.ub)` | `HVX_VectorPair Q6_Wh_vmpa_WubWub(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.w=vmpa(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vmpa_WhRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.w=vmpa(Vuu.uh,Rt.b)` | `HVX_VectorPair Q6_Ww_vmpa_WuhRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.h+=vmpa(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vmpaacc_WhWubRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.h+=vmpa(Vuu.ub,Rt.ub)` | `HVX_VectorPair Q6_Wh_vmpaacc_WhWubRub(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.w+=vmpa(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vmpaacc_WwWhRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.w+=vmpa(Vuu.uh,Rt.b)` | `HVX_VectorPair Q6_Ww_vmpaacc_WwWuhRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.h=vmpa(Vuu.ub,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.w=vmpa(Vuu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vxx.h+=vmpa(Vuu.ub,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vxx.w+=vmpa(Vuu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.h=vmpa(Vuu.ub,Rt.ub) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.w=vmpa(Vuu.uh,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vxx.w+=vmpa(Vuu.uh,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vxx.h+=vmpa(Vuu.ub,Rt.ub ) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.h=vmpa(Vuu.ub,Vvv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.h=vmpa(Vuu.ub,Vvv.u b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| Field name | Description |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply vector by scalar

Multiply groups of elements in the vector Vu by the corresponding elements in the scalar register Rt.

This operation has two forms. In the first form the product is not modified, and is optionally accumulated with the destination register. The even results are placed in the even vector register of the destination register pair, while the odd results are placed in the odd vector register.

Supports signed by signed halfword, unsigned by unsigned byte, unsigned by signed byte, and unsigned halfword by unsigned halfword.

Vxx.h [+]=vmpy(Vu.ub,Rt.b) Vd.h =vmpy(Vu.h,Rt.h):<<1:rnd:sat

|  |  |  |  |
|---|---|---|---|
| ub[3] | ub[2] | ub[1] | ub[0] |

Vu h[1] h[0] Vu

|  |  |
|---|---|
| h[1] | h[0] |

ub[3] ub[2] ub[1] ub[0] Vu Vu

X Rt.b[0] X Rt.h[0]

X Rt.b[1]

X Rt.b[2] X Rt.h[1]

X Rt.b[3]

<<1 <<1

+ +<sup>+0x8000</sup><sup>+0x8000</sup> Optional round

Optional accumulation

|  |  |  |  |  |
|---|---|---|---|---|
|  |  |  |  |  |
|  |  | h[1] |  | h[0] |
|  |  |  |  |  |

+ +

Saturate upper

SAT SAT

16 bits

Vdd.V[0]

H[1] H[1]

|  |  |
|---|---|
| h[1] | h[0] |

Vdd.V[1]h[1]h[0] Vd

|  |  |
|---|---|
| h[1] | h[0] |

h[1]h[0] Vdd.V[1] Vd

Each 32-bit lane Each 32 bit-lane

Syntax Behavior

|  |  |
|---|---|
| `Vdd.h=vmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vu.uh[i].ub[0] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vdd.v[1].h[i] = (Vu.uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vdd.uh=vmpy(Vu.ub,Rt.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = (Vu.uh[i].ub[0] * `<br>`Rt.ub[(2*i+0)%4]);`<br>`Vdd.v[1].uh[i] = (Vu.uh[i].ub[1] * `<br>`Rt.ub[(2*i+1)%4]);`<br>`}` |
| `Vdd.uw=vmpy(Vu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = (Vu.uw[i].uh[0] * Rt.uh[0]);`<br>`Vdd.v[1].uw[i] = (Vu.uw[i].uh[1] * Rt.uh[1]); `<br>`}` |
| `Vdd.w=vmpy(Vu.h,Rt.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vu.w[i].h[0] * Rt.h[0]);`<br>`Vdd.v[1].w[i] = (Vu.w[i].h[1] * Rt.h[1]);`<br>`}` |
| `Vxx.h+=vmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vu.uh[i].ub[0] * `<br>`Rt.b[(2*i+0)%4]);`<br>`Vxx.v[1].h[i] += (Vu.uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vxx.uh+=vmpy(Vu.ub,Rt.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].uh[i] += (Vu.uh[i].ub[0] * `<br>`Rt.ub[(2*i+0)%4]);`<br>`Vxx.v[1].uh[i] += (Vu.uh[i].ub[1] * `<br>`Rt.ub[(2*i+1)%4]);`<br>`}` |
| `Vxx.uw+=vmpy(Vu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].uw[i] += (Vu.uw[i].uh[0] * Rt.uh[0]);`<br>`Vxx.v[1].uw[i] += (Vu.uw[i].uh[1] * Rt.uh[1]);`<br>`}` |
| `Vxx.w+=vmpy(Vu.h,Rt.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] = Vxx.v[0].w[i].s64 + `<br>`(Vu.w[i].h[0] * Rt.h[0]);`<br>`Vxx.v[1].w[i] = Vxx.v[1].w[i].s64 + `<br>`(Vu.w[i].h[1] * Rt.h[1]);`<br>`}` |
| `Vxx.w+=vmpy(Vu.h,Rt.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] = sat₃₂(Vxx.v[0].w[i].s64 + `<br>`(Vu.w[i].h[0] * Rt.h[0]));`<br>`Vxx.v[1].w[i] = sat₃₂(Vxx.v[1].w[i].s64 + `<br>`(Vu.w[i].h[1] * Rt.h[1]));`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vmpy(Vu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vmpy_VubRb(HVX_Vector Vu, Word32 Rt)` |
| `Vdd.uh=vmpy(Vu.ub,Rt.ub)` | `HVX_VectorPair Q6_Wuh_vmpy_VubRub(HVX_Vector Vu, Word32 Rt)` |
| `Vdd.uw=vmpy(Vu.uh,Rt.uh)` | `HVX_VectorPair Q6_Wuw_vmpy_VuhRuh(HVX_Vector Vu, Word32 Rt)` |
| `Vdd.w=vmpy(Vu.h,Rt.h)` | `HVX_VectorPair Q6_Ww_vmpy_VhRh(HVX_Vector Vu, Word32 Rt)` |
| `Vxx.h+=vmpy(Vu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vmpyacc_WhVubRb(HVX_VectorPair Vxx, HVX_Vector Vu, Word32 Rt)` |
| `Vxx.uh+=vmpy(Vu.ub,Rt.ub)` | `HVX_VectorPair Q6_Wuh_vmpyacc_WuhVubRub (HVX_VectorPair Vxx, HVX_Vector Vu, Word32 Rt)` |
| `Vxx.uw+=vmpy(Vu.uh,Rt.uh)` | `HVX_VectorPair Q6_Wuw_vmpyacc_WuwVuhRuh (HVX_VectorPair Vxx, HVX_Vector Vu, Word32 Rt)` |
| `Vxx.w+=vmpy(Vu.h,Rt.h)` | `HVX_VectorPair Q6_Ww_vmpyacc_WwVhRh(HVX_VectorPair Vxx, HVX_Vector Vu, Word32 Rt)` |
| `Vxx.w+=vmpy(Vu.h,Rt.h):sat` | `HVX_VectorPair Q6_Ww_vmpyacc_WwVhRh_sat (HVX_VectorPair Vxx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.h=vmpy(Vu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vxx.h+=vmpy(Vu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.w=vmpy(Vu.h,Rt.h) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.uw=vmpy(Vu.uh,Rt.uh) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.w+=vmpy(Vu.h,Rt.h):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vxx.uw+=vmpy(Vu.uh,Rt.u h) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.uh+=vmpy(Vu.ub,Rt.ub ) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vxx.w+=vmpy(Vu.h,Rt.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.uh=vmpy(Vu.ub,Rt.ub) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply vector by vector

Multiply groups of elements in the vector Vu by the corresponding elements in the vector register Vv. This operation has two forms.

In the first form the product is not modified, and optionally accumulates with the destination register. The even results are placed in the even vector register of the destination register pair, while the odd results are placed in the odd vector register. Supports signed by signed halfword, unsigned by unsigned byte, unsigned by signed byte, and unsigned halfword by unsigned halfword.

The second form of this operation keeps the output precision the same as the input width by shifting the product left by 1, saturating the product to 32 bits, and placing the upper 16 bits in the output.

Vxx.h [+]=vmpy(Vu.ub,Vv.b) Vd.h =vmpy(Vu.h,Vv.h):<<1:rnd:sat

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vv h[1] h[0] Vv

|  |  |
|---|---|
| h[1] | h[0] |

b[3] b[2] b[1] b[0] Vv Vv

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |
| ub[3] |  | ub[2] |  | ub[1] |  | ub[0] |  |

Vu h[1] h[0] Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
| h[1] |  | h[0] |  |

ub[3] ub[2] ub[1] ub[0] Vu Vu

X X

X

X X

X

<<1 <<1

+ +<sup>+0x8000</sup><sup>+0x8000</sup> Optional roun

Optional accumulation

|  |  |  |  |  |
|---|---|---|---|---|
|  |  |  |  |  |
|  |  | h[1] |  | h[0] |
|  |  |  |  |  |

+ +

Saturate uppe

SAT SAT

16-bits

Vdd.V[0]

H[1] H[1]

|  |  |
|---|---|
| h[1] | h[0] |

Vdd.V[1]h[1]h[0] Vd

|  |  |
|---|---|
| h[1] | h[0] |

h[1]h[0] Vdd.V[1] Vd

|  |  |
|---|---|
| Each 32-bit lane | Each 32-bit lane |
| Syntax | Behavior |

|  |  |
|---|---|
| `Vdd.h=vmpy(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vu.h[i].b[0] * Vv.h[i].b[0]);`<br>`Vdd.v[1].h[i] = (Vu.h[i].b[1] * Vv.h[i].b[1]);`<br>`}` |
| `Vdd.h=vmpy(Vu.ub,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vu.uh[i].ub[0] * Vv.h[i].b[0]);`<br>`Vdd.v[1].h[i] = (Vu.uh[i].ub[1] * Vv.h[i].b[1]);`<br>`}` |
| `Vdd.uh=vmpy(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = (Vu.uh[i].ub[0] * `<br>`Vv.uh[i].ub[0]);`<br>`Vdd.v[1].uh[i] = (Vu.uh[i].ub[1] * `<br>`Vv.uh[i].ub[1]);`<br>`}` |
| `Vdd.uw=vmpy(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = (Vu.uw[i].uh[0] * `<br>`Vv.uw[i].uh[0]);`<br>`Vdd.v[1].uw[i] = (Vu.uw[i].uh[1] * `<br>`Vv.uw[i].uh[1]);`<br>`}` |
| `Vdd.w=vmpy(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vu.w[i].h[0] * Vv.w[i].h[0]);`<br>`Vdd.v[1].w[i] = (Vu.w[i].h[1] * Vv.w[i].h[1]);`<br>`}` |
| `Vdd.w=vmpy(Vu.h,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vu.w[i].h[0] * Vv.uw[i].uh[0]);`<br>`Vdd.v[1].w[i] = (Vu.w[i].h[1] * Vv.uw[i].uh[1]);`<br>`}` |
| `Vxx.h+=vmpy(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vu.h[i].b[0] * Vv.h[i].b[0]);`<br>`Vxx.v[1].h[i] += (Vu.h[i].b[1] * Vv.h[i].b[1]);`<br>`}` |
| `Vxx.h+=vmpy(Vu.ub,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vu.uh[i].ub[0] * `<br>`Vv.h[i].b[0]);`<br>`Vxx.v[1].h[i] += (Vu.uh[i].ub[1] * `<br>`Vv.h[i].b[1]);`<br>`}` |
| `Vxx.uh+=vmpy(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].uh[i] += (Vu.uh[i].ub[0] * `<br>`Vv.uh[i].ub[0]);`<br>`Vxx.v[1].uh[i] += (Vu.uh[i].ub[1] * `<br>`Vv.uh[i].ub[1]);`<br>`}` |
| `Vxx.uw+=vmpy(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].uw[i] += (Vu.uw[i].uh[0] * `<br>`Vv.uw[i].uh[0]);`<br>`Vxx.v[1].uw[i] += (Vu.uw[i].uh[1] * `<br>`Vv.uw[i].uh[1]);`<br>`}` |

| Syntax | Behavior |
|---|---|
| `Vxx.w+=vmpy(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vu.w[i].h[0] * Vv.w[i].h[0]);`<br>`Vxx.v[1].w[i] += (Vu.w[i].h[1] * Vv.w[i].h[1]);`<br>`}` |
| `Vxx.w+=vmpy(Vu.h,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vu.w[i].h[0] * `<br>`Vv.uw[i].uh[0]);`<br>`Vxx.v[1].w[i] += (Vu.w[i].h[1] * `<br>`Vv.uw[i].uh[1]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vmpy(Vu.b,Vv.b)` | `HVX_VectorPair Q6_Wh_vmpy_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.h=vmpy(Vu.ub,Vv.b)` | `HVX_VectorPair Q6_Wh_vmpy_VubVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.uh=vmpy(Vu.ub,Vv.ub)` | `HVX_VectorPair Q6_Wuh_vmpy_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.uw=vmpy(Vu.uh,Vv.uh)` | `HVX_VectorPair Q6_Wuw_vmpy_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vmpy(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Ww_vmpy_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.w=vmpy(Vu.h,Vv.uh)` | `HVX_VectorPair Q6_Ww_vmpy_VhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.h+=vmpy(Vu.b,Vv.b)` | `HVX_VectorPair Q6_Wh_vmpyacc_WhVbVb(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.h+=vmpy(Vu.ub,Vv.b)` | `HVX_VectorPair Q6_Wh_vmpyacc_WhVubVb(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.uh+=vmpy(Vu.ub,Vv.ub)` | `HVX_VectorPair Q6_Wuh_vmpyacc_WuhVubVub (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.uw+=vmpy(Vu.uh,Vv.uh)` | `HVX_VectorPair Q6_Wuw_vmpyacc_WuwVuhVuh (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.w+=vmpy(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Ww_vmpyacc_WwVhVh(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx.w+=vmpy(Vu.h,Vv.uh)` | `HVX_VectorPair Q6_Ww_vmpyacc_WwVhVuh(HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.h=vmpy(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.uh=vmpy(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.h=vmpy(Vu.ub,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.w=vmpy(Vu.h,Vv.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vxx.h+=vmpy(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vxx.uh+= vmpy(Vu.ub, Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vxx.h+=vmpy(Vu.ub,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vxx.w+=vmpy(Vu.h,Vv.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.uw= vmpy(Vu.uh, Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.w=vmpy(Vu.h,Vv.uh) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.uw+= vmpy(Vu.uh, Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vxx.w+=vmpy(Vu.h,Vv.uh) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply half precision vector by vector

Perform a vectorized single precision floating point multiply. The inputs are either both IEEE single precision, both 16-bit Qfloat, or a combination of each. The result is either a 16-bit Qfloat vector, or a double vector of widened 32-bit Qfloat.

| Syntax | Behavior |
|---|---|
| `Vd.qf16=vmpy(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.hf[i];`<br>`v = Vv.hf[i];`<br>`Vd.qf16[i] = rnd_sat(u.exp + v.exp, u.sig * `<br>`v.sig,0);`<br>`if(u.sign^v.sign) Vd.qf16[i] = -`<br>`(Vd.qf16[i]);`<br>`}` |
| `Vd.qf16=vmpy(Vu.qf16,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.hf[i];`<br>`Vd.qf16[i] = rnd_sat(u.exp+v.exp, u.sig * `<br>`v.sig,0);`<br>`if(v.sign) Vd.qf16[i] = -(Vd.qf16[i]);`<br>`}` |
| `Vd.qf16=vmpy(Vu.qf16,Vv.qf16)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.qf16[i];`<br>`Vd.qf16[i] = rnd_sat(u.exp + v.exp, u.sig * `<br>`v.sig,0);`<br>`}` |
| `Vdd.qf32=vmpy(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u0 = Vu.w[i] & 0xFFFF;`<br>`u1 = (Vu.w[i]>>16) & 0xFFFF;`<br>`v0 = Vv.w[i] & 0xFFFF;`<br>`v1 = (Vv.w[i]>>16) & 0xFFFF;`<br>`Vdd.v[0].qf32[i] = rnd_sat(u0.exp + v0.exp, `<br>`u0.sig * v0.sig, 0);`<br>`Vdd.v[1].qf32[i] = rnd_sat(u1.exp + v1.exp, `<br>`u1.sig * v1.sig, 0);`<br>`if(u0.sign^v0.sign) Vdd.v[0].qf32[i] = -`<br>`(Vdd.v[0].qf32[i]);`<br>`if(u1.sign^v1.sign) Vdd.v[1].qf32[i] = -`<br>`(Vdd.v[1].qf32[i]);`<br>`}` |
| `Vdd.qf32=vmpy(Vu.qf16,Vv.hf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u0 = Vu.w[i] & 0xFFFF;`<br>`u1 = (Vu.w[i]>>16) & 0xFFFF;`<br>`v0 = Vv.w[i] & 0xFFFF;`<br>`v1 = (Vv.w[i]>>16) & 0xFFFF;`<br>`Vdd.v[0].qf32[i] = rnd_sat(u0.exp + v0.exp, `<br>`u0.sig * v0.sig,0);`<br>`Vdd.v[1].qf32[i] = rnd_sat(u1.exp + v1.exp, `<br>`u1.sig * v1.sig,0);`<br>`if(v0.sign) Vdd.v[0].qf32[i] = -`<br>`(Vdd.v[0].qf32[i]);`<br>`if(v1.sign) Vdd.v[1].qf32[i] = -`<br>`(Vdd.v[1].qf32[i]);`<br>`}` |
| `Vdd.qf32=vmpy(Vu.qf16,Vv.qf16)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u0 = Vu.w[i] & 0xFFFF;`<br>`u1 = (Vu.w[i]>>16) & 0xFFFF;`<br>`v0 = Vv.w[i] & 0xFFFF;`<br>`v1 = (Vv.w[i]>>16) & 0xFFFF;`<br>`Vdd.v[0].qf32[i] = rnd_sat(u0.exp+v0.exp, `<br>`u0.sig*v0.sig, 0);`<br>`Vdd.v[1].qf32[i] = rnd_sat(u1.exp+v1.exp, `<br>`u1.sig*v1.sig, 0);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf16=vmpy(Vu.hf,Vv.hf)` | `HVX_Vector Q6_Vqf16_vmpy_VhfVhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vmpy(Vu.qf16,Vv.hf)` | `HVX_Vector Q6_Vqf16_vmpy_Vqf16Vhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vmpy(Vu.qf16,Vv.qf16)` | `HVX_Vector Q6_Vqf16_vmpy_Vqf16Vqf16(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.qf32=vmpy(Vu.hf,Vv.hf)` | `HVX_VectorPair Q6_Wqf32_vmpy_VhfVhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.qf32=vmpy(Vu.qf16,Vv.hf)` | `HVX_VectorPair Q6_Wqf32_vmpy_Vqf16Vhf (HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.qf32=vmpy(Vu.qf16,Vv.qf16)` | `HVX_VectorPair Q6_Wqf32_vmpy_Vqf16Vqf16 (HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.qf32= vmpy(Vu.qf16,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.qf16= vmpy(Vu.qf16,Vv.qf16) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.qf16=vmpy(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.qf16= vmpy(Vu.qf16,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.qf32= vmpy(Vu.qf16,Vv.qf16) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.qf32= vmpy(Vu.hf,Vv.hf) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Integer multiply vector by vector

Multiply corresponding elements in Vu by the corresponding elements in Vv, and place the lower half of the result in the destination vector register Vd. Supports signed halfwords, and optional accumulation of the product with the destination vector register Vx.

Vd.h = vmpyi(Vu.h,Vv.h)

h[0] Vv

|  |  |
|---|---|
|  | h[0] |

Vu

Output only lower

X

16 LSBs

+

Optional accumulate

<sup>h[0]</sup> Vd

Each 16-bit lane

| Syntax | Behavior |
|---|---|
| `Vd.h=vmpyi(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] * Vv.h[i]);`<br>`}` |
| `Vx.h+=vmpyi(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i] += (Vu.h[i] * Vv.h[i]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

```
Vd.h=vmpyi(Vu.h,Vv.h)HVX_Vector Q6_Vh_vmpyi_VhVh(HVX_Vector Vu, HVX_Vector
                        Vv)
Vx.h+=vmpyi(Vu.h,Vv.h)HVX_Vector Q6_Vh_vmpyiacc_VhVhVh(HVX_Vector Vx,
                        HVX_Vector Vu, HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vmpyi(Vu.h,Vv.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vx.h+=vmpyi(Vu.h,Vv.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Integer multiply (32 × 16)

Multiply words in one vector by even or odd halfwords in another vector. Take the lower part. Some versions of this operation perform unusual shifts to facilitate 32 × 32 multiply synthesis.

| Syntax | Behavior |
|---|---|
| `Vd.w=vmpyie(Vu.w,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Vv.w[i].uh[0]);`<br>`}` |
| `Vd.w=vmpyio(Vu.w,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Vv.w[i].h[1]);`<br>`}` |
| `Vx.w+=vmpyie(Vu.w,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] = Vx.w[i] + (Vu.w[i] * Vv.w[i].h[0]);`<br>`}` |
| `Vx.w+=vmpyie(Vu.w,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] = Vx.w[i] + (Vu.w[i] * Vv.w[i].uh[0]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vd.w=vmpyie(Vu.w,Vv.uh)` | `HVX_Vector Q6_Vw_vmpyie_VwVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vmpyio(Vu.w,Vv.h)` | `HVX_Vector Q6_Vw_vmpyio_VwVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vmpyie(Vu.w,Vv.h)` | `HVX_Vector Q6_Vw_vmpyieacc_VwVwVh(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vmpyie(Vu.w,Vv.uh)` | `HVX_Vector Q6_Vw_vmpyieacc_VwVwVuh(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.w+=vmpyie(Vu.w,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vx.w+=vmpyie(Vu.w,Vv.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vmpyie(Vu.w,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.w=vmpyio(Vu.w,Vv.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Integer multiply accumulate even/odd

Multiply groups of words in vector register Vu by the elements in Rt. The lower 32-bit results are placed in vector register Vd.

The operation has two forms: signed words or halfwords in Vu, multiplied by signed bytes in Rt.

Optionally, accumulates the product with the destination vector register Vx.

Vd.w [+]= vmpyi(Vu.w,Rt.b) Vd.w [+]= vmpyi(Vu.w,Rt.h)

|  |  |  |  |
|---|---|---|---|
| w[3] | w[2] | w[1] | w[0] |

Vu w[3] w[2] w[1] w[0] Vu

|  |  |  |  |
|---|---|---|---|
| w[3] | w[2] | w[1] | w[0] |

w[3] w[2] w[1] w[0] Vu Vu

X Rt.b[3] X Rt.h[1]

X Rt.b[2] X

X Rt.b[1] X

Output only lower 32 LSBs X Rt.b[0] Output only lower 32 LSBs X Rt.h[0]

+ + + +<sup>Optional</sup><sub>accumulate</sub> + + + +<sup>Optional</sup><sub>accumulate</sub>

|  |  |  |  |
|---|---|---|---|
| w[3] | w[2] | w[1] | w[0] |

Vd w[3] w[2] w[1] w[0] Vd

|  |  |  |  |
|---|---|---|---|
| w[3] | w[2] | w[1] | w[0] |

w[3] w[2] w[1] w[0] Vd Vd

Each 128-bit lane Each 128-bit lane

| Syntax | Behavior |
|---|---|
| `Vd.w=vmpyi(Vu.w,Rt.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Rt.h[i % 2]) ;`<br>`}` |
| `Vx.w+=vmpyi(Vu.w,Rt.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i] * Rt.h[i % 2]) ;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

```
Vd.w=vmpyi(Vu.w,Rt.h)HVX_Vector Q6_Vw_vmpyi_VwRh(HVX_Vector Vu, Word32 Rt)
Vx.w+=vmpyi(Vu.w,Rt.h)HVX_Vector Q6_Vw_vmpyiacc_VwVwRh(HVX_Vector Vx,
                        HVX_Vector Vu, Word32 Rt)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx.w+=vmpyi(Vu.w,Rt.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vmpyi(Vu.w,Rt.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply single precision vector by vector

Perform a vectorized single precision floating point multiply. The inputs are either both IEEE single precision or both 32-bit Qfloat. The result is a 32-bit Qfloat vector.

| Syntax | Behavior |
|---|---|
| `Vd.qf32=vmpy(Vu.qf32,Vv.qf32)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`v = Vv.qf32[i];`<br>`Vd.qf32[i] = rnd_sat(u.exp + v.exp, u.sig * `<br>`v.sig, 0);`<br>`}` |
| `Vd.qf32=vmpy(Vu.sf,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.sf[i];`<br>`v = Vv.sf[i];`<br>`Vd.qf32[i] = rnd_sat(u.exp + v.exp, u.sig * `<br>`v.sig,0);`<br>`if(u.sign^v.sign) Vd.qf32[i] = -`<br>`(Vd.qf32[i]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf32=vmpy(Vu.qf32,Vv.qf32)` | `HVX_Vector Q6_Vqf32_vmpy_Vqf32Vqf32(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf32=vmpy(Vu.sf,Vv.sf)` | `HVX_Vector Q6_Vqf32_vmpy_VsfVsf(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.qf32=vmpy(Vu.qf32,Vv. qf32) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.qf32=vmpy(Vu.sf,Vv.sf) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Multiply (32 × 16)

Multiply words in one vector by even or odd halfwords in another vector. Take the upper part. Some versions of this operation perform specific shifts to facilitate 32 × 32 multiply synthesis.

An important operation is a 32 × 32 fractional multiply, equivalent to (OP1 * OP2) >> 31. fn(0x80000000, 0x80000000) must saturate to 0x7fffffff.

The rounding fractional multiply: vectorize(sat₃₂(x * y + 0x40000000)>>31)) equivalent to: {V2 = vmpye(V0.w, V1.uh)} {V2 += vmpyo(V0.w, V1.h):<<1:rnd:sat:shift}

The nonrounding fractional multiply version: vectorize(sat₃₂(x * y)>>31)) equivalent to: {V2 = vmpye(V0.w, V1.uh)} {V2 += vmpyo(V0.w, V1.h):<<1:sat:shift}

A key function is a 32-bit × 32-bit signed multiply where the 64-bit result is kept: vectorize((int64) x * (int64) y) equivalent to: {V3:2 = vmpye(V0.w, V1.uh)} {V3:2 += vmpyo(V0.w, V1.h)}

The lower 32 bits of products are in V2 and the upper 32 bits in V3. If only the `vmpye` operation is performed, the result is a 48-bit product of 32 signed x 16-bit unsigned asserted into the upper 48 bits of Vdd. If only the `vmpyo` operation is performed (assuming Vxx = #0), the result is a 32 signed × 16 signed product asserted into the upper 48 bits of Vxx.

| Syntax | Behavior |
|---|---|
| `Vd.w=vmpye(Vu.w,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Vv.w[i].uh[0]) >> 16;`<br>`}` |
| `Vd.w=vmpyo(Vu.w,Vv.h):<<1[:rnd]:`<br>`sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = sat₃₂(((((Vu.w[i] * Vv.w[i].h[1]) >> `<br>`14) + 1) >> 1));`<br>`}` |
| `Vdd=vmpye(Vu.w,Vv.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`prod = (Vu.w[i] * Vv.w[i].uh[0]);`<br>`Vdd.v[1].w[i] = prod >> 16;`<br>`Vdd.v[0].w[i] = prod << 16;`<br>`}` |
| `Vx.w+=vmpyo(Vu.w,Vv.h):<<1[:rnd]`<br>`:sat:shift` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] = sat₃₂(((((Vx.w[i] + (Vu.w[i] * `<br>`Vv.w[i].h[1])) >> 14) + 1) >> 1));`<br>`}` |
| `Vxx+=vmpyo(Vu.w,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`prod = (Vu.w[i] * Vv.w[i].h[1]) + Vxx.v[1].w[i];`<br>`Vxx.v[1].w[i] = prod >> 16;`<br>`Vxx.v[0].w[i].h[0]=Vxx.v[0].w[i] >> 16;`<br>`Vxx.v[0].w[i].h[1]=prod & 0x0000ffff;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vd.w=vmpye(Vu.w,Vv.uh)` | `HVX_Vector Q6_Vw_vmpye_VwVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vmpyo(Vu.w,Vv.h):<<1:rnd:` | `HVX_Vector` |
| `sat` | `Q6_Vw_vmpyo_VwVh_s1_rnd_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vmpyo(Vu.w,Vv.h):<<1:sat` | `HVX_Vector Q6_Vw_vmpyo_VwVh_s1_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd=vmpye(Vu.w,Vv.uh)` | `HVX_VectorPair Q6_W_vmpye_VwVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vmpyo(Vu.w,Vv.h):<<1:rnd` | `HVX_Vector` |
| `:sat:shift` | `Q6_Vw_vmpyoacc_VwVwVh_s1_rnd_sat_shift(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vmpyo(Vu.w,Vv.h):<<1:sat` | `HVX_Vector Q6_Vw_vmpyoacc_VwVwVh_s1_sat_shift` |
| `:shift` | `(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vxx+=vmpyo(Vu.w,Vv.h)` | `HVX_VectorPair Q6_W_vmpyoacc_WVwVh (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vxx+=vmpyo(Vu.w,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vx.w+=vmpyo(Vu.w,Vv.h): <<1:sat:shift |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vx.w+=vmpyo(Vu.w,Vv.h): <<1:rnd:sat:shift |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd=vmpye(Vu.w,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vmpyo(Vu.w,Vv.h):<<1:rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.w=vmpye(Vu.w,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vmpyo(Vu.w,Vv.h):<<1:sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply bytes with 4-wide reduction vector by scalar

Perform multiplication between the elements in vector Vu and the corresponding elements in the scalar register Rt, followed by a 4-way reduction to a word in each 32-bit lane. Accumulate the result in Vx or Vxx.

Supports the multiplication of unsigned byte data by signed or unsigned bytes in the scalar.

The operation has two forms: the first performs simple dot product of four elements into a single result. The second form takes a one bit immediate input and generates a vector register pair.

For #1 = 0, the even destination contains a simple dot product, the odd destination contains a dot product of the coefficients rotated by two elements and the upper two data elements taken from the even register of Vuu.

For #u = 1, the even destination takes coefficients rotated by -1 and data element 0 from the odd register of Vuu. The odd destination uses coefficients rotated by -1 and takes data element 3 from the even register of Vuu.

Vdd.w[+]=vrmpy(Vuu.ub,Rt.b, #0) Vdd.w[+]=vrmpy(Vuu.h,Rt.b, #1)

Vd.w[+]=vrmpy(Vu.ub,Rt.b)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vu ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0] ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0]

|  |  |  |
|---|---|---|
| ub[3] | ub[2] | ub[1] |

b[3] b[2] b[1] b[0] Vu ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0] ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0]

|  |  |  |  |
|---|---|---|---|
| ub[3] | ub[2] | ub[1] | ub[0] |

b[3] b[2] b[1] b[0] Vu ub[3] ub[2] ub[1] ub[0] Vuu.V[1] Vuu.V[0] ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0]

|  |  |  |
|---|---|---|
| ub[3] | ub[2] | ub[1] |

b[3] b[2] b[1] b[0] Vu ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0]

|  |  |  |  |
|---|---|---|---|
| ub[3] | ub[2] | ub[1] | ub[0] |

b[3] b[2] b[1] b[0] Vu ub[3] ub[2] ub[1] ub[0] Vuu.V[1] ub[3] ub[2] ub[1] ub[0] Vuu.V[0] ub[3] ub[2] ub[1] ub[0] Vuu.V[1] Vuu.V[0]

|  |  |  |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

X Rt.b[0]

X Rt.b[1]

X Rt.b[2]

X Rt.b[3] X Rt.b[0] X X Rt.b[0] X

X Rt.b[1] X X Rt.b[1] X

+Optional X Rt.b[2] X X Rt.b[2] X

|  |  |
|---|---|
|  |  |
|  |  |

X Rt.b[3] X Rt.b[0] X X Rt.b[0] X

X Rt.b[1] X X Rt.b[1] X

+Optional X Rt.b[2] X X Rt.b[2] X

|  |  |
|---|---|
|  |  |

+Accumulation X Rt.b[2] X X Rt.b[2] X

X Rt.b[3] X X Rt.b[3] X

|  |  |  |  |
|---|---|---|---|
| w[0] |  |  |  |
|  |  | 32bit Lane |  |
|  | 32bit Lane | 32bit Lane |  |
|  | 32bit Lane | 32bit Lane |  |

Optional Optional

+Optional + Accumulation +Optional +Accumulation

Accumulation Accumulation

w[0] Vdd.V[1] w[0] Vdd.V[0] w[0] Vdd.V[1] w[0] Vdd.V[0]

32bit lane pair 32bit lane pair

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

| Syntax | Behavior |
|---|---|
| `Vdd.uw=vrmpy(Vuu.ub,Rt.ub,#u`<br>`1)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = (Vuu.v[#u ? 1:0].uw[i].ub[0] * `<br>`Rt.ub[(0-#u) & 0x3]);`<br>`Vdd.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[1] * Rt.ub[(1-`<br>`#u) & 0x3]);`<br>`Vdd.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[2] * Rt.ub[(2-`<br>`#u) & 0x3]);`<br>`Vdd.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.ub[(3-`<br>`#u) & 0x3]);`<br>`Vdd.v[1].uw[i] = (Vuu.v[1 ].uw[i].ub[0] * Rt.ub[(2-`<br>`#u) & 0x3]);`<br>`Vdd.v[1].uw[i] += (Vuu.v[1 ].uw[i].ub[1] * Rt.ub[(3-`<br>`#u) & 0x3]);`<br>`Vdd.v[1].uw[i] += (Vuu.v[#u ? 1:0].uw[i].ub[2] * `<br>`Rt.ub[(0-#u) & 0x3]);`<br>`Vdd.v[1].uw[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.ub[(1-`<br>`#u) & 0x3]);`<br>`}` |
| `Vdd.w=vrmpy(Vuu.ub,Rt.b,#u1)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vuu.v[#u ? 1:0].uw[i].ub[0] * `<br>`Rt.b[(0-#u) & 0x3]);`<br>`Vdd.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[1] * Rt.b[(1-`<br>`#u) & 0x3]);`<br>`Vdd.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[2] * Rt.b[(2-`<br>`#u) & 0x3]);`<br>`Vdd.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.b[(3-`<br>`#u) & 0x3]);`<br>`Vdd.v[1].w[i] = (Vuu.v[1 ].uw[i].ub[0] * Rt.b[(2-#u) `<br>`& 0x3]);`<br>`Vdd.v[1].w[i] += (Vuu.v[1 ].uw[i].ub[1] * Rt.b[(3-`<br>`#u) & 0x3]);`<br>`Vdd.v[1].w[i] += (Vuu.v[#u ? 1:0].uw[i].ub[2] * `<br>`Rt.b[(0-#u) & 0x3]);`<br>`Vdd.v[1].w[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.b[(1-`<br>`#u) & 0x3]);`<br>`}` |
| `Vxx.uw+=vrmpy(Vuu.ub,Rt.ub,#`<br>`u1)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].uw[i] += (Vuu.v[#u ? 1:0].uw[i].ub[0] * `<br>`Rt.ub[(0-#u) & 0x3]);`<br>`Vxx.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[1] * Rt.ub[(1-`<br>`#u) & 0x3]);`<br>`Vxx.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[2] * Rt.ub[(2-`<br>`#u) & 0x3]);`<br>`Vxx.v[0].uw[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.ub[(3-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].uw[i] += (Vuu.v[1 ].uw[i].ub[0] * Rt.ub[(2-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].uw[i] += (Vuu.v[1 ].uw[i].ub[1] * Rt.ub[(3-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].uw[i] += (Vuu.v[#u ? 1:0].uw[i].ub[2] * `<br>`Rt.ub[(0-#u) & 0x3]);`<br>`Vxx.v[1].uw[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.ub[(1-`<br>`#u) & 0x3]);`<br>`}` |
| `Vxx.w+=vrmpy(Vuu.ub,Rt.b,#u1`<br>`)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i] += (Vuu.v[#u ? 1:0].uw[i].ub[0] * `<br>`Rt.b[(0-#u) & 0x3]);`<br>`Vxx.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[1] * Rt.b[(1-`<br>`#u) & 0x3]);`<br>`Vxx.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[2] * Rt.b[(2-`<br>`#u) & 0x3]);`<br>`Vxx.v[0].w[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.b[(3-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].w[i] += (Vuu.v[1 ].uw[i].ub[0] * Rt.b[(2-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].w[i] += (Vuu.v[1 ].uw[i].ub[1] * Rt.b[(3-`<br>`#u) & 0x3]);`<br>`Vxx.v[1].w[i] += (Vuu.v[#u ? 1:0].uw[i].ub[2] * `<br>`Rt.b[(0-#u) & 0x3]);`<br>`Vxx.v[1].w[i] += (Vuu.v[0 ].uw[i].ub[3] * Rt.b[(1-`<br>`#u) & 0x3]);`<br>`}` |

##### Intrinsics

|  |  |
|---|---|
| `Vdd.uw=vrmpy(Vuu.ub,Rt.ub,#u1)` | `HVX_VectorPair Q6_Wuw_vrmpy_WubRubI(HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |
| `Vdd.w=vrmpy(Vuu.ub,Rt.b,#u1)` | `HVX_VectorPair Q6_Ww_vrmpy_WubRbI(HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |
| `Vxx.uw+=vrmpy(Vuu.ub,Rt.ub,#u1)` | `HVX_VectorPair Q6_Wuw_vrmpyacc_WuwWubRubI (HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |
| `Vxx.w+=vrmpy(Vuu.ub,Rt.b,#u1)` | `HVX_VectorPair Q6_Ww_vrmpyacc_WwWubRbI (HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | i | d | d | d | d | d | Vdd.w=vrmpy(Vuu.ub, Rt.b,#u1) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | i | x | x | x | x | x | Vxx.w+=vrmpy(Vuu.ub, Rt.b,#u1) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | i | x | x | x | x | x | Vxx.uw+=vrmpy(Vuu.ub, Rt.ub,#u1) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | i | d | d | d | d | d | Vdd.uw=vrmpy(Vuu.ub, Rt.ub,#u1) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| Field name | Description |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply by byte with accumulate and 4-wide reduction vector by

#### vector

The `vrmpy` instruction performs a dot product function between four byte elements in vector register Vu and four byte elements in Vv. the sum of products can optionally accumulate into Vx or write into Vd as words within each 32-bit lane.

Data types are unsigned by unsigned, signed by signed, or unsigned by signed.

Vd.w[+]=vrmpy(Vu.b,Vv.b)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vu

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |
| b[3] | b[3] | b[2] | b[2] | b[1] | b[1] | b[0] |

Vv

X X X X

+<sup>Optional accumulation</sup>

|  |  |  |
|---|---|---|
| w[0] | w[0] |  |
|  |  |  |

Vd

32-bit lane

| Syntax | Behavior |
|---|---|
| `Vx.uw+=vrmpy(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.uw[i] += (Vu.uw[i].ub[0] * `<br>`Vv.uw[i].ub[0]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[1] * `<br>`Vv.uw[i].ub[1]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[2] * `<br>`Vv.uw[i].ub[2]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[3] * `<br>`Vv.uw[i].ub[3]);`<br>`}` |
| `Vx.w+=vrmpy(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i].b[0] * Vv.w[i].b[0]);`<br>`Vx.w[i] += (Vu.w[i].b[1] * Vv.w[i].b[1]);`<br>`Vx.w[i] += (Vu.w[i].b[2] * Vv.w[i].b[2]);`<br>`Vx.w[i] += (Vu.w[i].b[3] * Vv.w[i].b[3]);`<br>`}` |
| `Vx.w+=vrmpy(Vu.ub,Vv.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.uw[i].ub[0] * Vv.w[i].b[0]);`<br>`Vx.w[i] += (Vu.uw[i].ub[1] * Vv.w[i].b[1]);`<br>`Vx.w[i] += (Vu.uw[i].ub[2] * Vv.w[i].b[2]);`<br>`Vx.w[i] += (Vu.uw[i].ub[3] * Vv.w[i].b[3]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vx.uw+=vrmpy(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vuw_vrmpyacc_VuwVubVub(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vrmpy(Vu.b,Vv.b)` | `HVX_Vector Q6_Vw_vrmpyacc_VwVbVb(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vrmpy(Vu.ub,Vv.b)` | `HVX_Vector Q6_Vw_vrmpyacc_VwVubVb(HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vx.uw+=vrmpy(Vu.ub,Vv.ub ) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vx.w+=vrmpy(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vx.w+=vrmpy(Vu.ub,Vv.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply with 3-wide reduction

Perform a 3-element sliding window pattern operation consisting of a two multiplies with an additional accumulation. Data elements are stored in the vector register pair Vuu, and coefficients in the scalar register Rt.

Vdd.h[+]=vtmpy(Vuu.b,Rt.b)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vuu.V[1] b[3] b[2] b[1] b[0] Vuu.V[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vuu.V[1] Vuu.V[0]

|  |  |  |  |  |  |
|---|---|---|---|---|---|
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

X Rt.b[0] X

X Rt.b[1] X

X Rt.b[2] X

X Rt.b[3] X

|  |  |
|---|---|
|  |  |
|  |  |

X Rt.b[1] X

X Rt.b[2] X

X Rt.b[3] X

+ +<sup>Optional accumulation</sup> + +Optional accumulation

|  |  |
|---|---|
| h[1] | h[0] |

Vdd.V[1] h[1] h[0] Vdd.V[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vdd.V[1] Vdd.V[0]

32-bit lane pair

Vdd[+]=vtmpyhb(Vuu,Rt)

|  |  |
|---|---|
| h[1] | h[0] |

Vuu.V[1] h[1] h[0] Vuu.V[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vuu.V[1] Vuu.V[0]

X X Rt.b[0/2]

X X Rt.b[1/3]

+ +<sup>Optional Accumulation</sup>

w[0] Vdd.V[1] w[0] Vdd.V[0]

32bit lane

| Syntax | Behavior |
|---|---|
| `Vdd.h=vtmpy(Vuu.b,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].h[i].b[0] * Rt.b[(2*i )%4]);`<br>`Vdd.v[0].h[i] += (Vuu.v[0].h[i].b[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[0].h[i] += Vuu.v[1].h[i].b[0];`<br>`Vdd.v[1].h[i] = (Vuu.v[0].h[i].b[1] * Rt.b[(2*i )%4]);`<br>`Vdd.v[1].h[i] += (Vuu.v[1].h[i].b[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[1].h[i] += Vuu.v[1].h[i].b[1] ;`<br>`}` |
| `Vdd.h=vtmpy(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = (Vuu.v[0].uh[i].ub[0] * Rt.b[(2*i `<br>`)%4]);`<br>`Vdd.v[0].h[i] += (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[0].h[i] += Vuu.v[1].uh[i].ub[0];`<br>`Vdd.v[1].h[i] = (Vuu.v[0].uh[i].ub[1] * Rt.b[(2*i `<br>`)%4]);`<br>`Vdd.v[1].h[i] += (Vuu.v[1].uh[i].ub[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vdd.v[1].h[i] += Vuu.v[1].uh[i].ub[1] ;`<br>`}` |
| `Vdd.w=vtmpy(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = (Vuu.v[0].w[i].h[0] * Rt.b[(2*i+0)%4]);`<br>`Vdd.v[0].w[i]+= (Vuu.v[0].w[i].h[1] * Rt.b[(2*i+1)%4]);`<br>`Vdd.v[0].w[i]+= Vuu.v[1].w[i].h[0];`<br>`Vdd.v[1].w[i] = (Vuu.v[0].w[i].h[1] * Rt.b[(2*i+0)%4]);`<br>`Vdd.v[1].w[i]+= (Vuu.v[1].w[i].h[0] * Rt.b[(2*i+1)%4]);`<br>`Vdd.v[1].w[i]+= Vuu.v[1].w[i].h[1] ;`<br>`}` |
| `Vxx.h+=vtmpy(Vuu.b,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vuu.v[0].h[i].b[0] * Rt.b[(2*i )%4]);`<br>`Vxx.v[0].h[i] += (Vuu.v[0].h[i].b[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[0].h[i] += Vuu.v[1].h[i].b[0];`<br>`Vxx.v[1].h[i] += (Vuu.v[0].h[i].b[1] * Rt.b[(2*i )%4]);`<br>`Vxx.v[1].h[i] += (Vuu.v[1].h[i].b[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[1].h[i] += Vuu.v[1].h[i].b[1] ;`<br>`}` |
| `Vxx.h+=vtmpy(Vuu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.v[0].h[i] += (Vuu.v[0].uh[i].ub[0] * Rt.b[(2*i `<br>`)%4]);`<br>`Vxx.v[0].h[i] += (Vuu.v[0].uh[i].ub[1] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[0].h[i] += Vuu.v[1].uh[i].ub[0];`<br>`Vxx.v[1].h[i] += (Vuu.v[0].uh[i].ub[1] * Rt.b[(2*i `<br>`)%4]);`<br>`Vxx.v[1].h[i] += (Vuu.v[1].uh[i].ub[0] * `<br>`Rt.b[(2*i+1)%4]);`<br>`Vxx.v[1].h[i] += Vuu.v[1].uh[i].ub[1] ;`<br>`}` |
| `Vxx.w+=vtmpy(Vuu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].w[i]+= (Vuu.v[0].w[i].h[0] * Rt.b[(2*i+0)%4]);`<br>`Vxx.v[0].w[i]+= (Vuu.v[0].w[i].h[1] * Rt.b[(2*i+1)%4]);`<br>`Vxx.v[0].w[i]+= Vuu.v[1].w[i].h[0];`<br>`Vxx.v[1].w[i]+= (Vuu.v[0].w[i].h[1] * Rt.b[(2*i+0)%4]);`<br>`Vxx.v[1].w[i]+= (Vuu.v[1].w[i].h[0] * Rt.b[(2*i+1)%4]);`<br>`Vxx.v[1].w[i]+= Vuu.v[1].w[i].h[1] ;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vtmpy(Vuu.b,Rt.b)` | `HVX_VectorPair Q6_Wh_vtmpy_WbRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.h=vtmpy(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vtmpy_WubRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vdd.w=vtmpy(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vtmpy_WhRb(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.h+=vtmpy(Vuu.b,Rt.b)` | `HVX_VectorPair Q6_Wh_vtmpyacc_WhWbRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.h+=vtmpy(Vuu.ub,Rt.b)` | `HVX_VectorPair Q6_Wh_vtmpyacc_WhWubRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.w+=vtmpy(Vuu.h,Rt.b)` | `HVX_VectorPair Q6_Ww_vtmpyacc_WwWhRb(HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.h=vtmpy(Vuu.b,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.h=vtmpy(Vuu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.h+=vtmpy(Vuu.b,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vxx.h+=vtmpy(Vuu.ub,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vxx.w+=vtmpy(Vuu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.w=vtmpy(Vuu.h,Rt.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Sum of reduction of absolute differences halfwords

Takes groups of two unsigned halfwords from the vector register source Vuu, subtracts the halfwords from the scalar register Rt, and takes the absolute value as an unsigned result. Sum these and optionally add them to the destination register Vxx, or write directly to Vdd. The even destination register contains the data from Vuu[0] and Rt. Vdd[1] contains the absolute difference of half of the data from Vuu[0] and half from Vuu[1].

This operation implements a sliding window.

Vdd.uw=vdsad(Vuu.uh,Rt.uh)

|  |  |
|---|---|
| h[1] | h[0] |

Vuu[1] h[1] h[0] Vuu[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vuu[1] Vuu[0]

- Rt.uh[0] -

-Rt.uh[1] -

|.| |.| |.| |.|<sup>ABS</sup>

Optional

+ + Accumulate

w[0] Vdd[1] w[0] Vdd[0]

|  |  |
|---|---|
| 32-bit lane | 32-bit lane |
| Syntax | Behavior |

|  |  |
|---|---|
| `Vdd.uw=vdsad(Vuu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = ABS(Vuu.v[0].uw[i].uh[0] - `<br>`Rt.uh[0]);`<br>`Vdd.v[0].uw[i] += ABS(Vuu.v[0].uw[i].uh[1] - `<br>`Rt.uh[1]);`<br>`Vdd.v[1].uw[i] = ABS(Vuu.v[0].uw[i].uh[1] - `<br>`Rt.uh[0]);`<br>`Vdd.v[1].uw[i] += ABS(Vuu.v[1].uw[i].uh[0] - `<br>`Rt.uh[1]);`<br>`}` |
| `Vxx.uw+=vdsad(Vuu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[0].uw[i].uh[0] - `<br>`Rt.uh[0]);`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[0].uw[i].uh[1] - `<br>`Rt.uh[1]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[0].uw[i].uh[1] - `<br>`Rt.uh[0]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[1].uw[i].uh[0] - `<br>`Rt.uh[1]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.uw=vdsad(Vuu.uh,Rt.uh)` | `HVX_VectorPair Q6_Wuw_vdsad_WuhRuh(HVX_VectorPair Vuu, Word32 Rt)` |
| `Vxx.uw+=vdsad(Vuu.uh,Rt.uh)` | `HVX_VectorPair Q6_Wuw_vdsadacc_WuwWuhRuh (HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.uw=vdsad(Vuu.uh,Rt.u h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.uw+=vdsad(Vuu.uh,Rt. uh) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Sum of absolute differences byte

Takes groups of four bytes from the vector register source Vuu, subtract the bytes from the scalar register Rt, and take the absolute value as an unsigned result. Sum together and optionally add to the destination register Vxx, or write directly to Vdd.

If #u1 is 0, the even destination register contains the data from Vuu[0] and Rt, Vdd[1] contains the absolute difference of half of the data from Vuu[0] and half from Vuu[1]. If #u1 is 1, Vdd[0] takes byte 0 from Vuu[1] and bytes 1,2,3 from Vuu[0], while Vdd[1] takes byte 3 from Vuu[0] and the rest from Vuu[1].

This operation implements a sliding window between data in Vuu and Rt.

Vdd.uw=vrsad(Vuu.ub,Rt.ub, #0) Vdd.uw=vrsad(Vuu.ub,Rt.ub, #1)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vuu[1] b[3] b[2] b[1] b[0] Vuu[0] b[3] b[2] b[1] b[0] Vuu[1] b[3] b[2] b[1] b[0] Vuu[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vuu[1] Vuu[0] b[3] b[2] b[1] b[0] Vuu[1] b[3] b[2] b[1] b[0] Vuu[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vuu[1] b[3] b[2] b[1] b[0] Vuu[0] Vuu[1] b[3] b[2] b[1] b[0] Vuu[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vuu[1] b[3] b[2] b[1] b[0] Vuu[0] b[3] b[2] b[1] b[0] Vuu[1] Vuu[0]

|  |  |  |  |  |  |
|---|---|---|---|---|---|
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  | Rt.b[0] |  |  |  |  |
|  |  | Rt.b[0] |  |  |  |
|  |  | Rt.b[1] |  |  |  |
|  |  | Rt.b[1] |  |  |  |
|  |  | Rt.b[2] |  |  |  |
|  |  | Rt.b[3] |  |  |  |
|  |  | Rt.b[3] |  |  |  |

- - - Rt.b[0] -

- - -Rt.b[1] -

- - -Rt.b[2] -

- - -Rt.b[3] -

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |
|  |  | Rt.b[0] |  |  |  |  |
|  |  |  | Rt.b[0] |  |  |  |
|  |  |  | Rt.b[1] |  |  |  |
|  |  |  | Rt.b[1] |  |  |  |
|  |  |  | Rt.b[2] |  |  |  |
|  |  |  | Rt.b[3] |  |  |  |
|  |  |  | Rt.b[3] |  |  |  |

- Rt.b[0] - - -

- Rt.b[1] - - -

- Rt.b[2] - - -

- Rt.b[3] - - -

|.| |.| |.| |.| |.| |.| |.| |.|<sup>ABS</sup> |.| |.| |.| |.| |.| |.| |.| |.|ABS

Optional Optional

+ + + + accumulate accumulate

w[0] Vdd[1] w[0] Vdd[0] w[0] Vdd[1] w[0] Vdd[0]

32-bit lane 32-bit lane 32-bit lane 32-bit lane

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses both HVX multiply resources.

| Syntax | Behavior |
|---|---|
| `Vdd.uw=vrsad(Vuu.ub,Rt.ub,#u1)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = ABS(Vuu.v[#u? 1:0].uw[i].ub[0] - `<br>`Rt.ub[(0-#u)&3]);`<br>`Vdd.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[1] - `<br>`Rt.ub[(1-#u)&3]);`<br>`Vdd.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[2] - `<br>`Rt.ub[(2-#u)&3]);`<br>`Vdd.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[3] - `<br>`Rt.ub[(3-#u)&3]);`<br>`Vdd.v[1].uw[i] = ABS(Vuu.v[1 ].uw[i].ub[0] - `<br>`Rt.ub[(2-#u)&3]);`<br>`Vdd.v[1].uw[i] += ABS(Vuu.v[1 ].uw[i].ub[1] - `<br>`Rt.ub[(3-#u)&3]);`<br>`Vdd.v[1].uw[i] += ABS(Vuu.v[#u?1:0].uw[i].ub[2] - `<br>`Rt.ub[(0-#u)&3]);`<br>`Vdd.v[1].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[3] - `<br>`Rt.ub[(1-#u)&3]);`<br>`}` |
| `Vxx.uw+=vrsad(Vuu.ub,Rt.ub,#u1`<br>`)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[#u? 1:0].uw[i].ub[0] - `<br>`Rt.ub[(0-#u)&3]);`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[1] - `<br>`Rt.ub[(1-#u)&3]);`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[2] - `<br>`Rt.ub[(2-#u)&3]);`<br>`Vxx.v[0].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[3] - `<br>`Rt.ub[(3-#u)&3]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[1 ].uw[i].ub[0] - `<br>`Rt.ub[(2-#u)&3]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[1 ].uw[i].ub[1] - `<br>`Rt.ub[(3-#u)&3]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[#u?1:0].uw[i].ub[2] - `<br>`Rt.ub[(0-#u)&3]);`<br>`Vxx.v[1].uw[i] += ABS(Vuu.v[0 ].uw[i].ub[3] - `<br>`Rt.ub[(1-#u)&3]);`<br>`}` |

##### Intrinsics

|  |  |
|---|---|
| `Vdd.uw=vrsad(Vuu.ub,Rt.ub,#u1)` | `HVX_VectorPair Q6_Wuw_vrsad_WubRubI (HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |
| `Vxx.uw+=vrsad(Vuu.ub,Rt.ub,#u1)` | `HVX_VectorPair Q6_Wuw_vrsadacc_WuwWubRubI (HVX_VectorPair Vxx, HVX_VectorPair Vuu, Word32 Rt, Word32 Iu1)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | i | d | d | d | d | d | Vdd.uw=vrsad(Vuu.ub,Rt.u b,#u1) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | i | x | x | x | x | x | Vxx.uw+=vrsad(Vuu.ub,Rt. ub,#u1) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
