# 2 Registers

HVX is a load-store architecture where compute operands originate from registers and load/store instructions move data between memory and registers.

The vector registers are not for addressing or control information, but rather hold intermediate vector computation results. They are only accessible using HVX compute or load/store instructions.

The vector predicate registers contain the decision bits for each 8-bit quantity of the vector data registers.

## 2.1 Vector data registers

The HVX coprocessor contains 32 vector registers (named V0 through V31). These registers store operand data for the vector instructions.

For example:

|  |  |
|---|---|
| `V1 = vmem(R0)` | `// Load a vector of data// from address R0` |
| `V4.w = vadd(V2.w, V3.w)` | `// Add each word in V2 // to corresponding word in V3` |

The vector data registers can be specified as register pairs representing a double-vector of data.

For example:

```
V5:4.w = vadd(V3:2.w, V1:0.w) // Add each word in V1:0 to
                              // corresponding word in V3:2
```

### 2.1.1 Unaligned vector pairs

Starting with V69, unaligned pairs are supported for vector pair register operands.

For example:

```
v6:7.b = vadd(v2:3.b, v4:5.b)    // Add vector pairs of bytes
v0:1.h = vadd(v12:13.h, v5:4.h)  // Add vector pairs of halfwords
```

### 2.1.2 VRF to GRF transfers

Table 2-1 lists the Hexagon instructions that transfer values between the vector register file (VRF) and the general register file (GRF).

A packet can contain up to two insert instructions or one extract instruction. The extract instruction incurs a long-latency stall and is primarily meant for debug purposes.

**Table 2-1  VRF to GRF transfer instructions**

| Syntax | Behavior | Description |
|---|---|---|
| `Rd.w=extractw(Vu,Rs) ` | Rd = Vu.uw[Rs & 0xF]; | Extract word from a vector into Rd with location specified by Rs. Primarily meant for debug. |
| `Vx.w=insertw(Rss) ` | Vx.uw[Rss.w[1] & 0xF] = Rss.w[0]; | Insert word into vector at specified location. The low word in Rss specifies the data to insert, and the upper word specifies the location. |

## 2.2 Vector predicate registers

Vector predicate registers hold the result of vector compare instructions, for example:

```
Q3 = vcmp.eq(V2.w, V5.w)
```

This example compares each 32-bit field of V2 and V5 and the corresponding 4-bit field is set in the corresponding predicate register Q3. For half-word operations, two bits are set per half-word. For byte operations, one bit is set per byte.

The `vmux` instruction frequently uses vector predicate instruction. This takes each bit in the predicate register and selects the first or second byte in each source, and places it in the corresponding destination output field.

```
V4 = vmux(Q2, V5, V6)
```
