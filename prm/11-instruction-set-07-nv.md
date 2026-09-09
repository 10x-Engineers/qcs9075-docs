## 11.7 NV

The NV instruction class includes instructions that take the register source operand from another instruction in the same packet.

NV instructions are executable on slot 0.

### 11.7.1 NV J

The NV J instruction subclass includes jump instructions that take the register source operand from another instruction in the same packet.

#### Jump to address condition on new register value

Compare a register or constant against the value produced by a slot 1 instruction. If the comparison is true, the program counter is changed to a target address, relative to the current PC.

This instruction is executable only on slot 0.

| Syntax | Behavior |
|---|---|
| `if ([!]cmp.eq(Ns.new,#-1)) jump:<hint> `<br>`#r9:2` | `if ((Ns.new[!]=(-1))) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.eq(Ns.new,#U5)) jump:<hint> `<br>`#r9:2` | `if ((Ns.new[!]=(#U))) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.eq(Ns.new,Rt)) jump:<hint> `<br>`#r9:2` | `if ((Ns.new[!]=Rt)) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gt(Ns.new,#-1)) jump:<hint> `<br>`#r9:2` | `if ([!](Ns.new>(-1))) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gt(Ns.new,#U5)) jump:<hint> `<br>`#r9:2` | `if ([!](Ns.new>(#U))) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gt(Ns.new,Rt)) jump:<hint> `<br>`#r9:2` | `if ([!](Ns.new>Rt)) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gt(Rt,Ns.new)) jump:<hint> `<br>`#r9:2` | `if ([!](Rt>Ns.new)) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gtu(Ns.new,#U5)) jump:<hint> `<br>`#r9:2` | `if ([!](Ns.new.uw[0]>(#U))) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gtu(Ns.new,Rt)) jump:<hint> `<br>`#r9:2` | `if ([!](Ns.new.uw[0]>Rt.uw[0])) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]cmp.gtu(Rt,Ns.new)) jump:<hint> `<br>`#r9:2` | `if ([!](Rt.uw[0]>Ns.new.uw[0])) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `if ([!]tstbit(Ns.new,#0)) jump:<hint> `<br>`#r9:2` | `if ([!]((Ns.new) & 1)) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |

##### Class: NV (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | s3 | s3 | s3 | Parse | Parse |  | t5 | t5 | t5 | t5 | t5 |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gtu(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gtu(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gtu(Ns.new,Rt)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gtu(Ns.new,Rt)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gt(Rt,Ns.new)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gt(Rt,Ns.new)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gt(Rt,Ns.new)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gt(Rt,Ns.new)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gtu(Rt,Ns.new)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (cmp.gtu(Rt,Ns.new)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gtu(Rt,Ns.new)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | t | t | t | t | t | i | i | i | i | i | i | i | - | if (!cmp.gtu(Rt,Ns.new)) jump:t #r9:2 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | s3 | s3 | s3 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.gtu(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (cmp.gtu(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.gtu(Ns.new,#U5)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | if (!cmp.gtu(Ns.new,#U5)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (tstbit(Ns.new,#0)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (tstbit(Ns.new,#0)) jump:t#r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 1 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!tstbit(Ns.new,#0)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 1 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!tstbit(Ns.new,#0)) jump:t#r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,#-1)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (cmp.eq(Ns.new,#-1)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,#-1)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!cmp.eq(Ns.new,#-1)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,#-1)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (cmp.gt(Ns.new,#-1)) jump:t #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 0 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,#-1)) jump:nt #r9:2 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | i | i | - | s | s | s | P | P | 1 | - | - | - | - | - | i | i | i | i | i | i | i | - | if (!cmp.gt(Ns.new,#-1)) jump:t #r9:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s3` | Field to encode register s |
| `t5` | Field to encode register t |

### 11.7.2 NV ST

The NV ST instruction subclass includes store instructions which take the register source operand from another instruction in the same packet.

#### Store new-value byte

Store the least-significant byte in a source register in memory at the effective address.

| Syntax | Behavior |
|---|---|
| `memb(Re=#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Nt.new.b[0];`<br>`Re=#U;` |
| `memb(Rs+#s11:0)=Nt.new` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Nt.new.b[0];` |
| `memb(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`*EA = Nt.new.b[0];` |
| `memb(Ru<<#u2+#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Nt.new.b[0];` |
| `memb(Rx++#s4:0)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Nt.new.b[0];` |
| `memb(Rx++#s4:0:circ(Mu))=Nt.`<br>`new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Nt.new.b[0];` |
| `memb(Rx++I:circ(Mu))=Nt.new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<0,MuV);`<br>`*EA = Nt.new.b[0];` |
| `memb(Rx++Mu)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new.b[0];` |
| `memb(Rx++Mu:brev)=Nt.new` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new.b[0];` |
| `memb(gp+#u16:0)=Nt.new` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Nt.new.b[0];` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction that use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | 0 | 0 | t | t | t | memb(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 1 | 0 | 1 | i | i | i | i | i | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | i | i | i | memb(gp+#u16:0)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | i | i | i | memb(Rs+#s11:0)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 0 | t | t | t | 0 | - | - | - | - | - | 1 | - | memb(Rx++I:circ(Mu))=Nt. new |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 0 | t | t | t | 0 | i | i | i | i | - | 0 | - | memb(Rx++#s4:0:circ(Mu))=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | e | e | e | e | e | P | P | 0 | 0 | 0 | t | t | t | 1 | - | I | I | I | I | I | I | memb(Re=#U6)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 0 | 0 | 0 | t | t | t | 0 | i | i | i | i | - | 0 | - | memb(Rx++#s4:0)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | u | u | u | u | u | P | P | i | 0 | 0 | t | t | t | 1 | i | I | I | I | I | I | I | memb(Ru<<#u2+#U6)=Nt. new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 0 | t | t | t | 0 | - | - | - | - | - | - | - | memb(Rx++Mu)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 0 | t | t | t | 0 | - | - | - | - | - | - | - | memb(Rx++Mu:brev)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store new-value byte conditionally

Store the least-significant byte in a source register in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) `<br>`memb(#u6)=Nt.new` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memb(Rs+#u6:0)=Nt.new` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memb(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].b[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memb(Rx++#s4:0)=Nt.new` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Nt[.new].b[0];`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction which use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 0 | t | t | t | if (Pv) memb(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 0 | t | t | t | if (!Pv) memb(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 0 | t | t | t | if (Pv.new) memb(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 0 | t | t | t | if (!Pv.new) memb(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memb(Rs+#u6:0)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memb(Rs+#u6:0)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memb(Rs+#u6:0)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memb(Rs+#u6:0)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 0 | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memb(Rx++#s4:0)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 0 | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memb(Rx++#s4:0)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memb(Rx++#s4:0)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memb(Rx++#s4:0)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 0 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memb(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 0 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memb(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 0 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memb(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 0 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memb(#u6)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store new-value halfword

Store the upper or lower 16-bits of a source register in memory at the effective address.

| Syntax | Behavior |
|---|---|
| `memh(Re=#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Nt.new.h[0];`<br>`Re=#U;` |
| `memh(Rs+#s11:1)=Nt.new` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Nt.new.h[0];` |
| `memh(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`*EA = Nt.new.h[0];` |
| `memh(Ru<<#u2+#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Nt.new.h[0];` |
| `memh(Rx++#s4:1)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Nt.new.h[0];` |
| `memh(Rx++#s4:1:circ(Mu))=Nt.`<br>`new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Nt.new.h[0];` |
| `memh(Rx++I:circ(Mu))=Nt.new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<1,MuV);`<br>`*EA = Nt.new.h[0];` |
| `memh(Rx++Mu)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new.h[0];` |
| `memh(Rx++Mu:brev)=Nt.new` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new.h[0];` |
| `memh(gp+#u16:1)=Nt.new` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Nt.new.h[0];` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction that use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | 0 | 1 | t | t | t | memh(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 1 | 0 | 1 | i | i | i | i | i | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | i | i | i | memh(gp+#u16:1)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | i | i | i | memh(Rs+#s11:1)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 1 | t | t | t | 0 | - | - | - | - | - | 1 | - | memh(Rx++I:circ(Mu))=Nt. new |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 1 | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1:circ(Mu))=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | e | e | e | e | e | P | P | 0 | 0 | 1 | t | t | t | 1 | - | I | I | I | I | I | I | memh(Re=#U6)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 0 | 0 | 1 | t | t | t | 0 | i | i | i | i | - | 0 | - | memh(Rx++#s4:1)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | u | u | u | u | u | P | P | i | 0 | 1 | t | t | t | 1 | i | I | I | I | I | I | I | memh(Ru<<#u2+#U6)=Nt. new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 1 | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 0 | 1 | t | t | t | 0 | - | - | - | - | - | - | - | memh(Rx++Mu:brev)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store new-value halfword conditionally

Store the upper or lower 16 bits of a source register in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memh(#u6)=Nt.new` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memh(Rs+#u6:1)=Nt.new` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memh(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new].h[0];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memh(Rx++#s4:1)=Nt.new` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Nt[.new].h[0];`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction that use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 1 | t | t | t | if (Pv) memh(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 1 | t | t | t | if (!Pv) memh(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 1 | t | t | t | if (Pv.new) memh(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 0 | 1 | t | t | t | if (!Pv.new) memh(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memh(Rs+#u6:1)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rs+#u6:1)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memh(Rs+#u6:1)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 0 | 1 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memh(Rs+#u6:1)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 1 | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memh(Rx++#s4:1)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 1 | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memh(Rx++#s4:1)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 1 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(Rx++#s4:1)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 0 | 1 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(Rx++#s4:1)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 0 | 1 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memh(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 0 | 1 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memh(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 0 | 1 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memh(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 0 | 1 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memh(#u6)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store new-value word

Store a 32-bit register in memory at the effective address.

| Syntax | Behavior |
|---|---|
| `memw(Re=#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U;`<br>`*EA = Nt.new;`<br>`Re=#U;` |
| `memw(Rs+#s11:2)=Nt.new` | `apply_extension(#s);`<br>`EA=Rs+#s;`<br>`*EA = Nt.new;` |
| `memw(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`*EA = Nt.new;` |
| `memw(Ru<<#u2+#U6)=Nt.new` | `apply_extension(#U);`<br>`EA=#U+(Ru<<#u);`<br>`*EA = Nt.new;` |
| `memw(Rx++#s4:2)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+#s;`<br>`*EA = Nt.new;` |
| `memw(Rx++#s4:2:circ(Mu))=Nt.`<br>`new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,#s,MuV);`<br>`*EA = Nt.new;` |
| `memw(Rx++I:circ(Mu))=Nt.new` | `EA=Rx;`<br>`Rx=Rx=circ_add(Rx,I<<2,MuV);`<br>`*EA = Nt.new;` |
| `memw(Rx++Mu)=Nt.new` | `EA=Rx;`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new;` |
| `memw(Rx++Mu:brev)=Nt.new` | `EA=Rx.h[1] \| brev(Rx.h[0]);`<br>`Rx=Rx+MuV;`<br>`*EA = Nt.new;` |
| `memw(gp+#u16:2)=Nt.new` | `apply_extension(#u);`<br>`EA=(Constant_extended ? (0) : GP)+#u;`<br>`*EA = Nt.new;` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction that use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | - | - | 1 | 0 | t | t | t | memw(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  | Type | Type | Type |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 1 | i | i | 0 | 1 | 0 | 1 | i | i | i | i | i | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | i | i | i | memw(gp+#u16:2)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 0 | i | i | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | i | i | i | memw(Rs+#s11:2)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 1 | 0 | t | t | t | 0 | - | - | - | - | - | 1 | - | memw(Rx++I:circ(Mu))=Nt. new |
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 1 | 0 | t | t | t | 0 | i | i | i | i | - | 0 | - | memw(Rx++#s4:2:circ(Mu))=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | e5 | e5 | e5 | e5 | e5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | e | e | e | e | e | P | P | 0 | 1 | 0 | t | t | t | 1 | - | I | I | I | I | I | I | memw(Re=#U6)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 0 | 1 | 0 | t | t | t | 0 | i | i | i | i | - | 0 | - | memw(Rx++#s4:2)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | u5 | u5 | u5 | u5 | u5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | u | u | u | u | u | P | P | i | 1 | 0 | t | t | t | 1 | i | I | I | I | I | I | I | memw(Ru<<#u2+#U6)=Nt. new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse | u1 |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 1 | 0 | t | t | t | 0 | - | - | - | - | - | - | - | memw(Rx++Mu)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | u | 1 | 0 | t | t | t | 0 | - | - | - | - | - | - | - | memw(Rx++Mu:brev)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `Parse` | Packet/loop parse bits |
| `e5` | Field to encode register e |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u1` | Field to encode register u |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |

#### Store new-value word conditionally

Store a 32-bit register in memory at the effective address.

This instruction is conditional based on a predicate value. If the predicate is true, the instruction is performed, otherwise it is treated as a NOP.

| Syntax | Behavior |
|---|---|
| `if ([!]Pv[.new]) memw(#u6)=Nt.new` | `apply_extension(#u);`<br>`EA=#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memw(Rs+#u6:2)=Nt.new` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memw(Rs+Ru<<#u2)=Nt.new` | `EA=Rs+(Ru<<#u);`<br>`if ([!]Pv[.new][0]) {`<br>`*EA = Nt[.new];`<br>`} else {`<br>`NOP;`<br>`}` |
| `if ([!]Pv[.new]) `<br>`memw(Rx++#s4:2)=Nt.new` | `EA=Rx;`<br>`if ([!]Pv[.new][0]){`<br>`Rx=Rx+#s;`<br>`*EA = Nt[.new];`<br>`} else {`<br>`NOP;`<br>`}` |

##### Class: NV (slots 0)

##### Notes

- Forms of this instruction that use a new-value operand produced in the packet must execute on slot 0.
- This instruction can execute only in slot 0, even though it is an ST instruction.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  |  |  | t3 | t3 | t3 |  |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 1 | 0 | t | t | t | if (Pv) memw(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 1 | 0 | t | t | t | if (!Pv) memw(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 1 | 0 | t | t | t | if (Pv.new) memw(Rs+Ru<<#u2)=Nt.n ew |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | u | u | u | u | u | i | v | v | 1 | 0 | t | t | t | if (!Pv.new) memw(Rs+Ru<<#u2)=Nt.n ew |
| ICLASS | ICLASS | ICLASS | ICLASS |  | Se ns e | Pr ed Ne w |  | Type | Type | Type | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv) memw(Rs+#u6:2)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (Pv.new) memw(Rs+#u6:2)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv) memw(Rs+#u6:2)=Nt.new |
| 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | i | 1 | 0 | t | t | t | i | i | i | i | i | 0 | v | v | if (!Pv.new) memw(Rs+#u6:2)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | x5 | x5 | x5 | x5 | x5 | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 1 | 0 | t | t | t | 0 | i | i | i | i | 0 | v | v | if (Pv) memw(Rx++#s4:2)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 1 | 0 | t | t | t | 0 | i | i | i | i | 1 | v | v | if (!Pv) memw(Rx++#s4:2)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 1 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memw(Rx++#s4:2)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | x | x | x | x | x | P | P | 1 | 1 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memw(Rx++#s4:2)=Nt.new |
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N |  |  |  |  |  | Parse | Parse |  |  |  | t3 | t3 | t3 |  |  |  |  |  |  |  |  |  |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 1 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv) memw(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 0 | 1 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv) memw(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 1 | 0 | t | t | t | 1 | i | i | i | i | 0 | v | v | if (Pv.new) memw(#u6)=Nt.new |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | - | - | - | i | i | P | P | 1 | 1 | 0 | t | t | t | 1 | i | i | i | i | 1 | v | v | if (!Pv.new) memw(#u6)=Nt.new |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Type` | Type |
| `PredNew` | PredNew |
| `Sense` | Sense |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t3` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `x5` | Field to encode register x |
| `Amode` | Amode |
| `UN` | Unsigned |
