# Instruction index

### A

```
add
```

`Rdd=add(Rss,Rtt,Px):carry` 65

```
and
```

`Qd4=and(Qs4,[!]Qt4)` 41

### B

```
bf
```

`Qd4=vcmp.gt(Vu.bf,Vv.bf)` 75 `Qx4[&|]=vcmp.gt(Vu.bf,Vv.bf)` 76 `Qx4^=vcmp.gt(Vu.bf,Vv.bf)` 78

### H

```
hf
```

`Vd.hf=Vu.qf16` 262 `Vd.hf=Vuu.qf32` 262 `Vd.qf16=vadd(Vu.hf,Vv.hf)` 246 `Vd.qf16=vadd(Vu.qf16,Vv.hf)` 246 `Vd.qf16=vmpy(Vu.hf,Vv.hf)` 145 `Vd.qf16=vmpy(Vu.qf16,Vv.hf)` 145 `Vd.qf16=vsub(Vu.hf,Vv.hf)` 267 `Vd.qf16=vsub(Vu.qf16,Vv.hf)` 268 `Vdd.qf32=vmpy(Vu.hf,Vv.hf)` 145 `Vdd.qf32=vmpy(Vu.qf16,Vv.hf)` 146

### N

```
no mnemonic
```

`if ([!]Ps) Vd=Vu` 68 `if ([!]Qv4) Vx.b[+-]=Vu.b` 83 `if ([!]Qv4) Vx.h[+-]=Vu.h` 83 `if ([!]Qv4) Vx.w[+-]=Vu.w` 83 `Vd.tmp=Vu` 69 `Vd=Vu` 68

```
not
```

`Qd4=not(Qs4)` 55

### O

```
or
```

`Qd4=or(Qs4,[!]Qt4)` 41

### P

```
prefixsum
```

`Vd.b=prefixsum(Qv4)` 244 `Vd.h=prefixsum(Qv4)` 244 `Vd.w=prefixsum(Qv4)` 244

### Q

```
qf16
```

`Vd.qf16=vadd(Vu.qf16,Vv.qf16)` 247 `Vd.qf16=vmpy(Vu.qf16,Vv.qf16)` 145 `Vd.qf16=vsub(Vu.qf16,Vv.qf16)` 268 `Vdd.qf32=vmpy(Vu.qf16,Vv.qf16)` 146

```
qf32
```

`Vd.qf32=vadd(Vu.qf32,Vv.qf32)` 248 `Vd.qf32=vmpy(Vu.qf32,Vv.qf32)` 154 `Vd.qf32=vsub(Vu.qf32,Vv.qf32)` 270

### S

```
sf
```

`Vd.qf32=vadd(Vu.qf32,Vv.sf)` 248 `Vd.qf32=vadd(Vu.sf,Vv.sf)` 249 `Vd.qf32=vmpy(Vu.sf,Vv.sf)` 154 `Vd.qf32=vsub(Vu.qf32,Vv.sf)` 270 `Vd.qf32=vsub(Vu.sf,Vv.sf)` 271 `Vd.sf=Vu.qf32` 262

```
sub
```

`Rdd=sub(Rss,Rtt,Px):carry` 65

### U

```
ub
```

