## 6.2 HVX ALU DOUBLE RESOURCE

The HVX ALU DOUBLE RESOURCE instruction subclass includes ALU instructions that use a pair of

HVX resources.

#### Predicate operations

Perform bitwise logical operations between two vector predicate registers Qs and Qt, and place the result in Qd. The operations are element-size agnostic.

The following combinations are implemented: Qs & Qt, Qs & !Qt, Qs | Qt, Qs | !Qt, Qs ^ Qt. Interleave predicate bits from two vectors to match a shuffling operation like `vsat `or `vround`. Forms that match word-to-halfword and halfword-to-byte shuffling are available.

| Syntax | Behavior |
|---|---|
| `Qd4.b=vshuffe(Qs4.h,Qt4.h)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=(i & 1) ? QsV[i-1] : QtV[i] ;`<br>`}` |
| `Qd4.h=vshuffe(Qs4.w,Qt4.w)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=(i & 2) ? QsV[i-2] : QtV[i] ;`<br>`}` |
| `Qd4=and(Qs4,[!]Qt4)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=QsV[i] && [!]QtV[i] ;`<br>`}` |
| `Qd4=or(Qs4,[!]Qt4)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=QsV[i] \|\| [!]QtV[i] ;`<br>`}` |
| `Qd4=xor(Qs4,Qt4)` | `for (i = 0; i < VELEM(8); i++) {`<br>`QdV[i]=QsV[i] ^ QtV[i] ;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

|  |  |
|---|---|
| `Qd4.b=vshuffe(Qs4.h,Qt4.h)` | `HVX_VectorPred Q6_Qb_vshuffe_QhQh (HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4.h=vshuffe(Qs4.w,Qt4.w)` | `HVX_VectorPred Q6_Qh_vshuffe_QwQw (HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4=and(Qs4,!Qt4)` | `HVX_VectorPred Q6_Q_and_QQn(HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4=and(Qs4,Qt4)` | `HVX_VectorPred Q6_Q_and_QQ(HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4=or(Qs4,!Qt4)` | `HVX_VectorPred Q6_Q_or_QQn(HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4=or(Qs4,Qt4)` | `HVX_VectorPred Q6_Q_or_QQ(HVX_VectorPred Qs, HVX_VectorPred Qt)` |
| `Qd4=xor(Qs4,Qt4)` | `HVX_VectorPred Q6_Q_xor_QQ(HVX_VectorPred Qs, HVX_VectorPred Qt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | t2 | t2 |  |  |  |  |  |  | Parse | Parse |  |  |  |  | s2 | s2 |  |  |  |  |  |  | d2 | d2 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 0 | 0 | 0 | d | d | Qd4=and(Qs4,Qt4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 0 | 0 | 1 | d | d | Qd4=or(Qs4,Qt4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 0 | 1 | 1 | d | d | Qd4=xor(Qs4,Qt4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 1 | 0 | 0 | d | d | Qd4=or(Qs4,!Qt4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 1 | 0 | 1 | d | d | Qd4=and(Qs4,!Qt4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 1 | 1 | 0 | d | d | Qd4.b=vshuffe(Qs4.h,Qt4.h ) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | t | t | 0 | - | - | - | 1 | 1 | P | P | 0 | - | - | - | s | s | 0 | 0 | 0 | 1 | 1 | 1 | d | d | Qd4.h=vshuffe(Qs4.w,Qt4. w) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `s2` | Field to encode register s |
| `t2` | Field to encode register t |

#### Combine

Combine two input vector registers into a single destination vector register pair.

Using a scalar predicate, conditionally copy a single vector register to a destination vector register, or conditionally combine two input vectors into a destination vector register pair. A scalar predicate guards the entire operation. If the scalar predicate is true, perform the operation. Otherwise the instruction is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `Vdd=vcombine(Vu,Vv)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = Vv.ub[i];`<br>`Vdd.v[1].ub[i] = Vu.ub[i];`<br>`}` |
| `if ([!]Ps) `<br>`Vdd=vcombine(Vu,Vv)` | `if ([!]Ps[0]) {`<br>`for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = Vv.ub[i];`<br>`Vdd.v[1].ub[i] = Vu.ub[i];`<br>`}`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

```
Vdd=vcombine(Vu,Vv)HVX_VectorPair Q6_W_vcombine_VV(HVX_Vector Vu, HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | s2 | s2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | v | v | v | v | v | P | P | - | u | u | u | u | u | - | s | s | d | d | d | d | d | if (!Ps) Vdd=vcombine(Vu,Vv) |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | - | u | u | u | u | u | - | s | s | d | d | d | d | d | if (Ps) Vdd=vcombine(Vu,Vv) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd=vcombine(Vu,Vv) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `s2` | Field to encode register s |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### In-lane shuffle

The `vshuffoe` instruction performs both the `vshuffo` and `vshuffe` operation at the same time, with even elements placed into the even vector register of Vdd, and odd elements placed in the odd vector register of the destination vector pair.

Vdd.b=vshuffoe(Vu.b,Vv.b)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vu b[3] b[2] b[1] b[0] Vv

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vu Vv

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

Vdd.V[1] b[3] b[2] b[1] b[0] Vdd.V[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[3] b[2] b[1] b[0] Vdd.V[1] Vdd.V[0]

Vdd.h=vshuffoe(Vu.h,Vv.h)

|  |  |
|---|---|
| h[1] | h[0] |

Vu h[1] h[0] Vv

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vu Vv

|  |  |
|---|---|
| h[1] | h[0] |

Vdd.V[1] h[1] h[0] Vdd.V[0]

|  |  |
|---|---|
| h[1] | h[0] |

h[1] h[0] Vdd.V[1] Vdd.V[0]

Repeated for each 32-bit lane

This group of shuffles is limited to bytes and halfwords.

| Syntax | Behavior |
|---|---|
| `Vdd.b=vshuffoe(Vu.b,Vv.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i].b[0]=Vv.uh[i].ub[0];`<br>`Vdd.v[0].uh[i].b[1]=Vu.uh[i].ub[0];`<br>`Vdd.v[1].uh[i].b[0]=Vv.uh[i].ub[1];`<br>`Vdd.v[1].uh[i].b[1]=Vu.uh[i].ub[1];`<br>`}` |
| `Vdd.h=vshuffoe(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i].h[0]=Vv.uw[i].uh[0];`<br>`Vdd.v[0].uw[i].h[1]=Vu.uw[i].uh[0];`<br>`Vdd.v[1].uw[i].h[0]=Vv.uw[i].uh[1];`<br>`Vdd.v[1].uw[i].h[1]=Vu.uw[i].uh[1];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

|  |  |
|---|---|
| `Vdd.b=vshuffoe(Vu.b,Vv.b)` | `HVX_VectorPair Q6_Wb_vshuffoe_VbVb (HVX_Vector Vu, HVX_Vector Vv)` |
| `Vdd.h=vshuffoe(Vu.h,Vv.h)` | `HVX_VectorPair Q6_Wh_vshuffoe_VhVh (HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.h=vshuffoe(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.b=vshuffoe(Vu.b,Vv.b) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Swap

Based on a predicate bit in a vector predicate register, if the bit is set, place the corresponding byte from vector register Vu in the even destination vector register of Vdd, and place the byte from Vv in the even destination vector register of Vdd. Otherwise, the corresponding byte from Vv is written to the even register, and Vu to the odd register. The operation works on bytes, so it can handle all data sizes. It is similar to the `vmux `operation, but places the opposite case output into the odd vector register of the destination vector register pair.

Vdd=vswap(Qt4,Vu,Vv)

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[N-1] Vu

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |
| b[3] |  | b[2] |  | b[1] |  | b[0] |

b[N-1] Vv

1 – pass 0 - swap

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

Qt.b[0]

Qt.b[1]

Qt.b[2]

Qt.b[3]

N is number of slices implemented

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  | b[3] |  | b[2] | b[2] |  | b[1] | b[1] |  | b[0] |

Qt.b[1]

Qt.b[2]

Qt.b[3]

...

Qt.b[N-1]

N is number of slices implemented

b[N-1] Vdd[0]

|  |  |
|---|---|
|  | b[N-1] |

b[3]b[2]b[1]b[0] Vdd[0]

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[N-1] Vdd[1]

| Syntax | Behavior |
|---|---|
| `Vdd=vswap(Qt4,Vu,Vv)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = QtV[i] ? Vu.ub[i]:Vv.ub[i];`<br>`Vdd.v[1].ub[i] = !QtV[i] ? Vu.ub[i]:Vv.ub[i];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

```
Vdd=vswap(Qt4,Vu,Vv)HVX_VectorPair Q6_W_vswap_QVV(HVX_VectorPred Qt,
                        HVX_Vector Vu, HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  | t2 | t2 | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | - | t | t | d | d | d | d | d | Vdd=vswap(Qt4,Vu,Vv) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t2` | Field to encode register t |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Sign/zero extension

Perform sign extension on each even element in Vu, and place it in the even destination vector register Vdd[0]. Odd elements are sign-extended and placed in the odd destination vector register Vdd[1]. Bytes convert to halfwords, and halfwords convert to words.

Sign extension of words is a cross-lane operation, and can only execute on the permute slot.

Vdd.h=vsxt(Vu.b)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | [N<sup>*</sup>-1] | [N<sup>*</sup>-1] | [N<sup>*</sup>-2] | [N<sup>*</sup>-2] | ... | ... | [3] | [3] | [2] | [2] | [1] | [1] | [0] |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| sign fill | sign fill | [N-1] | [N-1] | ... | ... | sign fill | sign fill | [3] | [3] | sign fill | sign fill | [1] | [1] |

Vu

Vdd.V[1]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| sign fill | [N-2] | ... | sign fill | [2] | sign fill | [0] |

Vdd.V[0]

* N is number of operations in vector

Perform zero extension on each even element in Vu, and place it in the even destination vector register Vdd[0]. Odd elements are zero-extended and placed in the odd destination vector register Vdd[1]. Bytes convert to halfwords, and halfwords convert to words.

Zero extension of words is a cross-lane operation, and can only execute on the permute slot.

Vdd.uh=vzxt(Vu.ub)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | [N<sup>*</sup>-1] | [N<sup>*</sup>-1] | [N<sup>*</sup>-2] | [N<sup>*</sup>-2] | ... | ... | [3] | [3] | [2] | [2] | [1] | [1] | [0] |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0x0 | 0x0 | [N-1] | [N-1] | ... | ... | 0x0 | 0x0 | [3] | [3] | 0x0 | 0x0 | [1] | [1] |

Vu

Vdd.V[1]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| 0x0 | [N-2] | ... | 0x0 | [2] | 0x0 | [0] |

Vdd.V[0]

* N is number of operations in vector

| Syntax | Behavior |
|---|---|
| `Vdd.h=vsxt(Vu.b)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = Vu.h[i].b[0];`<br>`Vdd.v[1].h[i] = Vu.h[i].b[1];`<br>`}` |
| `Vdd.uh=vzxt(Vu.ub)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = Vu.uh[i].ub[0];`<br>`Vdd.v[1].uh[i] = Vu.uh[i].ub[1];`<br>`}` |
| `Vdd.uw=vzxt(Vu.uh)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = Vu.uw[i].uh[0];`<br>`Vdd.v[1].uw[i] = Vu.uw[i].uh[1];`<br>`}` |
| `Vdd.w=vsxt(Vu.h)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = Vu.w[i].h[0];`<br>`Vdd.v[1].w[i] = Vu.w[i].h[1];`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vsxt(Vu.b)` | `HVX_VectorPair Q6_Wh_vsxt_Vb(HVX_Vector Vu)` |
| `Vdd.uh=vzxt(Vu.ub)` | `HVX_VectorPair Q6_Wuh_vzxt_Vub(HVX_Vector Vu)` |
| `Vdd.uw=vzxt(Vu.uh)` | `HVX_VectorPair Q6_Wuw_vzxt_Vuh(HVX_Vector Vu)` |
| `Vdd.w=vsxt(Vu.h)` | `HVX_VectorPair Q6_Ww_vsxt_Vh(HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.uh=vzxt(Vu.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.uw=vzxt(Vu.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.h=vsxt(Vu.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.w=vsxt(Vu.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |

#### Arithmetic

Perform simple arithmetic operations, add and subtract, between elements of the two vectors Vu and Vv. Supports word, halfword (signed and unsigned), and byte (signed and unsigned).

Optionally saturate for word and halfword. Always saturate for unsigned types.

| Syntax | Behavior |
|---|---|
| `Vdd.b=vadd(Vuu.b,Vvv.b)[:sat]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].b[i] = [sat₈](Vuu.v[0].b[i]+ `<br>`Vvv.v[0].b[i]);`<br>`Vdd.v[1].b[i] = [sat₈](Vuu.v[1].b[i]+ `<br>`Vvv.v[1].b[i]);`<br>`}` |
| `Vdd.b=vsub(Vuu.b,Vvv.b)[:sat]` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].b[i] = [sat₈](Vuu.v[0].b[i]-`<br>`Vvv.v[0].b[i]);`<br>`Vdd.v[1].b[i] = [sat₈](Vuu.v[1].b[i]-`<br>`Vvv.v[1].b[i]);`<br>`}` |
| `Vdd.h=vadd(Vuu.h,Vvv.h)[:sat]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = [sat₁₆](Vuu.v[0].h[i]+ `<br>`Vvv.v[0].h[i]);`<br>`Vdd.v[1].h[i] = [sat₁₆](Vuu.v[1].h[i]+ `<br>`Vvv.v[1].h[i]);`<br>`}` |
| `Vdd.h=vsub(Vuu.h,Vvv.h)[:sat]` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].h[i] = [sat₁₆](Vuu.v[0].h[i]-`<br>`Vvv.v[0].h[i]);`<br>`Vdd.v[1].h[i] = [sat₁₆](Vuu.v[1].h[i]-`<br>`Vvv.v[1].h[i]);`<br>`}` |
| `Vdd.ub=vadd(Vuu.ub,Vvv.ub):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = `<br>`usat₈(Vuu.v[0].ub[i]+Vvv.v[0].ub[i]);`<br>`Vdd.v[1].ub[i] = `<br>`usat₈(Vuu.v[1].ub[i]+Vvv.v[1].ub[i]);`<br>`}` |
| `Vdd.ub=vsub(Vuu.ub,Vvv.ub):sat` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.v[0].ub[i] = usat₈(Vuu.v[0].ub[i]-`<br>`Vvv.v[0].ub[i]);`<br>`Vdd.v[1].ub[i] = usat₈(Vuu.v[1].ub[i]-`<br>`Vvv.v[1].ub[i]);`<br>`}` |
| `Vdd.uh=vadd(Vuu.uh,Vvv.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = usat₁₆(Vuu.v[0].uh[i]+ `<br>`Vvv.v[0].uh[i]);`<br>`Vdd.v[1].uh[i] = usat₁₆(Vuu.v[1].uh[i]+ `<br>`Vvv.v[1].uh[i]);`<br>`}` |
| `Vdd.uh=vsub(Vuu.uh,Vvv.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.v[0].uh[i] = usat₁₆(Vuu.v[0].uh[i]-`<br>`Vvv.v[0].uh[i]);`<br>`Vdd.v[1].uh[i] = usat₁₆(Vuu.v[1].uh[i]-`<br>`Vvv.v[1].uh[i]) ;`<br>`}` |
| `Vdd.uw=vadd(Vuu.uw,Vvv.uw):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = usat₃₂(Vuu.v[0].uw[i]+ `<br>`Vvv.v[0].uw[i]);`<br>`Vdd.v[1].uw[i] = usat₃₂(Vuu.v[1].uw[i]+ `<br>`Vvv.v[1].uw[i]) ;`<br>`}` |
| `Vdd.uw=vsub(Vuu.uw,Vvv.uw):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].uw[i] = usat₃₂(Vuu.v[0].uw[i]-`<br>`Vvv.v[0].uw[i]);`<br>`Vdd.v[1].uw[i] = usat₃₂(Vuu.v[1].uw[i]-`<br>`Vvv.v[1].uw[i]) ;`<br>`}` |
| `Vdd.w=vadd(Vuu.w,Vvv.w)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = [sat₃₂](Vuu.v[0].w[i]+ `<br>`Vvv.v[0].w[i]);`<br>`Vdd.v[1].w[i] = [sat₃₂](Vuu.v[1].w[i]+ `<br>`Vvv.v[1].w[i]) ;`<br>`}` |
| `Vdd.w=vsub(Vuu.w,Vvv.w)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vdd.v[0].w[i] = [sat₃₂](Vuu.v[0].w[i]-`<br>`Vvv.v[0].w[i]);`<br>`Vdd.v[1].w[i] = [sat₃₂](Vuu.v[1].w[i]-`<br>`Vvv.v[1].w[i]) ;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses any pair of the HVX resources (both multiply or shift/permute).

##### Intrinsics

|  |  |
|---|---|
| `Vdd.b=vadd(Vuu.b,Vvv.b)` | `HVX_VectorPair Q6_Wb_vadd_WbWb(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.b=vadd(Vuu.b,Vvv.b):sat` | `HVX_VectorPair Q6_Wb_vadd_WbWb_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.b=vsub(Vuu.b,Vvv.b)` | `HVX_VectorPair Q6_Wb_vsub_WbWb (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.b=vsub(Vuu.b,Vvv.b):sat` | `HVX_VectorPair Q6_Wb_vsub_WbWb_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.h=vadd(Vuu.h,Vvv.h)` | `HVX_VectorPair Q6_Wh_vadd_WhWh(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.h=vadd(Vuu.h,Vvv.h):sat` | `HVX_VectorPair Q6_Wh_vadd_WhWh_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.h=vsub(Vuu.h,Vvv.h)` | `HVX_VectorPair Q6_Wh_vsub_WhWh(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.h=vsub(Vuu.h,Vvv.h):sat` | `HVX_VectorPair Q6_Wh_vsub_WhWh_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.ub=vadd(Vuu.ub,Vvv.ub):sat` | `HVX_VectorPair Q6_Wub_vadd_WubWub_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.ub=vsub(Vuu.ub,Vvv.ub):sat` | `HVX_VectorPair Q6_Wub_vsub_WubWub_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.uh=vadd(Vuu.uh,Vvv.uh):sat` | `HVX_VectorPair Q6_Wuh_vadd_WuhWuh_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.uh=vsub(Vuu.uh,Vvv.uh):sat` | `HVX_VectorPair Q6_Wuh_vsub_WuhWuh_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.uw=vadd(Vuu.uw,Vvv.uw):sat` | `HVX_VectorPair Q6_Wuw_vadd_WuwWuw_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.uw=vsub(Vuu.uw,Vvv.uw):sat` | `HVX_VectorPair Q6_Wuw_vsub_WuwWuw_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.w=vadd(Vuu.w,Vvv.w)` | `HVX_VectorPair Q6_Ww_vadd_WwWw(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.w=vadd(Vuu.w,Vvv.w):sat` | `HVX_VectorPair Q6_Ww_vadd_WwWw_sat( HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.w=vsub(Vuu.w,Vvv.w)` | `HVX_VectorPair Q6_Ww_vsub_WwWw(HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |
| `Vdd.w=vsub(Vuu.w,Vvv.w):sat` | `HVX_VectorPair Q6_Ww_vsub_WwWw_sat (HVX_VectorPair Vuu, HVX_VectorPair Vvv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.b=vadd(Vuu.b,Vvv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.h=vadd(Vuu.h,Vvv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.w=vadd(Vuu.w,Vvv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.ub=vadd(Vuu.ub,Vvv.u b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.uh=vadd(Vuu.uh,Vvv.u h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.h=vadd(Vuu.h,Vvv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.w=vadd(Vuu.w,Vvv.w): sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.b=vsub(Vuu.b,Vvv.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.h=vsub(Vuu.h,Vvv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vdd.w=vsub(Vuu.w,Vvv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.ub=vsub(Vuu.ub,Vvv.u b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vdd.uh=vsub(Vuu.uh,Vvv.u h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.h=vsub(Vuu.h,Vvv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.w=vsub(Vuu.w,Vvv.w): sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.b=vadd(Vuu.b,Vvv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.b=vsub(Vuu.b,Vvv.b):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.uw=vadd(Vuu.uw,Vvv. uw):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.uw=vsub(Vuu.uw,Vvv.u w):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
