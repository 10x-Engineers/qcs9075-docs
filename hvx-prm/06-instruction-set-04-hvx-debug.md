## 6.4 HVX DEBUG

The HVX DEBUG instruction subclass includes debugging instructions.

#### Extract vector element

Extract a word from the vector register Vu using bits 5:2 of Rs as the word index. The result is placed in the scalar register Rd. A memory address can be used as the control selection Rs after data is read from memory using a vector load.

This is a very high latency instruction and should only be used in debug. A memory to memory transfer is more efficient.

Rs 28 >>2

Rd.w=vextract(Vu,Rs)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| w[15] | w[14] | w[13] | w[12] | w[11] | w[10] | w[9] | w[8] | w[7] | w[6] | w[5] | w[4] | w[3] | w[2] | w[1] | w[0] |

Vu

Rd<sup>w[7]</sup>

| Syntax | Behavior |
|---|---|
| `Rd.w=vextract(Vu,Rs)` | `Assembler mapped to: "Rd=vextract(Vu,Rs)"` |
| `Rd=vextract(Vu,Rs)` | `Rd = Vu.uw[ (Rs & (VWIDTH-1)) >> 2];` |

##### Class: LD (slots 0)

##### Notes

- This is a solo instruction. It must not be grouped with other instructions in a packet.

##### Intrinsics

```
Rd=vextract(Vu,Rs)Word32 Q6_R_vextract_VR(HVX_Vector Vu, Word32 Rs)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS | Amode | Amode | Amode | Type | Type | Type | U N | s5 | s5 | s5 | s5 | s5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | s | s | s | s | s | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Rd=vextract(Vu,Rs) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Amode` | Amode |
| Field name | Description |
| `Type` | Type |
| `UN` | Unsigned |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `s5` | Field to encode register s |
| `u5` | Field to encode register u |