`Qd4=vcmp.eq(Vu.ub,Vv.ub)` 75 `Qd4=vcmp.gt(Vu.ub,Vv.ub)` 76 `Qx4[&|]=vcmp.eq(Vu.ub,Vv.ub)` 76 `Qx4[&|]=vcmp.gt(Vu.ub,Vv.ub)` 77 `Qx4^=vcmp.eq(Vu.ub,Vv.ub)` 77 `Qx4^=vcmp.gt(Vu.ub,Vv.ub)` 78 `Vd.b=vnavg(Vu.ub,Vv.ub)` 71 `Vd.h=vdmpy(Vu.ub,Rt.b)` 172 `Vd.ub=vabs(Vu.b)` 60 `Vd.ub=vabsdiff(Vu.ub,Vv.ub)` 192 `Vd.ub=vadd(Vu.ub,Vv.b):sat` 62 `Vd.ub=vadd(Vu.ub,Vv.ub):sat` 62 `Vd.ub=vasr(Vu.h,Vv.h,Rt)[:rnd]:sat` 241, 255 `Vd.ub=vavg(Vu.ub,Vv.ub)[:rnd]` 71 `Vd.ub=vlsr(Vu.ub,Rt)` 256 `Vd.ub=vmax(Vu.ub,Vv.ub)` 57 `Vd.ub=vmin(Vu.ub,Vv.ub)` 57 `Vd.ub=vpack(Vu.h,Vv.h):sat` 207 `Vd.ub=vround(Vu.h,Vv.h):sat` 264 `Vd.ub=vsat(Vu.h,Vv.h)` 88 `Vd.ub=vsub(Vu.ub,Vv.b):sat` 62 `Vd.ub=vsub(Vu.ub,Vv.ub):sat` 62 `Vd.uw=vrmpy(Vu.ub,Rt.ub)` 183 `Vd.uw=vrmpy(Vu.ub,Vv.ub)` 186 `Vd.w=vmpyi(Vu.w,Rt.ub)` 180 `Vd.w=vrmpy(Vu.ub,Rt.b)` 184 `Vd.w=vrmpy(Vu.ub,Vv.b)` 187 `Vdd.h=vadd(Vu.ub,Vv.ub)` 122 `Vdd.h=vdmpy(Vuu.ub,Rt.b)` 127 `Vdd.h=vmpa(Vuu.ub,Rt.b)` 133 `Vdd.h=vmpa(Vuu.ub,Rt.ub)` 133 `Vdd.h=vmpa(Vuu.ub,Vvv.b)` 133 `Vdd.h=vmpa(Vuu.ub,Vvv.ub)` 134 `Vdd.h=vmpy(Vu.ub,Rt.b)` 138 `Vdd.h=vmpy(Vu.ub,Vv.b)` 142 `Vdd.h=vsub(Vu.ub,Vv.ub)` 122 `Vdd.h=vtmpy(Vuu.ub,Rt.b)` 164 `Vdd.ub=vadd(Vuu.ub,Vvv.ub):sat` 51 `Vdd.ub=vsub(Vuu.ub,Vvv.ub):sat` 51 `Vdd.uw=vrmpy(Vuu.ub,Rt.ub,#u1)` 158 `Vdd.uw=vrsad(Vuu.ub,Rt.ub,#u1)` 170 `Vdd.w=v6mpy(Vuu.ub,Vvv.b,#u2):h` 117 `Vdd.w=v6mpy(Vuu.ub,Vvv.b,#u2):v` 118 `Vdd.w=vrmpy(Vuu.ub,Rt.b,#u1)` 158 `Vx.h+=vdmpy(Vu.ub,Rt.b)` 172 `Vx.uw+=vrmpy(Vu.ub,Rt.ub)` 184 `Vx.uw+=vrmpy(Vu.ub,Vv.ub)` 161 `Vx.w+=vmpyi(Vu.w,Rt.ub)` 180 `Vx.w+=vrmpy(Vu.ub,Rt.b)` 184 `Vx.w+=vrmpy(Vu.ub,Vv.b)` 162 `Vxx.h+=vadd(Vu.ub,Vv.ub)` 123 `Vxx.h+=vdmpy(Vuu.ub,Rt.b)` 127 `Vxx.h+=vmpa(Vuu.ub,Rt.b)` 134 `Vxx.h+=vmpa(Vuu.ub,Rt.ub)` 134 `Vxx.h+=vmpy(Vu.ub,Rt.b)` 138 `Vxx.h+=vmpy(Vu.ub,Vv.b)` 142 `Vxx.h+=vtmpy(Vuu.ub,Rt.b)` 165 `Vxx.uw+=vrmpy(Vuu.ub,Rt.ub,#u1)` 158 `Vxx.uw+=vrsad(Vuu.ub,Rt.ub,#u1)` 170 `Vxx.w+=v6mpy(Vuu.ub,Vvv.b,#u2):h` 119 `Vxx.w+=v6mpy(Vuu.ub,Vvv.b,#u2):v` 120, 121 `Vxx.w+=vrmpy(Vuu.ub,Rt.b,#u1)` 159

```
uh
```

