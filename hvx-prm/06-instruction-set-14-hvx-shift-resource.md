## 6.14 HVX SHIFT RESOURCE

The HVX SHIFT RESOURCE instruction subclass includes instructions that use the HVX shift

resource.

#### Narrowing shift

Arithmetically shift-right the elements in vector registers Vu and Vv by the lower bits of the scalar register Rt. Each result is optionally saturated, rounded to infinity, and packed into a single destination vector register. Each even element in the destination vector register Vd comes from the vector register Vv, and each odd element in Vd comes from the vector register Vu.

Vd.h=vasr(Vu.w,Vv.w,Rt)[:rnd][:sat]

|  |  |
|---|---|
| [1] | [0] |

[N-1] Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | [1] |  | [0] |

[N-1] Vv

|  |  |
|---|---|
|  | [N-1] |

[1] [0] Vv

rnd rnd rnd rnd rnd rnd Optional round

Arithmetic

>>Rt >>Rt >>Rt >>Rt >>Rt >>Rt

shift by Rt

Optional saturate to next

sat sat sat sat sat sat

smaller element limits

|  |  |
|---|---|
| [2N-1] | [2N-2] |

[3][2][1][0] Vd

|  |  |  |  |
|---|---|---|---|
| [3] | [2] | [1] | [0] |

[2N-1][2N-2] Vd

