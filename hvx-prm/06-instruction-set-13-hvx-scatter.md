## 6.13 HVX SCATTER

The HVX SCATTER instruction subclass includes instructions that perform scatter operations to

the vector TCM.

#### Vector scatter

Scatter operations copy values from the register file to a region in VTCM. Two scalar registers specify this region of memory: Rt32 is the base and Mu2 specified the length-1 of the region in bytes. This region must reside in VTCM and cannot cross a page boundary. A vector register, Vv32, specifies byte offsets in this region. Elements of either halfword or word granularity, specified by Vw32, are sent to addresses pointed to by Rt + Vv32 for each element. In the memory, the element is either write to memory or accumulated with the memory (scatter-accumulate).

If multiple values are written to the same memory location, ordering is not guaranteed.

The offset vector, Vv32, can contain byte offsets specified in either halfword or word sizes. The final element addresses do not have to be byte aligned for regular scatter operations. However, for scatter accumulate instructions, the addresses are aligned. If an offset crosses the end of the scatter region, it is dropped. Offsets must be positive, otherwise they are dropped.

Vectors registers can be used immediately after the scatter operation.

vscatter(Rt,Mu,Vv.h)=Vw.h

|  |  |
|---|---|
| Rt – Scalar Indicating base address in VTCM | Vv – Vector with byte offsets from baseVw – Vector with halfword elements to be |
| Mu – Scalar indicating length-1 of Region | scattered |

Example of vscatter (only first 4 elements shown)

Rt+Mu

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | ... | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| ... | ... | ... | ... | Region End | Region End | Vw.h [2] | Vw.h [2] |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
| ... | ... | ... | ... |  |  |  |  |  |  |  | Vw.h [3] |  |  |  |  |  |  |  |  |  | ... |
|  | ... | ... |  |  |  |  |  |  |  |  |  | Vw.h [1] |  |  |  |  |  |  |  |  | ... |
|  | ... | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
|  | ... | ... |  | *(Rt+Vv.h[2])=Vw.h[2] |  | *(Rt+Vv.h[3])=Vw.h[3] | *(Rt+Vv.h[3])=Vw.h[3] |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
|  | ... |  |  |  |  |  |  |  | *(Rt+Vv.h[1]) = Vw.h[1] |  |  |  | Vw.h [0] |  | Region Base | Region Base |  |  |  |  | ... |
|  | ... | ... |  |  |  |  |  |  |  | *(Rt+Vv.h[0]) = Vw.h[0] |  |  |  |  |  |  |  |  | ... | ... | VTCM Base |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Scatter VTCM Region

Rt

|  |  |  |  |
|---|---|---|---|
| h3 | h2 | h1 | h0 |

Vw.hoffset3offset2offset1offset0 Vv.h

|  |  |  |  |
|---|---|---|---|
| offset3 | offset2 | offset1 | offset0 |

h3 h2 h1 h0 Vw.h Vv.h

|  |  |
|---|---|
| Values to Scatter | Byte Offsets from Rt |
| Syntax | Behavior |