`Qd4=vcmp.eq(Vu.uh,Vv.uh)` 75 `Qd4=vcmp.gt(Vu.uh,Vv.uh)` 76 `Qx4[&|]=vcmp.eq(Vu.uh,Vv.uh)` 76 `Qx4[&|]=vcmp.gt(Vu.uh,Vv.uh)` 77 `Qx4^=vcmp.eq(Vu.uh,Vv.uh)` 77 `Qx4^=vcmp.gt(Vu.uh,Vv.uh)` 78 `Vd.h=vlut4(Vu.uh,Rtt.h)` 130 `Vd.ub=vasr(Vu.uh,Vv.uh,Rt)[:rnd]:sat` 241, 256 `Vd.ub=vasr(Vuu.uh,Vv.ub)[:rnd]:sat` 260 `Vd.ub=vround(Vu.uh,Vv.uh):sat` 264 `Vd.uh=vabs(Vu.h)` 60 `Vd.uh=vabsdiff(Vu.h,Vv.h)` 192 `Vd.uh=vabsdiff(Vu.uh,Vv.uh)` 192 `Vd.uh=vadd(Vu.uh,Vv.uh):sat` 62 `Vd.uh=vasr(Vu.uw,Vv.uw,Rt)[:rnd]:sat` 241, 256 `Vd.uh=vasr(Vu.w,Vv.w,Rt)[:rnd]:sat` 241, 256 `Vd.uh=vasr(Vuu.w,Vv.uh)[:rnd]:sat` 261 `Vd.uh=vavg(Vu.uh,Vv.uh)[:rnd]` 71 `Vd.uh=vcl0(Vu.uh)` 273 `Vd.uh=vlsr(Vu.uh,Rt)` 256 `Vd.uh=vmax(Vu.uh,Vv.uh)` 57 `Vd.uh=vmin(Vu.uh,Vv.uh)` 57 `Vd.uh=vmpy(Vu.uh,Vv.uh):>>16` 178 `Vd.uh=vpack(Vu.w,Vv.w):sat` 207 `Vd.uh=vround(Vu.uw,Vv.uw):sat` 264 `Vd.uh=vround(Vu.w,Vv.w):sat` 264 `Vd.uh=vsat(Vu.uw,Vv.uw)` 88 `Vd.uh=vsub(Vu.uh,Vv.uh):sat` 62 `Vd.uw=vmpye(Vu.uh,Rt.uh)` 182 `Vd.w=vdmpy(Vu.h,Rt.uh):sat` 174 `Vd.w=vdmpy(Vuu.h,Rt.uh,#1):sat` 126 `Vd.w=vmpye(Vu.w,Vv.uh)` 155 `Vd.w=vmpyie(Vu.w,Vv.uh)` 150 `Vdd.uh=vadd(Vuu.uh,Vvv.uh):sat` 51 `Vdd.uh=vmpy(Vu.ub,Rt.ub)` 138 `Vdd.uh=vmpy(Vu.ub,Vv.ub)` 142 `Vdd.uh=vsub(Vuu.uh,Vvv.uh):sat` 52 `Vdd.uh=vunpack(Vu.ub)` 231 `Vdd.uh=vzxt(Vu.ub)` 49 `Vdd.uw=vdsad(Vuu.uh,Rt.uh)` 168 `Vdd.uw=vmpy(Vu.uh,Rt.uh)` 138 `Vdd.uw=vmpy(Vu.uh,Vv.uh)` 142 `Vdd.uw=vunpack(Vu.uh)` 231 `Vdd.uw=vzxt(Vu.uh)` 49 `Vdd.w=vadd(Vu.uh,Vv.uh)` 123 `Vdd.w=vmpa(Vuu.uh,Rt.b)` 134 `Vdd.w=vmpy(Vu.h,Vv.uh)` 142 `Vdd.w=vsub(Vu.uh,Vv.uh)` 123 `Vdd=vmpye(Vu.w,Vv.uh)` 155 `Vx.h=vmpa(Vx.h,Vu.uh,Rtt.uh):sat` 131 `Vx.h=vmps(Vx.h,Vu.uh,Rtt.uh):sat` 131 `Vx.uw+=vmpye(Vu.uh,Rt.uh)` 182 `Vx.w+=vdmpy(Vu.h,Rt.uh):sat` 175 `Vx.w+=vdmpy(Vuu.h,Rt.uh,#1):sat` 127 `Vx.w+=vmpyie(Vu.w,Vv.uh)` 150 `Vxx.uh+=vmpy(Vu.ub,Rt.ub)` 138 `Vxx.uh+=vmpy(Vu.ub,Vv.ub)` 142 `Vxx.uw+=vdsad(Vuu.uh,Rt.uh)` 168 `Vxx.uw+=vmpy(Vu.uh,Rt.uh)` 138 `Vxx.uw+=vmpy(Vu.uh,Vv.uh)` 142 `Vxx.w+=vadd(Vu.uh,Vv.uh)` 123 `Vxx.w+=vmpa(Vuu.uh,Rt.b)` 134 `Vxx.w+=vmpy(Vu.h,Vv.uh)` 143

### V

```
vabs
```

`Vd.b=vabs(Vu.b)[:sat]` 60 `Vd.h=vabs(Vu.h)[:sat]` 60 `Vd.uw=vabs(Vu.w)` 60 `Vd.w=vabs(Vu.w)[:sat]` 60

```
vabsdiff
```

`Vd.uw=vabsdiff(Vu.w,Vv.w)` 192

```
vadd
```

`Vd.b=vadd(Vu.b,Vv.b)[:sat]` 62 `Vd.h=vadd(Vu.h,Vv.h)[:sat]` 62 `Vd.uw=vadd(Vu.uw,Vv.uw):sat` 62 `Vd.w,Qe4=vadd(Vu.w,Vv.w):carry` 65 `Vd.w=vadd(Vu.w,Vv.w,Qs4):carry:sat` 65 `Vd.w=vadd(Vu.w,Vv.w,Qx4):carry` 65 `Vd.w=vadd(Vu.w,Vv.w)[:sat]` 62 `Vdd.b=vadd(Vuu.b,Vvv.b)[:sat]` 51 `Vdd.h=vadd(Vuu.h,Vvv.h)[:sat]` 51 `Vdd.uw=vadd(Vuu.uw,Vvv.uw):sat` 52 `Vdd.w=vadd(Vu.h,Vv.h)` 122 `Vdd.w=vadd(Vuu.w,Vvv.w)[:sat]` 52 `Vxx.w+=vadd(Vu.h,Vv.h)` 123

