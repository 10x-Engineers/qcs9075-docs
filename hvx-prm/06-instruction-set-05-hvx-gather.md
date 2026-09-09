## 6.5 HVX GATHER

The HVX GATHER instruction subclass performs gather operations in the vector TCM.

#### Vector gather

Gather operations are effectively element copies from a large region in VTCM to a smaller vector-sized region. The larger region of memory is specified by two scalar registers: Rt32 is the base and Mu2 specified the length-1 of the region in bytes. This region must reside in VTCM and cannot cross a page boundary. A vector register, Vv32, specifies byte offsets to this region. Elements of either halfword or word granularity are copied from the address pointed to by Rt + Vv32 for each element in the vector to the corresponding element in the linear element pointed to by the accompanying store.

The offset vector, Vv32, can contain byte offsets specified in either halfword or word sizes. The final element addresses do not have to be byte aligned. If an offset crosses the end of the gather region, it is dropped. Offsets must be positive, otherwise they are dropped. A vector predicate register can also be specified. If a the predicate is false, that byte is not copied. This can be used to emulate a byte gather.

The gather instruction must be paired with a VMEM .new store that uses a temporary register source. For example, { VMEM(R0+#0) = Vtmp.new; Vtmp.h = vgather(R1,M0, V0.h); } gathers halfwords with halfword addresses and saves the results to the address pointed to by R0 of the VMEM instruction. A `vgather` operation that is not accompanied with a store is dropped.

{ vmem(Rs+#I)=Vtmp.h; vtmp.h = vgather(Rt,Mu,Vv.h) }

Rs – Address of gathered values in VTCM Rt – Scalar Indicating base address in VTCM

Mu – Scalar indicating length-1 of Region

Vv – Vector with byte offsets from base

Rt+Mu Example of vgather (only first 4 elements shown)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| ... | ... | Region End | Region End |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
| ... | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
| ... | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | ... |
| ... | ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  | *(Rs+2) = *(Rt+Vv.h[1]) |  |  |  |  | ... |
| ... | ... |  |  |  |  |  |  |  |  |  |  | *(Rs+4)=*(Rt+Vv.h[2]) |  |  |  |  |  |  |  | *(Rs+0) = *(Rt+Vv.h[0]) | ... |
| ... |  |  |  |  |  |  |  |  |  |  |  | *(Rs+4)=*(Rt+Vv.h[2]) |  | Region Base | Region Base |  |  |  |  |  | ... |
| ... | ... |  |  |  |  |  |  |  | *(Rs+6)=*(Rt+Vv.h[3]) | *(Rs+6)=*(Rt+Vv.h[3]) |  |  |  |  |  |  |  |  |  |  | ... |
| ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| ... |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | VTCM Base |

Scatter VTCM Region

Gather

Results

at address Rs

Rt

| Syntax | Behavior |
|---|---|
| `if (Qs4) vtmp.h = vgather(Rt, `<br>`Mu, Vv.h).h` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(16); i++) {`<br>` EA = Rt+Vv.uh[i];`<br>` if((Rt<=EA<= Rt + MuV)& QsV)TEMP.uh[i] = *EA;`<br>`}` |
| `if (Qs4) vtmp.w = vgather(Rt, `<br>`Mu, Vv.w).w` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>` EA = Rt+Vv.uw[i];`<br>` if((Rt<=EA<= Rt + MuV)& QsV)TEMP.uw[i] = *EA;`<br>`}` |
| `vtmp.h=vgather(Rt,Mu,Vv.h).h` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(16); i++) {`<br>` EA = Rt+Vv.uh[i];`<br>` if (Rt <= EA <= Rt + MuV) TEMP.uh[i] = *EA;`<br>`}` |
| `vtmp.w=vgather(Rt,Mu,Vv.w).w` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>` EA = Rt+Vv.uw[i];`<br>` if (Rt <= EA <= Rt + MuV) TEMP.uw[i] = *EA;`<br>`}` |

##### Class: COPROC_VMEM (slots 0,1)

##### Notes

- This instruction can use any HVX resource.
- Scatter and gather instructions do not support error correcting code (ECC). Enabling ECC with unprotected access instructions results in undetermined behavior.

##### Intrinsics

|  |  |
|---|---|
| `if (Qs4) vtmp.h = vgather(Rt,` | `void Q6_vgather_AQRMVh(HVX_Vector* A,` |
| `Mu, Vv.h).h` | `HVX_VectorPred Qs, HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv)` |
| `if (Qs4) vtmp.w = vgather(Rt,` | `void Q6_vgather_AQRMVw(HVX_Vector* A,` |
| `Mu, Vv.w).w` | `HVX_VectorPred Qs, HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv)` |
| `vtmp.h=vgather(Rt,Mu,Vv.h).h` | `void Q6_vgather_ARMVh(HVX_Vector* A, HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv)` |
| `vtmp.w=vgather(Rt,Mu,Vv.w).w` | `void Q6_vgather_ARMVw(HVX_Vector* A, HVX_Vector* Rb, Word32 Mu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 0 | 0 | 0 | - | - | - | v | v | v | v | v | vtmp.w = vgather(Rt,Mu, Vv.w).w |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 0 | 0 | 1 | - | - | - | v | v | v | v | v | vtmp.h= vgather(Rt,Mu, Vv.h).h |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  | s2 | s2 |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 1 | 0 | 0 | - | s | s | v | v | v | v | v | if (Qs4) vtmp.w= vgather(Rt,Mu, Vv.w).w |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 1 | 0 | 1 | - | s | s | v | v | v | v | v | if (Qs4) vtmp.h= vgather(Rt,Mu, Vv.h).h |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s2` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v5` | Field to encode register v |
