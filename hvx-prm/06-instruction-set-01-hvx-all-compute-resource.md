# 6 Instruction set

Instructions are listed alphabetically within instruction categories. The following information is provided for each instruction:

- Instruction name
- A brief description of the instruction
- A high-level functional description (syntax and behavior) with all possible operand types
- Instruction class and slot information for grouping instructions in packets
- Notes on miscellaneous issues
- C intrinsic functions that provide access to the instruction
- Instruction encoding

Table 6-1 lists the symbols used to specify the instruction syntax.

**Table 6-1  Instruction syntax symbols**

| Symbol | Example | Meaning |
|---|---|---|
| = | R2 = R3; | Assignment of RHS to LHS |
| ; | R2 = R3; | Marks the end of an instruction or group of instructions |
| { … } | {R2 = R3; R5 = R6;} | Indicates a group of parallel instructions. |
| # | #100 | Immediate constant value |
| 0x | R2 = #0x1fe; | Indicates hexadecimal number |
| :sat | R2 = add(r1,r2):sat | Perform optional saturation |
| :rnd | R2 = mpy(r1.h,r2.h):rnd | Perform optional rounding |

Table 6-2 lists the symbols used to specify instruction operands.

**Table 6-2  Instruction operand symbols**

| Symbol | Example | Meaning |
|---|---|---|
| #uN | R2 = #u16 | Unsigned N-bit immediate value |
| #sN | R2 = add(R3,#s16) | Signed N-bit immediate value |
| #mN | Rd = mpyi(Rs,#m9) | Signed N-bit immediate value |
| #uN:S | R2 = memh(#u16:1) | Unsigned N-bit immediate value representing integral multiples of 2S in specified range |
| #sN:S | Rd = memw(Rs++#s4:2) | Signed N-bit immediate value representing integral multiples of 2S in specified range |
| #rN:S | call #r22:2 | Same as #sN:S, but value is offset from PC of current packet |
| ## | call ##32 | Same as #, but associated value (u,s,m,r) is 32 bits |

