## 6.11 HVX PERMUTE SHIFT RESOURCE

The HVX PERMUTE SHIFT RESOURCE instruction subclass includes instructions that use both the

HVX permute and shift resources.

#### Vector ASR overlay

Complete a 64-bit bidirectional arithmetic shift right (ASR) by shifting the high-word source (Vu.w[i]) and merging with the destination register. This assumes a rotate on the low-word source was already performed and placed in the low-word of the destination register. This instruction can concatenate LSB portions of the source and destination registers and placed into the high or low word of the destination depending on the shift amount.

| Syntax | Behavior |
|---|---|
| `Vxx.w=vasrinto(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`shift = (Vu.w[i] << 32);`<br>`mask = (((Vxx.v[0].w[i]) << 32) \| Vxx.v[0].w[i]);`<br>`lomask = (((1) << 32) - 1);`<br>`count = -(0x40 & Vv.w[i]) + (Vv.w[i] & 0x3f);`<br>`result = (count == -0x40) ? 0 : (((count < 0) ? ((shift `<br>`<< -(count)) \| (mask & (lomask << -(count)))) : ((shift >> `<br>`count) \| (mask & (lomask >> count)))));`<br>`Vxx.v[1].w[i] = ((result >> 32) & 0xffffffff);`<br>`Vxx.v[0].w[i] = (result & 0xffffffff);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX permute resource.
- This instruction uses the HVX shift resource.

##### Intrinsics

