## 6.15 HVX STORE

The HVX STORE instruction subclass includes memory store instructions.

#### Store byte-enabled aligned

Of the bytes in vector register Vs, store to memory only those where the corresponding bit in the predicate register Qv is enabled. The block of memory to store into is at a vector-size-aligned address.

The operation has three ways to generate the memory pointer address:

- Rt with a constant 4-bit signed offset
- Rx with a signed post-increment
- Rx with a modifier register Mu post-increment

For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

If all bits in Qv are set to zero, no data is stored to memory, but the post-increment of the pointer in Rt occurs.

If the pointer presented to the instruction is not aligned, the instruction ignores the lower bits, yielding an aligned address.

If (Qv4) vmem(Rt) = Vs

|  |  |  |  |  |
|---|---|---|---|---|
| [N-1] | ... | [2] | [1] | [0] |

Vs.b

|  |  |
|---|---|
| En | Qv.b[0] |
| En | Qv.b[1] |
| En | Qv.b[2] |

En Qv.b[N-1]

MEMORY

| Syntax | Behavior |
|---|---|
| `if ([!]Qv4) vmem(Rt):nt=Vs` | `Assembler mapped to: "if ([!]Qv4) `<br>`vmem(Rt+#0):nt=Vs"` |
| `if ([!]Qv4) vmem(Rt)=Vs` | `Assembler mapped to: "if ([!]Qv4) vmem(Rt+#0)=Vs"` |
| `if ([!]Qv4) `<br>`vmem(Rt+#s4):nt=Vs` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;` |
| `if ([!]Qv4) vmem(Rt+#s4)=Vs` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;` |
| `if ([!]Qv4) `<br>`vmem(Rx++#s3):nt=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;` |
| `if ([!]Qv4) vmem(Rx++#s3)=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;` |
| `if ([!]Qv4) `<br>`vmem(Rx++Mu):nt=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;` |
| `if ([!]Qv4) vmem(Rx++Mu)=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate the data has no reuse.
- Immediates used in address computation are specified in multiples of vector length.

##### Intrinsics

|  |  |
|---|---|
| `if (!Qv4) vmem(Rt+#s4):nt=Vs` | `void Q6_vmem_QnRIV_nt(HVX_VectorPred Qv, HVX_Vector* A, HVX_Vector Vs)` |
| `if (!Qv4) vmem(Rt+#s4)=Vs` | `void Q6_vmem_QnRIV(HVX_VectorPred Qv, HVX_Vector* A, HVX_Vector Vs)` |
| `if (Qv4) vmem(Rt+#s4):nt=Vs` | `void Q6_vmem_QRIV_nt(HVX_VectorPred Qv, HVX_Vector* A, HVX_Vector Vs)` |
| `if (Qv4) vmem(Rt+#s4)=Vs` | `void Q6_vmem_QRIV(HVX_VectorPred Qv, HVX_Vector* A, HVX_Vector Vs)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 15 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rt+#s4):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rt+#s4):nt=Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rx++#s3):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rx++#s3):nt=Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 0 | s | s | s | s | s | if (Qv4) vmem(Rx++Mu):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 1 | s | s | s | s | s | if (!Qv4) vmem(Rx++Mu):nt=Vs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Store new

Store the result of an operation in the current packet to memory, using a vector-aligned address. The result is also written to the vector register file at the vector register location.

For example, in the instruction vmem(R8++#1) = V12.new, the value in V12 in this packet is written to memory, and V12 is also written to the vector register file.

The operation has three ways to generate the memory pointer address: Rt with a constant 4-bit signed offset, Rx with a 3-bit signed post-increment, and Rx with a modifier register Mu post-increment. For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

The store is conditional, based on the value of the scalar predicate register Pv. If the condition evaluates false, the operation becomes a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv) `<br>`vmem(Rt+#s4):nt=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rt+#s4)=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++#s3):nt=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++#s3)=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++Mu):nt=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++Mu)=Os8.new` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `vmem(Rt):nt=Os8.new` | `Assembler mapped to: `<br>`"vmem(Rt+#0):nt=Os8.new"` |
| `vmem(Rt)=Os8.new` | `Assembler mapped to: "vmem(Rt+#0)=Os8.new"` |
| `vmem(Rt+#s4):nt=Os8.new` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;` |
| `vmem(Rt+#s4)=Os8.new` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;` |
| `vmem(Rx++#s3):nt=Os8.new` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+#s*VBYTES;` |
| `vmem(Rx++#s3)=Os8.new` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+#s*VBYTES;` |
| `vmem(Rx++Mu):nt=Os8.new` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+MuV;` |
| `vmem(Rx++Mu)=Os8.new` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = OsN.new;`<br>`Rx=Rx+MuV;` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate that the data has no reuse.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  | s3 | s3 | s3 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | t | t | t | t | t | P | P | i | - | - | i | i | i | 0 | 0 | 1 | - | 0 | s | s | s | vmem(Rt+#s4)=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | t | t | t | t | t | P | P | i | - | - | i | i | i | 0 | 0 | 1 | - | - | s | s | s | vmem(Rt+#s4):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 0 | 0 | 0 | s | s | s | if (Pv) vmem(Rt+#s4)=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 1 | 0 | 1 | s | s | s | if (!Pv) vmem(Rt+#s4)=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 0 | 1 | 0 | s | s | s | if (Pv) vmem(Rt+#s4):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 1 | 1 | 1 | s | s | s | if (!Pv) vmem(Rt+#s4):nt=Os8.new |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  | s3 | s3 | s3 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | - | - | - | i | i | i | 0 | 0 | 1 | - | 0 | s | s | s | vmem(Rx++#s3)=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | - | - | - | i | i | i | 0 | 0 | 1 | - | - | s | s | s | vmem(Rx++#s3):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 0 | 0 | 0 | s | s | s | if (Pv) vmem(Rx++#s3)= Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 1 | 0 | 1 | s | s | s | if (!Pv) vmem(Rx++#s3)= Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 0 | 1 | 0 | s | s | s | if (Pv) vmem(Rx++#s3):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 1 | 1 | 1 | s | s | s | if (!Pv) vmem(Rx++#s3):nt=Os8.new |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  |  |  | s3 | s3 | s3 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | u | - | - | - | - | - | 0 | 0 | 1 | - | 0 | s | s | s | vmem(Rx++Mu)=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | - | - | - | - | - | 0 | 0 | 1 | - | - | s | s | s | vmem(Rx++Mu):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 0 | 0 | 0 | s | s | s | if (Pv) vmem(Rx++Mu)= Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 1 | 0 | 1 | s | s | s | if (!Pv) vmem(Rx++Mu)= Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 0 | 1 | 0 | s | s | s | if (Pv) vmem(Rx++Mu):nt=Os8.new |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 1 | 1 | 1 | s | s | s | if (!Pv) vmem(Rx++Mu):nt=Os8.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s3` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Store aligned

Write a full vector register Vs to memory, using a vector-size-aligned address. The operation has three ways to generate the memory pointer address: Rt with a constant 4-bit signed offset, Rx with a signed post-increment, and Rx with a modifier register Mu post-increment. For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

If the pointer presented to the instruction is not aligned, the instruction ignores the lower bits, yielding an aligned address.

If a scalar predicate register Pv evaluates true, store a full vector register Vs to memory, using a vector-size-aligned address. Otherwise, the operation becomes a NOP

| Syntax | Behavior |
|---|---|
| `if ([!]Pv) vmem(Rt):nt=Vs` | `Assembler mapped to: "if ([!]Pv) `<br>`vmem(Rt+#0):nt=Vs"` |
| `if ([!]Pv) vmem(Rt)=Vs` | `Assembler mapped to: "if ([!]Pv) `<br>`vmem(Rt+#0)=Vs"` |
| `if ([!]Pv) `<br>`vmem(Rt+#s4):nt=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) vmem(Rt+#s4)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++#s3):nt=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) vmem(Rx++#s3)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`vmem(Rx++Mu):nt=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) vmem(Rx++Mu)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `vmem(Rt):nt=Vs` | `Assembler mapped to: "vmem(Rt+#0):nt=Vs"` |
| `vmem(Rt)=Vs` | `Assembler mapped to: "vmem(Rt+#0)=Vs"` |
| `vmem(Rt+#s4):nt=Vs` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;` |
| `vmem(Rt+#s4)=Vs` | `EA=Rt+#s*VBYTES;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;` |
| `vmem(Rx++#s3):nt=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;` |
| `vmem(Rx++#s3)=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+#s*VBYTES;` |
| `vmem(Rx++Mu):nt=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;` |
| `vmem(Rx++Mu)=Vs` | `EA=Rx;`<br>`*(EA&~(ALIGNMENT-1)) = Vs;`<br>`Rx=Rx+MuV;` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate the data has no reuse.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | t | t | t | t | t | P | P | i | - | - | i | i | i | 0 | 0 | 0 | s | s | s | s | s | vmem(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | t | t | t | t | t | P | P | i | - | - | i | i | i | 0 | 0 | 0 | s | s | s | s | s | vmem(Rt+#s4):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rt+#s4):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rt+#s4):nt=Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | - | - | - | i | i | i | 0 | 0 | 0 | s | s | s | s | s | vmem(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | - | - | - | i | i | i | 0 | 0 | 0 | s | s | s | s | s | vmem(Rx++#s3):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rx++#s3):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rx++#s3):nt=Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | u | - | - | - | - | - | 0 | 0 | 0 | s | s | s | s | s | vmem(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | x | x | x | x | x | P | P | u | - | - | - | - | - | 0 | 0 | 0 | s | s | s | s | s | vmem(Rx++Mu):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 0 | s | s | s | s | s | if (Pv) vmem(Rx++Mu):nt=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 0 | 1 | s | s | s | s | s | if (!Pv) vmem(Rx++Mu):nt=Vs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction Class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Store unaligned

Write a full vector register Vs to memory, using an arbitrary byte-aligned address.

The operation has three ways to generate the memory pointer address:

- Rt with a constant 4-bit signed offset
- Rx with a 3-bit signed post-increment
- Rx with a modifier register Mu post-increment.

For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

Unaligned memory operations require two accesses to the memory system, and thus incur increased power and bandwidth over aligned accesses. However, they require fewer instructions. Use aligned memory operations and combinations of permute operations when possible.

This instruction uses both slot 0 and slot 1, allowing at most 3 instructions to execute in a packet with `vmemu` in it.

If the scalar predicate register Pv is true, store a full vector register Vs to memory, using an arbitrary byte-aligned address. Otherwise, the operation becomes a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv) vmemu(Rt)=Vs` | `Assembler mapped to: "if ([!]Pv) `<br>`vmemu(Rt+#0)=Vs"` |
| `if ([!]Pv) vmemu(Rt+#s4)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`*EA = Vs;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) vmemu(Rx++#s3)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*EA = Vs;`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) vmemu(Rx++Mu)=Vs` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`*EA = Vs;`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `vmemu(Rt)=Vs` | `Assembler mapped to: "vmemu(Rt+#0)=Vs"` |
| `vmemu(Rt+#s4)=Vs` | `EA=Rt+#s*VBYTES;`<br>`*EA = Vs;` |
| `vmemu(Rx++#s3)=Vs` | `EA=Rx;`<br>`*EA = Vs;`<br>`Rx=Rx+#s*VBYTES;` |
| `vmemu(Rx++Mu)=Vs` | `EA=Rx;`<br>`*EA = Vs;`<br>`Rx=Rx+MuV;` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction uses the HVX permute resource.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | t | t | t | t | t | P | P | i | - | - | i | i | i | 1 | 1 | 1 | s | s | s | s | s | vmemu(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 0 | s | s | s | s | s | if (Pv) vmemu(Rt+#s4)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 1 | s | s | s | s | s | if (!Pv) vmemu(Rt+#s4)=Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | - | - | - | i | i | i | 1 | 1 | 1 | s | s | s | s | s | vmemu(Rx++#s3)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 0 | s | s | s | s | s | if (Pv) vmemu(Rx++#s3)= Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 1 | s | s | s | s | s | if (!Pv) vmemu(Rx++#s3)= Vs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | x | x | x | x | x | P | P | u | - | - | - | - | - | 1 | 1 | 1 | s | s | s | s | s | vmemu(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 0 | s | s | s | s | s | if (Pv) vmemu(Rx++Mu)=Vs |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 1 | s | s | s | s | s | if (!Pv) vmemu(Rx++Mu)= Vs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
