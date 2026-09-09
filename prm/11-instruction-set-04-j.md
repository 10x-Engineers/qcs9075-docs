## 11.4 J

The J instruction class includes branch instructions (jumps and calls) that obtain the target address from a (PC-relative) immediate address value.

J instructions are executable on slot 2 and slot 3.

#### Call subroutine

Change the program flow to a subroutine. This instruction first transfers the next program counter (NPC) value into the link register, and then jumps to the target address.

This instruction can appear in slots 2 or 3.

| Syntax | Behavior |
|---|---|
| `call #r22:2` | `apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`LR=NPC;`<br>`PC=PC+#r;` |
| `if ([!]Pu) call #r15:2` | `apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`if ([!]Pu[0]) {`<br>`LR=NPC;`<br>`PC=PC+#r;`<br>`}` |

##### Class: J (slots 2,3)

##### Notes

- This instruction can conditionally execute based on the value of a predicate register. If the instruction is preceded by 'if Pn', the instruction only executes if the least-significant bit of the predicate register is 1. Similarly, if the instruction is preceded by 'if !Pn', the instruction is executed only if the least-significant bit of Pn is 0.
- The Next PC value is the address immediately following the last instruction in the packet containing this instruction.
- The PC value is the address of the start of the packet
- A PC-relative address is formed by taking the decoded immediate value and adding it to the current PC value.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 1 | 0 | 1 | i | i | i | i | i | i | i | i | i | P | P | i | i | i | i | i | i | i | i | i | i | i | i | i | 0 | call #r22:2 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  | D N |  | u2 | u2 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | i | i | 0 | i | i | i | i | i | P | P | i | - | 0 | - | u | u | i | i | i | i | i | i | i | - | if (Pu) call #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | i | i | 1 | i | i | i | i | i | P | P | i | - | 0 | - | u | u | i | i | i | i | i | i | i | - | if (!Pu) call #r15:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `DN` | Dot-new |
| `Parse` | Packet/loop parse bits |
| `u2` | Field to encode register u |

#### Compare and jump

Compare two registers, or a register and immediate value, and write a predicate with the result. Then use the predicate result to conditionally jump to a PC-relative target address.

The registers available as operands are restricted to R0-R7 and R16-R23. The predicate destination is restricted to P0 and P1.

In assembly syntax, this instruction appears as two instructions in the packet: a compare and a separate conditional jump. The assembler may convert adjacent compare and jump instructions into compound compare-jump form.

| Syntax | Behavior |
|---|---|
| `p[01]=cmp.eq(Rs,#-1); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs==-1) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.eq(Rs,#U5); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs==#U) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.eq(Rs,Rt); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs==Rt) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.gt(Rs,#-1); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs>-1) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.gt(Rs,#U5); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs>#U) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.gt(Rs,Rt); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs>Rt) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.gtu(Rs,#U5); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs.uw[0]>#U) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=cmp.gtu(Rs,Rt); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs.uw[0]>Rt) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `p[01]=tstbit(Rs,#0); if `<br>`([!]p[01].new) jump:<hint> #r9:2` | `P[01]=(Rs & 1) ? 0xff : 0x00 if `<br>`([!]P[01].new[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |

##### Class: J (slots 0,1,2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  | s4 | s4 | s4 | s4 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#-1); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#-1); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p0=tstbit(Rs,#0); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#-1); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#-1); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p0=tstbit(Rs,#0); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#-1); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#-1); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p0=tstbit(Rs,#0); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#-1); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#-1); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p0=tstbit(Rs,#0); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#U5); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#U5); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#U5); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,#U5); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#U5); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#U5); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#U5); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,#U5); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,#U5); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,#U5); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,#U5); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,#U5); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#-1); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#-1); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p1=tstbit(Rs,#0); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#-1); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#-1); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p1=tstbit(Rs,#0); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#-1); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#-1); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p1=tstbit(Rs,#0); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 0 | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#-1); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 0 | 1 | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#-1); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | - | - | - | 1 | 1 | i | i | i | i | i | i | i | - | p1=tstbit(Rs,#0); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#U5); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#U5); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#U5); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,#U5); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#U5); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#U5); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#U5); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,#U5); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,#U5); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,#U5); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,#U5); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | I | I | I | I | I | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,#U5); if (!p1.new) jump:t #r9:2 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  | s4 | s4 | s4 | s4 | Parse | Parse |  |  | t4 | t4 | t4 | t4 |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,Rt); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,Rt); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,Rt); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,Rt); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,Rt); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,Rt); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.eq(Rs,Rt); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.eq(Rs,Rt); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,Rt); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,Rt); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,Rt); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,Rt); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,Rt); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,Rt); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gt(Rs,Rt); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gt(Rs,Rt); if (!p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,Rt); if (p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,Rt); if (p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,Rt); if (p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,Rt); if (p1.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,Rt); if (!p0.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 0 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,Rt); if (!p1.new) jump:nt #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | 0 | t | t | t | t | i | i | i | i | i | i | i | - | p0=cmp.gtu(Rs,Rt); if (!p0.new) jump:t #r9:2 |
| 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | i | i | s | s | s | s | P | P | 1 | 1 | t | t | t | t | i | i | i | i | i | i | i | - | p1=cmp.gtu(Rs,Rt); if (!p1.new) jump:t #r9:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s4` | Field to encode register s |
| `t4` | Field to encode register t |

#### Jump to address

Change the program flow to a target address. This instruction changes the program counter to a target address that is relative to the PC address. The offset from the current PC address is contained in the instruction encoding.

A speculated jump instruction includes a hint ("taken" or "not taken") that specifies the expected value of the conditional expression. If the actual generated value of the predicate differs from this expected value, the jump instruction incurs a performance penalty.

This instruction can appear in slots 2 or 3.

| Syntax | Behavior |
|---|---|
| `if ([!]Pu) jump #r15:2` | `Assembler mapped to: "if ([!]Pu) ""jump"":nt `<br>`""#r15:2"` |
| `if ([!]Pu) jump:<hint> `<br>`#r15:2` | `if ([!]Pu[0]) {`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |
| `jump #r22:2` | `apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;` |

##### Class: J (slots 0,1,2,3)

##### Notes

- This instruction can conditionally execute based on the value of a predicate register. If the instruction is preceded by 'if Pn', the instruction only executes if the least-significant bit of the predicate register is 1. Similarly, if the instruction is preceded by 'if !Pn', the instruction executes only if the least-significant bit of Pn is 0.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 1 | 0 | 0 | i | i | i | i | i | i | i | i | i | P | P | i | i | i | i | i | i | i | i | i | i | i | i | i | - | jump #r22:2 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | PT | D N |  | u2 | u2 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 0 | i | i | i | i | i | P | P | i | 0 | 0 | - | u | u | i | i | i | i | i | i | i | - | if (Pu) jump:nt #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 0 | i | i | i | i | i | P | P | i | 1 | 0 | - | u | u | i | i | i | i | i | i | i | - | if (Pu) jump:t #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 1 | i | i | i | i | i | P | P | i | 0 | 0 | - | u | u | i | i | i | i | i | i | i | - | if (!Pu) jump:nt #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 1 | i | i | i | i | i | P | P | i | 1 | 0 | - | u | u | i | i | i | i | i | i | i | - | if (!Pu) jump:t #r15:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `DN` | Dot-new |
| `PT` | Predict-taken |
| `Parse` | Packet/loop parse bits |
| `u2` | Field to encode register u |

#### Jump to address conditioned on new predicate

Perform speculated jump.

Jump if the LSB of the newly-generated predicate is true. The predicate must be generated in the same packet as the speculated jump instruction.

A speculated jump instruction includes a hint ("taken" or "not taken") that specifies the expected value of the conditional expression. If the actual generated value of the predicate differs from this expected value, the jump instruction incurs a performance penalty.

This instruction can appear in slots 2 or 3.

| Syntax | Behavior |
|---|---|
| `if ([!]Pu.new) jump:<hint> `<br>`#r15:2` | `{`<br>`if([!]Pu.new[0]){`<br>`apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`PC=PC+#r;`<br>`}` |

##### Class: J (slots 0,1,2,3)

##### Notes

- This instruction can conditionally execute based on the value of a predicate register. If the instruction is preceded by 'if Pn', the instruction only executes if the least-significant bit of the predicate register is 1. Similarly, if the instruction is preceded by 'if !Pn', the instruction executes only if the least-significant bit of Pn is 0.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | PT | D N |  | u2 | u2 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 0 | i | i | i | i | i | P | P | i | 0 | 1 | - | u | u | i | i | i | i | i | i | i | - | if (Pu.new) jump:nt #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 0 | i | i | i | i | i | P | P | i | 1 | 1 | - | u | u | i | i | i | i | i | i | i | - | if (Pu.new) jump:t #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 1 | i | i | i | i | i | P | P | i | 0 | 1 | - | u | u | i | i | i | i | i | i | i | - | if (!Pu.new) jump:nt #r15:2 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | i | i | 1 | i | i | i | i | i | P | P | i | 1 | 1 | - | u | u | i | i | i | i | i | i | i | - | if (!Pu.new) jump:t #r15:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `DN` | Dot-new |
| `PT` | Predict-taken |
| `Parse` | Packet/loop parse bits |
| `u2` | Field to encode register u |

#### Jump to address condition on register value

Perform register-conditional jump.

Jump if the specified register expression is true.

A register-conditional jump includes a hint ("taken" or "not taken") that specifies the expected value of the register expression. If the actual generated value of the expression differs from this expected value, the jump instruction incurs a performance penalty.

This instruction can appear only in slot 3.

| Syntax | Behavior |
|---|---|
| `if (Rs!=#0) jump:nt #r13:2` | `if (Rs != 0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs!=#0) jump:t #r13:2` | `if (Rs != 0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs<=#0) jump:nt #r13:2` | `if (Rs<=0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs<=#0) jump:t #r13:2` | `if (Rs<=0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs==#0) jump:nt #r13:2` | `if (Rs == 0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs==#0) jump:t #r13:2` | `if (Rs == 0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs>=#0) jump:nt #r13:2` | `if (Rs>=0) {`<br>`PC=PC+#r;`<br>`}` |
| `if (Rs>=#0) jump:t #r13:2` | `if (Rs>=0) {`<br>`PC=PC+#r;`<br>`}` |

##### Class: J (slot 3)

##### Notes

- This instruction will be deprecated in a future version.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  | sm |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | i | s | s | s | s | s | P | P | i | 0 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs!=#0) jump:nt #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | i | s | s | s | s | s | P | P | i | 1 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs!=#0) jump:t #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | i | s | s | s | s | s | P | P | i | 0 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs>=#0) jump:nt #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | i | s | s | s | s | s | P | P | i | 1 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs>=#0) jump:t #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | i | s | s | s | s | s | P | P | i | 0 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs==#0) jump:nt #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | i | s | s | s | s | s | P | P | i | 1 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs==#0) jump:t #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | i | s | s | s | s | s | P | P | i | 0 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs<=#0) jump:nt #r13:2 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | i | s | s | s | s | s | P | P | i | 1 | i | i | i | i | i | i | i | i | i | i | i | - | if (Rs<=#0) jump:t #r13:2 |

| Field name | Description |
|---|---|
| `sm` | Supervisor mode only |
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |

#### Transfer and jump

Move an unsigned immediate or register value into a destination register and unconditionally jump. In assembly syntax, this instruction appears as two instructions in the packet, a transfer and a separate jump. The assembler may convert adjacent transfer and jump instructions into compound transfer-jump form.

| Syntax | Behavior |
|---|---|
| `Rd=#U6 ; jump #r9:2` | `apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`Rd=#U;`<br>`PC=PC+#r;` |
| `Rd=Rs ; jump #r9:2` | `apply_extension(#r);`<br>`#r=#r & ~PCALIGN_MASK;`<br>`Rd=Rs;`<br>`PC=PC+#r;` |

##### Class: J (slots 2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  | d4 | d4 | d4 | d4 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | - | - | i | i | d | d | d | d | P | P | I | I | I | I | I | I | i | i | i | i | i | i | i | - | Rd=#U6 ; jump #r9:2 |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  | s4 | s4 | s4 | s4 | Parse | Parse |  |  | d4 | d4 | d4 | d4 |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 0 | 1 | 1 | 1 | - | - | i | i | s | s | s | s | P | P | - | - | d | d | d | d | i | i | i | i | i | i | i | - | Rd=Rs ; jump #r9:2 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d4` | Field to encode register d |
| `s4` | Field to encode register s |