```
valign
```

`Vd=valign(Vu,Vv,#u3)` 196 `Vd=valign(Vu,Vv,Rt)` 196

```
vand
```

`Qd4=vand(Vu,Rt)` 190 `Qx4|=vand(Vu,Rt)` 190 `Vd=vand([!]Qu4,Rt)` 191 `Vd=vand([!]Qv4,Vu)` 56 `Vd=vand(Vu,Vv)` 67 `Vx|=vand([!]Qu4,Rt)` 191

```
vasl
```

`Vd.h=vasl(Vu.h,Rt)` 255 `Vd.h=vasl(Vu.h,Vv.h)` 255 `Vd.w=vasl(Vu.w,Rt)` 256 `Vd.w=vasl(Vu.w,Vv.w)` 256 `Vx.h+=vasl(Vu.h,Rt)` 252 `Vx.w+=vasl(Vu.w,Rt)` 252

```
vasr
```

`Vd.b=vasr(Vu.h,Vv.h,Rt)[:rnd]:sat` 240, 255 `Vd.h=vasr(Vu.h,Rt)` 255 `Vd.h=vasr(Vu.h,Vv.h)` 255 `Vd.h=vasr(Vu.w,Vv.w,Rt):rnd:sat` 241, 255 `Vd.h=vasr(Vu.w,Vv.w,Rt)[:sat]` 241, 255 `Vd.w=vasr(Vu.w,Rt)` 256 `Vd.w=vasr(Vu.w,Vv.w)` 256 `Vx.h+=vasr(Vu.h,Rt)` 252 `Vx.w+=vasr(Vu.w,Rt)` 252

```
vasrinto
```

`Vxx.w=vasrinto(Vu.w,Vv.w)` 216

```
vavg
```

`Vd.b=vavg(Vu.b,Vv.b)[:rnd]` 71 `Vd.h=vavg(Vu.h,Vv.h)[:rnd]` 71 `Vd.uw=vavg(Vu.uw,Vv.uw)[:rnd]` 72 `Vd.w=vavg(Vu.w,Vv.w)[:rnd]` 72

```
vcl0
```

`Vd.uw=vcl0(Vu.uw)` 273

```
vclb
```

`Vd.h=vadd(vclb(Vu.h),Vv.h)` 273 `Vd.w=vadd(vclb(Vu.w),Vv.w)` 273

```
vcmp.eq
```

`Qd4=vcmp.eq(Vu.b,Vv.b)` 75 `Qd4=vcmp.eq(Vu.h,Vv.h)` 75 `Qd4=vcmp.eq(Vu.uw,Vv.uw)` 75 `Qd4=vcmp.eq(Vu.w,Vv.w)` 75 `Qx4[&|]=vcmp.eq(Vu.b,Vv.b)` 76 `Qx4[&|]=vcmp.eq(Vu.h,Vv.h)` 76 `Qx4[&|]=vcmp.eq(Vu.uw,Vv.uw)` 76 `Qx4[&|]=vcmp.eq(Vu.w,Vv.w)` 76 `Qx4^=vcmp.eq(Vu.b,Vv.b)` 77 `Qx4^=vcmp.eq(Vu.h,Vv.h)` 77 `Qx4^=vcmp.eq(Vu.uw,Vv.uw)` 77 `Qx4^=vcmp.eq(Vu.w,Vv.w)` 77

```
vcmp.gt
```

`Qd4=vcmp.gt(Vu.b,Vv.b)` 75 `Qd4=vcmp.gt(Vu.h,Vv.h)` 75 `Qd4=vcmp.gt(Vu.hf,Vv.hf)` 75 `Qd4=vcmp.gt(Vu.sf,Vv.sf)` 76 `Qd4=vcmp.gt(Vu.uw,Vv.uw)` 76 `Qd4=vcmp.gt(Vu.w,Vv.w)` 76 `Qx4[&|]=vcmp.gt(Vu.b,Vv.b)` 76 `Qx4[&|]=vcmp.gt(Vu.h,Vv.h)` 77 `Qx4[&|]=vcmp.gt(Vu.hf,Vv.hf)` 77 `Qx4[&|]=vcmp.gt(Vu.sf,Vv.sf)` 77 `Qx4[&|]=vcmp.gt(Vu.uw,Vv.uw)` 77 `Qx4[&|]=vcmp.gt(Vu.w,Vv.w)` 77 `Qx4^=vcmp.gt(Vu.b,Vv.b)` 78 `Qx4^=vcmp.gt(Vu.h,Vv.h)` 78 `Qx4^=vcmp.gt(Vu.hf,Vv.hf)` 78 `Qx4^=vcmp.gt(Vu.sf,Vv.sf)` 78 `Qx4^=vcmp.gt(Vu.uw,Vv.uw)` 78 `Qx4^=vcmp.gt(Vu.w,Vv.w)` 78