When an instruction contains more than one immediate operand, the operand symbols are specified in upper and lower case (for example, #uN and #UN) to indicate where they appear in the instruction encodings.

The instruction behavior is specified using a superset of the C language. Table 6-3 lists symbols not defined in C that specify the instruction behavior.

**Table 6-3  Instruction behavior symbols**

| Symbol | Example | Meaning |
|---|---|---|
| usat_N | usat_16(Rs) | Saturate a value to an unsigned N-bit |
| sat_N | sat_16(Rs) | Saturate a value to a signed N-bit number |
| sxt x->y | sxt32->64(Rs) | Sign-extend value from x to y bits |
| zxt x->y | zxt32->64(Rs) | Zero-extend value from x to y bits |
| >>> | Rss >>> offset | Logical right shift |

## 6.1 HVX ALL COMPUTE-RESOURCE

The HVX ALL COMPUTE-RESOURCE instruction subclass includes ALU instructions that use a pair

of HVX resources.

#### Histogram

The `vhist` instructions use all of the HVX core resources: the register file, V0 through V31, and all four instruction pipes. The instruction also takes four execution packets to complete.

The basic unit of the histogram instruction is four or eight 128-bit wide slices, depending on the particular configuration. The 32 vector registers are configured as multiple 256-entry histograms, where each histogram bin has a width of 16 bits. This allows up to 65,535 8-bit elements of the same value to accumulate.

Each histogram is 128 bits wide and 32 elements deep, for a total of 256 histogram bins. A vector is read from memory and stored in a temporary location outside of the register file. The data read is then divided equally between the histograms.

For example:

Bytes 0 to 15 are profiled into bits 0 to 127 of all 32 vector registers, histogram 0.

Bytes 16 to 31 are profiled into bits 128 to 255 of all 32 vector registers, histogram 1.

... and so on.

The bytes process over multiple cycles to update the histogram bins. For each of the histogram slices, the lower three bits of each byte element in the 128-bit slice is used to select the 16-bit position, while the upper 5 bits select the vector register. The register file entry is then incremented by one.

The `vhist` instruction is the only instruction that occupies all pipes and resources.

Before use, the vector register file must be cleared to begin a new histogram, otherwise the current state is added to the histograms of the next data.

The `vhist` instruction supports the same addressing modes as standard loads. In addition, a byte-enabled version is available that enables the selection of the elements used in the accumulation.

The following diagram shows a single 8-bit element in position 2 of the source data. The value is 124, the register number assigned to this is 124 >> 3 = V15, and the element number in the register is 124 & 7 = 4. The byte position in the example is 2, which is in the first 16 bytes of the input line from memory, so the data affects the first 128-bit wide slice of the register file. The 16-bit histogram bin location is then incremented by 1. Each 64-bit input group of bytes affects the respective 128-bit histogram slice.

For a 64-byte vector size, peak total consumption is 64(bytes per vector)/4(packets per operation) * 4(threads) = 64 bytes per clock cycle per core, assuming threads are performing histogramming.

vhist(Qv4)

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|  | b[31:16] | b[15] | b[14:3] | b[2] =124 | b[1] | b[0] |

Line from

memory

|  |  |  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Multiple data path slices | Histogram data path 1 | Histogram data path 1 | & 0x7 >>3<br>Histogram<br>data path 0<br>Element select Register select |  |  |  |  |  |  |  |  |
| Vector register file V0-V31 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  | h[15:8] | h[15:8] | h[7] | h[6] | h[5] | h[4] | h[4] | h[3] | h[2] | h[1] | h[0] |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |

V31

Increment element +

V15

V1-V30

Histogram 1 storage Histogram 0 storage

V0

|  |  |
|---|---|
|  | V1-V30 |

V0-V31

| Syntax | Behavior |
|---|---|
| `vhist` | `inputVec=Data from .tmp load;`<br>`for (lane = 0; lane < VELEM(128); lane++) {`<br>`for (i=0; i<128/8; ++i) {`<br>`unsigned char value = inputVec.ub [(128/8)*lane+i];`<br>`unsigned char regno = value>>3;`<br>`unsigned char element = value & 7;`<br>`READ_EXT_VREG(regno,tmp,0);`<br>`tmp.uh[(128/16)*lane+(element)]++;`<br>`WRITE_EXT_VREG(regno,tmp,EXT_NEW);`<br>`}`<br>`}` |
| `vhist(Qv4)` | `inputVec=Data from .tmp load;`<br>`for (lane = 0; lane < VELEM(128); lane++) {`<br>`for (i=0; i<128/8; ++i) {`<br>`unsigned char value = inputVec.ub[(128/8)*lane+i];`<br>`unsigned char regno = value>>3;`<br>`unsigned char element = value & 7;`<br>`READ_EXT_VREG(regno,tmp,0);`<br>`if (QvV[128/8*lane+i]) tmp.uh[(128/16)* `<br>`lane+(element)]++;`<br>`WRITE_EXT_VREG(regno,tmp,EXT_NEW);`<br>`}`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | - | 0 | 0 | 0 | - | 1 | 0 | 0 | - | - | - | - | - | vhist |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | - | - | 0 | 0 | - | 1 | 0 | 0 | - | - | - | - | - | vhist(Qv4) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `v2` | Field to encode register v |

#### Weighted histogram

The `vwhist `instructions use all of the HVX core resources: the register file, V0 through V31, and all four instruction pipes. The instruction also takes four execution packets to complete.

The basic unit of the histogram instruction is four or eight 128-bit wide slices, depending on the particular configuration.

The 32 vector registers are configured as multiple 256-entry histograms for the `vwhist256` instruction, where each histogram bin has a width of 16 bits. Each histogram is 128 bits wide and 32 elements deep, for a total of 256 histogram bins.

For the `vwhist128` instruction, the 32 vector registers are configured as multiple 128-entry histograms where each histogram bin has a width of 32 bits. Each histogram is 128 bits wide and 16 elements deep, giving a total of 128 histogram bins.

A vector is read from memory and stored in a temporary location, outside of the register file. The vector carries both the weight and the data that is used for the index into the histogram. The data occupies the even byte of each halfword and the weight the odd byte of each halfword. The data read is then divided equally between the histograms.

For example:

Even bytes 0 to 15 profile into bits 0 to 127 of all 32 vector registers, histogram 0.

Even bytes 16 to 31 profile into bits 128 to 255 of all 32 vector registers, histogram 1.

... and so on.

The bytes process over multiple cycles to update the histogram bins. For each of the histogram slices in the `vwhist256` instruction, the lower three bits of each even byte element in the 128-bit slice is used to select the 16-bit position, while the upper five bits select the vector register.

For each of the histogram slices in the `vwhist128` instruction, bits 2:1 of each even byte element in the 128-bit slice are used to select the 32-bit position, while the upper five bits select the vector register. The LSB of the bye is ignored.

The register file entry is then incremented by corresponding weight from the odd byte.

Like the `vhist` instruction, `vwhist` also occupies all pipes and resources.

Before use, the vector register file must be cleared to begin a new histogram, otherwise the current state is added to the histograms of the next data.

The `vwhist` instruction supports the same addressing modes as standard loads. A byte-enabled version is available that enables selection of the elements used in the accumulation.

The following diagram shows a single 8-bit element in byte position 2 of the source data with corresponding weight in byte position 3. The value is 124, the register number assigned to this is 124 >> 3 = V15, and the element number in the register is 124 & 7 = 4. The byte position in the example is 2, which is in the first 16 bytes of the input line from memory, so the data affects the first 128-bit wide slice of the register file. The 16-bit histogram bin location is then incremented by the weight from byte position 3. Each 64-bit input group of bytes affects the respective 128-bit histogram slice.

For a 64-byte vector size, peak total consumption is 64(bytes per vector)/4(packets per operation) * 4(threads) = 64 bytes per clock cycle per core, assuming all threads are performing histogramming.

VWHIST128(Rt/Rx+#I)

|  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|
|  | b31 down to b16 | b15 | b14 down to b3 | b3= 6 | b2 = 124 | b1 | b0 |

Line From

Memory

|  |  |  |
|---|---|---|
| Multiple Datapath Slices | Histogram Datapath 1<br>Histogram Datapath 0 | & 0x7 >>3<br>Element Select<br>Register Select |
| Vector Register File V0-V31 |  |  |
|  |  |  |

V31

Increment

element by

weight

+

h15 down to h8 h[7] h[6] h[5] h[4] h[3] h[2] h[1] h[0] V15

V1-V30

Histogram 1 Storage Histogram 0 Storage

V0

|  |  |
|---|---|
| & 0x7 | >>3 |

|  |  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
| h15 down to h8 | h[7] | h[6] | h[5] | h[4] | h[4] | h[3] | h[2] | h[1] | h[0] |
|  |  |  |  |  |  |  |  |  |  |

V15

Vector Register File

|  |  |
|---|---|
|  | V1-V30 |

V0-V31

| Syntax | Behavior |
|---|---|
| `vwhist128` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>1) & (~3)) \| ((bucket>>1) & 3);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`tmp.uw[elindex] = (tmp.uw[elindex] + weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist128(#u1)` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>1) & (~3)) \| ((bucket>>1) & 3);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`if ((bucket & 1) == #u) tmp.uw[elindex] = `<br>`(tmp.uw[elindex] + weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist128(Qv4)` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>1) & (~3)) \| ((bucket>>1) & 3);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`if (QvV[2*i])tmp.uw[elindex] = (tmp.uw[elindex] + `<br>`weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);;`<br>`}` |
| `vwhist128(Qv4,#u1)` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>1) & (~3)) \| ((bucket>>1) & 3);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`if (((bucket & 1) == #u) && QvV[2*i]) `<br>`tmp.uw[elindex] = (tmp.uw[elindex] + weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist256` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>0) & (~7)) \| ((bucket>>0) & 7);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`tmp.uh[elindex] = (tmp.uh[elindex] + weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist256(Qv4)` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>0) & (~7)) \| ((bucket>>0) & 7);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`if (QvV[2*i]) tmp.uh[elindex] = (tmp.uh[elindex] + `<br>`weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist256(Qv4):sat` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>0) & (~7)) \| ((bucket>>0) & 7);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`if (QvV[2*i]) tmp.uh[elindex] = `<br>`usat₁₆(tmp.uh[elindex] + weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |
| `vwhist256:sat` | `input = Data from .tmp load;`<br>`{`<br>`for (i = 0; i < VELEM(16); i++) {`<br>`bucket = input.h[i].ub[0];`<br>`weight = input.h[i].ub[1];`<br>`vindex = (bucket >> 3) & 0x1F;`<br>`elindex = ((i>>0) & (~7)) \| ((bucket>>0) & 7);`<br>`READ_EXT_VREG(vindex,tmp,0);`<br>`tmp.uh[elindex] = usat₁₆(tmp.uh[elindex] + `<br>`weight);`<br>`WRITE_EXT_VREG(vindex,tmp,EXT_NEW);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | - | 0 | 0 | 1 | 0 | 1 | 0 | 0 | - | - | - | - | - | vwhist256 |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | - | 0 | 0 | 1 | 1 | 1 | 0 | 0 | - | - | - | - | - | vwhist256:sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | - | 0 | 1 | 0 | - | 1 | 0 | 0 | - | - | - | - | - | vwhist128 |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 0 | 0 | 0 | P | P | 1 | - | 0 | 1 | 1 | i | 1 | 0 | 0 | - | - | - | - | - | vwhist128(#u1) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | - | - | 0 | 1 | 0 | 1 | 0 | 0 | - | - | - | - | - | vwhist256(Qv4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | - | - | 0 | 1 | 1 | 1 | 0 | 0 | - | - | - | - | - | vwhist256(Qv4):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | - | - | 1 | 0 | - | 1 | 0 | 0 | - | - | - | - | - | vwhist128(Qv4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 0 | P | P | 1 | - | - | 1 | 1 | i | 1 | 0 | 0 | - | - | - | - | - | vwhist128(Qv4,#u1) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `v2` | Field to encode register v |
