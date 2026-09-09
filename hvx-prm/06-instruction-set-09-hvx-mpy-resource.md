## 6.9 HVX MPY RESOURCE

The HVX MPY RESOURCE instruction subclass includes instructions that use a single HVX multiply

resource.

#### Multiply by byte with 2-wide reduction

Multiply elements from Vu by the corresponding elements in the scalar register Rt. Add the products in pairs to yield a by-2 reduction. The products can optionally be accumulated with Vx.

Supports multiplication of unsigned bytes by bytes, and halfwords by signed bytes. The double-vector version performs a sliding-window 2-way reduction, where the odd register output contains the offset computation.

Vd.h[+]=vdmpy(Vu.ub, Rt.b) / Vd.w[+]=vdmpy(Vu.h, Rt.b) Vdd.h[+]=vdmpy(Vuu.ub, Rt.b) / Vdd.w[+]=vdmpy(Vuu.h, Rt.b)

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

|  |  |  |  |
|---|---|---|---|
| h/w[1] |  | h/w[0] |  |

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

| Syntax | Behavior |
|---|---|
| `Vd.h=vdmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.uh[i].ub[0] * Rt.b[(2*i) % 4]);`<br>`Vd.h[i] += (Vu.uh[i].ub[1] * Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vd.w=vdmpy(Vu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i].h[0] * Rt.b[(2*i+0)%4]);`<br>`Vd.w[i] += (Vu.w[i].h[1] * Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vx.h+=vdmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i] += (Vu.uh[i].ub[0] * Rt.b[(2*i) % 4]);`<br>`Vx.h[i] += (Vu.uh[i].ub[1] * Rt.b[(2*i+1)%4]);`<br>`}` |
| `Vx.w+=vdmpy(Vu.h,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i].h[0] * Rt.b[(2*i+0)%4]);`<br>`Vx.w[i] += (Vu.w[i].h[1] * Rt.b[(2*i+1)%4]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vdmpy(Vu.ub,Rt.b)` | `HVX_Vector Q6_Vh_vdmpy_VubRb(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vdmpy(Vu.h,Rt.b)` | `HVX_Vector Q6_Vw_vdmpy_VhRb(HVX_Vector Vu, Word32 Rt)` |
| `Vx.h+=vdmpy(Vu.ub,Rt.b)` | `HVX_Vector Q6_Vh_vdmpyacc_VhVubRb(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vdmpy(Vu.h,Rt.b)` | `HVX_Vector Q6_Vw_vdmpyacc_VwVhRb(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.w=vdmpy(Vu.h,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.h=vdmpy(Vu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx.w+=vdmpy(Vu.h,Rt.b) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | Vx.h+=vdmpy(Vu.ub,Rt.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply by halfword with 2-wide reduction

Multiply elements from Vu by the corresponding elements in the scalar register Rt. Add the products in pairs to yield a by-2 reduction. The products can optionally be accumulated with Vx.

Supports multiplication of unsigned bytes by bytes, and halfwords by signed bytes. The double-vector version performs a sliding-window 2-way reduction, where the odd register output contains the offset computation.

Vd.h[+]=vdmpy(Vu.ub, Rt.b) / Vd.w[+]=vdmpy(Vu.h, Rt.b) Vdd.h[+]=vdmpy(Vuu.ub, Rt.b) / Vdd.w[+]=vdmpy(Vuu.h, Rt.b)

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

|  |  |  |  |
|---|---|---|---|
| h/w[1] |  | h/w[0] |  |

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

| Syntax | Behavior |
|---|---|
| `Vd.w=vdmpy(Vu.h,Rt.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vu.w[i].h[0] * Rt.h[0]);`<br>`accum += (Vu.w[i].h[1] * Rt.h[1]);`<br>`Vd.w[i] = sat₃₂(accum);`<br>`}` |
| `Vd.w=vdmpy(Vu.h,Rt.uh):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vu.w[i].h[0] * Rt.uh[0]);`<br>`accum += (Vu.w[i].h[1] * Rt.uh[1]);`<br>`Vd.w[i] = sat₃₂(accum);`<br>`}` |
| `Vd.w=vdmpy(Vu.h,Vv.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = (Vu.w[i].h[0] * Vv.w[i].h[0]);`<br>`accum += (Vu.w[i].h[1] * Vv.w[i].h[1]);`<br>`Vd.w[i] = sat₃₂(accum);`<br>`}` |
| `Vx.w+=vdmpy(Vu.h,Rt.h):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum = Vx.w[i];`<br>`accum += (Vu.w[i].h[0] * Rt.h[0]);`<br>`accum += (Vu.w[i].h[1] * Rt.h[1]);`<br>`Vx.w[i] = sat₃₂(accum);`<br>`}` |
| `Vx.w+=vdmpy(Vu.h,Rt.uh):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`accum=Vx.w[i];`<br>`accum += (Vu.w[i].h[0] * Rt.uh[0]);`<br>`accum += (Vu.w[i].h[1] * Rt.uh[1]);`<br>`Vx.w[i] = sat₃₂(accum);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.w=vdmpy(Vu.h,Rt.h):sat` | `HVX_Vector Q6_Vw_vdmpy_VhRh_sat(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vdmpy(Vu.h,Rt.uh):sat` | `HVX_Vector Q6_Vw_vdmpy_VhRuh_sat(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vdmpy(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vw_vdmpy_VhVh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vx.w+=vdmpy(Vu.h,Rt.h):sat` | `HVX_Vector Q6_Vw_vdmpyacc_VwVhRh_sat(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vdmpy(Vu.h,Rt.uh):sat` | `HVX_Vector Q6_Vw_vdmpyacc_VwVhRuh_sat(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vdmpy(Vu.h,Rt.uh):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.w=vdmpy(Vu.h,Rt.h):sat |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vx.w+=vdmpy(Vu.h,Rt.uh): sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx.w+=vdmpy(Vu.h,Rt.h):sat |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.w=vdmpy(Vu.h,Vv.h):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Multiply vector by scalar nonwidening

Multiply groups of elements in the vector Vu by the corresponding elements in the scalar register Rt.

This operation keeps the output precision the same as the input width by shifting the product left by one, saturating the product to 32 bits, and placing the upper 16 bits in the output. Optional rounding of the result is supported.

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

| Syntax | Behavior |
|---|---|
| `Vd.h=vmpy(Vu.h,Rt.h):<<1:rnd:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i].h[0]=sat₁₆(sat₃₂(round(((Vu.w[i].h[0] * `<br>`Rt.h[0])<<1))).h[1]);`<br>`Vd.w[i].h[1]=sat_16(sat₃₂(round(((Vu.w[i].h[1] * `<br>`Rt.h[1])<<1))).h[1]);`<br>`}` |
| `Vd.h=vmpy(Vu.h,Rt.h):<<1:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i].h[0]=sat₁₆(sat₃₂(((Vu.w[i].h[0] * `<br>`Rt.h[0])<<1)).h[1]);`<br>`Vd.w[i].h[1]=sat₁₆(sat₃₂(((Vu.w[i].h[1] * `<br>`Rt.h[1])<<1)).h[1]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vmpy(Vu.h,Rt.h):<<1:rnd:sat` | `HVX_Vector Q6_Vh_vmpy_VhRh_s1_rnd_sat(HVX_Vector Vu, Word32 Rt)` |
| `Vd.h=vmpy(Vu.h,Rt.h):<<1:sat` | `HVX_Vector Q6_Vh_vmpy_VhRh_s1_sat (HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.h=vmpy(Vu.h,Rt.h):<<1: sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.h=vmpy(Vu.h,Rt.h):<<1: rnd:sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |

#### Multiply vector by vector nonwidening

Multiply elements in the vector Vu by the corresponding elements in the vector register Vv and take the upper halfword result.

| Syntax | Behavior |
|---|---|
| `Vd.h=vmpy(Vu.h,Vv.h):<<1:rnd:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = sat₁₆(sat₃₂(round(((Vu.h[i] * `<br>`Vv.h[i])<<1))).h[1]);`<br>`}` |
| `Vd.uh=vmpy(Vu.uh,Vv.uh):>>16` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i] * Vv.uh[i]).uh[1];`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vmpy(Vu.h,Vv.h):<<1:rnd:sat` | `HVX_Vector Q6_Vh_vmpy_VhVh_s1_rnd_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vmpy(Vu.uh,Vv.uh):>>16` | `HVX_Vector Q6_Vuh_vmpy_VuhVuh_rs16(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.h=vmpy(Vu.h,Vv.h):<<1: rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.uh=vmpy(Vu.uh,Vv.uh): >>16 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Multiply half of the elements (16 × 16)

Multiply even elements of Vu by odd elements of Vv, shift the result left by 16 bits, and place the result in each lane of Vd. This instruction is useful for 32 × 32 low-half multiplies.

| Syntax | Behavior |
|---|---|
| `Vd.w=vmpyieo(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i].h[0]*Vv.w[i].h[1]) << 16;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

```
Vd.w=vmpyieo(Vu.h,Vv.h)HVX_Vector Q6_Vw_vmpyieo_VhVh(HVX_Vector Vu,
                             HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vmpyieo(Vu.h,Vv.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Integer multiply by byte

Multiply groups of words in vector register Vu by the elements in Rt. The lower 32-bit results are placed in vector register Vd.

The operation has one form: signed words in Vu multiplied by signed bytes in Rt.

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

Output only lower 32 LSBs X Rt.b[0]Output only lower 32 LSBs X Rt.h[0]

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
| `Vd.h=vmpyi(Vu.h,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] * Rt.b[i % 4]);`<br>`}` |
| `Vd.w=vmpyi(Vu.w,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Rt.b[i % 4]);`<br>`}` |
| `Vd.w=vmpyi(Vu.w,Rt.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] * Rt.ub[i % 4]);`<br>`}` |
| `Vx.h+=vmpyi(Vu.h,Rt.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i] += (Vu.h[i] * Rt.b[i % 4]);`<br>`}` |
| `Vx.w+=vmpyi(Vu.w,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i] * Rt.b[i % 4]);`<br>`}` |
| `Vx.w+=vmpyi(Vu.w,Rt.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i] * Rt.ub[i % 4]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vmpyi(Vu.h,Rt.b)` | `HVX_Vector Q6_Vh_vmpyi_VhRb(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vmpyi(Vu.w,Rt.b)` | `HVX_Vector Q6_Vw_vmpyi_VwRb(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vmpyi(Vu.w,Rt.ub)` | `HVX_Vector Q6_Vw_vmpyi_VwRub(HVX_Vector Vu, Word32 Rt)` |
| `Vx.h+=vmpyi(Vu.h,Rt.b)` | `HVX_Vector Q6_Vh_vmpyiacc_VhVhRb(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vmpyi(Vu.w,Rt.b)` | `HVX_Vector Q6_Vw_vmpyiacc_VwVwRb(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vmpyi(Vu.w,Rt.ub)` | `HVX_Vector Q6_Vw_vmpyiacc_VwVwRub(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vx.w+=vmpyi(Vu.w,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.h=vmpyi(Vu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vx.h+=vmpyi(Vu.h,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.w=vmpyi(Vu.w,Rt.ub) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vx.w+=vmpyi(Vu.w,Rt.ub) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vmpyi(Vu.w,Rt.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply half of the elements with scalar (16 ×16)

Unsigned 16 × 16 multiply of the lower halfword of each word in the vector with the lower halfword of the 32-bit scalar.

| Syntax | Behavior |
|---|---|
| `Vd.uw=vmpye(Vu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.uw[i].uh[0] * Rt.uh[0]);`<br>`}` |
| `Vx.uw+=vmpye(Vu.uh,Rt.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.uw[i] += (Vu.uw[i].uh[0] * Rt.uh[0]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.uw=vmpye(Vu.uh,Rt.uh)` | `HVX_Vector Q6_Vuw_vmpye_VuhRuh(HVX_Vector Vu, Word32 Rt)` |
| `Vx.uw+=vmpye(Vu.uh,Rt.uh)` | `HVX_Vector Q6_Vuw_vmpyeacc_VuwVuhRuh(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uw=vmpye(Vu.uh,Rt.uh) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx.uw+=vmpye(Vu.uh,Rt.u h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply bytes with 4-wide reduction vector by scalar

Perform multiplication between the elements in vector Vu and the corresponding elements in the scalar register Rt, followed by a 4-way reduction to a word in each 32-bit lane.

Supports the multiplication of unsigned byte data by signed or unsigned bytes in the scalar.

The operation has two forms: the first performs simple dot product of four elements into a single result. The second form takes a one bit immediate input and generates a vector register pair.

For #1 = 0 the even destination contains a simple dot product, the odd destination contains a dot product of the coefficients rotated by two elements and the upper two data elements taken from the even register of Vuu.

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

| Syntax | Behavior |
|---|---|
| `Vd.uw=vrmpy(Vu.ub,Rt.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.uw[i].ub[0] * Rt.ub[0]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[1] * Rt.ub[1]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[2] * Rt.ub[2]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[3] * Rt.ub[3]);`<br>`}` |
| `Vd.w=vrmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.uw[i].ub[0] * Rt.b[0]);`<br>`Vd.w[i] += (Vu.uw[i].ub[1] * Rt.b[1]);`<br>`Vd.w[i] += (Vu.uw[i].ub[2] * Rt.b[2]);`<br>`Vd.w[i] += (Vu.uw[i].ub[3] * Rt.b[3]);`<br>`}` |
| `Vx.uw+=vrmpy(Vu.ub,Rt.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.uw[i] += (Vu.uw[i].ub[0] * Rt.ub[0]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[1] * Rt.ub[1]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[2] * Rt.ub[2]);`<br>`Vx.uw[i] += (Vu.uw[i].ub[3] * Rt.ub[3]);`<br>`}` |
| `Vx.w+=vrmpy(Vu.ub,Rt.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.uw[i].ub[0] * Rt.b[0]);`<br>`Vx.w[i] += (Vu.uw[i].ub[1] * Rt.b[1]);`<br>`Vx.w[i] += (Vu.uw[i].ub[2] * Rt.b[2]);`<br>`Vx.w[i] += (Vu.uw[i].ub[3] * Rt.b[3]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.uw=vrmpy(Vu.ub,Rt.ub)` | `HVX_Vector Q6_Vuw_vrmpy_VubRub(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vrmpy(Vu.ub,Rt.b)` | `HVX_Vector Q6_Vw_vrmpy_VubRb(HVX_Vector Vu, Word32 Rt)` |
| `Vx.uw+=vrmpy(Vu.ub,Rt.ub)` | `HVX_Vector Q6_Vuw_vrmpyacc_VuwVubRub(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vrmpy(Vu.ub,Rt.b)` | `HVX_Vector Q6_Vw_vrmpyacc_VwVubRb(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.uw=vrmpy(Vu.ub,Rt.ub) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.w=vrmpy(Vu.ub,Rt.b) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | Vx.uw+=vrmpy(Vu.ub,Rt.ub ) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.w+=vrmpy(Vu.ub,Rt.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Multiply by byte with 4-wide reduction vector by vector

The `vrmpy` instruction performs a dot product function between 4-byte elements in vector register Vu, and 4-byte elements in Vv. The sum of the products writes into Vd as words within each 32-bit lane.

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
| `Vd.uw=vrmpy(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.uw[i].ub[0] * Vv.uw[i].ub[0]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[1] * Vv.uw[i].ub[1]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[2] * Vv.uw[i].ub[2]);`<br>`Vd.uw[i] += (Vu.uw[i].ub[3] * Vv.uw[i].ub[3]);`<br>`}` |
| `Vd.w=vrmpy(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i].b[0] * Vv.w[i].b[0]);`<br>`Vd.w[i] += (Vu.w[i].b[1] * Vv.w[i].b[1]);`<br>`Vd.w[i] += (Vu.w[i].b[2] * Vv.w[i].b[2]);`<br>`Vd.w[i] += (Vu.w[i].b[3] * Vv.w[i].b[3]);`<br>`}` |
| `Vd.w=vrmpy(Vu.ub,Vv.b)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.uw[i].ub[0] * Vv.w[i].b[0]);`<br>`Vd.w[i] += (Vu.uw[i].ub[1] * Vv.w[i].b[1]);`<br>`Vd.w[i] += (Vu.uw[i].ub[2] * Vv.w[i].b[2]);`<br>`Vd.w[i] += (Vu.uw[i].ub[3] * Vv.w[i].b[3]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.uw=vrmpy(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vuw_vrmpy_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vrmpy(Vu.b,Vv.b)` | `HVX_Vector Q6_Vw_vrmpy_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vrmpy(Vu.ub,Vv.b)` | `HVX_Vector Q6_Vw_vrmpy_VubVb(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.uw=vrmpy(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.w=vrmpy(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.w=vrmpy(Vu.ub,Vv.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Splat from scalar

Set the destination vector register words to the value specified by the contents of scalar register Rt.

Vd=vsplat(Rt)

w Rt

|  |  |  |  |
|---|---|---|---|
| w[N<sup>*</sup>-1] | ... | w[1] | w[0] |

Vd

*N number of operations in vector

| Syntax | Behavior |
|---|---|
| `Vd.b=vsplat(Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = Rt ;`<br>`}` |
| `Vd.h=vsplat(Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = Rt ;`<br>`}` |
| `Vd=vsplat(Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = Rt ;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vsplat(Rt)` | `HVX_Vector Q6_Vb_vsplat_R(Word32 Rt)` |
| `Vd.h=vsplat(Rt)` | `HVX_Vector Q6_Vh_vsplat_R(Word32 Rt)` |
| `Vd=vsplat(Rt)` | `HVX_Vector Q6_V_vsplat_R(Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | - | - | - | - | 0 | 0 | 0 | 1 | d | d | d | d | d | Vd=vsplat(Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | t | t | t | t | t | P | P | 0 | - | - | - | - | - | 0 | 0 | 1 | d | d | d | d | d | Vd.h=vsplat(Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | t | t | t | t | t | P | P | 0 | - | - | - | - | - | 0 | 1 | 0 | d | d | d | d | d | Vd.b=vsplat(Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |

#### Vector to predicate transfer

Copy bits into the destination vector predicate register, under the control of the scalar register Rt and the input vector register Vu. Instead of a direct write, the destination can also OR with the result. If the corresponding byte i of Vu matches any of the bits in Rt byte[i%4], the destination Qd is OR'd with or set to 1 or 0.

If Rt contains 0x01010101, the LSBs of Vu can effectively fill Qt, one bit per byte.

| Syntax | Behavior |
|---|---|
| `Qd4=vand(Vu,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=((Vu.ub[i]& Rt.ub[i % 4])!= 0)? 1: 0;`<br>`}` |
| `Qx4\|=vand(Vu,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QxV[i]=QxV[i]\|(((Vu.ub[i] & Rt.ub[i % 4]) != 0)? 1: 0);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Qd4=vand(Vu,Rt)` | `HVX_VectorPred Q6_Q_vand_VR(HVX_Vector Vu, Word32 Rt)` |
| `Qx4\|=vand(Vu,Rt)` | `HVX_VectorPred Q6_Q_vandor_QVR(HVX_VectorPred Qx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | x2 | x2 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | - | - | - | x | x | Qx4\|=vand(Vu,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | d2 | d2 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | - | 1 | 0 | d | d | Qd4=vand(Vu,Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x2` | Field to encode register x |

#### Predicate to vector transfer

Copy the byte elements of scalar register Rt into the destination vector register Vd, under the control of the vector predicate register. Instead of a direct write, the destination can also OR with the result. If the corresponding bit i of Qu is set, the contents of byte[i % 4] write or OR into Vd or Vx.

If Rt contains 0x01010101, Qt can effectively expand into Vd or Vx, 1 bit per byte.

| Syntax | Behavior |
|---|---|
| `Vd=vand([!]Qu4,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = [!]QuV[i] ? Rt.ub[i % 4] : 0 ;`<br>`}` |
| `Vx\|=vand([!]Qu4,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vx.ub[i] \|= [!](QuV[i]) ? Rt.ub[i % 4] : 0 ;`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd=vand(!Qu4,Rt)` | `HVX_Vector Q6_V_vand_QnR(HVX_VectorPred Qu, Word32 Rt)` |
| `Vd=vand(Qu4,Rt)` | `HVX_Vector Q6_V_vand_QR(HVX_VectorPred Qu, Word32 Rt)` |
| `Vx\|=vand(!Qu4,Rt)` | `HVX_Vector Q6_V_vandor_VQnR(HVX_Vector Vx, HVX_VectorPred Qu, Word32 Rt)` |
| `Vx\|=vand(Qu4,Rt)` | `HVX_Vector Q6_V_vandor_VQR(HVX_Vector Vx, HVX_VectorPred Qu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  | u2 | u2 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | - | - | 0 | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx\|=vand(Qu4,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | - | - | 1 | u | u | 0 | 1 | 1 | x | x | x | x | x | Vx\|=vand(!Qu4,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  | u2 | u2 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | - | - | 0 | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd=vand(Qu4,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 0 | - | - | 1 | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd=vand(!Qu4,Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u2` | Field to encode register u |
| `x5` | Field to encode register x |

#### Absolute value of difference

Returns the absolute value of the difference between corresponding elements in vector registers Vu and Vv, and places the result in Vd. Supports unsigned byte, signed and unsigned halfword, and signed word.

Vd.uh=vabsdiff(Vu.h,Vv.h)

|  |  |
|---|---|
| [1] | [0] |

[N-1] Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | [1] |  | [0] |

[N-1] Vv

|  |  |
|---|---|
|  | [N-1] |

[1] [0] Vv

- - -

Abs Abs Abs

|  |  |
|---|---|
| [1] | [0] |

[N-1] Vd

N is the number of elements implemented in a vector register.

| Syntax | Behavior |
|---|---|
| `Vd.ub=vabsdiff(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = (Vu.ub[i] > Vv.ub[i]) ? (Vu.ub[i] - `<br>`Vv.ub[i]) : (Vv.ub[i] - Vu.ub[i]);`<br>`}` |
| `Vd.uh=vabsdiff(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.h[i] > Vv.h[i]) ? (Vu.h[i] - Vv.h[i]) `<br>`: (Vv.h[i] - Vu.h[i]);`<br>`}` |
| `Vd.uh=vabsdiff(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i] > Vv.uh[i]) ? (Vu.uh[i] - `<br>`Vv.uh[i]) : (Vv.uh[i] - Vu.uh[i]);`<br>`}` |
| `Vd.uw=vabsdiff(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.w[i] > Vv.w[i]) ? (Vu.w[i] - Vv.w[i]) `<br>`: (Vv.w[i] - Vu.w[i]);`<br>`}` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.ub=vabsdiff(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vub_vabsdiff_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vabsdiff(Vu.h,Vv.h)` | `HVX_Vector Q6_Vuh_vabsdiff_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vabsdiff(Vu.uh,Vv.uh)` | `HVX_Vector Q6_Vuh_vabsdiff_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uw=vabsdiff(Vu.w,Vv.w)` | `HVX_Vector Q6_Vuw_vabsdiff_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.ub=vabsdiff(Vu.ub,Vv.ub ) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uh=vabsdiff(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vabsdiff(Vu.uh,Vv.uh ) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.uw=vabsdiff(Vu.w,Vv.w) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Insert element

Insert a 32-bit element in Rt into the destination vector register Vx, at the word element 0.

| Syntax | Behavior |
|---|---|
| `Vx.w=vinsert(Rt)` | `Vx.uw[0] = Rt;` |

##### Class: COPROC_VX (slots 2,3)

##### Notes

- This instruction uses a HVX multiply resource.

##### Intrinsics

```
Vx.w=vinsert(Rt)HVX_Vector Q6_Vw_vinsert_VwR(HVX_Vector Vx, Word32 Rt)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 1 | - | - | - | - | - | 0 | 0 | 1 | x | x | x | x | x | Vx.w=vinsert(Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `t5` | Field to encode register t |
| `x5` | Field to encode register x |