|  |  |
|---|---|
| `if (Qs4) `<br>`vscatter(Rt,Mu,Vv.h).h=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`EA = Rt+Vv.uh[i];`<br>`if ( (Rt <= EA <= Rt + MuV) & QsV) *EA = `<br>`VwV.uh[i];`<br>`}` |
| `if (Qs4) `<br>`vscatter(Rt,Mu,Vv.h)=Vw32.h` | `Assembler mapped to: "if (Qs4) `<br>`vscatter(Rt,Mu2,Vv.h).h=Vw32"` |
| `if (Qs4) `<br>`vscatter(Rt,Mu,Vv.w).w=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>`EA = Rt+Vv.uw[i];`<br>`if ( (Rt <= EA <= Rt + MuV) & QsV) *EA = `<br>`VwV.uw[i];`<br>`}` |
| `if (Qs4) `<br>`vscatter(Rt,Mu,Vv.w)=Vw32.w` | `Assembler mapped to: "if (Qs4) `<br>`vscatter(Rt,Mu2,Vv.w).w=Vw32"` |
| `vscatter(Rt,Mu,Vv.h)+=Vw32.h` | `Assembler mapped to: `<br>`"vscatter(Rt,Mu2,Vv.h).h+=Vw32"` |
| `vscatter(Rt,Mu,Vv.h).h+=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`EA = (Rt+Vv.uh[i] = Vv.uh[i] & ~(ALIGNMENT-`<br>`1));`<br>`if (Rt <= EA <= Rt + MuV) *EA += VwV.uh[i];`<br>`}` |
| `vscatter(Rt,Mu,Vv.h).h=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`EA = Rt+Vv.uh[i];`<br>`if (Rt <= EA <= Rt + MuV) *EA = VwV.uh[i];`<br>`}` |
| `vscatter(Rt,Mu,Vv.h)=Vw32.h` | `Assembler mapped to: `<br>`"vscatter(Rt,Mu2,Vv.h).h=Vw32"` |
| `vscatter(Rt,Mu,Vv.w)+=Vw32.w` | `Assembler mapped to: `<br>`"vscatter(Rt,Mu2,Vv.w).w+=Vw32"` |
| `vscatter(Rt,Mu,Vv.w).w+=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>`EA = (Rt+Vv.uw[i] = Vv.uw[i] & ~(ALIGNMENT-`<br>`1));`<br>`if (Rt <= EA <= Rt + MuV) *EA += VwV.uw[i];`<br>`}` |
| `vscatter(Rt,Mu,Vv.w).w=Vw32` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>`EA = Rt+Vv.uw[i];`<br>`if (Rt <= EA <= Rt + MuV) *EA = VwV.uw[i];`<br>`}` |

| Syntax | Behavior |
|---|---|
| `vscatter(Rt,Mu,Vv.w)=Vw32.w` | `Assembler mapped to: `<br>`"vscatter(Rt,Mu2,Vv.w).w=Vw32"` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction can use any HVX resource.
- ECC is not supported for scatter and gather instructions. Enabling ECC with unprotected access instructions result in undetermined behavior.

##### Intrinsics

|  |  |
|---|---|
| `if (Qs4)` | `void Q6_vscatter_QRMVhV(HVX_VectorPred Qs,` |
| `vscatter(Rt,Mu,Vv.h).h=Vw32` | `HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |
| `if (Qs4)` | `void Q6_vscatter_QRMVwV(HVX_VectorPred Qs,` |
| `vscatter(Rt,Mu,Vv.w).w=Vw32` | `HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |
| `vscatter(Rt,Mu,Vv.h).h+=Vw32` | `void Q6_vscatteracc_RMVhV(HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |
| `vscatter(Rt,Mu,Vv.h).h=Vw32` | `void Q6_vscatter_RMVhV(HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |
| `vscatter(Rt,Mu,Vv.w).w+=Vw32` | `void Q6_vscatteracc_RMVwV(HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |
| `vscatter(Rt,Mu,Vv.w).w=Vw32` | `void Q6_vscatter_RMVwV(HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv, HVX_Vector Vw)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | u | v | v | v | v | v | 0 | 0 | 0 | w | w | w | w | w | vscatter(Rt,Mu,Vv.w).w=Vw 32 |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | u | v | v | v | v | v | 0 | 0 | 1 | w | w | w | w | w | vscatter(Rt,Mu,Vv.h).h=Vw 32 |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | u | v | v | v | v | v | 1 | 0 | 0 | w | w | w | w | w | vscatter(Rt,Mu,Vv.w).w+=V w32 |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | t | t | t | t | t | P | P | u | v | v | v | v | v | 1 | 0 | 1 | w | w | w | w | w | vscatter(Rt,Mu,Vv.h).h+=V w32 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  | s2 | s2 |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | u | v | v | v | v | v | 0 | s | s | w | w | w | w | w | if (Qs4) vscatter(Rt,Mu,Vv.w).w=Vw 32 |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | u | v | v | v | v | v | 1 | s | s | w | w | w | w | w | if (Qs4) vscatter(Rt,Mu,Vv.h).h=Vw 32 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s2` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v5` | Field to encode register v |