```
vcombine
```

`if ([!]Ps) Vdd=vcombine(Vu,Vv)` 43 `Vdd.tmp=vcombine(Vu,Vv)` 69 `Vdd=vcombine(Vu,Vv)` 43

```
vdeal
```

`Vd.b=vdeal(Vu.b)` 204 `Vd.h=vdeal(Vu.h)` 204 `Vdd=vdeal(Vu,Vv,Rt)` 220 `vdeal(Vy,Vx,Rt)` 221

```
vdeale
```

`Vd.b=vdeale(Vu.b,Vv.b)` 204

```
vdelta
```

`Vd=vdelta(Vu,Vv)` 201

```
vdmpy
```

`Vd.w=vdmpy(Vu.h,Rt.b)` 172 `Vd.w=vdmpy(Vu.h,Rt.h):sat` 174 `Vd.w=vdmpy(Vu.h,Vv.h):sat` 174 `Vd.w=vdmpy(Vuu.h,Rt.h):sat` 126 `Vdd.w=vdmpy(Vuu.h,Rt.b)` 127 `Vx.w+=vdmpy(Vu.h,Rt.b)` 172 `Vx.w+=vdmpy(Vu.h,Rt.h):sat` 174 `Vx.w+=vdmpy(Vu.h,Vv.h):sat` 127 `Vx.w+=vdmpy(Vuu.h,Rt.h):sat` 127 `Vxx.w+=vdmpy(Vuu.h,Rt.b)` 128

```
vextract
```

`Rd.w=vextract(Vu,Rs)` 92 `Rd=vextract(Vu,Rs)` 92

```
vhist
```

`vhist` 35 `vhist(Qv4)` 35

```
vinsert
```

`Vx.w=vinsert(Rt)` 194

```
vlalign
```

`Vd=vlalign(Vu,Vv,#u3)` 196 `Vd=vlalign(Vu,Vv,Rt)` 196

```
vlsr
```

`Vd.h=vlsr(Vu.h,Vv.h)` 255 `Vd.uw=vlsr(Vu.uw,Rt)` 256 `Vd.w=vlsr(Vu.w,Vv.w)` 256

```
vlut16
```

`Vdd.h=vlut16(Vu.b,Vv.h,#u3)` 227 `Vdd.h=vlut16(Vu.b,Vv.h,Rt)` 228 `Vdd.h=vlut16(Vu.b,Vv.h,Rt):nomatch` 228 `Vxx.h|=vlut16(Vu.b,Vv.h,#u3)` 229 `Vxx.h|=vlut16(Vu.b,Vv.h,Rt)` 229

```
vlut32
```

`Vd.b=vlut32(Vu.b,Vv.b,#u3)` 214 `Vd.b=vlut32(Vu.b,Vv.b,Rt)` 214 `Vd.b=vlut32(Vu.b,Vv.b,Rt):nomatch` 215 `Vx.b|=vlut32(Vu.b,Vv.b,#u3)` 228 `Vx.b|=vlut32(Vu.b,Vv.b,Rt)` 228

```
vmax
```

`Vd.b=vmax(Vu.b,Vv.b)` 57 `Vd.h=vmax(Vu.h,Vv.h)` 57 `Vd.hf=vmax(Vu.hf,Vv.hf)` 57 `Vd.sf=vmax(Vu.sf,Vv.sf)` 57 `Vd.w=vmax(Vu.w,Vv.w)` 58

```
vmem
```

`if ([!]Pv) Vd.cur=vmem(Rt)` 102 `if ([!]Pv) Vd.cur=vmem(Rt):nt` 102 `if ([!]Pv) Vd.cur=vmem(Rt+#s4)` 102 `if ([!]Pv) Vd.cur=vmem(Rt+#s4):nt` 103 `if ([!]Pv) Vd.cur=vmem(Rx++#s3)` 103 `if ([!]Pv) Vd.cur=vmem(Rx++#s3):nt` 103 `if ([!]Pv) Vd.cur=vmem(Rx++Mu)` 103 `if ([!]Pv) Vd.cur=vmem(Rx++Mu):nt` 103 `if ([!]Pv) Vd.tmp=vmem(Rt)` 105 `if ([!]Pv) Vd.tmp=vmem(Rt):nt` 105 `if ([!]Pv) Vd.tmp=vmem(Rt+#s4)` 106 `if ([!]Pv) Vd.tmp=vmem(Rt+#s4):nt` 106 `if ([!]Pv) Vd.tmp=vmem(Rx++#s3)` 106 `if ([!]Pv) Vd.tmp=vmem(Rx++#s3):nt` 106 `if ([!]Pv) Vd.tmp=vmem(Rx++Mu)` 106 `if ([!]Pv) Vd.tmp=vmem(Rx++Mu):nt` 106 `if ([!]Pv) Vd=vmem(Rt)` 99 `if ([!]Pv) Vd=vmem(Rt):nt` 99 `if ([!]Pv) Vd=vmem(Rt+#s4)` 99 `if ([!]Pv) Vd=vmem(Rt+#s4):nt` 100 `if ([!]Pv) Vd=vmem(Rx++#s3)` 100 `if ([!]Pv) Vd=vmem(Rx++#s3):nt` 100 `if ([!]Pv) Vd=vmem(Rx++Mu)` 100 `if ([!]Pv) Vd=vmem(Rx++Mu):nt` 100 `if ([!]Pv) vmem(Rt):nt=Vs` 281 `if ([!]Pv) vmem(Rt)=Vs` 281 `if ([!]Pv) vmem(Rt+#s4):nt=Os8.new` 278 `if ([!]Pv) vmem(Rt+#s4):nt=Vs` 281 `if ([!]Pv) vmem(Rt+#s4)=Os8.new` 278 `if ([!]Pv) vmem(Rt+#s4)=Vs` 281 `if ([!]Pv) vmem(Rx++#s3):nt=Os8.new` 278 `if ([!]Pv) vmem(Rx++#s3):nt=Vs` 281 `if ([!]Pv) vmem(Rx++#s3)=Os8.new` 278 `if ([!]Pv) vmem(Rx++#s3)=Vs` 281 `if ([!]Pv) vmem(Rx++Mu):nt=Os8.new` 278 `if ([!]Pv) vmem(Rx++Mu):nt=Vs` 281 `if ([!]Pv) vmem(Rx++Mu)=Os8.new` 279 `if ([!]Pv) vmem(Rx++Mu)=Vs` 282 `if ([!]Qv4) vmem(Rt):nt=Vs` 275 `if ([!]Qv4) vmem(Rt)=Vs` 275 `if ([!]Qv4) vmem(Rt+#s4):nt=Vs` 276 `if ([!]Qv4) vmem(Rt+#s4)=Vs` 276 `if ([!]Qv4) vmem(Rx++#s3):nt=Vs` 276 `if ([!]Qv4) vmem(Rx++#s3)=Vs` 276 `if ([!]Qv4) vmem(Rx++Mu):nt=Vs` 276 `if ([!]Qv4) vmem(Rx++Mu)=Vs` 276 `Vd.cur=vmem(Rt+#s4)` 102 `Vd.cur=vmem(Rt+#s4):nt` 102 `Vd.cur=vmem(Rx++#s3)` 102 `Vd.cur=vmem(Rx++#s3):nt` 102 `Vd.cur=vmem(Rx++Mu)` 102 `Vd.cur=vmem(Rx++Mu):nt` 102 `Vd.tmp=vmem(Rt+#s4)` 105 `Vd.tmp=vmem(Rt+#s4):nt` 105 `Vd.tmp=vmem(Rx++#s3)` 105 `Vd.tmp=vmem(Rx++#s3):nt` 105 `Vd.tmp=vmem(Rx++Mu)` 105 `Vd.tmp=vmem(Rx++Mu):nt` 105 `Vd=vmem(Rt)` 99 `Vd=vmem(Rt):nt` 99 `Vd=vmem(Rt+#s4)` 99 `Vd=vmem(Rt+#s4):nt` 99 `Vd=vmem(Rx++#s3)` 99 `Vd=vmem(Rx++#s3):nt` 99 `Vd=vmem(Rx++Mu)` 99 `Vd=vmem(Rx++Mu):nt` 99 `vmem(Rt):nt=Os8.new` 279 `vmem(Rt):nt=Vs` 282 `vmem(Rt)=Os8.new` 279 `vmem(Rt)=Vs` 282 `vmem(Rt+#s4):nt=Os8.new` 279

`vmem(Rt+#s4):nt=Vs` 282 `vmem(Rt+#s4)=Os8.new` 279 `vmem(Rt+#s4)=Vs` 282 `vmem(Rx++#s3):nt=Os8.new` 279 `vmem(Rx++#s3):nt=Vs` 282 `vmem(Rx++#s3)=Os8.new` 279 `vmem(Rx++#s3)=Vs` 282 `vmem(Rx++Mu):nt=Os8.new` 279 `vmem(Rx++Mu):nt=Vs` 282 `vmem(Rx++Mu)=Os8.new` 279 `vmem(Rx++Mu)=Vs` 282

```
vmemu
```

`if ([!]Pv) vmemu(Rt)=Vs` 284 `if ([!]Pv) vmemu(Rt+#s4)=Vs` 284 `if ([!]Pv) vmemu(Rx++#s3)=Vs` 284 `if ([!]Pv) vmemu(Rx++Mu)=Vs` 284 `Vd=vmemu(Rt)` 108 `Vd=vmemu(Rt+#s4)` 108 `Vd=vmemu(Rx++#s3)` 108 `Vd=vmemu(Rx++Mu)` 108 `vmemu(Rt)=Vs` 284 `vmemu(Rt+#s4)=Vs` 284 `vmemu(Rx++#s3)=Vs` 284 `vmemu(Rx++Mu)=Vs` 285