```
Vxx.w=vasrinto(Vu.w,Vv.w)HVX_VectorPair Q6_Ww_vasrinto_WwVwVw
                             (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vxx.w=vasrinto(Vu.w,Vv.w) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Vector shuffle and deal cross-lane

The `vshuff `operation (formerly vtrans2x2) and `vdeal `operation perform a multiple-level transpose operation between groups of elements in two vectors. The element size is specified by the scalar register Rt. Rt=1 indicates an element size of 1 byte, Rt=2 indicates halfwords, Rt=4 words, Rt=8 8 bytes, Rt=16 16 bytes, and Rt=32 32 bytes. Consider the data in the two registers as two rows of 64 bytes each. Each two-by-two group is transposed.

For example, Rt = 4 indicates that each element contains four bytes. The matrix of four of these elements is composed of two elements from the even register and two corresponding elements of the odd register. This two-by-two array is then transposed, and the resulting elements are then presented in the two destination registers. A value of Rt = 0 leaves the input unchanged.

The following figures show examples for Rt = 1,2,4,8,16,32 where `vdeal` and `vshuff` perform the same operation. The diagram is valid for the `vshuff` and `vdeal` instructions.

vshuff/vdeal(Vy,Vx,Rt) N = 64/Rt Rt = 2^i

|  |  |  |  |  |
|---|---|---|---|---|
| [N-1] | [N-2] | ... | [1] | [0] |

Vy [N-1] [N-2] ... [1] [0] Vx

|  |  |  |  |  |
|---|---|---|---|---|
| [N-1] | [N-2] | ... | [1] | [0] |

[N-1] [N-2] ... [1] [0] Vy Vx

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| [N-1] | [N-2] | [N-3] | [N-4] | ... | [0] |

Vy’ [N-1] ... [3] [2] [1] [0] Vx’

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| [N-1] | ... | [3] | [2] | [1] | [0] |

[N-1] [N-2] [N-3] [N-4] ... [0] Vy’ Vx’

Vdd = vshuff/vdeal(Vu,Vv,Rt) N = 64 / Rt Rt = 2^i

|  |  |  |  |  |
|---|---|---|---|---|
| [N-1] | [N-2] | ... | [1] | [0] |

Vu [N-1] [N-2] ... [1] [0] Vv

|  |  |  |  |  |
|---|---|---|---|---|
| [N-1] | [N-2] | ... | [1] | [0] |

[N-1] [N-2] ... [1] [0] Vu Vv

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| [N-1] | [N-2] | [N-3] | [N-4] | ... | [0] |

Vdd[1] [N-1] [N-2] [3] [2] [1] [0]Vdd[0]

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| [N-1] | [N-2] | [3] | [2] | [1] | [0] |

[N-1] [N-2] [N-3] [N-4] ... [0]Vdd[1]Vdd[0]

|  |  |  |  |
|---|---|---|---|
| 3 | 2 | 1 | 0 |

Elements

Element Rt = 4 N = 16

When using a value of Rt other than 1,2,4,8,16, or 32, the effect is a compound hierarchical transpose.

For example, for the value 23, 23 = 1+2+4+16 indicates that the transformation is the same as performing the `vshuff` instruction with Rt = 1, then Rt = 2 on that result, then Rt = 4 on its result, then Rt = 16 on its result. The order is in increasing element size. For the `vdeal` instruction, the order is reversed, starting with the largest element size first, then working down to the smallest.

When the Rt value is the negated power of 2: -1,-2,-4,-8,-16,-32, it performs a a perfect shuffle for `vshuff`, or a deal for `vdeal` of the smallest element size. For example, if Rt = -24 this is a multiple of 8, so 8 is the smallest element size. With a -ve value of Rt, the upper bits of the value Rt are set. For example, with Rt = -8 this is the same as 32 + 16 + 8. The following diagram shows the effect of this transform for both the `vshuff` and `vdeal` instructions. vshuff(Vy,Vx,Rt) Rt = -8 == 32+16+8

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [13] | [12] | [11] | [10] | [9] | [8] |

Vy [7] [6] [5] [4] [3] [2] [1] [0] Vx

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [7] | [6] | [5] | [4] | [3] | [2] | [1] | [0] |

[15] [14] [13] [12] [11] [10] [9] [8] Vy Vx

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [7] | [13] | [5] | [11] | [3] | [9] | [1] |

[14] [6] [12] [4] [10] [2] [8] [0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [14] | [6] | [12] | [4] | [10] | [2] | [8] | [0] |

[15] [7] [13] [5] [11] [3] [9] [1]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [7] | [14] | [6] | [11] | [3] | [10] | [2] |

[13] [5] [12] [4] [9] [1] [8] [0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [13] | [5] | [12] | [4] | [9] | [1] | [8] | [0] |

[15] [7] [14] [6] [11] [3] [10] [2]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [7] | [14] | [6] | [13] | [5] | [12] | [4] |

Vy’ [11] [3] [10] [2] [9] [1] [8] [0] Vx’

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [11] | [3] | [10] | [2] | [9] | [1] | [8] | [0] |

[15] [7] [14] [6] [13] [5] [12] [4] Vy’ Vx’

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |

Element size 8

Vdd = vshuff(Vu,Vv,Rt) Rt = 24

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [13] | [12] | [11] | [10] | [9] | [8] |

Vu [7] [6] [5] [4] [3] [2] [1] [0] Vv

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [7] | [6] | [5] | [4] | [3] | [2] | [1] | [0] |

[15] [14] [13] [12] [11] [10] [9] [8] Vu Vv

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [7] | [14] | [6] | [13] | [5] | [12] | [4] |

Vdd[1] [11] [3] [10] [2] [9] [1] [8] [0] Vdd[0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [11] | [3] | [10] | [2] | [9] | [1] | [8] | [0] |

[15] [7] [14] [6] [13] [5] [12] [4] Vdd[1] Vdd[0]

vdeal(Vy,Vx,Rt) Rt = -8 or 56

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [13] | [12] | [11] | [10] | [9] | [8] |

Vx [7] [6] [5] [4] [3] [2] [1] [0] Vy

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [7] | [6] | [5] | [4] | [3] | [2] | [1] | [0] |

[15] [14] [13] [12] [11] [10] [9] [8] Vx Vy

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [13] | [12] | [7] | [6] | [5] | [4] |

[11] [10] [9] [8] [3] [2] [1] [0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [11] | [10] | [9] | [8] | [3] | [2] | [1] | [0] |

[15] [14] [13] [12] [7] [6] [5] [4]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [11] | 10] | [7] | [6] | [3] | [2] |

[13] [12] [9] [8] [5] [4] [1] [0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [13] | [12] | [9] | [8] | [5] | [4] | [1] | [0] |

[15] [14] [11] 10] [7] [6] [3] [2]

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [13] | [11] | [9] | [7] | [5] | [3] | [1] |

Vx’ [14] [12] [10] [8] [6] [4] [2] [0] Vy’

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [14] | [12] | [10] | [8] | [6] | [4] | [2] | [0] |

[15] [13] [11] [9] [7] [5] [3] [1] Vx’ Vy’

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |

Element size 8

Vdd = vdeal(Vu,Vv,Rt) Rt = -8 or 56

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [14] | [13] | [12] | [11] | [10] | [9] | [8] |

Vu [7] [6] [5] [4] [3] [2] [1] [0] Vv

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [7] | [6] | [5] | [4] | [3] | [2] | [1] | [0] |

[15] [14] [13] [12] [11] [10] [9] [8] Vu Vv

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

|  |  |  |
|---|---|---|
|  |  |  |

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [15] | [13] | [11] | [9] | [7] | [5] | [3] | [1] |

Vdd[1] [14] [12] [10] [8] [6] [4] [2] [0]Vdd[0]

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
| [14] | [12] | [10] | [8] | [6] | [4] | [2] | [0] |

[15] [13] [11] [9] [7] [5] [3] [1]Vdd[1]Vdd[0]

If in addition to this family of transformations, a block size is defined B, and the element size is defined as E, if Rt = B - E, the resulting transformation is a set of B contiguous blocks, each containing perfectly shuffled or dealt elements of element size E. Each block B contains 128/B elements in the 64 byte vector case. This represents the majority of common data transformations. When B is set to 0, the result is a shuffle or deal of elements across the whole vector register pair.

| Syntax | Behavior |
|---|---|
| `Vdd=vdeal(Vu,Vv,Rt)` | `Vdd.v[0] = Vv;`<br>`Vdd.v[1] = Vu;`<br>`for (offset=VWIDTH>>1; offset>0; offset>>=1) {`<br>`if ( Rt & offset) {`<br>`for (k = 0; k < VELEM(8); k++) {`<br>`if (!( k & offset)) {`<br>`SWAP(Vdd.v[1].ub[k],Vdd.v[0].ub[k+offset]);`<br>`}`<br>`}`<br>`}`<br>`}` |
| `Vdd=vshuff(Vu,Vv,Rt)` | `Vdd.v[0] = Vv;`<br>`Vdd.v[1] = Vu;`<br>`for (offset=1; offset<VWIDTH; offset<<=1) {`<br>`if ( Rt & offset) {`<br>`for (k = 0; k < VELEM(8); k++) {`<br>`if (!( k & offset)) {`<br>`SWAP(Vdd.v[1].ub[k],Vdd.v[0].ub[k+offset]);`<br>`}`<br>`}`<br>`}`<br>`}` |
| `vdeal(Vy,Vx,Rt)` | `for (offset=VWIDTH>>1; offset>0; offset>>=1) {`<br>`if ( Rt & offset) {`<br>`for (k = 0; k < VELEM(8); k++) {`<br>`if (!( k & offset)) {`<br>`SWAP(Vy.ub[k],Vx.ub[k+offset]);`<br>`}`<br>`}`<br>`}`<br>`}` |
| `vshuff(Vy,Vx,Rt)` | `for (offset=1; offset<VWIDTH; offset<<=1) {`<br>`if ( Rt & offset) {`<br>`for (k = 0; k < VELEM(8); k++) {`<br>`if (!( k & offset)) {`<br>`SWAP(Vy.ub[k],Vx.ub[k+offset]);`<br>`}`<br>`}`<br>`}`<br>`}` |
| `vtrans2x2(Vy,Vx,Rt)` | `Assembler mapped to: "vshuff(Vy,Vx,Rt)"` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX permute resource
- Input scalar register Rt is limited to registers 0 through 7
- This instruction uses the HVX shift resource

##### Intrinsics

|  |  |
|---|---|
| `Vdd=vdeal(Vu,Vv,Rt)` | `HVX_VectorPair Q6_W_vdeal_VVR(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vdd=vshuff(Vu,Vv,Rt)` | `HVX_VectorPair Q6_W_vshuff_VVR(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | y5 | y5 | y5 | y5 | y5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | t | t | t | t | t | P | P | 1 | y | y | y | y | y | 0 | 0 | 1 | x | x | x | x | x | vshuff(Vy,Vx,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | t | t | t | t | t | P | P | 1 | y | y | y | y | y | 0 | 1 | 0 | x | x | x | x | x | vdeal(Vy,Vx,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd=vshuff(Vu,Vv,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd=vdeal(Vu,Vv,Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t3` | Field to encode register t |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `v3` | Field to encode register v |
| `x5` | Field to encode register x |
| `y5` | Field to encode register y |

#### Vector in-lane lookup table

The `vlut` instructions implement fast vectorized lookup-tables. The lookup table is contained in the Vv register while the indexes are held in Vu. Table elements are either 8-bit or 16-bit. An aggregation feature implements tables larger than 64 bytes in 64 byte mode and 128 bytes in 128 byte mode.

In both 64 and 128 byte modes, the maximum amount of lookup table accessible is 32 bytes for byte lookups (vlut32) and 16 half words in hwords lookup (`vlut16`).

##### 8-bit elements

For 64 byte mode, tables with 8-bit elements support 32 entry lookup tables using the vlut32 instructions. The required entry is conditionally selected by using the lower five bits of the input byte for the respective output byte. A control input register, Rt, contains match and select bits. The lower three bits of Rt must match the upper three bits of the input byte index for the table entry to write to or OR with the destination vector register byte in Vd or Vx respectively. The LSB of Rt selects odd or even (32 entry) lookup tables in Vv.

The following example is a 256 byte table stored naturally in memory:

```
127,126,.....66, 65, 64, 63, 62,.........2, 1, 0
255,254,....194,193,192,191,190,.......130,129,128
```

To prepare it for use with the `vlut` instruction in 64 byte mode, it must be shuffled in blocks of 32 bytes

```
63, 31, 62, 30,......36, 4, 35, 3, 34, 2, 33, 1, 32, 0 Rt=0, Rt=1 127,
95,126, 94,.....100, 68, 99, 67, 98, 66, 97, 65, 96, 64 Rt=2, Rt=3
```

same ordering for bytes 128 through 255 `Rt=4, 5, 6, 7`

For 128 byte mode, the data must be shuffled in blocks of 64 bytes.

```
127, 63,126, 62,........68, 4, 67, 3, 66, 2, 65, 1, 64, 0 Rt=0,1,2,3
```

same ordering for bytes 128 through 255 `Rt=4,5,6,7 `

Accessing data with 64 or 128 byte mode stored in this way gives the same results. For 128 byte mode, bit 1 of Rt selects whether to use the odd or even packed table and bit 0 chooses the high of low 32 elements of that high or low table.

Vd.b = vlut32(Vu.b, Vv.b, Rt) and Vx.b |= vlut32(Vu.b, Vv.b, Rt)

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| b[63:8] | Vd.b =vlut32(Vu.b, Vv.b, Rt) b[7] | b[6] | b[5] | b[4] | b[3] | b[2] | b[1] | b[0] |

Rt

Vu Input

Vector

b[7:5]

b[2:0]

Replicated for all other input bytes

== ?

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| b[i]/a[i] i = 31 to 4 | b[3] | a[3] | b[2] | a[2] | b[1] | a[1] | b[0] | a[0] |

Vv Table

Vector

b[31:4]

To other selects b[0]

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0

Other inputs

b[4:0]

‘0’

|  |  |
|---|---|
| 1 | 0 |

Replicated for all other output bytes<sub>|</sub>

|  |  |
|---|---|
| b[63:1] | b[0] |

Vd/Vx

Output Optional OR

Vector accumulate

Vd.b = vlut32(Vu.b, Vv.b, Rt) and Vx.b |= vlut32(Vu.b, Vv.b, Rt)

Rt

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
| Bytes 127 to 69 | B[68] | B[67] | B[65] | B[64] | Bytes 63 to 4 | B[3] | B[2] | B[1] | B[0] |

Vu Input

Vector

Bits 2

downto 0

Bits 2:0

bits 7 to 5

Replicated for all other input bytes

== ?

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
| b[i]/a[i] i = 63 to 34 | b[33] | a[33] | b[32] | a[32] | b[i]/a[i] i = 31 to 2 | b[1] | a[1] | b[0] | a[0] |

Vv Table

b31 to 4

Vector

Bit 1

|  |  |
|---|---|
|  |  |
|  |  |

To other selects

1 0 1 0

Bit 0

Select hi or lo 32 for Vv

32 x 32 to 1 selectorsbits 4 to 0

|  |  |
|---|---|
| 1 | 0 |

1 0

|  |  |
|---|---|
| 1 | 0 |

1 0

|  |  |
|---|---|
| 32 x 32 to 1 selectors | 32 x 32 to 1 selectors |

bits 4 to 0

‘0’

|  |  |
|---|---|
| 1 | 0 |

Replicated for all other output bytes<sub>|</sub>

|  |  |  |  |
|---|---|---|---|
| B127 downto 65 | B[64] | B63 downto 1 | B[0] |

Vd/Vx

Optional OR

Output

accumulate

Vector

128Byte mode

##### 16-bit elements

For tables with 16-bit elements, the basic unit is a 16-entry lookup table in 64 byte mode and 128 byte mode, supported by the `vlut16` instructions. The even byte entries conditionally select using the lower four bits for the even destination register Vdd0, the odd byte entries select table entries into the odd vector destination register Vdd1. A control input register, Rt, contains match and select bits in the same way as the byte table case.

For 64 byte mode, the lower four bits of Rt must match the upper four bits of the input bytes for the table entry to write to or OR with the destination vector register bytes in Vdd or Vxx respectively. Bit 0 of Rt selects the even or odd 16 entries in Vv.

For 128 byte mode, only the upper four bits of input bytes must also match the lower four of Rt. Bit 1 of Rt selects odd or even hwords and bit 0 selects the lower or upper 16 entries in the Vv register.

For larger than 32-element tables in the hword case (for example 256 entries), the user must access the main lookup table in eight different 32 hword sections.

The following example is a 256H table stored naturally in memory:

```
63, 62,.........2, 1, 0
127,126,.......66, 65, 64
191,190,......130,129,128
255,254,......194,193,192
```

To prepare it for use with the `vlut` instruction in 64 byte mode, it must be shuffled in blocks of 16 hwords; the LSB of Rt is used to choose the even or odd 16 entry hword tables in Vv.

```
31, 15, 30, 14,......20, 4, 19, 3, 18, 2, 17, 1, 16, 0 Rt=0, Rt=1 63, 47, 62,
46,..... 52, 36, 51, 35, 50, 34, 49, 33, 48, 32 Rt=2, Rt=3
```

same ordering for bytes 64 through 255 `Rt=4, 5, 6, 7, 8, 9, 10,11,12,13,14,15 `

For 128 byte mode, the data must be shuffled in blocks of 32 hwords. Bit 1 of Rt is used to choose between the even or odd 32 hwords in Vv. Bit 0 accesses the high or low 16 half words of the odd or even set.

```
63, 31, 62, 30,........36, 4, 35, 3, 34, 2, 33, 1, 32, 0 Rt=0,1 Rt=2,3
```

Same ordering for bytes 128 through 255 `Rt=4,5, Rt=6,7, Rt=8,9, Rt=10,11, Rt=12,13, `

```
Rt=14,15
```

The following diagram shows the `vlut16` instruction with even bytes used to look up a table value, with the result written into the even destination register. Odd values go into the odd destination, 64 byte and 128 byte modes are shown.

Vdd.h = vlut16(Vu.b, Vv.h, Rt) / Vxx.h |= vlut16(Vu.b, Vv.h, Rt)

Odd bytes Even bytes

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| Bytes i = 63 to 9 | b[7] |  | b[5] |  | b[3] |  | b[1] |  |

Vu input Bytes

Rt b[6] b[4] b[2] b[0]

vector i = 62 to 8

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| Bytes i = 62 to 8 |  | b[6] |  | b[4] |  | b[2] |  | b[0] |
|  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  | == ? |

Bytes Vu input

Rt b[7] b[5] b[3] b[1]

i = 63 to 9 vector

Bits 7:4 Bits 7:4

Bits 3:0

Replicated for all other odd input bytes Replicated for all other even input bytes

== ?

|  |  |  |
|---|---|---|
|  |  |  |
|  |  |  |
| == ? |  |  |

Bits 7:4 Bits 7:4

Bits 3:0

Replicated for all other odd input bytes Replicated for all other even input bytes

== ?

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| b[i]/a[i] i = 15 to 4 | b[3] | a[3] | b[2] | a[2] | b[1] | a[1] | b[0] | a[0] |

Vv table

Vv table b[i]/a[i]

vector b[3] a[3] b[2] a[2] b[1] a[1] b[0] a[0]

vector i = 15 to 4

(copy)

Bits 31:4

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| b[i]/a[i] i = 15 to 4 | b[3] | a[3] | b[2] | a[2] | b[1] | a[1] | b[0] | a[0] |

Vv table

Vv table b[i]/a[i]

b[3] a[3] b[2] a[2] b[1] a[1] b[0] a[0] vector

vector i = 15 to 4

(copy)

Bits 31:4

|  |  |  |
|---|---|---|
|  |  |  |
| 1 | 1 | 0 |

To other selects Bit 0 To other selects Bit 0

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |  |
|---|---|---|
|  |  |  |
| 1 | 1 | 0 |

To other selects Bit 0 To other selects Bit 0

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| 1 | 0 |

1 0 1 0 1 0 1 0 1 0 1 0 1 0

|  |  |
|---|---|
| Other | Other |
| inputs | inputs |
| Bits 3:0 | Bits 3:0 |
| ‘0’ | ‘0’ |

|  |  |
|---|---|
| 1 | 0 |

1 0

|  |  |
|---|---|
| 1 | 0 |

1 0

Replicated for all other output bytes<sub>|</sub> Replicated for all other output bytes|

|  |  |
|---|---|
| h[31:1] | h[0] |

Vdd1/Vxx1 Vdd0/Vxx0

output output

h[31:1] h[0]

vector vector

|  |  |
|---|---|
| h[31:1] | h[0] |

Vdd1/Vxx1 Vdd0/Vxx0

output output

h[31:1] h[0]

vector vector

|  |  |
|---|---|
| Optional OR | Optional OR |
| accumulate | accumulate |

Vdd.h = vlut16(Vu.b, Vv.h, Rt) /Vxx.h |= vlut16(Vu.b, Vv.h, Rt)

|  |  |  |  |
|---|---|---|---|
| Bytes 127 to 2i+2 | B[2i+1] | B[2i] | Bytes 2i-1 to 0 |

128B MODEVu InputVector

Rt

bits 7 to 4 bits 3 to 0 bits 7 to 4 bits 3 to 0

|  |  |
|---|---|
|  |  |
| == ? |  |

Bits 3

downto 0

== ?

|  |  |
|---|---|
|  |  |
|  |  |
|  |  |

Bits 3

downto 0

== ? == ?

b[i]/a[i]

bh[1] ah[1] bh[0] ah[0]

i = 31 to 2

Vv Table

Vector

Bits 31 down to 4

(hwords)

hword select

Bit 1 – odd / even

To other selects

To other selects Bit 1

1 0 1 0

1 0 1 0

Other

inputs

Choose hi or lo 16 hwords Bit 0 Choose hi or lo 16 hwords

Bit 0 – hi or lo 16 hwords

from Vv

Bits 3 to 0

Bits 3 to 0 16 x 16 to 1 selects of input

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  |  |  | b[i]/a[i] i = 31 to 2 | bh[1] | bh[1] | ah[1] | ah[1] | bh[0] | ah[0] |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |

Vv Table

Vector

Bits 31 down to 4

(hwords)

hword select

Bit 1 – odd / even

To other selects

To other selects Bit 1

1 0 1 0

1 0 1 0

Other

inputs

Choose hi or lo 16 hwords Bit 0 Choose hi or lo 16 hwords

|  |  |
|---|---|
|  |  |
| 1 | 0 |

To other selects

To other selects Bit 1

1 0

1 0 1 0

|  |  |
|---|---|
|  |  |
| 1 | 0 |

To other selects

1 0 1 0

1 0

|  |  |  |
|---|---|---|
|  |  |  |
| 1 | 1 | 0 |

To other selects

1 0 1 0

1 0

|  |  |
|---|---|
| 16 x 16 to 1 selects | 16 x 16 to 1 selects |

Bits 3 to 0

Bits 3 to 0 of input

byte

‘0’ ‘0’

1 0 1 0

Replicated for all other Replicated for all other odd bytes<sup>|</sup> even bytes<sup>|</sup>

|  |  |  |  |  |
|---|---|---|---|---|
| H127 down to i+65 | H[i+ 64] | H[i+ 64] |  | H[i+62] down to H64 |
|  |  |  |  |  |

Vdd1/Vxx1 Vdd0/Vxx0

H[i-1]

Output H63 down to i+1 H[i] Output

down to 0

Vector Vector

Optional OR Optional OR

|  |  |  |  |  |
|---|---|---|---|---|
| H63 down to i+1 | H[i] | H[i] |  | H[i-1] down to 0 |
|  |  |  |  |  |

Vdd1/Vxx1 Vdd0/Vxx0

H[i+H[i+62] down

H127 down to i+65 Output Output

64]to H64

Vector Vector

Optional OR Optional OR

accumulate accumulate

`vlut` operations with the no match extension do not look at the upper bits, and always produce a result. These are for small lookup tables.

| Syntax | Behavior |
|---|---|
| `Vdd.h=vlut16(Vu.b,Vv.h,#u3)` | `for (i = 0; i < VELEM(16); i++) {`<br>`matchval = #u & 0xF;`<br>`oddhalf = (#u >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.uh[i].ub[0];`<br>`Vdd.v[0].h[i] = ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`idx = Vu.uh[i].ub[1];`<br>`Vdd.v[1].h[i] = ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`}` |
| `Vdd.h=vlut16(Vu.b,Vv.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`matchval = Rt & 0xF;`<br>`oddhalf = (Rt >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.uh[i].ub[0];`<br>`Vdd.v[0].h[i] = ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`idx = Vu.uh[i].ub[1];`<br>`Vdd.v[1].h[i] = ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`}` |
| `Vdd.h=vlut16(Vu.b,Vv.h,Rt):nomatch` | `for (i = 0; i < VELEM(16); i++) {`<br>`matchval = Rt & 0xF;`<br>`oddhalf = (Rt >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.uh[i].ub[0];`<br>`idx = (idx&0x0F) \| (matchval<<4);`<br>`Vdd.v[0].h[i] = Vv.w[idx % `<br>`VBITS/32].h[oddhalf];`<br>`idx = Vu.uh[i].ub[1];`<br>`idx = (idx&0x0F) \| (matchval<<4);`<br>`Vdd.v[1].h[i] = Vv.w[idx % `<br>`VBITS/32].h[oddhalf];`<br>`}` |
| `Vx.b\|=vlut32(Vu.b,Vv.b,#u3)` | `for (i = 0; i < VELEM(8); i++) {`<br>`matchval = #u & 0x7;`<br>`oddhalf = (#u >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.ub[i];`<br>`Vx.b[i] \|= ((idx & 0xE0) == (matchval `<br>`<< 5)) ? Vv.h[idx % VBITS/16].b[oddhalf] : `<br>`0;`<br>`}` |
| `Vx.b\|=vlut32(Vu.b,Vv.b,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`matchval = Rt & 0x7;`<br>`oddhalf = (Rt >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.ub[i];`<br>`Vx.b[i] \|= ((idx & 0xE0) == (matchval `<br>`<< 5)) ? Vv.h[idx % VBITS/16].b[oddhalf] : `<br>`0;`<br>`}` |
| `Vxx.h\|=vlut16(Vu.b,Vv.h,#u3)` | `for (i = 0; i < VELEM(16); i++) {`<br>`matchval = #u & 0xF;`<br>`oddhalf = (#u >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.uh[i].ub[0];`<br>`Vxx.v[0].h[i] \|= ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`idx = Vu.uh[i].ub[1];`<br>`Vxx.v[1].h[i] \|= ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`}` |
| `Vxx.h\|=vlut16(Vu.b,Vv.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`matchval = Rt.ub[0] & 0xF;`<br>`oddhalf = (Rt >> (log2(VECTOR_SIZE)-6)) `<br>`& 0x1;`<br>`idx = Vu.uh[i].ub[0];`<br>`Vxx.v[0].h[i] \|= ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`idx = Vu.uh[i].ub[1];`<br>`Vxx.v[1].h[i] \|= ((idx & 0xF0) == `<br>`(matchval << 4)) ? Vv.w[idx % `<br>`VBITS/32].h[oddhalf] : 0;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX permute resource
- Input scalar register Rt is limited to registers 0 through 7
- This instruction uses the HVX shift resource

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vlut16(Vu.b,Vv.h,#u3)` | `HVX_VectorPair Q6_Wh_vlut16_VbVhI (HVX_Vector Vu, HVX_Vector Vv, Word32 Iu3)` |
| `Vdd.h=vlut16(Vu.b,Vv.h,Rt)` | `HVX_VectorPair Q6_Wh_vlut16_VbVhR (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vdd.h=vlut16(Vu.b,Vv.h,Rt):nomatch` | `HVX_VectorPair Q6_Wh_vlut16_VbVhR_nomatch (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vx.b\|=vlut32(Vu.b,Vv.b,#u3)` | `HVX_Vector Q6_Vb_vlut32or_VbVbVbI (HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv, Word32 Iu3)` |
| `Vx.b\|=vlut32(Vu.b,Vv.b,Rt)` | `HVX_Vector Q6_Vb_vlut32or_VbVbVbR (HVX_Vector Vx, HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vxx.h\|=vlut16(Vu.b,Vv.h,#u3)` | `HVX_VectorPair Q6_Wh_vlut16or_WhVbVhI (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv, Word32 Iu3)` |
| `Vxx.h\|=vlut16(Vu.b,Vv.h,Rt)` | `HVX_VectorPair Q6_Wh_vlut16or_WhVbVhR (HVX_VectorPair Vxx, HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vdd.h=vlut16(Vu.b,Vv.h,Rt): nomatch |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.b\|=vlut32(Vu.b,Vv.b,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vdd.h=vlut16(Vu.b,Vv.h,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vxx.h\|=vlut16(Vu.b,Vv.h,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | i | i | i | x | x | x | x | x | Vx.b\|=vlut32(Vu.b,Vv.b,#u3 ) |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | i | i | i | x | x | x | x | x | Vxx.h\|=vlut16(Vu.b,Vv.h,#u 3) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | i | i | i | d | d | d | d | d | Vdd.h=vlut16(Vu.b,Vv.h,#u 3) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t3` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `v3` | Field to encode register v |
| `v5` | Field to encode register v |
| `x5` | Field to encode register x |

#### Unpack

The unpack operation has two forms.

The first form takes each element in vector register Vu and either zero or sign extends it to the next largest element size. The results are written into the vector register Vdd. This operation supports the unpacking of signed or unsigned byte to halfword, signed or unsigned halfword to word, and unsigned word to unsigned double.

The second form inserts elements from Vu into the odd element locations of Vxx. The even elements of Vxx do not change. This operation supports the unpacking of signed or unsigned byte to halfword, and signed or unsigned halfword to word.

Vdd.h=vunpack(Vu.b)

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| [N-1] | ... | [3] | [2] | [1] | [0] |

Vu

|  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|
| sign | [2N-1] | ... | sign | [6] | sign | [4] | sign | [2] | sign | [0] |

Vdd

Vxx.h|=vunpacko(Vu.b)

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| [N-1] | ... | [4] | [3] | [2] | [1] | [0] |

Vu

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [2N-1] | [2N-2] | ... | [9] | [8] | [7] | [6] | [5] | [4] | [3] | [2] | [1] | [0] |

Vxx

Unmodified

| Syntax | Behavior |
|---|---|
| `Vdd.h=vunpack(Vu.b)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.h[i] = Vu.b[i];`<br>`}` |
| `Vdd.uh=vunpack(Vu.ub)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vdd.uh[i] = Vu.ub[i];`<br>`}` |
| `Vdd.uw=vunpack(Vu.uh)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.uw[i] = Vu.uh[i];`<br>`}` |
| `Vdd.w=vunpack(Vu.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vdd.w[i] = Vu.h[i];`<br>`}` |
| `Vxx.h\|=vunpacko(Vu.b)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vxx.uh[i] \|= Vu.ub[i]<<8;`<br>`}` |
| `Vxx.w\|=vunpacko(Vu.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vxx.uw[i] \|= Vu.uh[i]<<16;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX permute resource.
- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vdd.h=vunpack(Vu.b)` | `HVX_VectorPair Q6_Wh_vunpack_Vb(HVX_Vector Vu)` |
| `Vdd.uh=vunpack(Vu.ub)` | `HVX_VectorPair Q6_Wuh_vunpack_Vub(HVX_Vector Vu)` |
| `Vdd.uw=vunpack(Vu.uh)` | `HVX_VectorPair Q6_Wuw_vunpack_Vuh(HVX_Vector Vu)` |
| `Vdd.w=vunpack(Vu.h)` | `HVX_VectorPair Q6_Ww_vunpack_Vh(HVX_Vector Vu)` |
| `Vxx.h\|=vunpacko(Vu.b)` | `HVX_VectorPair Q6_Wh_vunpackoor_WhVb(HVX_VectorPair Vxx, HVX_Vector Vu)` |
| `Vxx.w\|=vunpacko(Vu.h)` | `HVX_VectorPair Q6_Ww_vunpackoor_WwVh(HVX_VectorPair Vxx, HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vdd.uh=vunpack(Vu.ub) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vdd.uw=vunpack(Vu.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vdd.h=vunpack(Vu.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 0 | 1 | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vdd.w=vunpack(Vu.h) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | x | x | x | x | x | Vxx.h\|=vunpacko(Vu.b) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | x | x | x | x | x | Vxx.w\|=vunpacko(Vu.h) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |
