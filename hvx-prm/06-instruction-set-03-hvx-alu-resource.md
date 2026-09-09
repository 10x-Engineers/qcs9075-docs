## 6.3 HVX ALU RESOURCE

The HVX ALU RESOURCE instruction subclass includes ALU instructions that use a single HVX

resource.

#### Predicate operations

Perform bitwise logical operation on a vector predicate register Qs, and place the result in Qd. This operation works on vectors with any element size.

The following combination is implemented: !Qs.

| Syntax | Behavior |
|---|---|
| `Qd4=not(Qs4)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=!QsV[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

```
Qd4=not(Qs4)HVX_VectorPred Q6_Q_not_Q(HVX_VectorPred Qs)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  | s2 | s2 |  |  |  |  |  |  | d2 | d2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 0 | 1 | 0 | d | d | Qd4=not(Qs4) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `s2` | Field to encode register s |

#### Byte-conditional vector assign

If the bit in Qv is set, copy the byte. Otherwise, set the byte in the destination to zero.

| Syntax | Behavior |
|---|---|
| `Vd=vand([!]Qv4,Vu)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = [!]QvV[i] ? Vu.b[i] : 0;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd=vand(!Qv4,Vu)` | `HVX_Vector Q6_V_vand_QnV(HVX_VectorPred Qv, HVX_Vector Vu)` |
| `Vd=vand(Qv4,Vu)` | `HVX_Vector Q6_V_vand_QV(HVX_VectorPred Qv, HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 1 | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd=vand(Qv4,Vu) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 1 | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd=vand(!Qv4,Vu) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |

#### Minimum/maximum

Compare the respective elements of Vu and Vv, and return the maximum or minimum. The result is placed in the same position as the inputs.

Supports unsigned byte, signed and unsigned halfword, and signed word.

| Syntax | Behavior |
|---|---|
| `Vd.b=vmax(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = (Vu.b[i] > Vv.b[i]) ? Vu.b[i]: Vv.b[i];`<br>`}` |
| `Vd.b=vmin(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = (Vu.b[i] < Vv.b[i]) ? Vu.b[i]: Vv.b[i];`<br>`}` |
| `Vd.h=vmax(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] > Vv.h[i]) ? Vu.h[i]: Vv.h[i];`<br>`}` |
| `Vd.h=vmin(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] < Vv.h[i]) ? Vu.h[i]: Vv.h[i];`<br>`}` |
| `Vd.hf=vmax(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.hf[i] = max(Vu.hf[i],Vv.hf[i]);`<br>`}` |
| `Vd.hf=vmin(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.hf[i] = min(Vu.hf[i],Vv.hf[i]);`<br>`}` |
| `Vd.sf=vmax(Vu.sf,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.sf[i] = max(Vu.sf[i],Vv.sf[i]);`<br>`}` |
| `Vd.sf=vmin(Vu.sf,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.sf[i] = min(Vu.sf[i],Vv.sf[i]);`<br>`}` |
| `Vd.ub=vmax(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = (Vu.ub[i] > Vv.ub[i]) ? Vu.ub[i]: `<br>`Vv.ub[i];`<br>`}` |
| `Vd.ub=vmin(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = (Vu.ub[i] < Vv.ub[i]) ? Vu.ub[i]: `<br>`Vv.ub[i];`<br>`}` |
| `Vd.uh=vmax(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i] > Vv.uh[i]) ? Vu.uh[i]: `<br>`Vv.uh[i];`<br>`}` |
| `Vd.uh=vmin(Vu.uh,Vv.uh)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i] < Vv.uh[i]) ? Vu.uh[i]: `<br>`Vv.uh[i];`<br>`}` |
| `Vd.w=vmax(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] > Vv.w[i]) ? Vu.w[i]: Vv.w[i];`<br>`}` |
| `Vd.w=vmin(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] < Vv.w[i]) ? Vu.w[i]: Vv.w[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vmax(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vmax_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vmin(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vmin_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vmax(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vmax_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vmin(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vmin_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.hf=vmax(Vu.hf,Vv.hf)` | `HVX_Vector Q6_Vhf_vmax_VhfVhf (HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.hf=vmin(Vu.hf,Vv.hf)` | `HVX_Vector Q6_Vhf_vmin_VhfVhf( HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.sf=vmax(Vu.sf,Vv.sf)` | `HVX_Vector Q6_Vsf_vmax_VsfVsf (HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.sf=vmin(Vu.sf,Vv.sf)` | `HVX_Vector Q6_Vsf_vmin_VsfVsf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vmax(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vub_vmax_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vmin(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vub_vmin_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vmax(Vu.uh,Vv.uh)` | `HVX_Vector Q6_Vuh_vmax_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vmin(Vu.uh,Vv.uh)` | `HVX_Vector Q6_Vuh_vmin_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vmax(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vmax_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vmin(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vmin_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.ub=vmin(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vmin(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vmin(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.w=vmin(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.ub=vmax(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.uh=vmax(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.h=vmax(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vmax(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.b=vmin(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.b=vmax(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.sf=vmax(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.sf=vmin(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.hf=vmax(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.hf=vmin(Vu.hf,Vv.hf) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Absolute value

Take the absolute value of the vector register elements. Supports signed halfword and word. Optionally, saturate to deal with the maximum negative value overflow case.

| Syntax | Behavior |
|---|---|
| `Vd.b=vabs(Vu.b)[:sat]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = [sat₈](ABS(Vu.b[i]));`<br>`}` |
| `Vd.h=vabs(Vu.h)[:sat]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = [sat₁₆](ABS(Vu.h[i]));`<br>`}` |
| `Vd.ub=vabs(Vu.b)` | `Assembler mapped to: "Vd.b=vabs(Vu.b)"` |
| `Vd.uh=vabs(Vu.h)` | `Assembler mapped to: "Vd.h=vabs(Vu.h)"` |
| `Vd.uw=vabs(Vu.w)` | `Assembler mapped to: "Vd.w=vabs(Vu.w)"` |
| `Vd.w=vabs(Vu.w)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = [sat₃₂](ABS(Vu.w[i]));`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vabs(Vu.b)` | `HVX_Vector Q6_Vb_vabs_Vb(HVX_Vector Vu)` |
| `Vd.b=vabs(Vu.b):sat` | `HVX_Vector Q6_Vb_vabs_Vb_sat(HVX_Vector Vu)` |
| `Vd.h=vabs(Vu.h)` | `HVX_Vector Q6_Vh_vabs_Vh(HVX_Vector Vu)` |
| `Vd.h=vabs(Vu.h):sat` | `HVX_Vector Q6_Vh_vabs_Vh_sat(HVX_Vector Vu)` |
| `Vd.w=vabs(Vu.w)` | `HVX_Vector Q6_Vw_vabs_Vw(HVX_Vector Vu)` |
| `Vd.w=vabs(Vu.w):sat` | `HVX_Vector Q6_Vw_vabs_Vw_sat(HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 0 | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.h=vabs(Vu.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 0 | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.h=vabs(Vu.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 0 | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.w=vabs(Vu.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 0 | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.w=vabs(Vu.w):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.b=vabs(Vu.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.b=vabs(Vu.b):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |

#### Arithmetic

Perform simple arithmetic operations, add and subtract, between the elements of the two vectors Vu and Vv. Supports unsigned and signed byte and halfword.

Optionally, saturate for word and signed halfword. Always saturate for unsigned types except byte.

| Syntax | Behavior |
|---|---|
| `Vd.b=vadd(Vu.b,Vv.b)[:sat]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = [sat₈](Vu.b[i]+Vv.b[i]);`<br>`}` |
| `Vd.b=vsub(Vu.b,Vv.b)[:sat]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = [sat₈](Vu.b[i]-Vv.b[i]);`<br>`}` |
| `Vd.h=vadd(Vu.h,Vv.h)[:sat]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = [sat₁₆](Vu.h[i]+Vv.h[i]);`<br>`}` |
| `Vd.h=vsub(Vu.h,Vv.h)[:sat]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = [sat₁₆](Vu.h[i]-Vv.h[i]);`<br>`}` |
| `Vd.ub=vadd(Vu.ub,Vv.b):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = usat₈(Vu.ub[i] + Vv.b[i]);`<br>`}` |
| `Vd.ub=vadd(Vu.ub,Vv.ub):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = usat₈(Vu.ub[i]+Vv.ub[i]);`<br>`}` |
| `Vd.ub=vsub(Vu.ub,Vv.b):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = usat₈(Vu.ub[i] - Vv.b[i]);`<br>`}` |
| `Vd.ub=vsub(Vu.ub,Vv.ub):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = usat₈(Vu.ub[i]-Vv.ub[i]);`<br>`}` |
| `Vd.uh=vadd(Vu.uh,Vv.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = usat₁₆(Vu.uh[i]+Vv.uh[i]);`<br>`}` |
| `Vd.uh=vsub(Vu.uh,Vv.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = usat₁₆(Vu.uh[i]-Vv.uh[i]);`<br>`}` |
| `Vd.uw=vadd(Vu.uw,Vv.uw):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = usat₃₂(Vu.uw[i]+Vv.uw[i]);`<br>`}` |
| `Vd.uw=vsub(Vu.uw,Vv.uw):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = usat₃₂(Vu.uw[i]-Vv.uw[i]);`<br>`}` |
| `Vd.w=vadd(Vu.w,Vv.w)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = [sat₃₂](Vu.w[i]+Vv.w[i]);`<br>`}` |
| `Vd.w=vsub(Vu.w,Vv.w)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = [sat₃₂](Vu.w[i]-Vv.w[i]);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vadd(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vadd_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vadd(Vu.b,Vv.b):sat` | `HVX_Vector Q6_Vb_vadd_VbVb_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vsub(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vsub_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vsub(Vu.b,Vv.b):sat` | `HVX_Vector Q6_Vb_vsub_VbVb_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vadd(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vadd_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vadd(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vh_vadd_VhVh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vsub(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vsub_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vsub(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vh_vsub_VhVh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vadd(Vu.ub,Vv.b):sat` | `HVX_Vector Q6_Vub_vadd_VubVb_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vadd(Vu.ub,Vv.ub):sat` | `HVX_Vector Q6_Vub_vadd_VubVub_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vsub(Vu.ub,Vv.b):sat` | `HVX_Vector Q6_Vub_vsub_VubVb_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vsub(Vu.ub,Vv.ub):sat` | `HVX_Vector Q6_Vub_vsub_VubVub_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vadd(Vu.uh,Vv.uh):sat` | `HVX_Vector Q6_Vuh_vadd_VuhVuh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vsub(Vu.uh,Vv.uh):sat` | `HVX_Vector Q6_Vuh_vsub_VuhVuh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uw=vadd(Vu.uw,Vv.uw):sat` | `HVX_Vector Q6_Vuw_vadd_VuwVuw_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uw=vsub(Vu.uw,Vv.uw):sat` | `HVX_Vector Q6_Vuw_vsub_VuwVuw_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vadd(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vadd_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vadd(Vu.w,Vv.w):sat` | `HVX_Vector Q6_Vw_vadd_VwVw_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vsub(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vsub_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vsub(Vu.w,Vv.w):sat` | `HVX_Vector Q6_Vw_vsub_VwVw_sat(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vadd(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.ub=vadd(Vu.ub,Vv.ub):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vadd(Vu.uh,Vv.uh):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vadd(Vu.h,Vv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.w=vadd(Vu.w,Vv.w):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.b=vsub(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.h=vsub(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vsub(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.ub=vsub(Vu.ub,Vv.ub):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uh=vsub(Vu.uh,Vv.uh):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.h=vsub(Vu.h,Vv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.w=vsub(Vu.w,Vv.w):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.ub=vadd(Vu.ub,Vv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.ub=vsub(Vu.ub,Vv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vadd(Vu.b,Vv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.b=vsub(Vu.b,Vv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uw=vadd(Vu.uw,Vv.uw): sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.b=vadd(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.h=vadd(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.uw=vsub(Vu.uw,Vv.uw): sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Arithmetic with carry bit

Perform simple arithmetic operations, add and subtract, between the word elements of the two vectors Vu and Vv and a carry-out bit.

Optionally, saturate for word.

| Syntax | Behavior |
|---|---|
| `Rdd=add(Rss,Rtt,Px):carry` | `PREDUSE_TIMING;`<br>`Rdd = Rss + Rtt + Px[0];`<br>`Px = carry_from_add(Rss,Rtt,Px[0]) ? 0xff: `<br>`0x00;` |
| `Rdd=sub(Rss,Rtt,Px):carry` | `PREDUSE_TIMING;`<br>`Rdd = Rss + ~Rtt + Px[0];`<br>`Px = carry_from_add(Rss,~Rtt,Px[0]) ? 0xff: `<br>`0x00;` |
| `Vd.w,Qe4=vadd(Vu.w,Vv.w):carry` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = Vu.w[i]+Vv.w[i];`<br>`QeV[4*i+4-1:4*i] = -carry_from(Vu.w[i], `<br>`Vv.w[i],0);`<br>`}` |
| `Vd.w, Qe4 = vsub(Vu.w, `<br>`Vv.w):carry` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = Vu.w[i]+~Vv.w[i]+1;`<br>`QeV[4*i+4-1:4*i] = -carry_from(Vu.w[i], `<br>`~Vv.w[i],1);`<br>`}` |
| `Vd.w = vadd(Vu.w, `<br>`Vv.w,Qs4):carry:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = sat₃₂(Vu.w[i]+Vv.w[i]+QsV[i*4]);`<br>`}` |
| `Vd.w=vadd(Vu.w,Vv.w,Qx4):carry` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = Vu.w[i]+Vv.w[i]+QxV[i*4];`<br>`QxV[4*i+4-1:4*i] = -carry_from(Vu.w[i], `<br>`Vv.w[i], QxV[i*4]);`<br>`}` |
| `Vd.w=vsub(Vu.w,Vv.w,Qx4):carry` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = Vu.w[i]+~Vv.w[i]+QxV[i*4];`<br>`QxV[4*i+4-1:4*i] = -carry_from(Vu.w[i], `<br>`~Vv.w[i], QxV[i*4]);`<br>`}` |

##### Class: XTYPE (slots 2,3)

##### Notes

- This instruction can use any HVX resource.
- The predicate generated by this instruction cannot be used as a .new predicate, nor can it be automatically AND’d with another predicate.

##### Intrinsics

|  |  |
|---|---|
| `Vd.w = vadd(Vu.w, Vv.w,` | `HVX_Vector Q6_Vw_vadd_VwVwQ_carry_sat` |
| `Qs4):carry:sat` | `(HVX_Vector Vu, HVX_Vector Vv, HVX_VectorPred Qs)` |
| `Vd.w=vadd(Vu.w,Vv.w,Qx4):carry` | `HVX_Vector Q6_Vw_vadd_VwVwQ_carry(HVX_Vector Vu, HVX_Vector Vv, HVX_VectorPred* Qp)` |
| `Vd.w=vsub(Vu.w,Vv.w,Qx4):carry` | `HVX_Vector Q6_Vw_vsub_VwVwQ_carry(HVX_Vector Vu, HVX_Vector Vv, HVX_VectorPred* Qp)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | x2 | x2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | x | x | d | d | d | d | d | Vd.w=vadd(Vu.w,Vv.w,Qx4) :carry |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | x | x | d | d | d | d | d | Vd.w=vsub(Vu.w,Vv.w,Qx4) :carry |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | s2 | s2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | s | s | d | d | d | d | d | Vd.w=vadd(Vu.w,Vv.w,Qs4) :carry:sat |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | e2 | e2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | e | e | d | d | d | d | d | Vd.w,Qe4=vadd(Vu.w,Vv.w) :carry |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | e | e | d | d | d | d | d | Vd.w,Qe4=vsub(Vu.w,Vv.w) :carry |
| ICLASS | ICLASS | ICLASS | ICLASS | RegType | RegType | RegType | RegType | Maj | Maj |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  | x2 | x2 | d5 | d5 | d5 | d5 | d5 |  |
| 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | - | t | t | t | t | t | - | x | x | d | d | d | d | d | Rdd=add(Rss,Rtt,Px):carry |
| 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 1 | s | s | s | s | s | P | P | - | t | t | t | t | t | - | x | x | d | d | d | d | d | Rdd=sub(Rss,Rtt,Px):carry |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `e2` | Field to encode register e |
| `s2` | Field to encode register s |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x2` | Field to encode register x |
| `Maj` | Major opcode |
| `Min` | Minor opcode |
| `RegType` | Register type |

#### Logical operations

Perform bitwise logical operations (AND OR, XOR) between the two vector registers. For VNOT, invert the input register.

| Syntax | Behavior |
|---|---|
| `Vd=vand(Vu,Vv)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = Vu.uh[i] & Vv.h[i];`<br>`}` |
| `Vd=vnot(Vu)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = ~Vu.uh[i];`<br>`}` |
| `Vd=vor(Vu,Vv)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = Vu.uh[i] \| Vv.h[i];`<br>`}` |
| `Vd=vxor(Vu,Vv)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = Vu.uh[i] ^ Vv.h[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd=vand(Vu,Vv)` | `HVX_Vector Q6_V_vand_VV(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd=vnot(Vu)` | `HVX_Vector Q6_V_vnot_V(HVX_Vector Vu)` |
| `Vd=vor(Vu,Vv)` | `HVX_Vector Q6_V_vor_VV(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd=vxor(Vu,Vv)` | `HVX_Vector Q6_V_vxor_VV(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd=vand(Vu,Vv) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd=vor(Vu,Vv) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd=vxor(Vu,Vv) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 0 | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd=vnot(Vu) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Copy

Copy a single input vector register to a new output vector register.

Using a scalar predicate, conditionally copy a single vector register to a destination vector register, or conditionally combine two input vectors into a destination vector register pair. A scalar predicate guards the entire operation. If the scalar predicate is true, the operation is performed. Otherwise the instruction is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `Vd=Vu` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i]=Vu.w[i];`<br>`}` |
| `if ([!]Ps) Vd=Vu` | `if ([!]Ps[0]) {`<br>`for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = Vu.ub[i];`<br>`}`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

```
Vd=VuHVX_Vector Q6_V_equals_V(HVX_Vector Vu)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | s2 | s2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | - | - | - | - | - | P | P | - | u | u | u | u | u | - | s | s | d | d | d | d | d | if (Ps) Vd=Vu |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | - | - | - | - | - | P | P | - | u | u | u | u | u | - | s | s | d | d | d | d | d | if (!Ps) Vd=Vu |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 1 | 1 | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd=Vu |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `s2` | Field to encode register s |
| `u5` | Field to encode register u |

#### Temporary assignment

Copy an input vector register(s) to a temporary vector register (pair) that is immediately used within the current packet.

| Syntax | Behavior |
|---|---|
| `Vd.tmp=Vu` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i]=Vu.w[i];`<br>`}` |
| `Vdd.tmp=vcombine(Vu,Vv)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = Vv.ub[i];`<br>`Vdd.v[1].ub[i] = Vu.ub[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.tmp=Vu |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.tmp=vcombine(Vu,Vv) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Average

Add the elements of Vu to the respective elements of Vv, and shift the results right by 1 bit. The intermediate precision of the sum is larger than the input data precision. Optionally, add a rounding constant 0x1 before shifting.

Supports unsigned byte, signed and unsigned halfword, and signed word. The operation is replicated to fill the implemented data path width.

Vd.w=vavg(Vu.w,Vv.w)[:rnd]

|  |  |
|---|---|
| [1] | [0] |

Vu

|  |  |
|---|---|
| [1] | [0] |

Vv

+ +

+1 +1<sup>Optional round</sup>

Other data path lanes

>>1 >>1

|  |  |
|---|---|
| [1] | [0] |

Vd

Subtract the elements of Vu from the respective elements of Vv, and shift the results right by 1 bit. The intermediate precision of the sum is larger than the input data precision. Saturate the data to the required precision.

Supports unsigned byte, halfword, and word. The operation is replicated to fill the implemented data path width.

Vd.w=vnavg(Vu.w,Vv.w)

|  |  |
|---|---|
| [1] | [0] |

Vu

|  |  |
|---|---|
| [1] | [0] |

Vv

- -

>>1 >>1

|  |  |
|---|---|
| [1] | [0] |

Vd

Other data path lanes

| Syntax | Behavior |
|---|---|
| `Vd.b=vavg(Vu.b,Vv.b)[:rnd]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = (Vu.b[i]+Vv.b[i]+1)/2;`<br>`}` |
| `Vd.b=vnavg(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = (Vu.b[i]-Vv.b[i])/2;`<br>`}` |
| `Vd.b=vnavg(Vu.ub,Vv.ub)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = (Vu.ub[i]-Vv.ub[i])/2;`<br>`}` |
| `Vd.h=vavg(Vu.h,Vv.h)[:rnd]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i]+Vv.h[i]+1)/2;`<br>`}` |
| `Vd.h=vnavg(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i]-Vv.h[i])/2;`<br>`}` |
| `Vd.ub=vavg(Vu.ub,Vv.ub)[:rnd]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = (Vu.ub[i]+Vv.ub[i]+1)/2;`<br>`}` |
| `Vd.uh=vavg(Vu.uh,Vv.uh)[:rnd]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i]+Vv.uh[i]+1)/2;`<br>`}` |
| `Vd.uw=vavg(Vu.uw,Vv.uw)[:rnd]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.uw[i]+Vv.uw[i]+1)/2;`<br>`}` |
| `Vd.w=vavg(Vu.w,Vv.w)[:rnd]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i]+Vv.w[i]+1)/2;`<br>`}` |
| `Vd.w=vnavg(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i]-Vv.w[i])/2;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vavg(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vavg_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vavg(Vu.b,Vv.b):rnd` | `HVX_Vector Q6_Vb_vavg_VbVb_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vnavg(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vnavg_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vnavg(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vb_vnavg_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vavg(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vavg_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vavg(Vu.h,Vv.h):rnd` | `HVX_Vector Q6_Vh_vavg_VhVh_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vnavg(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vnavg_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vavg(Vu.ub,Vv.ub)` | `HVX_Vector Q6_Vub_vavg_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vavg(Vu.ub,Vv.ub):rnd` | `HVX_Vector Q6_Vub_vavg_VubVub_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vavg(Vu.uh,Vv.uh)` | `HVX_Vector Q6_Vuh_vavg_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vavg(Vu.uh,Vv.uh):rnd` | `HVX_Vector Q6_Vuh_vavg_VuhVuh_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uw=vavg(Vu.uw,Vv.uw)` | `HVX_Vector Q6_Vuw_vavg_VuwVuw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uw=vavg(Vu.uw,Vv.uw):rnd` | `HVX_Vector Q6_Vuw_vavg_VuwVuw_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vavg(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vavg_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vavg(Vu.w,Vv.w):rnd` | `HVX_Vector Q6_Vw_vavg_VwVw_rnd(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vnavg(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vnavg_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.ub=vavg(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.uh=vavg(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.h=vavg(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vavg(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vnavg(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.h=vnavg(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.w=vnavg(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.ub=vavg(Vu.ub,Vv.ub):rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.uh=vavg(Vu.uh,Vv.uh):rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.h=vavg(Vu.h,Vv.h):rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.w=vavg(Vu.w,Vv.w):rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uw=vavg(Vu.uw,Vv.uw) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.uw=vavg(Vu.uw,Vv.uw): rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.b=vavg(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.b=vavg(Vu.b,Vv.b):rnd |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.b=vnavg(Vu.b,Vv.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Compare vectors

Compares between the two vector register inputs Vu and Vv. Depending on the element size, an appropriate number of bits are written into the vector predicate register Qd for each pair of elements.

Two types of compare are supported: equal (.eq) and greater than (.gt).

Supports comparison of word, signed and unsigned halfword, signed and unsigned byte.

For each element comparison, the respective number of bits in the destination register are: bytes one bit, halfwords two bits, and words four bits.

Optionally, supports XOR (^) with the destination, AND (&) with the destination, and OR (|) with the destination.

| Syntax | Behavior |
|---|---|
| `Qd4=vcmp.eq(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QdV[i+1-1:i] = ((Vu.b[i/1] == Vv.b[i/1]) ? `<br>`0x1:0);`<br>`}` |
| `Qd4=vcmp.eq(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QdV[i+2-1:i] = ((Vu.h[i/2] == Vv.h[i/2]) ? 0x3 `<br>`: 0);`<br>`}` |
| `Qd4=vcmp.eq(Vu.ub,Vv.ub)` | `Assembler mapped to: "Qd4=vcmp.eq(Vu." "b" ",Vv." `<br>`"b" ")"` |
| `Qd4=vcmp.eq(Vu.uh,Vv.uh)` | `Assembler mapped to: "Qd4=vcmp.eq(Vu." "h" ",Vv." `<br>`"h" ")"` |
| `Qd4=vcmp.eq(Vu.uw,Vv.uw)` | `Assembler mapped to: "Qd4=vcmp.eq(Vu." "w" ",Vv." `<br>`"w" ")"` |
| `Qd4=vcmp.eq(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QdV[i+4-1:i] = ((Vu.w[i/4] == Vv.w[i/4]) ? 0xF `<br>`: 0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QdV[i+1-1:i] = ((Vu.b[i/1] > Vv.b[i/1]) ? 0x1 `<br>`: 0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.bf,Vv.bf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.bf[i/2] > Vv.bf[i/2]) ? 0x3 : 0;`<br>`QdV[i+2-1:i] = VAL;`<br>`}` |
| `Qd4=vcmp.gt(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QdV[i+2-1:i] = ((Vu.h[i/2] > Vv.h[i/2])? 0x3 : `<br>`0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.hf,Vv.hf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.hf[i/2] > Vv.hf[i/2]) ? 0x3 : 0;`<br>`QdV[i+2-1:i] = VAL;`<br>`}` |
| `Qd4=vcmp.gt(Vu.sf,Vv.sf)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`VAL = (Vu.sf[i/4] > Vv.sf[i/4]) ? 0xF : 0;`<br>`QdV[i+4-1:i] = VAL;`<br>`}` |
| `Qd4=vcmp.gt(Vu.ub,Vv.ub)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QdV[i+1-1:i] = ((Vu.ub[i/1] > Vv.ub[i/1]) ? `<br>`0x1 : 0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.uh,Vv.uh)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QdV[i+2-1:i] = ((Vu.uh[i/2] > Vv.uh[i/2]) ? `<br>`0x3 : 0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.uw,Vv.uw)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QdV[i+4-1:i] = ((Vu.uw[i/4] > Vv.uw[i/4]) ? `<br>`0xF : 0);`<br>`}` |
| `Qd4=vcmp.gt(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QdV[i+4-1:i] = ((Vu.w[i/4] > Vv.w[i/4]) ? 0xF `<br>`: 0);`<br>`}` |
| `Qx4[&\|]=vcmp.eq(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] [\|&] ((Vu.b[i/1] `<br>`== Vv.b[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.eq(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] [\|&] ((Vu.h[i/2] `<br>`== Vv.h[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.eq(Vu.ub,Vv.ub)` | `Assembler mapped to: "Qx4[\|&]=vcmp.eq(Vu." "b" `<br>`",Vv." "b" ")"` |
| `Qx4[&\|]=vcmp.eq(Vu.uh,Vv.uh)` | `Assembler mapped to: "Qx4[\|&]=vcmp.eq(Vu." "h" `<br>`",Vv." "h" ")"` |
| `Qx4[&\|]=vcmp.eq(Vu.uw,Vv.uw)` | `Assembler mapped to: "Qx4[\|&]=vcmp.eq(Vu." "w" `<br>`",Vv." "w" ")"` |
| `Qx4[&\|]=vcmp.eq(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] [\|&] ((Vu.w[i/4] `<br>`== Vv.w[i/4]) ? 0xF : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] [\|&] ((Vu.b[i/1] > `<br>`Vv.b[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.bf,Vv.bf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.bf[i/2] > Vv.bf[i/2]) ? 0x3 : 0;`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] [\|&] VAL;`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] [\|&] ((Vu.h[i/2] > `<br>`Vv.h[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.hf,Vv.hf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.hf[i/2] > Vv.hf[i/2]) ? 0x3 : 0;`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] [\|&] VAL;`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.sf,Vv.sf)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`VAL = (Vu.sf[i/4] > Vv.sf[i/4]) ? 0xF : 0 ;`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] [\|&] VAL;`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.ub,Vv.ub)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] [\|&] ((Vu.ub[i/1] `<br>`> Vv.ub[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.uh,Vv.uh)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] [\|&] ((Vu.uh[i/2] `<br>`> Vv.uh[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.uw,Vv.uw)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] [\|&] ((Vu.uw[i/4] `<br>`> Vv.uw[i/4]) ? 0xF : 0);`<br>`}` |
| `Qx4[&\|]=vcmp.gt(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] [\|&] ((Vu.w[i/4] > `<br>`Vv.w[i/4]) ? 0xF : 0);`<br>`}` |
| `Qx4^=vcmp.eq(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] ^ ((Vu.b[i/1] == `<br>`Vv.b[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4^=vcmp.eq(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] ^ ((Vu.h[i/2] == `<br>`Vv.h[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4^=vcmp.eq(Vu.ub,Vv.ub)` | `Assembler mapped to: "Qx4^=vcmp.eq(Vu." "b" ", `<br>`Vv." "b" ")"` |
| `Qx4^=vcmp.eq(Vu.uh,Vv.uh)` | `Assembler mapped to: "Qx4^=vcmp.eq(Vu." "h" ", `<br>`Vv." "h" ")"` |
| `Qx4^=vcmp.eq(Vu.uw,Vv.uw)` | `Assembler mapped to: "Qx4^=vcmp.eq(Vu." "w" ", `<br>`Vv." "w" ")"` |
| `Qx4^=vcmp.eq(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] ^ ((Vu.w[i/4] == `<br>`Vv.w[i/4]) ? 0xF : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.b,Vv.b)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] ^ ((Vu.b[i/1] > `<br>`Vv.b[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.bf,Vv.bf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.bf[i/2] > Vv.bf[i/2]) ? 0x3 : 0;`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] ^ VAL;`<br>`}` |
| `Qx4^=vcmp.gt(Vu.h,Vv.h)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] ^ ((Vu.h[i/2] > `<br>`Vv.h[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.hf,Vv.hf)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`VAL = (Vu.hf[i/2] > Vv.hf[i/2]) ? 0x3 : 0;`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] ^ VAL;`<br>`}` |
| `Qx4^=vcmp.gt(Vu.sf,Vv.sf)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`VAL = (Vu.sf[i/4] > Vv.sf[i/4]) ? 0xF : 0;`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] ^ VAL;`<br>`}` |
| `Qx4^=vcmp.gt(Vu.ub,Vv.ub)` | `for( i = 0; i < VWIDTH; i += 1) {`<br>`QxV[i+1-1:i] = QxV[i+1-1:i] ^ ((Vu.ub[i/1] > `<br>`Vv.ub[i/1]) ? 0x1 : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.uh,Vv.uh)` | `for( i = 0; i < VWIDTH; i += 2) {`<br>`QxV[i+2-1:i] = QxV[i+2-1:i] ^ ((Vu.uh[i/2] > `<br>`Vv.uh[i/2]) ? 0x3 : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.uw,Vv.uw)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] ^ ((Vu.uw[i/4] > `<br>`Vv.uw[i/4]) ? 0xF : 0);`<br>`}` |
| `Qx4^=vcmp.gt(Vu.w,Vv.w)` | `for( i = 0; i < VWIDTH; i += 4) {`<br>`QxV[i+4-1:i] = QxV[i+4-1:i] ^ ((Vu.w[i/4] > `<br>`Vv.w[i/4]) ? 0xF : 0);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Qd4=vcmp.eq(Vu.b,Vv.b)` | `HVX_VectorPred Q6_Q_vcmp_eq_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.eq(Vu.h,Vv.h)` | `HVX_VectorPred Q6_Q_vcmp_eq_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.eq(Vu.w,Vv.w)` | `HVX_VectorPred Q6_Q_vcmp_eq_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.b,Vv.b)` | `HVX_VectorPred Q6_Q_vcmp_gt_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.bf,Vv.bf)` | `HVX_VectorPred Q6_Q_vcmp_gt_VbfVbf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.h,Vv.h)` | `HVX_VectorPred Q6_Q_vcmp_gt_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.hf,Vv.hf)` | `HVX_VectorPred Q6_Q_vcmp_gt_VhfVhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.sf,Vv.sf)` | `HVX_VectorPred Q6_Q_vcmp_gt_VsfVsf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.ub,Vv.ub)` | `HVX_VectorPred Q6_Q_vcmp_gt_VubVub(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.uh,Vv.uh)` | `HVX_VectorPred Q6_Q_vcmp_gt_VuhVuh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.uw,Vv.uw)` | `HVX_VectorPred Q6_Q_vcmp_gt_VuwVuw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qd4=vcmp.gt(Vu.w,Vv.w)` | `HVX_VectorPred Q6_Q_vcmp_gt_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.eq(Vu.b,Vv.b)` | `HVX_VectorPred Q6_Q_vcmp_eqand_QVbVb(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.eq(Vu.h,Vv.h)` | `HVX_VectorPred Q6_Q_vcmp_eqand_QVhVh(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.eq(Vu.w,Vv.w)` | `HVX_VectorPred Q6_Q_vcmp_eqand_QVwVw(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.b,Vv.b)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVbVb(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.bf,Vv.bf)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVbfVbf (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.h,Vv.h)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVhVh(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.hf,Vv.hf)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVhfVhf (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.sf,Vv.sf)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVsfVsf (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.ub,Vv.ub)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVubVub (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.uh,Vv.uh)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVuhVuh (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.uw,Vv.uw)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVuwVuw (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4&=vcmp.gt(Vu.w,Vv.w)` | `HVX_VectorPred Q6_Q_vcmp_gtand_QVwVw(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4^=vcmp.eq(Vu.b,Vv.b)` | `HVX_VectorPred Q6_Q_vcmp_eqxacc_QVbVb (HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |

|  |  |
|---|---|
|  | `HVX_VectorPred Q6_Q_vcmp_eqxacc_QVhVh `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_eqxacc_QVwVw `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVbVb `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
| `Qx4^=vcmp.gt(Vu.bf,Vv.bf)` | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVbfVbf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVhVh `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVhfVhf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVsfVsf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVubVub `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVuhVuh `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVuwVuw `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtxacc_QVwVw `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_eqor_QVbVb(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_eqor_QVhVh(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_eqor_QVwVw(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVbVb(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVbfVbf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVhVh(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVhfVhf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVsfVsf `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVubVub `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVuhVuh `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVuwVuw `<br>`(HVX_VectorPred Qx, HVX_Vector Vu, HVX_Vector Vv)` |
|  | `HVX_VectorPred Q6_Q_vcmp_gtor_QVwVw(HVX_VectorPred `<br>`Qx, HVX_Vector Vu, HVX_Vector Vv)` |

Qx4^=vcmp.eq(Vu.h,Vv.h)

Qx4^=vcmp.eq(Vu.w,Vv.w)

Qx4^=vcmp.gt(Vu.b,Vv.b)

Qx4^=vcmp.gt(Vu.h,Vv.h)

Qx4^=vcmp.gt(Vu.hf,Vv.hf)

Qx4^=vcmp.gt(Vu.sf,Vv.sf)

Qx4^=vcmp.gt(Vu.ub,Vv.ub)

Qx4^=vcmp.gt(Vu.uh,Vv.uh)

Qx4^=vcmp.gt(Vu.uw,Vv.uw)

Qx4^=vcmp.gt(Vu.w,Vv.w)

Qx4|=vcmp.eq(Vu.b,Vv.b)

Qx4|=vcmp.eq(Vu.h,Vv.h)

Qx4|=vcmp.eq(Vu.w,Vv.w)

Qx4|=vcmp.gt(Vu.b,Vv.b)

Qx4|=vcmp.gt(Vu.bf,Vv.bf)

Qx4|=vcmp.gt(Vu.h,Vv.h)

Qx4|=vcmp.gt(Vu.hf,Vv.hf)

Qx4|=vcmp.gt(Vu.sf,Vv.sf)

Qx4|=vcmp.gt(Vu.ub,Vv.ub)

Qx4|=vcmp.gt(Vu.uh,Vv.uh)

Qx4|=vcmp.gt(Vu.uw,Vv.uw)

Qx4|=vcmp.gt(Vu.w,Vv.w)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | x2 | x2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 0 | 0 | 0 | x | x | Qx4&=vcmp.eq(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 0 | 0 | 1 | x | x | Qx4&=vcmp.eq(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 0 | 1 | 0 | x | x | Qx4&=vcmp.eq(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 1 | 0 | 0 | x | x | Qx4&=vcmp.gt(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 1 | 0 | 1 | x | x | Qx4&=vcmp.gt(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | 1 | 1 | 0 | x | x | Qx4&=vcmp.gt(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 0 | 0 | 0 | x | x | Qx4&= vcmp.gt(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 0 | 0 | 1 | x | x | Qx4&= vcmp.gt(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 0 | 1 | 0 | x | x | Qx4&= vcmp.gt(Vu.uw,Vv.uw) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 1 | 0 | 0 | x | x | Qx4\|=vcmp.gt(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 1 | 0 | 1 | x | x | Qx4\|=vcmp.gt(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | 1 | 1 | 0 | x | x | Qx4\|=vcmp.gt(Vu.bf,Vv.bf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 0 | 0 | 0 | x | x | Qx4\|=vcmp.eq(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 0 | 0 | 1 | x | x | Qx4\|=vcmp.eq(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 0 | 1 | 0 | x | x | Qx4\|=vcmp.eq(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 1 | 0 | 0 | x | x | Qx4\|=vcmp.gt(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 1 | 0 | 1 | x | x | Qx4\|=vcmp.gt(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | 1 | 1 | 0 | x | x | Qx4\|=vcmp.gt(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 0 | 0 | 0 | x | x | Qx4\|=vcmp.gt(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 0 | 0 | 1 | x | x | Qx4\|=vcmp.gt(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 0 | 1 | 0 | x | x | Qx4\|= vcmp.gt(Vu.uw,Vv.uw) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | d2 | d2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 1 | 0 | 0 | d | d | Qd4=vcmp.gt(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 1 | 0 | 1 | d | d | Qd4=vcmp.gt(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | 1 | 1 | 0 | d | d | Qd4=vcmp.gt(Vu.bf,Vv.bf) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | x2 | x2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 0 | 0 | 0 | x | x | Qx4^=vcmp.eq(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 0 | 0 | 1 | x | x | Qx4^=vcmp.eq(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 0 | 1 | 0 | x | x | Qx4^=vcmp.eq(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 1 | 0 | 0 | x | x | Qx4^=vcmp.gt(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 1 | 0 | 1 | x | x | Qx4^=vcmp.gt(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | 1 | 1 | 0 | x | x | Qx4^=vcmp.gt(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | 0 | 0 | 0 | x | x | Qx4^= vcmp.gt(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | 0 | 0 | 1 | x | x | Qx4^= vcmp.gt(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | 0 | 1 | 0 | x | x | Qx4^= vcmp.gt(Vu.uw,Vv.uw) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | 0 | 1 | 0 | x | x | Qx4&=vcmp.gt(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | 0 | 1 | 1 | x | x | Qx4&=vcmp.gt(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | 1 | 0 | 0 | x | x | Qx4&=vcmp.gt(Vu.bf,Vv.bf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | 0 | 1 | 0 | x | x | Qx4^=vcmp.gt(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | 0 | 1 | 1 | x | x | Qx4^=vcmp.gt(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | 1 | 0 | 0 | x | x | Qx4^=vcmp.gt(Vu.bf,Vv.bf) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  |  | d2 | d2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 0 | 0 | 0 | d | d | Qd4=vcmp.eq(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 0 | 0 | 1 | d | d | Qd4=vcmp.eq(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 0 | 1 | 0 | d | d | Qd4=vcmp.eq(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 1 | 0 | 0 | d | d | Qd4=vcmp.gt(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 1 | 0 | 1 | d | d | Qd4=vcmp.gt(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | 1 | 1 | 0 | d | d | Qd4=vcmp.gt(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | 0 | 0 | 0 | d | d | Qd4=vcmp.gt(Vu.ub,Vv.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | 0 | 0 | 1 | d | d | Qd4=vcmp.gt(Vu.uh,Vv.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | 0 | 1 | 0 | d | d | Qd4=vcmp.gt(Vu.uw,Vv.uw) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x2` | Field to encode register x |

#### Conditional accumulate

Conditionally add or subtract a value to the destination register. If the corresponding bits are set in the vector predicate register, the elements in Vu are added to or subtracted from the corresponding elements in Vx. Supports byte, halfword, and word. No saturation is performed on the result.

if (Qv4) Vx.b +[-]= Vu.b

|  |  |
|---|---|
| [1] | [0] |

[N-1] Vu

|  |  |  |
|---|---|---|
| [1] |  | [0] |

[N-1] Qv

0 0 0

+/- +/- +/-

elements implemented

N is the number of data path

|  |  |
|---|---|
|  | [N-1] |
|  |  |

[1] [0] Vx

|  |  |  |  |
|---|---|---|---|
|  | [1] |  | [0] |
|  |  |  |  |

[N-1] Vx

| Syntax | Behavior |
|---|---|
| `if ([!]Qv4) Vx.b[+-]=Vu.b` | `for (i = 0; i < VELEM(8); i[+-][+-]) {`<br>`Vx.ub[i]=QvV.i ? Vx.ub[i] : Vx.ub[i][+-`<br>`]Vu.ub[i];`<br>`}` |
| `if ([!]Qv4) Vx.h[+-]=Vu.h` | `for (i = 0; i < VELEM(16); i[+-][+-]) {`<br>`Vx.h[i]=select_bytes(QvV,i,Vx.h[i], Vx.h[i][+-`<br>`]Vu.h[i]);`<br>`}` |
| `if ([!]Qv4) Vx.w[+-]=Vu.w` | `for (i = 0; i < VELEM(32); i[+-][+-]) {`<br>`Vx.w[i]=select_bytes(QvV,i,Vx.w[i], Vx.w[i][+-`<br>`]Vu.w[i]);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `if (!Qv4) Vx.b+=Vu.b` | `HVX_Vector Q6_Vb_condacc_QnVbVb(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (!Qv4) Vx.b-=Vu.b` | `HVX_Vector Q6_Vb_condnac_QnVbVb(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (!Qv4) Vx.h+=Vu.h` | `HVX_Vector Q6_Vh_condacc_QnVhVh(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (!Qv4) Vx.h-=Vu.h` | `HVX_Vector Q6_Vh_condnac_QnVhVh(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (!Qv4) Vx.w+=Vu.w` | `HVX_Vector Q6_Vw_condacc_QnVwVw(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (!Qv4) Vx.w-=Vu.w` | `HVX_Vector Q6_Vw_condnac_QnVwVw(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.b+=Vu.b` | `HVX_Vector Q6_Vb_condacc_QVbVb(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.b-=Vu.b` | `HVX_Vector Q6_Vb_condnac_QVbVb(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.h+=Vu.h` | `HVX_Vector Q6_Vh_condacc_QVhVh(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.h-=Vu.h` | `HVX_Vector Q6_Vh_condnac_QVhVh(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.w+=Vu.w` | `HVX_Vector Q6_Vw_condacc_QVwVw(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |
| `if (Qv4) Vx.w-=Vu.w` | `HVX_Vector Q6_Vw_condnac_QVwVw(HVX_VectorPred Qv, HVX_Vector Vx, HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | if (Qv4) Vx.b+=Vu.b |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | if (Qv4) Vx.h+=Vu.h |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | if (Qv4) Vx.w+=Vu.w |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | if (!Qv4) Vx.b+=Vu.b |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | x | x | x | x | x | if (!Qv4) Vx.h+=Vu.h |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | if (!Qv4) Vx.w+=Vu.w |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | x | x | x | x | x | if (Qv4) Vx.b-=Vu.b |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 0 | 1 | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | if (Qv4) Vx.h-=Vu.h |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | if (Qv4) Vx.w-=Vu.w |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | if (!Qv4) Vx.b-=Vu.b |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | if (!Qv4) Vx.h-=Vu.h |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | x | x | x | x | x | if (!Qv4) Vx.w-=Vu.w |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Mux select

Performs a parallel if-then-else operation. Based on a predicate bit in a vector predicate register, if the bit is set, the corresponding byte from vector register Vu is placed in the destination vector register Vd. Otherwise, the corresponding byte from Vv is written. The operation works on bytes so it can handle all data sizes.

Vd=vmux(Qt4,Vu,Vv)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[N-1] Vu

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |
| b[3] |  | b[2] |  | b[1] |  | b[0] |

b[N-1] Vv

Qt.b[0]

Qt.b[1]

|  |  |
|---|---|
|  |  |
|  |  |

Qt.b[2]

Qt.b[3]

...

Qt.b[N-1]

N is number of slices implemented

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[N-1] Vd

| Syntax | Behavior |
|---|---|
| `Vd=vmux(Qt4,Vu,Vv)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.ub[i] = QtV[i] ? Vu.ub[i] : Vv.ub[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

```
Vd=vmux(Qt4,Vu,Vv)HVX_Vector Q6_V_vmux_QVV(HVX_VectorPred Qt,
                             HVX_Vector Vu, HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | t2 | t2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | - | t | t | d | d | d | d | d | Vd=vmux(Qt4,Vu,Vv) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t2` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Saturation

Perform simple arithmetic operations, add and subtract, between the elements of the two vectors Vu and Vv. Supports word, halfword (signed and unsigned), and byte (signed and unsigned).

Optionally saturate for word and halfword. Always saturate for unsigned types.

| Syntax | Behavior |
|---|---|
| `Vd.h=vsat(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i].h[0]=sat₁₆(Vv.w[i]);`<br>`Vd.w[i].h[1]=sat₁₆(Vu.w[i]);`<br>`}` |
| `Vd.ub=vsat(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=usat₈(Vv.h[i]);`<br>`Vd.uh[i].b[1]=usat₈(Vu.h[i]);`<br>`}` |
| `Vd.uh=vsat(Vu.uw,Vv.uw)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i].h[0]=usat₁₆(Vv.uw[i]);`<br>`Vd.w[i].h[1]=usat₁₆(Vu.uw[i]);`<br>`}` |
| `Vd.w=vsatdw(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = usat₃₂(Vu.w[i]:Vv.w[i]);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vsat(Vu.w,Vv.w)` | `HVX_Vector Q6_Vh_vsat_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vsat(Vu.h,Vv.h)` | `HVX_Vector Q6_Vub_vsat_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vsat(Vu.uw,Vv.uw)` | `HVX_Vector Q6_Vuh_vsat_VuwVuw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vsatdw(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vsatdw_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vsatdw(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.uh=vsat(Vu.uw,Vv.uw) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.ub=vsat(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vsat(Vu.w,Vv.w) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### In-lane shuffle

Shuffle the even or odd elements respectively from two vector registers into one destination vector register. Supports bytes and halfwords.

Vd.b=vshuffe(Vu.b,Vv.b)

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| b[N-1] | b[N-2] | …. | b[3] | b[2] | b[1] | b[0] |

Vv

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |
| b[N-1] | b[N-2] |  | …. | b[3] | b[2] | b[1] | b[1] | b[0] |

Vu

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| b[N-1] | b[N-2] | …. | b[3] | b[2] | b[1] | b[0] |

Vd

Vd.b=vshuffo(Vu.b,Vv.b)

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| b[N-1] | b[N-2] | …. | b[3] | b[2] | b[1] | b[0] |

Vv

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |  |
| b[N-1] | b[N-2] | b[N-2] | …. | b[3] |  | b[2] | b[1] |  | b[0] |

Vu

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| b[N-1] | b[N-2] | …. | b[3] | b[2] | b[1] | b[0] |

Vd

This group of shuffles is limited to bytes and halfwords.

| Syntax | Behavior |
|---|---|
| `Vd.b=vshuffe(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=Vv.uh[i].ub[0];`<br>`Vd.uh[i].b[1]=Vu.uh[i].ub[0];`<br>`}` |
| `Vd.b=vshuffo(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=Vv.uh[i].ub[1];`<br>`Vd.uh[i].b[1]=Vu.uh[i].ub[1];`<br>`}` |
| `Vd.h=vshuffe(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i].h[0]=Vv.uw[i].uh[0];`<br>`Vd.uw[i].h[1]=Vu.uw[i].uh[0];`<br>`}` |
| `Vd.h=vshuffo(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i].h[0]=Vv.uw[i].uh[1];`<br>`Vd.uw[i].h[1]=Vu.uw[i].uh[1];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction can use any HVX resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vshuffe(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vshuffe_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.b=vshuffo(Vu.b,Vv.b)` | `HVX_Vector Q6_Vb_vshuffo_VbVb(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vshuffe(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vshuffe_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vshuffo(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vshuffo_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.b=vshuffe(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.b=vshuffo(Vu.b,Vv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vshuffe(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vshuffo(Vu.h,Vv.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
