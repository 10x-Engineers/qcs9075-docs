## 11.8 ST

The ST instruction class includes store instructions, used to store values in memory.

ST instructions are executable on slot 0 and slot 1.

#### Store doubleword

Store a 64-bit register pair in memory at the effective address.

| Syntax | Behavior |
|---|---|
| `memd(Re=#U6)=Rtt` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Rtt;`<br>`Re=#U;` |
| `memd(Rs+#s11:3)=Rtt` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Rtt;` |
| `memd(Rs+Ru<<#u2)=Rtt` | `EA=Rs+(Ru<<#u);`<br>`*EA = Rtt;` |
| `memd(Ru<<#u2+#U6)=Rtt` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Rtt;` |
| `memd(Rx++#s4:3)=Rtt` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Rtt;` |
| `memd(Rx++#s4:3:circ(Mu))=Rtt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Rtt;` |
| `memd(Rx++I:circ(Mu))=Rtt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<3,MuV);`<br>`*EA = Rtt;` |
| `memd(Rx++Mu)=Rtt` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Rtt;` |
| `memd(Rx++Mu:brev)=Rtt` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Rtt;` |
| `memd(gp+#u16:3)=Rtt` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Rtt;` |

##### Class: ST (slots 0,1)

##### Intrinsics

|  |  |
|---|---|
| `memd(Rx++#s4:3:circ(Mu))=R` | `void Q6_memd_IMP_circ(void** StartAddress, Word32` |
| `tt` | `Is4_3, Word32 Mu, Word64 Rtt, void* BaseAddress)` |
| `memd(Rx++I:circ(Mu))=Rtt` | `void Q6_memd_MP_circ(void** StartAddress, Word32 Mu, Word64 Rtt, void* BaseAddress)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | t | t | t | t | t | memd(Rs+Ru<<#u2)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 1 | 1 | 0 | i | i | i | i | i | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memd(gp+#u16:3)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memd(Rs+#s11:3)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | 1 | - | memd(Rx++I:circ(Mu))=Rtt |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memd(Rx++#s4:3:circ(Mu))=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | e | e | e | e | e | P | P | 0 | t | t | t | t | t | 1 | - | I | I | I | I | I | I | memd(Re=#U6)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | 0 | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memd(Rx++#s4:3)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | u | u | u | u | u | P | P | i | t | t | t | t | t | 1 | i | I | I | I | I | I | I | memd(Ru<<#u2+#U6)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memd(Rx++Mu)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memd(Rx++Mu:brev)=Rtt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store-release doubleword

Store a 64-bit register pair in memory at the effective address. The store-release memory operation is observed after all preceding memory operations have been observed at the local point of serialization. A different order may be observed at the global point of serialization. (see Ordering and Synchronization).

When the :st (same domain) option is specified, the preceding memory operations are those that were committed on any thread with the same consistency domain before this instruction was committed.

When the :at (all threads) option is specified, the preceding memory operations are those that were committed on any thread before this instruction was committed.

The store release address is limited to certain memory regions. The following are excluded memory regions: AHB memory space, AXI M2 memory space, Hexagon memory cut-out is excluded with the exception of addressable TCM and VTCM memory, and memory with the CCCC types 2, 3, or 4 are excluded. The :st option does not apply to cache operation by index or global cache operation. The :st option does not apply a consistency domain to vector operations, but instead uses a per hardware thread ordering scope.

| Syntax | Behavior |
|---|---|
| `memd_rl(Rs):at=Rtt` | `EA=Rs;`<br>`*EA = Rtt` |
| `memd_rl(Rs):st=Rtt` | `EA=Rs;`<br>`*EA = Rtt` |

##### Class: ST (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  | d2 | d2 |  |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | s | s | s | s | s | P | P | 0 | t | t | t | t | t | - | - | 0 | 0 | 1 | 0 | d | d | memd_rl(Rs):at=Rtt |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | s | s | s | s | s | P | P | 0 | t | t | t | t | t | - | - | 1 | 0 | 1 | 0 | d | d | memd_rl(Rs):st=Rtt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `Amode` | Amode |
| `Type` | Type |
| `UN` | Unsigned |

#### Store doubleword conditionally

Store a 64-bit register pair in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memd(#u6)=Rtt` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rtt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memd(Rs+#u6:3)=Rtt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rtt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memd(Rs+Ru<<#u2)=Rtt` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rtt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memd(Rx++#s4:3)=Rtt` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Rtt;`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: ST (slots 0,1)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv) memd(Rs+Ru<<#u2)=Rtt |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv) memd(Rs+Ru<<#u2)=Rtt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv.new) memd(Rs+Ru<<#u2)=Rtt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv.new) memd(Rs+Ru<<#u2)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memd(Rs+#u6:3)=Rtt |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memd(Rs+#u6:3)=Rtt |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memd(Rs+#u6:3)=Rtt |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memd(Rs+#u6:3)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memd(Rx++#s4:3)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memd(Rx++#s4:3)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memd(Rx++#s4:3)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memd(Rx++#s4:3)=Rtt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memd(#u6)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memd(#u6)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memd(#u6)=Rtt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memd(#u6)=Rtt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store byte

Store the least-significant byte in a source register at the effective address.

| Syntax | Behavior |
|---|---|
| `memb(Re=#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Rt.b[0];`<br>`Re=#U;` |
| `memb(Rs+#s11:0)=Rt` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Rt.b[0];` |
| `memb(Rs+#u6:0)=#S8` | `EA=Rs+#u;`<br>`apply_extension(#S);`<br>`*EA = #S;` |
| `memb(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`*EA = Rt.b[0];` |
| `memb(Ru<<#u2+#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Rt.b[0];` |
| `memb(Rx++#s4:0)=Rt` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Rt.b[0];` |
| `memb(Rx++#s4:0:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Rt.b[0];` |
| `memb(Rx++I:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<0,MuV);`<br>`*EA = Rt.b[0];` |
| `memb(Rx++Mu)=Rt` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.b[0];` |
| `memb(Rx++Mu:brev)=Rt` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.b[0];` |
| `memb(gp+#u16:0)=Rt` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Rt.b[0];` |

##### Class: ST (slots 0,1)

##### Intrinsics

|  |  |
|---|---|
| `memb(Rx++#s4:0:circ(Mu))=` | `void Q6_memb_IMR_circ(void** StartAddress, Word32` |
| `Rt` | `Is4_0, Word32 Mu, Word32 Rt, void* BaseAddress)` |
| `memb(Rx++I:circ(Mu))=Rt` | `void Q6_memb_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void* BaseAddress)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | t | t | t | t | t | memb(Rs+Ru<<#u2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | I | I | I | I | I | I | I | memb(Rs+#u6:0)=#S8 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 0 | 0 | 0 | i | i | i | i | i | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memb(gp+#u16:0)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memb(Rs+#s11:0)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | 1 | - | memb(Rx++I:circ(Mu))=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memb(Rx++#s4:0:circ(Mu))=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | e | e | e | e | e | P | P | 0 | t | t | t | t | t | 1 | - | I | I | I | I | I | I | memb(Re=#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | 0 | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memb(Rx++#s4:0)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | u | u | u | u | u | P | P | i | t | t | t | t | t | 1 | i | I | I | I | I | I | I | memb(Ru<<#u2+#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memb(Rx++Mu)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memb(Rx++Mu:brev)=Rt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store byte conditionally

Store the least-significant byte in a source register at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memb(#u6)=Rt` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memb(Rs+#u6:0)=#S6` | `EA=Rs+#u;`<br>`if ([!]Pv[.new][0]){`<br>`apply_extension(#S);`<br>`*EA = #S;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memb(Rs+#u6:0)=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memb(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memb(Rx++#s4:0)=Rt` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Rt.b[0];`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: ST (slots 0,1)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv) memb(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv) memb(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv.new) memb(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv.new) memb(Rs+Ru<<#u2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv) memb(Rs+#u6:0)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv) memb(Rs+#u6:0)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv.new) memb(Rs+#u6:0)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv.new) memb(Rs+#u6:0)=#S6 |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memb(Rs+#u6:0)=Rt |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memb(Rs+#u6:0)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memb(Rs+#u6:0)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memb(Rs+#u6:0)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memb(Rx++#s4:0)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memb(Rx++#s4:0)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memb(Rx++#s4:0)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memb(Rx++#s4:0)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memb(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memb(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memb(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memb(#u6)=Rt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| Field name | Description |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store halfword

Store the upper or lower 16-bits of a source register at the effective address.

| Syntax | Behavior |
|---|---|
| `memh(Re=#U6)=Rt.H` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Rt.h[1];`<br>`Re=#U;` |
| `memh(Re=#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Rt.h[0];`<br>`Re=#U;` |
| `memh(Rs+#s11:1)=Rt.H` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Rt.h[1];` |
| `memh(Rs+#s11:1)=Rt` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Rt.h[0];` |
| `memh(Rs+#u6:1)=#S8` | `EA=Rs+#u;`<br>`apply_extension(#S);`<br>`*EA = #S;` |
| `memh(Rs+Ru<<#u2)=Rt.H` | `EA=Rs+(Ru<<#u);`<br>`*EA = Rt.h[1];` |
| `memh(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`*EA = Rt.h[0];` |
| `memh(Ru<<#u2+#U6)=Rt.H` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Rt.h[1];` |
| `memh(Ru<<#u2+#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Rt.h[0];` |
| `memh(Rx++#s4:1)=Rt.H` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Rt.h[1];` |
| `memh(Rx++#s4:1)=Rt` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Rt.h[0];` |
| `memh(Rx++#s4:1:circ(Mu))=Rt.`<br>`H` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Rt.h[1];` |
| `memh(Rx++#s4:1:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Rt.h[0];` |
| `memh(Rx++I:circ(Mu))=Rt.H` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<1,MuV);`<br>`*EA = Rt.h[1];` |
| `memh(Rx++I:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<1,MuV);`<br>`*EA = Rt.h[0];` |
| `memh(Rx++Mu)=Rt.H` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.h[1];` |
| `memh(Rx++Mu)=Rt` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.h[0];` |
| `memh(Rx++Mu:brev)=Rt.H` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.h[1];` |
| `memh(Rx++Mu:brev)=Rt` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Rt.h[0];` |
| `memh(gp+#u16:1)=Rt.H` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Rt.h[1];` |
| `memh(gp+#u16:1)=Rt` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Rt.h[0];` |

##### Class: ST (slots 0,1)

##### Intrinsics

|  |  |
|---|---|
| `memh(Rx++#s4:1:circ(Mu))=Rt.` | `void Q6_memh_IMRh_circ(void** StartAddress, Word32` |
| `H` | `Is4_1, Word32 Mu, Word32 Rt, void* BaseAddress)` |
| `memh(Rx++#s4:1:circ(Mu))=Rt` | `void Q6_memh_IMR_circ(void** StartAddress, Word32 Is4_1, Word32 Mu, Word32 Rt, void* BaseAddress)` |
| `memh(Rx++I:circ(Mu))=Rt.H` | `void Q6_memh_MRh_circ(void** StartAddress, Word32 Mu, Word32 Rt, void* BaseAddress)` |
| `memh(Rx++I:circ(Mu))=Rt` | `void Q6_memh_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void* BaseAddress)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 15 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | t | t | t | t | t | memh(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | t | t | t | t | t | memh(Rs+Ru<<#u2)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | 1 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | I | I | I | I | I | I | I | memh(Rs+#u6:1)=#S8 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 0 | 1 | 0 | i | i | i | i | i | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memh(gp+#u16:1)=Rt |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 0 | 1 | 1 | i | i | i | i | i | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memh(gp+#u16:1)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memh(Rs+#s11:1)=Rt |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memh(Rs+#s11:1)=Rt.H |

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | 1 | - | memh(Rx++I:circ(Mu))=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1:circ(Mu))=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | 1 | - | memh(Rx++I:circ(Mu))=Rt. H |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1:circ(Mu))=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | e | e | e | e | e | P | P | 0 | t | t | t | t | t | 1 | - | I | I | I | I | I | I | memh(Re=#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | 0 | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | e | e | e | e | e | P | P | 0 | t | t | t | t | t | 1 | - | I | I | I | I | I | I | memh(Re=#U6)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | 0 | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | u | u | u | u | u | P | P | i | t | t | t | t | t | 1 | i | I | I | I | I | I | I | memh(Ru<<#u2+#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | u | u | u | u | u | P | P | i | t | t | t | t | t | 1 | i | I | I | I | I | I | I | memh(Ru<<#u2+#U6)=Rt. H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu:brev)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu:brev)=Rt.H |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store halfword conditionally

Store the upper or lower 16-bits of a source register in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memh(#u6)=Rt.H` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[1];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(#u6)=Rt` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rs+#u6:1)=#S6` | `EA=Rs+#u;`<br>`if ([!]Pv[.new][0]){`<br>`apply_extension(#S);`<br>`*EA = #S;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rs+#u6:1)=Rt.H` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[1];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rs+#u6:1)=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memh(Rs+Ru<<#u2)=Rt.H` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[1];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt.h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rx++#s4:1)=Rt.H` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Rt.h[1];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memh(Rx++#s4:1)=Rt` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Rt.h[0];`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: ST (slots 0,1)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv) memh(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv) memh(Rs+Ru<<#u2)=Rt.H |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv) memh(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv) memh(Rs+Ru<<#u2)=Rt.H |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv.new) memh(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv.new) memh(Rs+Ru<<#u2)=Rt.H |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv.new) memh(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv.new) memh(Rs+Ru<<#u2)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv) memh(Rs+#u6:1)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv) memh(Rs+#u6:1)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv.new) memh(Rs+#u6:1)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv.new) memh(Rs+#u6:1)=#S6 |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memh(Rs+#u6:1)=Rt |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memh(Rs+#u6:1)=Rt.H |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rs+#u6:1)=Rt |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rs+#u6:1)=Rt.H |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memh(Rs+#u6:1)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memh(Rs+#u6:1)=Rt.H |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memh(Rs+#u6:1)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memh(Rs+#u6:1)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memh(Rx++#s4:1)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memh(Rx++#s4:1)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rx++#s4:1)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(Rx++#s4:1)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memh(Rx++#s4:1)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memh(Rx++#s4:1)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rx++#s4:1)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(Rx++#s4:1)=Rt.H |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memh(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memh(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memh(#u6)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memh(#u6)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(#u6)=Rt.H |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(#u6)=Rt.H |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| Field name | Description |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Release

The release memory operation is observed after all preceding memory operations have been observed at the local point of serialization. A different order can be observed at the global point of serialization (see Ordering and Synchronization). No data is modified by this instruction.

When the :st (same domain) option is specified, the preceding memory operations are those that were committed on any thread with the same consistency domain before this instruction was committed.

When the :at (all threads) option is specified, the preceding memory operations are those that were committed on any thread before this instruction was committed.

The store release address is limited to certain memory regions. The following memory regions are excluded:

- AHB memory space
- AXI M2 memory space
- Hexagon memory cut-out is excluded with the exception of addressable TCM and VTCM memory
- Memory with the CCCC types 2, 3, or 4

The :st option does not apply to cache operation by index or global cache operation. The :stoption does not apply a consistency domain to vector operations, but instead uses a per hardware thread ordering scope.

| Syntax | Behavior |
|---|---|
| `release(Rs):at` | `EA=Rs;`<br>`*EA = Rs` |
| `release(Rs):st` | `EA=Rs;`<br>`*EA = Rs` |

##### Class: ST (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  | d2 | d2 |  |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | s | s | s | s | s | P | P | 0 | t | t | t | t | t | - | - | 0 | 0 | 1 | 1 | d | d | release(Rs):at |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | s | s | s | s | s | P | P | 0 | t | t | t | t | t | - | - | 1 | 0 | 1 | 1 | d | d | release(Rs):st |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `Amode` | Amode |
| `Type` | Type |
| `UN` | Unsigned |

#### Store word

Store a 32-bit register in memory at the effective address.

| Syntax | Behavior |
|---|---|
| `memw(Re=#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Rt;`<br>`Re=#U;` |
| `memw(Rs+#s11:2)=Rt` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Rt;` |
| `memw(Rs+#u6:2)=#S8` | `EA=Rs+#u;`<br>`apply_extension(#S);`<br>`*EA = #S;` |
| `memw(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`*EA = Rt;` |
| `memw(Ru<<#u2+#U6)=Rt` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Rt;` |
| `memw(Rx++#s4:2)=Rt` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Rt;` |
| `memw(Rx++#s4:2:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Rt;` |
| `memw(Rx++I:circ(Mu))=Rt` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<2,MuV);`<br>`*EA = Rt;` |
| `memw(Rx++Mu)=Rt` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Rt;` |
| `memw(Rx++Mu:brev)=Rt` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Rt;` |
| `memw(gp+#u16:2)=Rt` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Rt;` |

##### Class: ST (slots 0,1)

##### Intrinsics

|  |  |
|---|---|
| `memw(Rx++#s4:2:circ(Mu))=` | `void Q6_memw_IMR_circ(void** StartAddress, Word32` |
| `Rt` | `Is4_2, Word32 Mu, Word32 Rt, void* BaseAddress)` |
| `memw(Rx++I:circ(Mu))=Rt` | `void Q6_memw_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void* BaseAddress)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | t | t | t | t | t | memw(Rs+Ru<<#u2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 1 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | I | I | I | I | I | I | I | memw(Rs+#u6:2)=#S8 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 1 | 0 | 0 | i | i | i | i | i | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memw(gp+#u16:2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | i | i | i | memw(Rs+#s11:2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | 1 | - | memw(Rx++I:circ(Mu))=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memw(Rx++#s4:2:circ(Mu))=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | e | e | e | e | e | P | P | 0 | t | t | t | t | t | 1 | - | I | I | I | I | I | I | memw(Re=#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | 0 | t | t | t | t | t | 0 | i | i | i | i | - | 0 | - | memw(Rx++#s4:2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | u | u | u | u | u | P | P | i | t | t | t | t | t | 1 | i | I | I | I | I | I | I | memw(Ru<<#u2+#U6)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memw(Rx++Mu)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | t | t | t | t | t | 0 | - | - | - | - | - | - | - | memw(Rx++Mu:brev)=Rt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store-release word

Store a 32-bit register in memory at the effective address. The store-release memory operation is observed after all preceding memory operations have been observed at the local point of serialization. A different order can be observed at the global point of serialization (see Ordering and Synchronization).

When the :st (same domain) option is specified, the preceding memory operations are those that were committed on any thread with the same consistency domain before this instruction was committed.

When the :at (all threads) option is specified, the preceding memory operations are those that were committed on any thread before this instruction was committed.

The store release address is limited to certain memory regions. The following are excluded memory regions: AHB memory space, AXI M2 memory space, Hexagon memory cut-out is excluded with the exception of addressable TCM and VTCM memory, and memory with the CCCC types 2, 3, or 4 are excluded. The :st option does not apply to cache operation by index or global cache operation. The :st option does not apply a consistency domain to vector operations, but instead uses a per hardware thread ordering scope.

| Syntax | Behavior |
|---|---|
| `memw_rl(Rs):at=Rt` | `EA=Rs;`<br>`*EA = Rt` |
| `memw_rl(Rs):st=Rt` | `EA=Rs;`<br>`*EA = Rt` |

##### Class: ST (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  | d2 | d2 |  |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | - | t | t | t | t | t | - | - | 0 | 0 | 1 | 0 | d | d | memw_rl(Rs):at=Rt |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | - | t | t | t | t | t | - | - | 1 | 0 | 1 | 0 | d | d | memw_rl(Rs):st=Rt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d2` | Field to encode register d |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `Amode` | Amode |
| `Type` | Type |
| `UN` | Unsigned |

#### Store word conditionally

Store a 32-bit register in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memw(#u6)=Rt` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memw(Rs+#u6:2)=#S6` | `EA=Rs+#u;`<br>`if ([!]Pv[.new][0]){`<br>`apply_extension(#S);`<br>`*EA = #S;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memw(Rs+#u6:2)=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memw(Rs+Ru<<#u2)=Rt` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Rt;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) memw(Rx++#s4:2)=Rt` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Rt;`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: ST (slots 0,1)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv) memw(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv) memw(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (Pv.new) memw(Rs+Ru<<#u2)=Rt |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | t | t | t | t | t | if (!Pv.new) memw(Rs+Ru<<#u2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv) memw(Rs+#u6:2)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv) memw(Rs+#u6:2)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (Pv.new) memw(Rs+#u6:2)=#S6 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | s | s | s | s | s | P | P | I | i | i | i | i | i | i | v | v | I | I | I | I | I | if (!Pv.new) memw(Rs+#u6:2)=#S6 |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memw(Rs+#u6:2)=Rt |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memw(Rs+#u6:2)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memw(Rs+#u6:2)=Rt |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | i | t | t | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memw(Rs+#u6:2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memw(Rx++#s4:2)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memw(Rx++#s4:2)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memw(Rx++#s4:2)=Rt |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memw(Rx++#s4:2)=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memw(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | - | - | - | i | i | P | P | 0 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memw(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memw(#u6)=Rt |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | - | - | - | i | i | P | P | 1 | t | t | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memw(#u6)=Rt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| Field name | Description |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Allocate stack frame

Allocate a stack frame on the call stack. This instruction first pushes LR and FP to the top of stack. It then subtracts an unsigned immediate from SP to allocate room for local variables. FP is set to the address of the old frame pointer on the stack.

The following figure shows the stack layout.

Stack in memory

Saved LR

Saved FP

Higher address

Procedure local data on stack

Stack frame

Saved LR

Saved FP FP register

Procedure local data on stack

SP register

Lower address

Unallocated stack

| Syntax | Behavior |
|---|---|
| `allocframe(#u11:3)` | `Assembler mapped to: `<br>`"allocframe(r29,#u11:3):raw"` |
| `allocframe(Rx,#u11:3):raw` | `EA=Rx+-8;`<br>`*EA = frame_scramble((LR << 32) \| FP);`<br>`FP=EA;`<br>`frame_check_limit(EA-#u);`<br>`Rx = EA-#u;` |

##### Class: ST (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | x | x | x | x | x | P | P | 0 | 0 | 0 | i | i | i | i | i | i | i | i | i | i | i | allocframe(Rx,#u11:3):raw |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `Type` | Type |
| `UN` | Unsigned |