```
vmin
```

`Vd.b=vmin(Vu.b,Vv.b)` 57 `Vd.h=vmin(Vu.h,Vv.h)` 57 `Vd.hf=vmin(Vu.hf,Vv.hf)` 57 `Vd.sf=vmin(Vu.sf,Vv.sf)` 57 `Vd.w=vmin(Vu.w,Vv.w)` 58

```
vmpa
```

`Vdd.w=vmpa(Vuu.h,Rt.b)` 134 `Vx.h=vmpa(Vx.h,Vu.h,Rtt.h):sat` 131 `Vxx.w+=vmpa(Vuu.h,Rt.b)` 134

```
vmpy
```

`Vd.h=vmpy(Vu.h,Rt.h):<<1:rnd:sat` 176 `Vd.h=vmpy(Vu.h,Rt.h):<<1:sat` 177 `Vd.h=vmpy(Vu.h,Vv.h):<<1:rnd:sat` 178 `Vdd.h=vmpy(Vu.b,Vv.b)` 142 `Vdd.w=vmpy(Vu.h,Rt.h)` 138 `Vdd.w=vmpy(Vu.h,Vv.h)` 142 `Vxx.h+=vmpy(Vu.b,Vv.b)` 142 `Vxx.w+=vmpy(Vu.h,Rt.h)` 138 `Vxx.w+=vmpy(Vu.h,Rt.h):sat` 138 `Vxx.w+=vmpy(Vu.h,Vv.h)` 143

```
vmpyi
```

`Vd.h=vmpyi(Vu.h,Rt.b)` 180 `Vd.h=vmpyi(Vu.h,Vv.h)` 148 `Vd.w=vmpyi(Vu.w,Rt.b)` 180 `Vd.w=vmpyi(Vu.w,Rt.h)` 152 `Vx.h+=vmpyi(Vu.h,Rt.b)` 180 `Vx.h+=vmpyi(Vu.h,Vv.h)` 148 `Vx.w+=vmpyi(Vu.w,Rt.b)` 180 `Vx.w+=vmpyi(Vu.w,Rt.h)` 152

```
vmpyie
```

`Vx.w+=vmpyie(Vu.w,Vv.h)` 150

```
vmpyieo
```

`Vd.w=vmpyieo(Vu.h,Vv.h)` 179

```
vmpyio
```

`Vd.w=vmpyio(Vu.w,Vv.h)` 150

```
vmpyo
```

`Vd.w=vmpyo(Vu.w,Vv.h):<<1[:rnd]:sat` 155 `Vx.w+=vmpyo(Vu.w,Vv.h):<<1[:rnd]:sat:shift` 155 `Vxx+=vmpyo(Vu.w,Vv.h)` 155

```
vmux
```

`Vd=vmux(Qt4,Vu,Vv)` 86

```
vnavg
```

`Vd.b=vnavg(Vu.b,Vv.b)` 71 `Vd.h=vnavg(Vu.h,Vv.h)` 71 `Vd.w=vnavg(Vu.w,Vv.w)` 72

```
vnormamt
```

`Vd.h=vnormamt(Vu.h)` 273 `Vd.w=vnormamt(Vu.w)` 273

```
vnot
```

`Vd=vnot(Vu)` 67

```
vor
```

`Vd=vor(Vu,Vv)` 67

```
vpack
```

`Vd.b=vpack(Vu.h,Vv.h):sat` 206 `Vd.h=vpack(Vu.w,Vv.w):sat` 207

```
vpacke
```

`Vd.b=vpacke(Vu.h,Vv.h)` 206 `Vd.h=vpacke(Vu.w,Vv.w)` 207

```
vpacko
```

`Vd.b=vpacko(Vu.h,Vv.h)` 207 `Vd.h=vpacko(Vu.w,Vv.w)` 207

```
vpopcount
```

`Vd.h=vpopcount(Vu.h)` 273

```
vrdelta
```

`Vd=vrdelta(Vu,Vv)` 202

```
vrmpy
```

`Vd.w=vrmpy(Vu.b,Vv.b)` 186 `Vx.w+=vrmpy(Vu.b,Vv.b)` 162

```
vror
```

`Vd=vror(Vu,Rt)` 196

```
vrotr
```

`Vd.uw=vrotr(Vu.uw,Vv.uw)` 266

```
vround
```

`Vd.b=vround(Vu.h,Vv.h):sat` 263 `Vd.h=vround(Vu.w,Vv.w):sat` 264

```
vsat
```

`Vd.h=vsat(Vu.w,Vv.w)` 88

```
vsatdw
```

`Vd.w=vsatdw(Vu.w,Vv.w)` 88

```
vscatter
```

