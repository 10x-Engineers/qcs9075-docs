## 6.6 HVX GATHER DOUBLE RESOURCE

The following instruction subclass performs gather operations in the vector TCM.

#### Vector gather

Gather operations are effectively element copies from a large region in VTCM to a smaller vector-sized region. The larger region of memory is specified by two scalar registers: Rt32 is the base and Mu2 specified the length-1 of the region in bytes. This region must reside in VTCM and cannot cross a page boundary. A vector register, Vv32, specifies byte offsets to this region. Elements of either halfword or word granularity are copied from the address pointed to by Rt + Vv32 for each element in the vector to the corresponding element in the linear element pointed to by the accompanying store.

The offset vector, Vv32, can contain byte offsets specified in either halfword or word sizes. The final element addresses do not have to be byte aligned. If an offset crosses the end of the gather region, it is dropped. Offsets must be positive, otherwise they are dropped. A vector predicate register can also be specified. If a the predicate is false, that byte is not copied. This can emulate a byte gather.

The gather instruction must be paired with a VMEM .new store that uses a tmp register source. Example: {VMEM(R0+#0) = Vtmp.new; Vtmp.h = vgather(R1, M0, V1:0.w);} gathers halfwords with halfword addresses and saves the results to the address pointed to by R0 of the VMEM instruction. A `vgather` that is not accompanied with a store is dropped.

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
| `if (Qs4) vtmp.h = vgather(Rt, `<br>`Mu, Vvv.w).h` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>` for(j = 0; j < 2; j++) {`<br>` EA = Rt+Vvv.v[j].uw[i];`<br>` if ((Rt <= EA <= Rt + MuV) & QsV)`<br>` TEMP.uw[i].uh[j] = *EA;`<br>` }`<br>`}` |
| `vtmp.h = vgather(Rt, Mu, `<br>`Vvv.w).h` | `MuV = MuV \| (element_size-1);`<br>`Rt = Rt & ~(element_size-1);`<br>`for (i = 0; i < VELEM(32); i++) {`<br>` for(j = 0; j < 2; j++) {`<br>` EA = Rt+Vvv.v[j].uw[i];`<br>` if (Rt <= EA <= Rt + MuV) `<br>` TEMP.uw[i].uh[j] = *EA;`<br>` }}` |

##### Class: COPROC_VMEM (slots 0,1)

##### Notes

- This instruction can use any HVX resource.
- ECC is not supported for scatter and gather instructions. Enabling ECC with unprotected access instructions results in undetermined behavior.

##### Intrinsics

|  |  |
|---|---|
| `if (Qs4) vtmp.h =` | `void Q6_vgather_AQRMWw(HVX_Vector* A,` |
| `vgather(Rt, Mu, Vvv.w).h` | `HVX_VectorPred Qs, HVX_Vector* Rb, Word32 Mu, HVX_VectorPair Vvv)` |
| `vtmp.h = vgather(Rt, Mu,` | `void Q6_vgather_ARMWw(HVX_Vector* A, HVX_Vector*` |
| `Vvv.w).h` | `Rb, Word32 Mu, HVX_VectorPair Vvv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  |  |  |  |  |  | [#6] vgather,vscatter |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 0 | 1 | 0 | - | - | - | v | v | v | v | v | vtmp.h = vgather(Rt, Mu, Vvv.w).h |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse | u1 |  |  |  |  |  |  | s2 | s2 |  |  |  |  |  | [#6] vgather,vscatter |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | t | t | t | t | t | P | P | u | - | - | 1 | 1 | 0 | - | s | s | v | v | v | v | v | if (Qs4) vtmp.h = vgather(Rt, Mu, Vvv.w).h |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s2` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v5` | Field to encode register v |
