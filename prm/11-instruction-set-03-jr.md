## 11.3 JR

The JR instruction class includes instructions to change the program flow to a new location contained in a register.

JR instructions are executable on slot 2.

#### Call subroutine from register

Change the program flow to a subroutine. This instruction first transfers the next program counter (NPC) value into the link register, and then jumps to a target address contained in a register.

This instruction can only appear in slot 2.

| Syntax | Behavior |
|---|---|
| `callr Rs` | `LR=NPC;`<br>`PC=Rs;` |
| `callrh Rs` | `LR=NPC;`<br>`PC=Rs;` |
| `if ([!]Pu) callr Rs` | `if ([!]Pu[0]) {`<br>`LR=NPC;`<br>`PC=Rs;`<br>`}` |

##### Class: JR (slot 2)

##### Notes

- This instruction can conditionally execute based on the value of a predicate register. If the instruction is preceded by 'if Pn', the instruction only executes if the least-significant bit of the predicate register is 1. Similarly, if the instruction is preceded by 'if !Pn', the instruction executes only if the least-significant bit of Pn is 0.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | callr Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | callrh Rs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  | u2 | u2 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | s | s | s | s | s | P | P | - | - | - | - | u | u | - | - | - | - | - | - | - | - | if (Pu) callr Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | s | s | s | s | s | P | P | - | - | - | - | u | u | - | - | - | - | - | - | - | - | if (!Pu) callr Rs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `u2` | Field to encode register u |

#### Hinted call subroutine from register

Change the program flow to a subroutine. This instruction first transfers the next program counter (NPC) value into the link register, and then jumps to a target address contained in a register. This instruction is effective only when a preceding hintjr exists.

This instruction can only appear in slot 2.

| Syntax | Behavior |
|---|---|
| `callrh Rs` | `LR=NPC;`<br>`PC=Rs;` |

##### Class: JR (slot 2)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | callrh Rs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |

#### Hint an indirect jump address

Provide a hint indicating that there will soon be an indirect call to the address specified in Rs. The indirect call can be either jumprh or callrh.

This instruction can appear in either slot 2 or slot 3.

| Syntax | Behavior |
|---|---|
| `hintjr(Rs)` | `;` |

##### Class: JR (slot 2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | hintjr(Rs) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |

#### Jump to address from register

Change the program flow to a target address. This instruction changes the program counter to a target address contained in a register.

This instruction can appear only in slot 2.

| Syntax | Behavior |
|---|---|
| `if ([!]Pu) jumpr Rs` | `Assembler mapped to: "if ([!]Pu) `<br>`""jumpr"":nt ""Rs"` |
| `if ([!]Pu[.new]) `<br>`jumpr:<hint> Rs` | `{`<br>`if([!]Pu[.new][0]){`<br>`PC=Rs;`<br>`}` |
| `jumpr Rs` | `PC=Rs;` |
| `jumprh Rs` | `PC=Rs;` |

##### Class: JR (slot 2)

##### Notes

- This instruction can conditionally execute based on the value of a predicate register. If the instruction is preceded by 'if Pn', the instruction only executes if the least-significant bit of the predicate register is 1. Similarly, if the instruction is preceded by 'if !Pn', the instruction executes only if the least-significant bit of Pn is 0.

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | jumpr Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | jumprh Rs |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  | u2 | u2 |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | - | 0 | 0 | - | u | u | - | - | - | - | - | - | - | - | if (Pu) jumpr:nt Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | - | 0 | 1 | - | u | u | - | - | - | - | - | - | - | - | if (Pu.new) jumpr:nt Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | - | 1 | 0 | - | u | u | - | - | - | - | - | - | - | - | if (Pu) jumpr:t Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | s | s | s | s | s | P | P | - | 1 | 1 | - | u | u | - | - | - | - | - | - | - | - | if (Pu.new) jumpr:t Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | - | 0 | 0 | - | u | u | - | - | - | - | - | - | - | - | if (!Pu) jumpr:nt Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | - | 0 | 1 | - | u | u | - | - | - | - | - | - | - | - | if (!Pu.new) jumpr:nt Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | - | 1 | 0 | - | u | u | - | - | - | - | - | - | - | - | if (!Pu) jumpr:t Rs |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | s | s | s | s | s | P | P | - | 1 | 1 | - | u | u | - | - | - | - | - | - | - | - | if (!Pu.new) jumpr:t Rs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
| `u2` | Field to encode register u |

#### Hinted jump to address from register

Change the program flow to a target address. This instruction changes the program counter to a target address contained in a register. This instruction is effective only when a preceding hintjr exists.

This instruction can appear only in slot 2.

| Syntax | Behavior |
|---|---|
| `jumprh Rs` | `PC=Rs;` |

##### Class: JR (slot 2)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | s | s | s | s | s | P | P | - | - | - | - | - | - | - | - | - | - | - | - | - | - | jumprh Rs |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `s5` | Field to encode register s |