`if (Qs4) vscatter(Rt,Mu,Vv.h).h=Vw32` 237 `if (Qs4) vscatter(Rt,Mu,Vv.h)=Vw32.h` 237 `if (Qs4) vscatter(Rt,Mu,Vv.w).w=Vw32` 237 `if (Qs4) vscatter(Rt,Mu,Vv.w)=Vw32.w` 237 `if (Qs4) vscatter(Rt,Mu,Vvv.w).h=Vw32` 234 `if (Qs4) vscatter(Rt,Mu,Vvv.w)=Vw32.h` 234 `vscatter(Rt,Mu,Vv.h).h+=Vw32` 237 `vscatter(Rt,Mu,Vv.h).h=Vw32` 237 `vscatter(Rt,Mu,Vv.h)+=Vw32.h` 237 `vscatter(Rt,Mu,Vv.h)=Vw32.h` 237 `vscatter(Rt,Mu,Vv.w).w+=Vw32` 237 `vscatter(Rt,Mu,Vv.w).w=Vw32` 237 `vscatter(Rt,Mu,Vv.w)+=Vw32.w` 237 `vscatter(Rt,Mu,Vv.w)=Vw32.w` 238 `vscatter(Rt,Mu,Vvv.w).h+=Vw32` 234 `vscatter(Rt,Mu,Vvv.w).h=Vw32` 234 `vscatter(Rt,Mu,Vvv.w)+=Vw32.h` 234 `vscatter(Rt,Mu,Vvv.w)=Vw32.h` 234

```
vsetq
```

`Qd4=vsetq(Rt)` 209

```
vsetq2
```

`Qd4=vsetq2(Rt)` 209

```
vshuff
```

`Vd.b=vshuff(Vu.b)` 204 `Vd.h=vshuff(Vu.h)` 204 `Vdd=vshuff(Vu,Vv,Rt)` 221 `vshuff(Vy,Vx,Rt)` 221

```
vshuffe
```

`Qd4.b=vshuffe(Qs4.h,Qt4.h)` 41 `Qd4.h=vshuffe(Qs4.w,Qt4.w)` 41 `Vd.b=vshuffe(Vu.b,Vv.b)` 90 `Vd.h=vshuffe(Vu.h,Vv.h)` 91

```
vshuffo
```

`Vd.b=vshuffo(Vu.b,Vv.b)` 91 `Vd.h=vshuffo(Vu.h,Vv.h)` 91

```
vshuffoe
```

`Vdd.b=vshuffoe(Vu.b,Vv.b)` 44 `Vdd.h=vshuffoe(Vu.h,Vv.h)` 44

```
vsplat
```

`Vd.b=vsplat(Rt)` 188 `Vd.h=vsplat(Rt)` 188 `Vd=vsplat(Rt)` 188

```
vsub
```

`Vd.b=vsub(Vu.b,Vv.b)[:sat]` 62 `Vd.h=vsub(Vu.h,Vv.h)[:sat]` 62 `Vd.uw=vsub(Vu.uw,Vv.uw):sat` 62 `Vd.w,Qe4=vsub(Vu.w,Vv.w):carry` 65 `Vd.w=vsub(Vu.w,Vv.w,Qx4):carry` 65 `Vd.w=vsub(Vu.w,Vv.w)[:sat]` 63 `Vdd.b=vsub(Vuu.b,Vvv.b)[:sat]` 51 `Vdd.h=vsub(Vuu.h,Vvv.h)[:sat]` 51 `Vdd.uw=vsub(Vuu.uw,Vvv.uw):sat` 52 `Vdd.w=vsub(Vu.h,Vv.h)` 123 `Vdd.w=vsub(Vuu.w,Vvv.w)[:sat]` 52

```
vswap
```

`Vdd=vswap(Qt4,Vu,Vv)` 46

```
vsxt
```

`Vdd.h=vsxt(Vu.b)` 49 `Vdd.w=vsxt(Vu.h)` 49

```
vtmpy
```

`Vdd.h=vtmpy(Vuu.b,Rt.b)` 164 `Vdd.w=vtmpy(Vuu.h,Rt.b)` 165 `Vxx.h+=vtmpy(Vuu.b,Rt.b)` 165 `Vxx.w+=vtmpy(Vuu.h,Rt.b)` 165

```
vtrans2x2
```

`vtrans2x2(Vy,Vx,Rt)` 221

```
vunpack
```

`Vdd.h=vunpack(Vu.b)` 231 `Vdd.w=vunpack(Vu.h)` 231

```
vunpacko
```

`Vxx.h|=vunpacko(Vu.b)` 232 `Vxx.w|=vunpacko(Vu.h)` 232

```
vwhist128
```

`vwhist128` 38 `vwhist128(#u1)` 38 `vwhist128(Qv4,#u1)` 39 `vwhist128(Qv4)` 39

```
vwhist256
   sat
```

`vwhist256:sat` 40

`vwhist256` 39 `vwhist256(Qv4)` 39 `vwhist256(Qv4):sat` 40

```
vxor
```

`Vd=vxor(Vu,Vv)` 67

### X

```
xor
```

`Qd4=xor(Qs4,Qt4)` 41
