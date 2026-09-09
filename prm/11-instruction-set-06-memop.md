[← Contents](README.md)

## 11.6 MEMOP

The MEMOP instruction class includes simple operations on values in memory.

MEMOP instructions are executable on slot 0.

#### Operation on memory byte

Perform ALU or bit operation on the memory byte at the effective address.

| Syntax | Behavior |
|---|---|
| `memb(Rs+#u6:0)=clrbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp &= (~(1<<#U));`<br>`*EA = tmp;` |
| `memb(Rs+#u6:0)=setbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp \|= (1<<#U);`<br>`*EA = tmp;` |
| `memb(Rs+#u6:0)[+-]=#U5` | `apply_extension(#u);`<br>`EA=Rs[+-]#u;`<br>`tmp = *EA;`<br>`tmp [+-]= #U;`<br>`*EA = tmp;` |
| `memb(Rs+#u6:0)[+-\|&]=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp [+-\|&]= Rt;`<br>`*EA = tmp;` |

##### Class: MEMOP (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | t | t | t | t | t | memb(Rs+#u6:0)+=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | t | t | t | t | t | memb(Rs+#u6:0)-=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | t | t | t | t | t | memb(Rs+#u6:0)&=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | t | t | t | t | t | memb(Rs+#u6:0)\|=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | I | I | I | I | I | memb(Rs+#u6:0)+=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | I | I | I | I | I | memb(Rs+#u6:0)-=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | I | I | I | I | I | memb(Rs+#u6:0)=clrbit(#U5) |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | I | I | I | I | I | memb(Rs+#u6:0)=setbit(#U5) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |

#### Operation on memory halfword

Perform ALU or bit operation on the memory halfword at the effective address.

| Syntax | Behavior |
|---|---|
| `memh(Rs+#u6:1)=clrbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp &= (~(1<<#U));`<br>`*EA = tmp;` |
| `memh(Rs+#u6:1)=setbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp \|= (1<<#U);`<br>`*EA = tmp;` |
| `memh(Rs+#u6:1)[+-]=#U5` | `apply_extension(#u);`<br>`EA=Rs[+-]#u;`<br>`tmp = *EA;`<br>`tmp [+-]= #U;`<br>`*EA = tmp;` |
| `memh(Rs+#u6:1)[+-\|&]=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp [+-\|&]= Rt;`<br>`*EA = tmp;` |

##### Class: MEMOP (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | t | t | t | t | t | memh(Rs+#u6:1)+=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | t | t | t | t | t | memh(Rs+#u6:1)-=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | t | t | t | t | t | memh(Rs+#u6:1)&=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | t | t | t | t | t | memh(Rs+#u6:1)\|=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | I | I | I | I | I | memh(Rs+#u6:1)+=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | I | I | I | I | I | memh(Rs+#u6:1)-=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | I | I | I | I | I | memh(Rs+#u6:1)=clrbit(#U5) |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 0 | 1 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | I | I | I | I | I | memh(Rs+#u6:1)=setbit(#U5) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |

#### Operation on memory word

Perform ALU or bit operation on the memory word at the effective address.

| Syntax | Behavior |
|---|---|
| `memw(Rs+#u6:2)=clrbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp &= (~(1<<#U));`<br>`*EA = tmp;` |
| `memw(Rs+#u6:2)=setbit(#U5)` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp \|= (1<<#U);`<br>`*EA = tmp;` |
| `memw(Rs+#u6:2)[+-]=#U5` | `apply_extension(#u);`<br>`EA=Rs[+-]#u;`<br>`tmp = *EA;`<br>`tmp [+-]= #U;`<br>`*EA = tmp;` |
| `memw(Rs+#u6:2)[+-\|&]=Rt` | `apply_extension(#u);`<br>`EA=Rs+#u;`<br>`tmp = *EA;`<br>`tmp [+-\|&]= Rt;`<br>`*EA = tmp;` |

##### Class: MEMOP (slots 0)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | t | t | t | t | t | memw(Rs+#u6:2)+=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | t | t | t | t | t | memw(Rs+#u6:2)-=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | t | t | t | t | t | memw(Rs+#u6:2)&=Rt |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | t | t | t | t | t | memw(Rs+#u6:2)\|=Rt |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 0 | I | I | I | I | I | memw(Rs+#u6:2)+=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 0 | 1 | I | I | I | I | I | memw(Rs+#u6:2)-=#U5 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 0 | I | I | I | I | I | memw(Rs+#u6:2)=clrbit(#U5) |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | - | 1 | 0 | s | s | s | s | s | P | P | 0 | i | i | i | i | i | i | 1 | 1 | I | I | I | I | I | memw(Rs+#u6:2)=setbit(#U5) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `t5` | Field to encode register t |
