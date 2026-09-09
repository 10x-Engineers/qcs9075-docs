## 6.7 HVX LOAD

The HVX LOAD instruction subclass includes memory load instructions.

#### Load aligned

Reads a full vector register Vd from memory, using a vector-size-aligned address. The operation has three ways to generate the memory pointer address: Rt with a constant 4-bit signed offset, Rx with a signed post-increment, and Rx with a modifier register Mu post-increment. For the immediate forms, the value specifies the number of vectors worth of data. Mu contains the actual byte offset.

If the pointer presented to the instruction is not aligned, the instruction ignores the lower bits, yielding an aligned address.

If a scalar predicate register Pv evaluates true, load a full vector register Vs from memory, using a vector-size-aligned address. Otherwise, the operation becomes a NOP.

| Syntax | Behavior |
|---|---|
| `Vd=vmem(Rt)` | `Assembler mapped to: "Vd=vmem(Rt+#0)"` |
| `Vd=vmem(Rt):nt` | `Assembler mapped to: "Vd=vmem(Rt+#0):nt"` |
| `Vd=vmem(Rt+#s4)` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd=vmem(Rt+#s4):nt` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd=vmem(Rx++#s3)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd=vmem(Rx++#s3):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd=vmem(Rx++Mu)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `Vd=vmem(Rx++Mu):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `if ([!]Pv) Vd=vmem(Rt)` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd=vmem(Rt+#0)"` |
| `if ([!]Pv) Vd=vmem(Rt):nt` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd=vmem(Rt+#0):nt"` |
| `if ([!]Pv) Vd=vmem(Rt+#s4)` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) Vd = vmem(Rt + `<br>`#s4):nt` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) Vd=vmem(Rx++#s3)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) Vd = vmem(Rx ++ `<br>`#s3):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) Vd=vmem(Rx++Mu)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) Vd = vmem(Rx ++ `<br>`Mu):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: COPROC_VMEM (slots 0,1)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate that the data has no reuse.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rt+#s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rt+#s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd=vmem(Rt+#s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd=vmem(Rt+#s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd=vmem(Rt + #s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd= vmem(Rt + #s4):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rx++#s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rx++#s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd=vmem(Rx++#s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd=vmem(Rx++#s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd= vmem(Rx++ #s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd=vmem(Rx++ #s3):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rx++Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 0 | 0 | d | d | d | d | d | Vd=vmem(Rx++Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd=vmem(Rx++Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd=vmem(Rx++Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 0 | d | d | d | d | d | if (Pv) Vd=vmem(Rx++ Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 0 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd=vmem(Rx++ Mu):nt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Load immediate use

Reads a full vector register Vd (and/or temporary vector register) from memory, using a vector-size-aligned address. The operation has three ways to generate the memory pointer address: Rt with a constant 4-bit signed offset, Rx with a signed post-increment, and Rx with a modifier register Mu post-increment. For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

If the pointer presented to the instruction is not aligned, the instruction ignores the lower bits, yielding an aligned address. The value is used immediately in the packet as a source operand of any instruction.

The `Vd.cur` instruction writes the load value to a vector register in addition to consuming it within the packet.

The `Vd.tmp `instruction does not write the incoming data to the vector register file. The data is only used as a source in the current packet, and then immediately discarded. This form does not consume any vector resources, allowing it to be placed in parallel with some instructions that a normal align load cannot.

If a scalar predicate register Pv evaluates true, load a full vector register Vs from memory using a vector-size-aligned address. Otherwise, the operation becomes a NOP.

| Syntax | Behavior |
|---|---|
| `Vd.cur=vmem(Rt+#s4)` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd.cur=vmem(Rt+#s4):nt` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd.cur=vmem(Rx++#s3)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd.cur=vmem(Rx++#s3):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd.cur=vmem(Rx++Mu)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `Vd.cur=vmem(Rx++Mu):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `if ([!]Pv) Vd.cur=vmem(Rt)` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd.cur=vmem(Rt+#0)"` |
| `if ([!]Pv) Vd.cur = `<br>`vmem(Rt):nt` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd.cur=vmem(Rt+#0):nt"` |
| `if ([!]Pv) Vd.cur = vmem(Rt `<br>`+ #s4)` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.cur=vmem(Rt+#s4):nt` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.cur=vmem(Rx++#s3)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.cur=vmem(Rx++#s3):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.cur=vmem(Rx++Mu)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.cur=vmem(Rx++Mu):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: COPROC_VMEM (slots 0,1)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate the data has no reuse.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rt+#s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rt+#s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rt+ #s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rt+ #s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rt+ #s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rt+ #s4):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rx++#s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rx++#s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rx++ #s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rx++ #s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rx++ #s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rx++ #s3):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rx++Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 0 | 1 | d | d | d | d | d | Vd.cur=vmem(Rx++Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rx++ Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rx++ Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 0 | 0 | d | d | d | d | d | if (Pv) Vd.cur=vmem(Rx++ Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 0 | 1 | d | d | d | d | d | if (!Pv) Vd.cur=vmem(Rx++ Mu):nt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Load temporary immediate use

Read a full vector register Vd (and/or temporary vector register) from memory, using a vector-size-aligned address. The operation has three ways to generate the memory pointer address:

- Rt with a constant 4-bit signed offset
- Rx with a signed post-increment
- Rx with a modifier register Mu post-increment

For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset.

If the pointer presented to the instruction is not aligned, the instruction ignores the lower bits, yielding an aligned address. The value is used immediately in the packet as a source operand of any instruction.

The Vd.tmp instruction does not write the incoming data to the vector register file. The data is only used as a source in the current packet, and then immediately discarded. This form does not consume any vector resources, allowing it to be placed in parallel with some instructions that a normal align load cannot.

If a scalar predicate register Pv evaluates true, load a full vector register Vs from memory, using a vector-size-aligned address. Otherwise, the operation becomes a NOP.

| Syntax | Behavior |
|---|---|
| `Vd.tmp=vmem(Rt+#s4)` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd.tmp=vmem(Rt+#s4):nt` | `EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));` |
| `Vd.tmp=vmem(Rx++#s3)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd.tmp=vmem(Rx++#s3):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd.tmp=vmem(Rx++Mu)` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `Vd.tmp=vmem(Rx++Mu):nt` | `EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;` |
| `if ([!]Pv) Vd.tmp=vmem(Rt)` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd.tmp=vmem(Rt+#0)"` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rt):nt` | `Assembler mapped to: "if ([!]Pv) `<br>`Vd.tmp=vmem(Rt+#0):nt"` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rt+#s4)` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rt+#s4):nt` | `if ([!]Pv[0]) {`<br>`EA=Rt+#s*VBYTES;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rx++#s3)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rx++#s3):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+#s*VBYTES;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rx++Mu)` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv) `<br>`Vd.tmp=vmem(Rx++Mu):nt` | `if ([!]Pv[0]) {`<br>`EA=Rx;`<br>`Vd = *(EA&~(ALIGNMENT-1));`<br>`Rx=Rx+MuV;`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: COPROC_VMEM (slots 0,1)

##### Notes

- This instruction can use any HVX resource.
- An optional nontemporal hint to the microarchitecture can be specified to indicate the data has no reuse.
- The tmp load instruction destination register cannot be an accumulator register.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rt+#s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rt+#s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rt+ #s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rt+ #s4) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rt+ #s4):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | t | t | t | t | t | P | P | i | v | v | i | i | i | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rt+ #s4):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rx++ #s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rx++#s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rx++ #s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rx++ #s3) |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rx++ #s3):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | - | v | v | i | i | i | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rx++ #s3):nt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rx++Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 0 | 1 | 0 | d | d | d | d | d | Vd.tmp=vmem(Rx++Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rx++ Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rx++ Mu) |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 0 | d | d | d | d | d | if (Pv) Vd.tmp=vmem(Rx++ Mu):nt |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | x | x | x | x | x | P | P | u | v | v | - | - | - | 1 | 1 | 1 | d | d | d | d | d | if (!Pv) Vd.tmp=vmem(Rx++ Mu):nt |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |

#### Load unaligned

Reads a full vector register Vd from memory, using an arbitrary byte-aligned address. The operation has three ways to generate the memory pointer address:

- Rt with a constant 4-bit signed offset
- Rx with a 3-bit signed post-increment,
- Rx with a modifier register Mu post-increment

For the immediate forms, the value indicates the number of vectors worth of data. Mu contains the actual byte offset. Unaligned memory operations require two accesses to the memory system, and thus incur increased power and bandwidth over aligned accesses. However, they require fewer instructions.

Use aligned memory operations when possible, and sometimes multiple aligned memory accesses and the `valign` operation, to synthesize a nonaligned access.

This instruction uses both slot 0 and slot 1, allowing at most three instructions to execute in a packet with `vmemu` in it.

| Syntax | Behavior |
|---|---|
| `Vd=vmemu(Rt)` | `Assembler mapped to: "Vd=vmemu(Rt+#0)"` |
| `Vd=vmemu(Rt+#s4)` | `EA=Rt+#s*VBYTES;`<br>`Vd = *EA;` |
| `Vd=vmemu(Rx++#s3)` | `EA=Rx;`<br>`Vd = *EA;`<br>`Rx=Rx+#s*VBYTES;` |
| `Vd=vmemu(Rx++Mu)` | `EA=Rx;`<br>`Vd = *EA;`<br>`Rx=Rx+MuV;` |

##### Class: COPROC_VMEM (slots 0)

##### Notes

- This instruction uses the HVX permute resource.
- Immediates used in address computation are specified in multiples of vector length.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | t | t | t | t | t | P | P | i | 0 | 0 | i | i | i | 1 | 1 | 1 | d | d | d | d | d | Vd=vmemu(Rt+#s4) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | - | 0 | 0 | i | i | i | 1 | 1 | 1 | d | d | d | d | d | Vd=vmemu(Rx++#s3) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  | NT |  | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | x | x | x | x | x | P | P | u | 0 | 0 | - | - | - | 1 | 1 | 1 | d | d | d | d | d | Vd=vmemu(Rx++Mu) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `NT` | Nontemporal |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t5` | Field to encode register t |
| `u1` | Field to encode register u |
| `x5` | Field to encode register x |