| Syntax | Behavior |
|---|---|
| `Vd.b=vasr(Vu.h,Vv.h,Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.h[i].b[0]=sat₈(Vv.h[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`Vd.h[i].b[1]=sat₈(Vu.h[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`}` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=sat₁₆(Vv.w[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`Vd.w[i].h[1]=sat₁₆(Vu.w[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`}` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=[sat₁₆](Vv.w[i] >> shamt);`<br>`Vd.w[i].h[1]=[sat₁₆](Vu.w[i] >> shamt);`<br>`}` |
| `Vd.ub=vasr(Vu.h,Vv.h,Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.h[i].b[0]=usat₈(Vv.h[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`Vd.h[i].b[1]=usat₈(Vu.h[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`}` |
| `Vd.ub=vasr(Vu.uh,Vv.uh,Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.uh[i].b[0]=usat₈(Vv.uh[i] + (1<<(shamt-`<br>`1)) >> shamt);`<br>`Vd.uh[i].b[1]=usat₈(Vu.uh[i] + (1<<(shamt-`<br>`1)) >> shamt);`<br>`}` |
| `Vd.uh=vasr(Vu.uw,Vv.uw,Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.uw[i].h[0]=usat₁₆(Vv.uw[i] + (1<<(shamt-`<br>`1)) >> shamt);`<br>`Vd.uw[i].h[1]=usat₁₆(Vu.uw[i] + (1<<(shamt-`<br>`1)) >> shamt) ;`<br>`}` |
| `Vd.uh=vasr(Vu.w,Vv.w,Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=usat₁₆(Vv.w[i] + (1<<(shamt-1)) `<br>`>> shamt);`<br>`Vd.w[i].h[1]=usat₁₆(Vu.w[i] + (1<<(shamt-1)) `<br>`>> shamt) ;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- Input scalar register Rt is limited to registers 0 through 7
- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vasr(Vu.h,Vv.h,Rt):rnd:sat` | `HVX_Vector Q6_Vb_vasr_VhVhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.b=vasr(Vu.h,Vv.h,Rt):sat` | `HVX_Vector Q6_Vb_vasr_VhVhR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt)` | `HVX_Vector Q6_Vh_vasr_VwVwR(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat` | `HVX_Vector Q6_Vh_vasr_VwVwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt):sat` | `HVX_Vector Q6_Vh_vasr_VwVwR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.h,Vv.h,Rt):rnd:sat` | `HVX_Vector Q6_Vub_vasr_VhVhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.h,Vv.h,Rt):sat` | `HVX_Vector Q6_Vub_vasr_VhVhR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.uh,Vv.uh,Rt):rnd:sat` | `HVX_Vector Q6_Vub_vasr_VuhVuhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.uh,Vv.uh,Rt):sat` | `HVX_Vector Q6_Vub_vasr_VuhVuhR_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.uw,Vv.uw,Rt):rnd:sat` | `HVX_Vector Q6_Vuh_vasr_VuwVuwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.uw,Vv.uw,Rt):sat` | `HVX_Vector Q6_Vuh_vasr_VuwVuwR_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.w,Vv.w,Rt):rnd:sat` | `HVX_Vector Q6_Vuh_vasr_VwVwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.w,Vv.w,Rt):sat` | `HVX_Vector Q6_Vuh_vasr_VwVwR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vasr(Vu.h,Vv.h,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uh=vasr(Vu.uw,Vv.uw,Rt ):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vasr(Vu.w,Vv.w,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.uh,Vv.uh,Rt ):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.uh=vasr(Vu.uw,Vv.uw,Rt ):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.uh,Vv.uh,Rt ):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.uh=vasr(Vu.w,Vv.w,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.ub=vasr(Vu.h,Vv.h,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.h,Vv.h,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vasr(Vu.h,Vv.h,Rt):rnd:sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `t3` | Field to encode register t |
| `u5` | Field to encode register u |
| `v2` | Field to encode register v |
| `v3` | Field to encode register v |

#### Compute contiguous offsets for valid positions

Perform a cumulative sum of the bits in the predicate register.

Vd32.h = prefixsum(qv4)

|  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
| ... | q[5] | q[4] | q[3] | q[2] | q[1] | q[0] |

Qv

+ + +

Remained of the + adders

+

|  |  |  |  |
|---|---|---|---|
| ... | h[2] | h[1] | h[0] |

Vd

| Syntax | Behavior |
|---|---|
| `Vd.b=prefixsum(Qv4)` | `for (i = 0; i < VELEM(8); i++) {`<br>`acc += QvV[i];`<br>`Vd.ub[i] = acc;`<br>`}` |
| `Vd.h=prefixsum(Qv4)` | `for (i = 0; i < VELEM(16); i++) {`<br>`acc += QvV[i*2+0];`<br>`acc += QvV[i*2+1];`<br>`Vd.uh[i] = acc;`<br>`}` |
| `Vd.w=prefixsum(Qv4)` | `for (i = 0; i < VELEM(32); i++) {`<br>`acc += QvV[i*4+0];`<br>`acc += QvV[i*4+1];`<br>`acc += QvV[i*4+2];`<br>`acc += QvV[i*4+3];`<br>`Vd.uw[i] = acc;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=prefixsum(Qv4)` | `HVX_Vector Q6_Vb_prefixsum_Q(HVX_VectorPred Qv)` |
| `Vd.h=prefixsum(Qv4)` | `HVX_Vector Q6_Vh_prefixsum_Q(HVX_VectorPred Qv)` |
| `Vd.w=prefixsum(Qv4)` | `HVX_Vector Q6_Vw_prefixsum_Q(HVX_VectorPred Qv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  |  |  |  |  |  |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 1 | P | P | 1 | - | - | 0 | 0 | 0 | 0 | 1 | 0 | d | d | d | d | d | Vd.b=prefixsum(Qv4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 1 | P | P | 1 | - | - | 0 | 0 | 1 | 0 | 1 | 0 | d | d | d | d | d | Vd.h=prefixsum(Qv4) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | v | v | 0 | - | - | 0 | 1 | 1 | P | P | 1 | - | - | 0 | 1 | 0 | 0 | 1 | 0 | d | d | d | d | d | Vd.w=prefixsum(Qv4) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `v2` | Field to encode register v |

#### Add half precision vector by vector

These instructions perform a vectorized half precision floating point add. The inputs are either both IEEE single precision, both 16-bit Qfloat, or one of each. The result is a 16-bit Qfloat vector.

| Syntax | Behavior |
|---|---|
| `Vd.qf16=vadd(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.hf[i];`<br>`v = Vv.hf[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-`<br>`(FRAC_HF+1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-`<br>`(FRAC_HF+1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`if((u.sign^v.sign)==0){`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+sig_v : `<br>`(sig_v-sig)+sig_u;`<br>`} else if((u.sign==0) && (v.sign==1)) {`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-sig_v : `<br>`sig_u-(sig_v+sig);`<br>`} else{`<br>`sig = sig_v - sig_u;`<br>`sig_low = (v.exp>u.exp) ? (sig_v-sig)-sig_u : `<br>`sig_v-(sig_u+sig);`<br>`}`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`if(u.sign && v.sign) Vd.qf16[i] = -(Vd.qf16[i]) ;`<br>`}` |
| `Vd.qf16=vadd(Vu.qf16,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.hf[i];`<br>`if(v.sign) v.sig = (-1.0)*v.sig;`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-`<br>`(FRAC_HF+1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-`<br>`(FRAC_HF+1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+sig_v : `<br>`(sig_v-sig)+sig_u;`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf16 = vadd(Vu.qf16, `<br>`Vv.qf16)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.qf16[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_HF+ 1 `<br>`)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_HF+1 `<br>`)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+sig_v : `<br>`(sig_v-sig) + sig_u;`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf16=vadd(Vu.hf,Vv.hf)` | `HVX_Vector Q6_Vqf16_vadd_VhfVhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vadd(Vu.qf16,Vv.hf)` | `HVX_Vector Q6_Vqf16_vadd_Vqf16Vhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vadd(Vu.qf16,Vv.qf16)` | `HVX_Vector Q6_Vqf16_vadd_Vqf16Vqf16(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.qf16=vadd(Vu.qf16,Vv.q f16) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.qf16=vadd(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.qf16=vadd(Vu.qf16,Vv.h f) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Add single precision vector by vector

These instructions perform a vectorized single precision floating point add. The inputs are either both IEEE single precision, both 32-bit Qfloat, or one of each. The result is a 32-bit Qfloat vector.

| Syntax | Behavior |
|---|---|
| `Vd.qf32=vadd(Vu.qf32,Vv.qf32)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`v = Vv.qf32[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+sig_v `<br>`: (sig_v-sig)+sig_u;`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf32=vadd(Vu.qf32,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`v = Vv.sf[i];`<br>`if(v.sign) v.sig = (-1.0)*v.sig;`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+sig_v `<br>`: (sig_v-sig)+sig_u;`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf32=vadd(Vu.sf,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.sf[i];`<br>`v = Vv.sf[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-`<br>`(FRAC_SF+1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`if((u.sign^v.sign)==0){`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-`<br>`sig)+sig_v : (sig_v-sig)+sig_u;`<br>`} else if((u.sign==0) && (v.sign==1)) {`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-`<br>`sig_v : sig_u-(sig_v+sig);`<br>`} else{`<br>`sig = sig_v - sig_u;`<br>`sig_low = (v.exp>u.exp) ? (sig_v-sig)-`<br>`sig_u : sig_v-(sig_u+sig);`<br>`}`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`if(u.sign && v.sign) Vd.qf32[i] = -`<br>`(Vd.qf32[i]);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf32=vadd(Vu.qf32,Vv.qf32)` | `HVX_Vector Q6_Vqf32_vadd_Vqf32Vqf32(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf32=vadd(Vu.qf32,Vv.sf)` | `HVX_Vector Q6_Vqf32_vadd_Vqf32Vsf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf32=vadd(Vu.sf,Vv.sf)` | `HVX_Vector Q6_Vqf32_vadd_VsfVsf(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.qf32=vadd(Vu.qf32,Vv.q f32) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.qf32=vadd(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.qf32=vadd(Vu.qf32,Vv.s f) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Shift and add

Each element in the vector register Vu is arithmetically shifted right by the value specified by the lower bits of the scalar register Rt. The result is then added to the destination vector register Vx. For signed word shifts, the lower 5 bits of Rt specify the shift amount.

The left shift does not saturate the result to the element size.

Vx.w += vasr(Vu.w,Rt)

|  |  |
|---|---|
| w[1] | w[0] |

w[N-1] Vu

Shift right, and

>> >> >> sign fill, by lower

5 bits of Rt

+ + +

|  |  |
|---|---|
|  | w[N-1] |
|  |  |

w[1] w[0] Vx

|  |  |  |  |
|---|---|---|---|
|  | w[1] |  | w[0] |
|  |  |  |  |

w[N-1] Vx

*N is the number of operations implemented in each vector

Vx.w += vasl(Vu.w,Rt)

|  |  |
|---|---|
| w[1] | w[0] |

w[N-1] Vu

Shift by lower

<< << <<

5 bits of Rt

+ + +

|  |  |
|---|---|
|  | w[N-1] |
|  |  |

w[1] w[0] Vx

|  |  |  |  |
|---|---|---|---|
|  | w[1] |  | w[0] |
|  |  |  |  |

w[N-1] Vx

*N is the number of operations implemented in each vector

| Syntax | Behavior |
|---|---|
| `Vx.h+=vasl(Vu.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i] += (Vu.h[i] << (Rt & (16-1)));`<br>`}` |
| `Vx.h+=vasr(Vu.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vx.h[i] += (Vu.h[i] >> (Rt & (16-1)));`<br>`}` |
| `Vx.w+=vasl(Vu.w,Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i] << (Rt & (32-1)));`<br>`}` |
| `Vx.w+=vasr(Vu.w,Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vx.w[i] += (Vu.w[i] >> (Rt & (32-1)));`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vx.h+=vasl(Vu.h,Rt)` | `HVX_Vector Q6_Vh_vaslacc_VhVhR(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.h+=vasr(Vu.h,Rt)` | `HVX_Vector Q6_Vh_vasracc_VhVhR(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vasl(Vu.w,Rt)` | `HVX_Vector Q6_Vw_vaslacc_VwVwR(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |
| `Vx.w+=vasr(Vu.w,Rt)` | `HVX_Vector Q6_Vw_vasracc_VwVwR(HVX_Vector Vx, HVX_Vector Vu, Word32 Rt)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | x5 | x5 | x5 | x5 | x5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 1 | 0 | x | x | x | x | x | Vx.w+=vasl(Vu.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.w+=vasr(Vu.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | x | x | x | x | x | Vx.h+=vasr(Vu.h,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | t | t | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | x | x | x | x | x | Vx.h+=vasl(Vu.h,Rt) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `t5` | Field to encode register t |
| `u5` | Field to encode register u |
| `x5` | Field to encode register x |

#### Shift

Each element in the vector register Vu is arithmetically (logically) shifted right (left) by the value specified in the lower bits of the corresponding element of vector register Vv (or scalar register Rt). The lower four bits are for halfword shifts, while word shifts use the lower five bits.

The logical left shift does not saturate the result to the element size.

Vd.w=vlsr(Vu.w,Rt)

Rt Rt

|  |  |
|---|---|
| [N-1] | Don’t care |

Don’t

[0] Vu

care

|  |  |
|---|---|
| [0] | Don’t care |

Don’t

[N-1] Vu

care

Logical

N-1 to 1 Shift by Rt

|  |  |
|---|---|
| Zero fill | [N-1] |

Zero fill [0] Vd

|  |  |
|---|---|
| Zero fill | [0] |

Zero fill [N-1] Vd

Vd.w=vasl(Vu.w,Rt)

Rt Rt

|  |  |  |
|---|---|---|
| Don’t care | [N-1] | [N-1] |
|  |  |  |
| [N-1] | [N-1] | Zero fill |

Don’t

[0] Vu

care

Shift left

N-1 to 1 by Rt

[0] Zero fill Vd

|  |  |  |
|---|---|---|
| Don’t care | [0] | [0] |
|  |  |  |
| [0] | [0] | Zero fill |

Don’t

[N-1] Vu

care

Shift left

N-1 to 1 by Rt

[N-1] Zero fill Vd

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- Input scalar register Rt is limited to registers 0 through 7

| Syntax | Behavior |
|---|---|
| `Vd.b= vasr(Vu.h, Vv.h, `<br>`Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.h[i].b[0]=sat₈(Vv.h[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`Vd.h[i].b[1]=sat₈(Vu.h[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`}` |
| `Vd.h=vasl(Vu.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] << (Rt & (16-1)));`<br>`}` |
| `Vd.h=vasl(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (sxt<sub>(4+1)->16</sub>(Vv.h[i]) >0)?(Vu.h[i] << `<br>`sxt<sub>(4+1)->16</sub>(Vv.h[i])):(Vu.h[i]>>sxt<sub>(4+1)->16</sub>(Vv.h[i]));`<br>`}` |
| `Vd.h=vasr(Vu.h,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (Vu.h[i] >> (Rt & (16-1)));`<br>`}` |
| `Vd.h=vasr(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = (sxt<sub>(4+1)->16</sub>(Vv.h[i])>0)?(Vu.h[i] >> `<br>`sxt<sub>(4+1)->16</sub>(Vv.h[i])):(Vu.h[i]<<sxt<sub>(4+1)->16</sub>(Vv.h[i]));`<br>`}` |
| `Vd.h = vasr(Vu.w, Vv.w, `<br>`Rt):rnd:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=sat₁₆(Vv.w[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`Vd.w[i].h[1]=sat₁₆(Vu.w[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`}` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt)[:sat]` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=[sat₁₆](Vv.w[i] >> shamt);`<br>`Vd.w[i].h[1]=[sat₁₆](Vu.w[i] >> shamt);`<br>`}` |
| `Vd.h=vlsr(Vu.h,Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (sxt<sub>(4+1)->16</sub>(Vv.h[i])> 0)?(Vu.uh[i] >>> `<br>`sxt<sub>(4+1)->16</sub>(Vv.h[i])):(Vu.uh[i]<<sxt<sub>(4+1)->16</sub>(Vv.h[i]));`<br>`}` |
| `Vd.ub = vasr(Vu.h,Vv.h, `<br>`Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.h[i].b[0]=usat₈(Vv.h[i] + (1<<(shamt-1))>> `<br>`shamt);`<br>`Vd.h[i].b[1]=usat₈(Vu.h[i] + (1<<(shamt-1))>> `<br>`shamt);`<br>`}` |
| `Vd.ub = vasr(Vu.uh, Vv.uh, `<br>`Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Rt & 0x7;`<br>`Vd.uh[i].b[0]=usat₈(Vv.uh[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`Vd.uh[i].b[1]=usat₈(Vu.uh[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`}` |
| `Vd.ub=vlsr(Vu.ub,Rt)` | `for (i = 0; i < VELEM(8); i++) {`<br>`Vd.b[i] = Vu.ub[i] >> (Rt & 0x7);`<br>`}` |
| `Vd.uh = vasr(Vu.uw,Vv.uw, `<br>`Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.uw[i].h[0]=usat₁₆(Vv.uw[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`Vd.uw[i].h[1]=usat₁₆(Vu.uw[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`}` |
| `Vd.uh = vasr(Vu.w,Vv.w, `<br>`Rt)[:rnd]:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Rt & 0xF;`<br>`Vd.w[i].h[0]=usat₁₆(Vv.w[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`Vd.w[i].h[1]=usat₁₆(Vu.w[i] + (1<<(shamt-1)) >> `<br>`shamt);`<br>`}` |
| `Vd.uh=vlsr(Vu.uh,Rt)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i] = (Vu.uh[i] >> (Rt & (16-1)));`<br>`}` |
| `Vd.uw=vlsr(Vu.uw,Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (Vu.uw[i] >> (Rt & (32-1)));`<br>`}` |
| `Vd.w=vasl(Vu.w,Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] << (Rt & (32-1)));`<br>`}` |
| `Vd.w=vasl(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (sxt<sub>(5+1)->32</sub>(Vv.w[i])> 0)?(Vu.w[i] << `<br>`sxt<sub>(5+1)->32</sub>(Vv.w[i])):(Vu.w[i]>>sxt<sub>(5+1)->32</sub>(Vv.w[i]));`<br>`}` |
| `Vd.w=vasr(Vu.w,Rt)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (Vu.w[i] >> (Rt & (32-1)));`<br>`}` |
| `Vd.w=vasr(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = (sxt<sub>(5+1)->32</sub>(Vv.w[i])>0)?(Vu.w[i]>> `<br>`sxt<sub>(5+1)->32</sub>(Vv.w[i])):(Vu.w[i]<<sxt<sub>(5+1)->32</sub>(Vv.w[i]));`<br>`}` |
| `Vd.w=vlsr(Vu.w,Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = (sxt<sub>(5+1)->32</sub>(Vv.w[i])>0)?(Vu.uw[i]>>> `<br>`sxt<sub>(5+1)->32</sub>(Vv.w[i])):(Vu.uw[i]<<sxt<sub>(5+1)->32</sub>(Vv.w[i]));`<br>`}` |

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vasr(Vu.h,Vv.h,Rt):rnd:sat` | `HVX_Vector Q6_Vb_vasr_VhVhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.b=vasr(Vu.h,Vv.h,Rt):sat` | `HVX_Vector Q6_Vb_vasr_VhVhR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasl(Vu.h,Rt)` | `HVX_Vector Q6_Vh_vasl_VhR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.h=vasl(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vasl_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vasr(Vu.h,Rt)` | `HVX_Vector Q6_Vh_vasr_VhR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.h=vasr(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vasr_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt)` | `HVX_Vector Q6_Vh_vasr_VwVwR(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat` | `HVX_Vector Q6_Vh_vasr_VwVwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vasr(Vu.w,Vv.w,Rt):sat` | `HVX_Vector Q6_Vh_vasr_VwVwR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.h=vlsr(Vu.h,Vv.h)` | `HVX_Vector Q6_Vh_vlsr_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vasr(Vu.h,Vv.h,Rt):rnd:sat` | `HVX_Vector Q6_Vub_vasr_VhVhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.h,Vv.h,Rt):sat` | `HVX_Vector Q6_Vub_vasr_VhVhR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.uh,Vv.uh,Rt):rnd:sat` | `HVX_Vector Q6_Vub_vasr_VuhVuhR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vasr(Vu.uh,Vv.uh,Rt):sat` | `HVX_Vector Q6_Vub_vasr_VuhVuhR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.ub=vlsr(Vu.ub,Rt)` | `HVX_Vector Q6_Vub_vlsr_VubR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.uh=vasr(Vu.uw,Vv.uw,Rt):rnd:sat` | `HVX_Vector Q6_Vuh_vasr_VuwVuwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.uw,Vv.uw,Rt):sat` | `HVX_Vector Q6_Vuh_vasr_VuwVuwR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.w,Vv.w,Rt):rnd:sat` | `HVX_Vector Q6_Vuh_vasr_VwVwR_rnd_sat (HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vasr(Vu.w,Vv.w,Rt):sat` | `HVX_Vector Q6_Vuh_vasr_VwVwR_sat(HVX_Vector Vu, HVX_Vector Vv, Word32 Rt)` |
| `Vd.uh=vlsr(Vu.uh,Rt)` | `HVX_Vector Q6_Vuh_vlsr_VuhR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.uw=vlsr(Vu.uw,Rt)` | `HVX_Vector Q6_Vuw_vlsr_VuwR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vasl(Vu.w,Rt)` | `HVX_Vector Q6_Vw_vasl_VwR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vasl(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vasl_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vasr(Vu.w,Rt)` | `HVX_Vector Q6_Vw_vasr_VwR(HVX_Vector Vu, Word32 Rt)` |
| `Vd.w=vasr(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vasr_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vlsr(Vu.w,Vv.w)` | `HVX_Vector Q6_Vw_vlsr_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vasr(Vu.h,Vv.h,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uh=vasr(Vu.uw,Vv.uw,Rt ):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vasr(Vu.w,Vv.w,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.uh,Vv.uh,Rt ):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.uh=vasr(Vu.uw,Vv.uw,Rt ):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.uh,Vv.uh,Rt ):sat |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  | t5 | t5 | t5 | t5 | t5 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.w=vasr(Vu.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.h=vasr(Vu.h,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.w=vasl(Vu.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.h=vasl(Vu.h,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uw=vlsr(Vu.uw,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.uh=vlsr(Vu.uh,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | t | t | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.ub=vlsr(Vu.ub,Rt) |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  | t3 | t3 | t3 | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt) |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.uh=vasr(Vu.w,Vv.w,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.ub=vasr(Vu.h,Vv.h,Rt):sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.ub=vasr(Vu.h,Vv.h,Rt):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | t | t | t | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.b=vasr(Vu.h,Vv.h,Rt):rnd:sat |
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.w=vasr(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.w=vlsr(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.h=vlsr(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.h=vasr(Vu.h,Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.w=vasl(Vu.w,Vv.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.h=vasl(Vu.h,Vv.h) |

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
| `v5` | Field to encode register v |

#### Narrowing shift by vector

Arithmetically shift-right the elements in vector register pair Vuu by the lower bits of the elements in vector register Vv. Each result is optionally saturated, rounded to infinity, and packed into a single destination vector register. Each even element in the destination vector register Vd comes from the vector register Vu+1, and each odd element in Vd comes from the vector register Vu.

Vd.h=vasr(Vu.w,Vv.w,Rt)[:rnd][:sat]

|  |  |
|---|---|
| [1] | [0] |

[N-1] Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | [1] |  | [0] |

[N-1] Vv

|  |  |
|---|---|
|  | [N-1] |

[1] [0] Vv

rnd rnd rnd rnd rnd rnd Optional round

Arithmetic

>>Rt >>Rt >>Rt >>Rt >>Rt >>Rt

shift by Rt

Optional saturate to next

sat sat sat sat sat sat

smaller element limits

|  |  |
|---|---|
| [2N-1] | [2N-2] |

[3][2][1][0] Vd

|  |  |  |  |
|---|---|---|---|
| [3] | [2] | [1] | [0] |

[2N-1][2N-2] Vd

| Syntax | Behavior |
|---|---|
| `Vd.ub= `<br>`vasr(Vuu.uh,Vv.ub)[:rnd]:sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`shamt = Vv.ub[2*i+0] & 0x7;`<br>`Vd.uh[i].b[0]=usat₈(Vuu.v[0].uh[i] + `<br>`(1<<(shamt-1)) >> shamt);`<br>`shamt = Vv.ub[2*i+1] & 0x7;`<br>`Vd.uh[i].b[1]=usat₈(Vuu.v[1].uh[i] + `<br>`(1<<(shamt-1)) >> shamt);`<br>`}` |
| `Vd.uh= `<br>`vasr(Vuu.w,Vv.uh)[:rnd]:sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`shamt = Vv.uh[2*i+0] & 0xF;`<br>`Vd.w[i].h[0]=usat₁₆(Vuu.v[0].w[i] + `<br>`(1<<(shamt-1)) >> shamt);`<br>`shamt = Vv.uh[2*i+1] & 0xF;`<br>`Vd.w[i].h[1]=usat₁₆(Vuu.v[1].w[i] + `<br>`(1<<(shamt-1)) >> shamt);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction cannot be paired with a HVX permute instruction
- This instruction uses the HVX shift resource.
- If a packet contains this instruction and an HVX ALU operation, the ALU operation must be unary.

##### Intrinsics

|  |  |
|---|---|
| `Vd.ub=vasr(Vuu.uh,Vv.ub):rnd:sat` | `HVX_Vector Q6_Vub_vasr_WuhVub_rnd_sat (HVX_VectorPair Vuu, HVX_Vector Vv)` |
| `Vd.ub=vasr(Vuu.uh,Vv.ub):sat` | `HVX_Vector Q6_Vub_vasr_WuhVub_sat (HVX_VectorPair Vuu, HVX_Vector Vv)` |
| `Vd.uh=vasr(Vuu.w,Vv.uh):rnd:sat` | `HVX_Vector Q6_Vuh_vasr_WwVuh_rnd_sat (HVX_VectorPair Vuu, HVX_Vector Vv)` |
| `Vd.uh=vasr(Vuu.w,Vv.uh):sat` | `HVX_Vector Q6_Vuh_vasr_WwVuh_sat (HVX_VectorPair Vuu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.uh=vasr(Vuu.w,Vv.uh):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.uh=vasr(Vuu.w,Vv.uh):rnd:sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 0 | d | d | d | d | d | Vd.ub=vasr(Vuu.uh,Vv.ub): sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.ub=vasr(Vuu.uh,Vv.ub):rnd:sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Convert qfloat to IEEE floating point

These instructions convert qfloat input vector register(s) to an IEEE output vector register.

| Syntax | Behavior |
|---|---|
| `Vd.hf=Vu.qf16` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`Vd.hf[i] = rnd_sat(u.exp,u.sig);`<br>`}` |
| `Vd.hf=Vuu.qf32` | `for (i = 0; i < VELEM(32); i++) {`<br>`u0 = Vuu.v[0].qf32[i];`<br>`u1 = Vuu.v[1].qf32[i];`<br>`Vd.hf[2*i] = rnd_sat(u0.exp,u0.sig);`<br>`Vd.hf[2*i+1] = rnd_sat(u1.exp,u1.sig);`<br>`}` |
| `Vd.sf=Vu.qf32` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`Vd.sf[i] = rnd_sat(u.exp,u.sig);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.hf=Vu.qf16` | `HVX_Vector Q6_Vhf_equals_Vqf16(HVX_Vector Vu)` |
| `Vd.hf=Vuu.qf32` | `HVX_Vector Q6_Vhf_equals_Wqf32(HVX_VectorPair Vuu)` |
| `Vd.sf=Vu.qf32` | `HVX_Vector Q6_Vsf_equals_Vqf32(HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 1 | 0 | 0 | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.sf=Vu.qf32 |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 1 | 0 | 0 | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.hf=Vu.qf16 |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | 1 | 0 | 0 | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.hf=Vuu.qf32 |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/Loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |

#### Round to next smaller element size

Pack signed words to signed or unsigned halfwords, add 0x8000 to the lower 16 bits, logically or arithmetically right-shift by 16, and saturate the results to unsigned or signed halfwords respectively. Alternatively pack signed halfwords to signed or unsigned bytes, add 0x80 to the lower 8 bits, logically or arithmetically right-shift by 8, and saturate the results to unsigned or signed bytes respectively. The odd elements in the destination vector register Vd come from vector register Vv, and the even elements from Vu.

Vd.b=vround(Vu.h,Vv.h):sat

|  |  |
|---|---|
| h[1] | h[0] |

h[N-1] Vu

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |
|  | h[1] |  | h[0] |

h[N-1] Vv

|  |  |
|---|---|
|  | h[N-1] |

h[1] h[0] Vv

<sup>+0x80</sup><sup>+0x80</sup><sup>+0x80</sup><sup>+0x80</sup><sup>+0x80</sup><sup>+0x80</sup> Round

>>8 >>8 >>8 >>8 >>8 >>8 Shift by 8

Saturate

sat sat sat sat sat sat to

byte

|  |  |
|---|---|
| b[2N-1] | b[2N-2] |

b[3]b[2]b[1]b[0] Vd

|  |  |  |  |
|---|---|---|---|
| b[3] | b[2] | b[1] | b[0] |

b[2N-1]b[2N-2] Vd

| Syntax | Behavior |
|---|---|
| `Vd.b=vround(Vu.h,Vv.h):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=sat₈((Vv.h[i] + 0x80) >> 8);`<br>`Vd.uh[i].b[1]=sat₈((Vu.h[i] + 0x80) >> 8);`<br>`}` |
| `Vd.h=vround(Vu.w,Vv.w):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i].h[0]=sat₁₆((Vv.w[i] + 0x8000) >> `<br>`16);`<br>`Vd.uw[i].h[1]=sat₁₆((Vu.w[i] + 0x8000) >> `<br>`16);`<br>`}` |
| `Vd.ub=vround(Vu.h,Vv.h):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=usat₈((Vv.h[i] + 0x80) >> 8);`<br>`Vd.uh[i].b[1]=usat₈((Vu.h[i] + 0x80) >> 8);`<br>`}` |
| `Vd.ub=vround(Vu.uh,Vv.uh):sat` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i].b[0]=usat₈((Vv.uh[i] + 0x80) >> 8);`<br>`Vd.uh[i].b[1]=usat₈((Vu.uh[i] + 0x80) >> 8);`<br>`}` |
| `Vd.uh=vround(Vu.uw,Vv.uw):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i].h[0]=usat₁₆((Vv.uw[i] + 0x8000) >> `<br>`16);`<br>`Vd.uw[i].h[1]=usat₁₆((Vu.uw[i] + 0x8000) >> `<br>`16);`<br>`}` |
| `Vd.uh=vround(Vu.w,Vv.w):sat` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i].h[0]=usat₁₆((Vv.w[i] + 0x8000) >> `<br>`16);`<br>`Vd.uw[i].h[1]=usat₁₆((Vu.w[i] + 0x8000) >> `<br>`16);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.b=vround(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vb_vround_VhVh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vround(Vu.w,Vv.w):sat` | `HVX_Vector Q6_Vh_vround_VwVw_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vround(Vu.h,Vv.h):sat` | `HVX_Vector Q6_Vub_vround_VhVh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.ub=vround(Vu.uh,Vv.uh):sat` | `HVX_Vector Q6_Vub_vround_VuhVuh_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vround(Vu.uw,Vv.uw):sat` | `HVX_Vector Q6_Vuh_vround_VuwVuw_sat(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.uh=vround(Vu.w,Vv.w):sat` | `HVX_Vector Q6_Vuh_vround_VwVw_sat(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.h=vround(Vu.w,Vv.w):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.uh=vround(Vu.w,Vv.w):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.b=vround(Vu.h,Vv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.ub=vround(Vu.h,Vv.h):sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.ub=vround(Vu.uh,Vv.uh) :sat |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | v | v | v | v | v | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.uh=vround(Vu.uw,Vv.uw ):sat |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Vector rotate right word

Rotate right each element of Vu.w by the unsigned amount specified by bits 4:0 of corresponding element of Vv.w, place the result in respective elements of Vd.w.

| Syntax | Behavior |
|---|---|
| `Vd.uw=vrotr(Vu.uw,Vv.uw)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i] = ((Vu.uw[i] >> (Vv.uw[i] & 0x1f)) \| `<br>`(Vu.uw[i] << (32 - (Vv.uw[i] & 0x1f))));`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

```
Vd.uw=vrotr(Vu.uw,Vv.uw)HVX_Vector Q6_Vuw_vrotr_VuwVuw(HVX_Vector Vu,
                          HVX_Vector Vv)
```

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.uw=vrotr(Vu.uw,Vv.uw) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Subtract half precision vector by vector

These instructions perform a vectorized half precision floating point subtract. The inputs are either both IEEE single precision, both 16-bit Qfloat, or one of each. The result is a 16-bit Qfloat vector.

| Syntax | Behavior |
|---|---|
| `Vd.qf16=vsub(Vu.hf,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.hf[i];`<br>`v = Vv.hf[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_HF + `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_HF + `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`if((u.sign==0) && (v.sign==0)) {`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-`<br>`sig_v : (sig_u-(sig_v+sig));`<br>`} else if(u.sign ^ v.sign){`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+ `<br>`sig_v : (sig_v-sig)+sig_u;`<br>`} else{`<br>`sig = sig_v - sig_u;`<br>`sig_low = (v.exp>u.exp) ? (sig_v-sig)-`<br>`sig_u : sig_v-(sig_u+sig);`<br>`}`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`if((u.sign==1) && (v.sign==0)) Vd.qf16[i] = `<br>`-(Vd.qf16[i]);`<br>`}` |
| `Vd.qf16=vsub(Vu.qf16,Vv.hf)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.hf[i];`<br>`if(v.sign) v.sig = (-1.0)*v.sig;`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_HF+ `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_HF+ `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-sig_v `<br>`: (sig_u-(sig_v+sig));`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf16=vsub(Vu.qf16,Vv.qf16)` | `for (i = 0; i < VELEM(16); i++) {`<br>`u = Vu.qf16[i];`<br>`v = Vv.qf16[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_HF+ `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_HF+ `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-sig_v `<br>`: (sig_u-(sig_v+sig));`<br>`Vd.qf16[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf16=vsub(Vu.hf,Vv.hf)` | `HVX_Vector Q6_Vqf16_vsub_VhfVhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vsub(Vu.qf16,Vv.hf)` | `HVX_Vector Q6_Vqf16_vsub_Vqf16Vhf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf16=vsub(Vu.qf16,Vv.qf16)` | `HVX_Vector Q6_Vqf16_vsub_Vqf16Vqf16(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.qf16=vsub(Vu.qf16,Vv.q f16) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.qf16=vsub(Vu.hf,Vv.hf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.qf16=vsub(Vu.qf16,Vv.h f) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Subtract single precision vector by vector

Perform a vectorized single precision floating point subtract. The inputs are either both IEEE single precision, both 32-bit Qfloat, or one of each. The result is a 32-bit Qfloat vector.

| Syntax | Behavior |
|---|---|
| `Vd.qf32=vsub(Vu.qf32,Vv.qf32)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`v = Vv.qf32[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-sig_v `<br>`: (sig_u-(sig_v+sig));`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf32=vsub(Vu.qf32,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.qf32[i];`<br>`v = Vv.sf[i];`<br>`if(v.sign) v.sig = (-1.0)*v.sig;`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-sig_v `<br>`: (sig_u-(sig_v+sig));`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`}` |
| `Vd.qf32=vsub(Vu.sf,Vv.sf)` | `for (i = 0; i < VELEM(32); i++) {`<br>`u = Vu.sf[i];`<br>`v = Vv.sf[i];`<br>`if (u.exp>v.exp) {`<br>`exp = u.exp+((u.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(u.sig));`<br>`if (exp<v.exp) exp = v.exp;`<br>`} else {`<br>`exp = v.exp+((v.sig==0.0)? (-(FRAC_SF+ `<br>`1)):ilogb(v.sig));`<br>`if (exp<u.exp) exp = u.exp;`<br>`}`<br>`sig_u = ldexp(u.sig, u.exp-exp);`<br>`sig_v = ldexp(v.sig, v.exp-exp);`<br>`if((u.sign==0) && (v.sign==0)) {`<br>`sig = sig_u - sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)-`<br>`sig_v : (sig_u-(sig_v+sig));`<br>`} else if(u.sign ^ v.sign){`<br>`sig = sig_u + sig_v;`<br>`sig_low = (u.exp>v.exp) ? (sig_u-sig)+ `<br>`sig_v : (sig_v-sig)+sig_u;`<br>`} else{`<br>`sig = sig_v - sig_u;`<br>`sig_low = (v.exp>u.exp) ? (sig_v-sig)-`<br>`sig_u : sig_v-(sig_u+sig);`<br>`}`<br>`Vd.qf32[i] = rnd_sat(exp,sig,sig_low);`<br>`if((u.sign==1) && (v.sign==0)) Vd.qf32[i] = `<br>`-(Vd.qf32[i]);`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.qf32=vsub(Vu.qf32,Vv.qf32)` | `HVX_Vector Q6_Vqf32_vsub_Vqf32Vqf32(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf32=vsub(Vu.qf32,Vv.sf)` | `HVX_Vector Q6_Vqf32_vsub_Vqf32Vsf(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.qf32=vsub(Vu.sf,Vv.sf)` | `HVX_Vector Q6_Vqf32_vsub_VsfVsf(HVX_Vector Vu, HVX_Vector Vv)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 1 | 1 | d | d | d | d | d | Vd.qf32=vsub(Vu.qf32,Vv.q f32) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.qf32=vsub(Vu.sf,Vv.sf) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.qf32=vsub(Vu.qf32,Vv.sf ) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |

#### Bit counting

The bit counting operations apply to each vector element in a vector register Vu, and place the result in the corresponding element in the vector destination register Vd.

Count leading zeros (vcl0) counts the number of consecutive zeros starting with the most significant bit. It supports unsigned halfword and word. Population count (vpopcount) counts the number of nonzero bits in a halfword element. Normalization amount (vnormamt) counts the number of bits for normalization (consecutive sign bits minus one, with zero treated specially). Count leading identical bits, and add a value to it for each lane.

| Syntax | Behavior |
|---|---|
| `Vd.h=vadd(vclb(Vu.h),Vv.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i] = max(count_leading_ones `<br>`(~Vu.h[i]),count_leading_ones(Vu.h[i])) + Vv.h[i];`<br>`}` |
| `Vd.h=vnormamt(Vu.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.h[i]=max(count_leading_ones(~Vu.h[i]),count`<br>`_leading_ones(Vu.h[i]))-1;`<br>`}` |
| `Vd.h=vpopcount(Vu.h)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i]=count_ones(Vu.uh[i]);`<br>`}` |
| `Vd.uh=vcl0(Vu.uh)` | `for (i = 0; i < VELEM(16); i++) {`<br>`Vd.uh[i]=count_leading_ones(~Vu.uh[i]);`<br>`}` |
| `Vd.uw=vcl0(Vu.uw)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.uw[i]=count_leading_ones(~Vu.uw[i]);`<br>`}` |
| `Vd.w=vadd(vclb(Vu.w),Vv.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i] = max(count_leading_ones (~Vu.w[i]), `<br>`count_leading_ones(Vu.w[i])) + Vv.w[i];`<br>`}` |
| `Vd.w=vnormamt(Vu.w)` | `for (i = 0; i < VELEM(32); i++) {`<br>`Vd.w[i]=max(count_leading_ones(~Vu.w[i]),count`<br>`_leading_ones(Vu.w[i]))-1;`<br>`}` |

##### Class: COPROC_VX (slots 0,1,2,3)

##### Notes

- This instruction uses the HVX shift resource.

##### Intrinsics

|  |  |
|---|---|
| `Vd.h=vadd(vclb(Vu.h),Vv.h)` | `HVX_Vector Q6_Vh_vadd_vclb_VhVh(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.h=vnormamt(Vu.h)` | `HVX_Vector Q6_Vh_vnormamt_Vh(HVX_Vector Vu)` |
| `Vd.h=vpopcount(Vu.h)` | `HVX_Vector Q6_Vh_vpopcount_Vh(HVX_Vector Vu)` |
| `Vd.uh=vcl0(Vu.uh)` | `HVX_Vector Q6_Vuh_vcl0_Vuh(HVX_Vector Vu)` |
| `Vd.uw=vcl0(Vu.uw)` | `HVX_Vector Q6_Vuw_vcl0_Vuw(HVX_Vector Vu)` |
| `Vd.w=vadd(vclb(Vu.w),Vv.w)` | `HVX_Vector Q6_Vw_vadd_vclb_VwVw(HVX_Vector Vu, HVX_Vector Vv)` |
| `Vd.w=vnormamt(Vu.w)` | `HVX_Vector Q6_Vw_vnormamt_Vw(HVX_Vector Vu)` |

##### Encoding

| 31 | 30 | 29 | 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ICLASS | ICLASS | ICLASS | ICLASS |  |  |  |  |  |  |  |  |  |  |  |  | Parse | Parse |  | u5 | u5 | u5 | u5 | u5 |  |  |  | d5 | d5 | d5 | d5 | d5 |  |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.uw=vcl0(Vu.uw) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 1 | 1 | 0 | d | d | d | d | d | Vd.h=vpopcount(Vu.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 0 | P | P | 0 | u | u | u | u | u | 1 | 1 | 1 | d | d | d | d | d | Vd.uh=vcl0(Vu.uh) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 1 | P | P | 0 | u | u | u | u | u | 1 | 0 | 0 | d | d | d | d | d | Vd.w=vnormamt(Vu.w) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | - | - | 0 | - | - | - | 1 | 1 | P | P | 0 | u | u | u | u | u | 1 | 0 | 1 | d | d | d | d | d | Vd.h=vnormamt(Vu.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 0 | d | d | d | d | d | Vd.h=vadd(vclb(Vu.h),Vv.h) |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | v | v | v | v | v | P | P | 1 | u | u | u | u | u | 0 | 0 | 1 | d | d | d | d | d | Vd.w=vadd(vclb(Vu.w),Vv.w ) |

| Field name | Description |
|---|---|
| `ICLASS` | Instruction class |
| `Parse` | Packet/loop parse bits |
| `d5` | Field to encode register d |
| `u5` | Field to encode register u |
| `v5` | Field to encode register v |
