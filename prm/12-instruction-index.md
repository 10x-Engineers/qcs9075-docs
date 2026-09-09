# Instruction Index

### A

```
abs
```

`Rd=abs(Rs)[:sat]` 330 `Rdd=abs(Rss)` 329

```
add
```

`if ([!]Pu[.new]) Rd=add(Rs,#s8)` 175 `if ([!]Pu[.new]) Rd=add(Rs,Rt)` 175 `Rd=add(#u6,mpyi(Rs,#U6))` 479 `Rd=add(#u6,mpyi(Rs,Rt))` 479 `Rd=add(Rs,#s16)` 153 `Rd=add(Rs,add(Ru,#s6))` 331 `Rd=add(Rs,Rt)` 153 `Rd=add(Rs,Rt):sat` 153 `Rd=add(Rs,Rt):sat:deprecated` 333 `Rd=add(Rt.[HL],Rs.[HL])[:sat]:<<16` 335 `Rd=add(Rt.L,Rs.[HL])[:sat]` 335 `Rd=add(Ru,mpyi(#u6:2,Rs))` 479 `Rd=add(Ru,mpyi(Rs,#u6))` 479 `Rdd=add(Rs,Rtt)` 333 `Rdd=add(Rss,Rtt,Px):carry` 337 `Rdd=add(Rss,Rtt)` 333 `Rdd=add(Rss,Rtt):raw:hi` 333 `Rdd=add(Rss,Rtt):raw:lo` 333 `Rdd=add(Rss,Rtt):sat` 333 `Rx+=add(Rs,#s8)` 331 `Rx+=add(Rs,Rt)` 331 `Rx-=add(Rs,#s8)` 331 `Rx-=add(Rs,Rt)` 331 `Ry=add(Ru,mpyi(Ry,Rs))` 480

```
addasl
```

`Rd=addasl(Rt,Rs,#u3)` 589

```
all8
```

`Pd=all8(Ps)` 194

```
allocframe
```

`allocframe(#u11:3)` 309 `allocframe(Rx,#u11:3):raw` 309

```
and
```

`if ([!]Pu[.new]) Rd=and(Rs,Rt)` 180 `Pd=and(Ps,and(Pt,[!]Pu))` 200 `Pd=and(Pt,[!]Ps)` 200 `Rd=and(Rs,#s10)` 155 `Rd=and(Rs,Rt)` 155 `Rd=and(Rt,~Rs)` 155 `Rdd=and(Rss,Rtt)` 339 `Rdd=and(Rtt,~Rss)` 339 `Rx[&|^]=and(Rs,~Rt)` 341 `Rx[&|^]=and(Rs,Rt)` 341 `Rx|=and(Rs,#s10)` 341

```
any8
```

`Pd=any8(Ps)` 194

```
asl
```

`Rd=asl(Rs,#u5)` 584 `Rd=asl(Rs,#u5):sat` 595 `Rd=asl(Rs,Rt)` 596 `Rd=asl(Rs,Rt):sat` 605 `Rdd=asl(Rss,#u6)` 584 `Rdd=asl(Rss,Rt)` 597 `Rx[&|]=asl(Rs,#u5)` 590 `Rx[&|]=asl(Rs,Rt)` 602 `Rx[+-]=asl(Rs,#u5)` 586 `Rx[+-]=asl(Rs,Rt)` 599 `Rx^=asl(Rs,#u5)` 590 `Rx=add(#u8,asl(Rx,#U5))` 586 `Rx=and(#u8,asl(Rx,#U5))` 590 `Rx=or(#u8,asl(Rx,#U5))` 590 `Rx=sub(#u8,asl(Rx,#U5))` 586 `Rxx[&|]=asl(Rss,#u6)` 590 `Rxx[&|]=asl(Rss,Rt)` 603 `Rxx[+-]=asl(Rss,#u6)` 586 `Rxx[+-]=asl(Rss,Rt)` 599 `Rxx^=asl(Rss,#u6)` 591 `Rxx^=asl(Rss,Rt)` 603

```
aslh
```

`if ([!]Pu[.new]) Rd=aslh(Rs)` 177 `Rd=aslh(Rs)` 173

```
asr
```

`Rd=asr(Rs,#u5)` 584 `Rd=asr(Rs,#u5):rnd` 593 `Rd=asr(Rs,Rt)` 596 `Rd=asr(Rs,Rt):sat` 605 `Rdd=asr(Rss,#u6)` 584 `Rdd=asr(Rss,#u6):rnd` 593 `Rdd=asr(Rss,Rt)` 597 `Rx[&|]=asr(Rs,#u5)` 590 `Rx[&|]=asr(Rs,Rt)` 602 `Rx[+-]=asr(Rs,#u5)` 586 `Rx[+-]=asr(Rs,Rt)` 599 `Rxx[&|]=asr(Rss,#u6)` 591 `Rxx[&|]=asr(Rss,Rt)` 603 `Rxx[+-]=asr(Rss,#u6)` 586 `Rxx[+-]=asr(Rss,Rt)` 600 `Rxx^=asr(Rss,Rt)` 603

```
asrh
```

`if ([!]Pu[.new]) Rd=asrh(Rs)` 177 `Rd=asrh(Rs)` 173

```
asrrnd
```

`Rd=asrrnd(Rs,#u5)` 593 `Rdd=asrrnd(Rss,#u6)` 593

### B

```
barrier
```

`barrier` 314

```
bitsclr
```

`Pd=[!]bitsclr(Rs,#u6)` 569 `Pd=[!]bitsclr(Rs,Rt)` 569

```
bitsplit
```

`Rdd=bitsplit(Rs,#u5)` 419 `Rdd=bitsplit(Rs,Rt)` 419

```
bitsset
```

`Pd=[!]bitsset(Rs,Rt)` 569

```
boundscheck
```

`Pd=boundscheck(Rs,Rtt)` 562 `Pd=boundscheck(Rss,Rtt):raw:hi` 562 `Pd=boundscheck(Rss,Rtt):raw:lo` 562

```
brev
```

`Rd=brev(Rs)` 416 `Rdd=brev(Rss)` 416

```
brkpt
```

`brkpt` 315

### C

```
call
```

`call #r22:2` 208 `if ([!]Pu) call #r15:2` 208

```
callr
```

`callr Rs` 203 `if ([!]Pu) callr Rs` 203

```
callrh
```

`callrh Rs` 203, 204

```
cl0
```

`Rd=cl0(Rs)` 404 `Rd=cl0(Rss)` 404

```
cl1
```

`Rd=cl1(Rs)` 404 `Rd=cl1(Rss)` 404

```
clb
```

`Rd=add(clb(Rs),#s6)` 404 `Rd=add(clb(Rss),#s6)` 404 `Rd=clb(Rs)` 404 `Rd=clb(Rss)` 404

```
clip
```

`Rd=clip(Rs,#u5)` 338

```
clrbit
```

`memb(Rs+#u6:0)=clrbit(#U5)` 265 `memh(Rs+#u6:1)=clrbit(#U5)` 267 `memw(Rs+#u6:2)=clrbit(#U5)` 268 `Rd=clrbit(Rs,#u5)` 417 `Rd=clrbit(Rs,Rt)` 417

```
cmp.eq
```

`if ([!]cmp.eq(Ns.new,#-1)) jump:<hint> #r9:2` 269 `if ([!]cmp.eq(Ns.new,#U5)) jump:<hint> #r9:2` 269 `if ([!]cmp.eq(Ns.new,Rt)) jump:<hint> #r9:2` 269 `p[01]=cmp.eq(Rs,#-1)` 210 `p[01]=cmp.eq(Rs,#U5)` 210 `p[01]=cmp.eq(Rs,Rt)` 210 `Pd=[!]cmp.eq(Rs,#s10)` 188 `Pd=[!]cmp.eq(Rs,Rt)` 188 `Pd=cmp.eq(Rss,Rtt)` 568 `Rd=[!]cmp.eq(Rs,#s8)` 190 `Rd=[!]cmp.eq(Rs,Rt)` 190

```
cmp.ge
```

`Pd=cmp.ge(Rs,#s8)` 188

```
cmp.geu
```

`Pd=cmp.geu(Rs,#u8)` 188

```
cmp.gt
```

`if ([!]cmp.gt(Ns.new,#-1)) jump:<hint> #r9:2` 269 `if ([!]cmp.gt(Ns.new,#U5)) jump:<hint> #r9:2` 269 `if ([!]cmp.gt(Ns.new,Rt)) jump:<hint> #r9:2` 270 `if ([!]cmp.gt(Rt,Ns.new)) jump:<hint> #r9:2` 270 `p[01]=cmp.gt(Rs,#-1)` 210 `p[01]=cmp.gt(Rs,#U5)` 210 `p[01]=cmp.gt(Rs,Rt)` 210 `Pd=[!]cmp.gt(Rs,#s10)` 188 `Pd=[!]cmp.gt(Rs,Rt)` 188 `Pd=cmp.gt(Rss,Rtt)` 568

```
cmp.gtu
```

`if ([!]cmp.gtu(Ns.new,#U5)) jump:<hint> #r9:2` 270 `if ([!]cmp.gtu(Ns.new,Rt)) jump:<hint> #r9:2` 270 `if ([!]cmp.gtu(Rt,Ns.new)) jump:<hint> #r9:2` 270 `p[01]=cmp.gtu(Rs,#U5)` 211 `p[01]=cmp.gtu(Rs,Rt)` 211 `Pd=[!]cmp.gtu(Rs,#u9)` 188 `Pd=[!]cmp.gtu(Rs,Rt)` 188 `Pd=cmp.gtu(Rss,Rtt)` 568

```
cmp.lt
```

`Pd=cmp.lt(Rs,Rt)` 188

```
cmp.ltu
```

`Pd=cmp.ltu(Rs,Rt)` 188

```
cmpb.eq
```

`Pd=cmpb.eq(Rs,#u8)` 564 `Pd=cmpb.eq(Rs,Rt)` 564

```
cmpb.gt
```

`Pd=cmpb.gt(Rs,#s8)` 564 `Pd=cmpb.gt(Rs,Rt)` 564

```
cmpb.gtu
```

`Pd=cmpb.gtu(Rs,#u7)` 564 `Pd=cmpb.gtu(Rs,Rt)` 564

```
cmph.eq
```

`Pd=cmph.eq(Rs,#s8)` 566 `Pd=cmph.eq(Rs,Rt)` 566

```
cmph.gt
```

`Pd=cmph.gt(Rs,#s8)` 566 `Pd=cmph.gt(Rs,Rt)` 566

```
cmph.gtu
```

`Pd=cmph.gtu(Rs,#u7)` 566 `Pd=cmph.gtu(Rs,Rt)` 566

```
cmpy
```

`Rd=cmpy(Rs,Rt)[:<<1]:rnd:sat` 434 `Rd=cmpy(Rs,Rt*)[:<<1]:rnd:sat` 434 `Rdd=cmpy(Rs,Rt)[:<<1]:sat` 428 `Rdd=cmpy(Rs,Rt*)[:<<1]:sat` 428 `Rxx+=cmpy(Rs,Rt)[:<<1]:sat` 429 `Rxx+=cmpy(Rs,Rt*)[:<<1]:sat` 429 `Rxx-=cmpy(Rs,Rt)[:<<1]:sat` 429 `Rxx-=cmpy(Rs,Rt*)[:<<1]:sat` 429

```
cmpyi
```

`Rdd=cmpyi(Rs,Rt)` 432 `Rxx+=cmpyi(Rs,Rt)` 432

```
cmpyiw
```

`Rd=cmpyiw(Rss,Rtt):<<1:rnd:sat` 438 `Rd=cmpyiw(Rss,Rtt):<<1:sat` 438 `Rd=cmpyiw(Rss,Rtt*):<<1:rnd:sat` 438 `Rd=cmpyiw(Rss,Rtt*):<<1:sat` 438 `Rdd=cmpyiw(Rss,Rtt)` 439 `Rdd=cmpyiw(Rss,Rtt*)` 439 `Rxx+=cmpyiw(Rss,Rtt)` 439 `Rxx+=cmpyiw(Rss,Rtt*)` 439

```
cmpyiwh
```

`Rd=cmpyiwh(Rss,Rt):<<1:rnd:sat` 436 `Rd=cmpyiwh(Rss,Rt*):<<1:rnd:sat` 436

```
cmpyr
```

`Rdd=cmpyr(Rs,Rt)` 432 `Rxx+=cmpyr(Rs,Rt)` 432

```
cmpyrw
```

`Rd=cmpyrw(Rss,Rtt):<<1:rnd:sat` 438 `Rd=cmpyrw(Rss,Rtt):<<1:sat` 438 `Rd=cmpyrw(Rss,Rtt*):<<1:rnd:sat` 439 `Rd=cmpyrw(Rss,Rtt*):<<1:sat` 439 `Rdd=cmpyrw(Rss,Rtt)` 439 `Rdd=cmpyrw(Rss,Rtt*)` 439 `Rxx+=cmpyrw(Rss,Rtt)` 439 `Rxx+=cmpyrw(Rss,Rtt*)` 439

```
cmpyrwh
```

`Rd=cmpyrwh(Rss,Rt):<<1:rnd:sat` 436 `Rd=cmpyrwh(Rss,Rt*):<<1:rnd:sat` 436

```
combine
```

`if ([!]Pu[.new]) Rdd=combine(Rs,Rt)` 179 `Rd=combine(Rt.[HL],Rs.[HL])` 169 `Rdd=combine(#s8,#S8)` 169 `Rdd=combine(#s8,#U6)` 169 `Rdd=combine(#s8,Rs)` 169 `Rdd=combine(Rs,#s8)` 169 `Rdd=combine(Rs,Rt)` 170

```
convert_d2df
```

`Rdd=convert_d2df(Rss)` 462

```
convert_d2sf
```

`Rd=convert_d2sf(Rss)` 462

```
convert_df2d
```

`Rdd=convert_df2d(Rss)` 464 `Rdd=convert_df2d(Rss):chop` 464

```
convert_df2sf
```

`Rd=convert_df2sf(Rss)` 461

```
convert_df2ud
```

`Rdd=convert_df2ud(Rss)` 464 `Rdd=convert_df2ud(Rss):chop` 464

```
convert_df2uw
```

`Rd=convert_df2uw(Rss)` 464 `Rd=convert_df2uw(Rss):chop` 464

```
convert_df2w
```

`Rd=convert_df2w(Rss)` 464 `Rd=convert_df2w(Rss):chop` 464

```
convert_sf2d
```

`Rdd=convert_sf2d(Rs)` 464 `Rdd=convert_sf2d(Rs):chop` 464

```
convert_sf2df
```

`Rdd=convert_sf2df(Rs)` 461

```
convert_sf2ud
```

`Rdd=convert_sf2ud(Rs)` 464 `Rdd=convert_sf2ud(Rs):chop` 464

```
convert_sf2uw
```

`Rd=convert_sf2uw(Rs)` 464 `Rd=convert_sf2uw(Rs):chop` 464

```
convert_sf2w
```

`Rd=convert_sf2w(Rs)` 464 `Rd=convert_sf2w(Rs):chop` 464

```
convert_ud2df
```

`Rdd=convert_ud2df(Rss)` 462

```
convert_ud2sf
```

`Rd=convert_ud2sf(Rss)` 462

```
convert_uw2df
```

`Rdd=convert_uw2df(Rs)` 462

```
convert_uw2sf
```

`Rd=convert_uw2sf(Rs)` 462

```
convert_w2df
```

`Rdd=convert_w2df(Rs)` 462

```
convert_w2sf
```

`Rd=convert_w2sf(Rs)` 462

```
cround
```

`Rd=cround(Rs,#u5)` 350 `Rd=cround(Rs,Rt)` 350 `Rdd=cround(Rss,#u6)` 350 `Rdd=cround(Rss,Rt)` 351

```
ct0
```

`Rd=ct0(Rs)` 407 `Rd=ct0(Rss)` 407

```
ct1
```

`Rd=ct1(Rs)` 407 `Rd=ct1(Rss)` 407

### D

```
dccleana
```

`dccleana(Rs)` 317

```
dccleaninva
```

`dccleaninva(Rs)` 317

```
dcfetch
```

`dcfetch(Rs)` 316 `dcfetch(Rs+#u11:3)` 316

```
dcinva
```

`dcinva(Rs)` 317

```
dczeroa
```

`dczeroa(Rs)` 313

```
dealloc_return
```

`dealloc_return` 255 `if ([!]Pv.new) Rdd=dealloc_return(Rs):nt:raw` 255 `if ([!]Pv.new) Rdd=dealloc_return(Rs):t:raw` 255 `if ([!]Pv) dealloc_return` 255 `if ([!]Pv) Rdd=dealloc_return(Rs):raw` 255

```
nt
```

`if ([!]Pv.new) dealloc_return:nt` 255

`Rdd=dealloc_return(Rs):raw` 255

```
t
```

`if ([!]Pv.new) dealloc_return:t` 255

```
deallocframe
```

`deallocframe` 253 `Rdd=deallocframe(Rs):raw` 253

```
decbin
```

`Rdd=decbin(Rss,Rtt)` 535

```
deinterleave
```

`Rdd=deinterleave(Rss)` 413

```
dfadd
```

`Rdd=dfadd(Rss,Rtt)` 456

```
dfclass
```

`Pd=dfclass(Rss,#u5)` 457

```
dfcmp.eq
```

`Pd=dfcmp.eq(Rss,Rtt)` 459

```
dfcmp.ge
```

`Pd=dfcmp.ge(Rss,Rtt)` 459

```
dfcmp.gt
```

`Pd=dfcmp.gt(Rss,Rtt)` 459

```
dfcmp.uo
```

`Pd=dfcmp.uo(Rss,Rtt)` 459

```
dfmake
```

`Rdd=dfmake(#u10):neg` 473 `Rdd=dfmake(#u10):pos` 473

```
dfmax
```

`Rdd=dfmax(Rss,Rtt)` 474

```
dfmin
```

`Rdd=dfmin(Rss,Rtt)` 475

```
dfmpyfix
```

`Rdd=dfmpyfix(Rss,Rtt)` 476

```
dfmpyhh
```

`Rxx+=dfmpyhh(Rss,Rtt)` 468

```
dfmpylh
```

`Rxx+=dfmpylh(Rss,Rtt)` 468

```
dfmpyll
```

`Rdd=dfmpyll(Rss,Rtt)` 476

```
dfsub
```

`Rdd=dfsub(Rss,Rtt)` 478

```
diag
```

`diag(Rs)` 319

```
diag0
```

`diag0(Rss,Rtt)` 319

```
diag1
```

`diag1(Rss,Rtt)` 319

```
dmsyncht
```

`Rd=dmsyncht` 325

### E

```
endloop0
```

`endloop0` 191

```
endloop01
```

`endloop01` 191

```
endloop1
```

`endloop1` 191

```
extract
```

`Rd=extract(Rs,#u5,#U5)` 408 `Rd=extract(Rs,Rtt)` 408 `Rdd=extract(Rss,#u6,#U6)` 408 `Rdd=extract(Rss,Rtt)` 409

```
extractu
```

`Rd=extractu(Rs,#u5,#U5)` 408 `Rd=extractu(Rs,Rtt)` 408 `Rdd=extractu(Rss,#u6,#U6)` 409 `Rdd=extractu(Rss,Rtt)` 409

### F

```
fastcorner9
```

`Pd=[!]fastcorner9(Ps,Pt)` 193

### H

```
hintjr
```

`hintjr(Rs)` 205

### I

```
icinva
```

`icinva(Rs)` 320

`if ([!]p[01].new) jump:<hint> #r9:2` 210, 210, 210, 210, 210, 210, 211, 211, 211

```
insert
```

`Rx=insert(Rs,#u5,#U5)` 411 `Rx=insert(Rs,Rtt)` 411 `Rxx=insert(Rss,#u6,#U6)` 411 `Rxx=insert(Rss,Rtt)` 412

```
interleave
```

`Rdd=interleave(Rss)` 413

```
isync
```

`isync` 321

### J

```
jump
```

`if ([!]Pu.new) jump:<hint> #r15:2` 215 `if ([!]Pu) jump #r15:2` 214 `if ([!]Pu) jump:<hint> #r15:2` 214 `jump #r22:2` 214

```
nt
```

`if (Rs!=#0) jump:nt #r13:2` 216 `if (Rs<=#0) jump:nt #r13:2` 216 `if (Rs==#0) jump:nt #r13:2` 216 `if (Rs>=#0) jump:nt #r13:2` 216

`Rd=#U6` 218 `Rd=Rs` 218

```
t
```

`if (Rs!=#0) jump:t #r13:2` 216 `if (Rs<=#0) jump:t #r13:2` 216 `if (Rs==#0) jump:t #r13:2` 216 `if (Rs>=#0) jump:t #r13:2` 216

`jump #r9:2` 218, 218

```
jumpr
```

`if ([!]Pu) jumpr Rs` 206 `if ([!]Pu[.new]) jumpr:<hint> Rs` 206 `jumpr Rs` 206

```
jumprh
```

`jumprh Rs` 206, 207

### L

```
l2fetch
```

`l2fetch(Rs,Rt)` 323 `l2fetch(Rs,Rtt)` 323

```
lfs
```

`Rdd=lfs(Rss,Rtt)` 414

```
linecpy
```

`Rdd=linecpy(Rs,Rtt)` 239

```
loop0
```

`loop0(#r7:2,#U10)` 195 `loop0(#r7:2,Rs)` 195

```
loop1
```

`loop1(#r7:2,#U10)` 195 `loop1(#r7:2,Rs)` 195

```
lsl
```

`Rd=lsl(#s6,Rt)` 596 `Rd=lsl(Rs,Rt)` 596 `Rdd=lsl(Rss,Rt)` 597 `Rx[&|]=lsl(Rs,Rt)` 602 `Rx[+-]=lsl(Rs,Rt)` 599 `Rxx[&|]=lsl(Rss,Rt)` 603 `Rxx[+-]=lsl(Rss,Rt)` 600 `Rxx^=lsl(Rss,Rt)` 603

```
lsr
```

`Rd=lsr(Rs,#u5)` 584 `Rd=lsr(Rs,Rt)` 596 `Rdd=lsr(Rss,#u6)` 584 `Rdd=lsr(Rss,Rt)` 597 `Rx[&|]=lsr(Rs,#u5)` 590 `Rx[&|]=lsr(Rs,Rt)` 602 `Rx[+-]=lsr(Rs,#u5)` 586 `Rx[+-]=lsr(Rs,Rt)` 599 `Rx^=lsr(Rs,#u5)` 590 `Rx=add(#u8,lsr(Rx,#U5))` 586 `Rx=and(#u8,lsr(Rx,#U5))` 590 `Rx=or(#u8,lsr(Rx,#U5))` 590 `Rx=sub(#u8,lsr(Rx,#U5))` 586 `Rxx[&|]=lsr(Rss,#u6)` 591 `Rxx[&|]=lsr(Rss,Rt)` 603 `Rxx[+-]=lsr(Rss,#u6)` 586 `Rxx[+-]=lsr(Rss,Rt)` 600 `Rxx^=lsr(Rss,#u6)` 591 `Rxx^=lsr(Rss,Rt)` 603

### M

```
mask
```

`Rd=mask(#u5,#U5)` 583 `Rdd=mask(Pt)` 570

```
max
```

`Rd=max(Rs,Rt)` 344 `Rdd=max(Rss,Rtt)` 345

```
maxu
```

`Rd=maxu(Rs,Rt)` 344 `Rdd=maxu(Rss,Rtt)` 345

```
memb
```

`if ([!]Pt[.new]) Rd=memb(#u6)` 226 `if ([!]Pt[.new]) Rd=memb(Rs+#u6:0)` 226 `if ([!]Pt[.new]) Rd=memb(Rx++#s4:0)` 226 `if ([!]Pv[.new]) memb(#u6)=Nt.new` 275 `if ([!]Pv[.new]) memb(#u6)=Rt` 292 `if ([!]Pv[.new]) memb(Rs+#u6:0)=#S6` 292 `if ([!]Pv[.new]) memb(Rs+#u6:0)=Nt.new` 275 `if ([!]Pv[.new]) memb(Rs+#u6:0)=Rt` 292 `if ([!]Pv[.new]) memb(Rs+Ru<<#u2)=Nt.new` 275 `if ([!]Pv[.new]) memb(Rs+Ru<<#u2)=Rt` 292 `if ([!]Pv[.new]) memb(Rx++#s4:0)=Nt.new` 275 `if ([!]Pv[.new]) memb(Rx++#s4:0)=Rt` 292 `if ([!]Pv[.new]) Rd=memb(Rs+Rt<<#u2)` 226 `memb(gp+#u16:0)=Nt.new` 273 `memb(gp+#u16:0)=Rt` 290 `memb(Re=#U6)=Nt.new` 273 `memb(Re=#U6)=Rt` 290 `memb(Rs+#s11:0)=Nt.new` 273 `memb(Rs+#s11:0)=Rt` 290 `memb(Rs+#u6:0)[+-]=#U5` 265 `memb(Rs+#u6:0)[+-|&]=Rt` 265 `memb(Rs+#u6:0)=#S8` 290 `memb(Rs+Ru<<#u2)=Nt.new` 273 `memb(Rs+Ru<<#u2)=Rt` 290 `memb(Ru<<#u2+#U6)=Nt.new` 273 `memb(Ru<<#u2+#U6)=Rt` 290 `memb(Rx++#s4:0:circ(Mu))=Nt.new` 273 `memb(Rx++#s4:0:circ(Mu))=Rt` 290 `memb(Rx++#s4:0)=Nt.new` 273 `memb(Rx++#s4:0)=Rt` 290 `memb(Rx++I:circ(Mu))=Nt.new` 273 `memb(Rx++I:circ(Mu))=Rt` 290 `memb(Rx++Mu:brev)=Nt.new` 273 `memb(Rx++Mu:brev)=Rt` 290 `memb(Rx++Mu)=Nt.new` 273 `memb(Rx++Mu)=Rt` 290 `Rd=memb(gp+#u16:0)` 224 `Rd=memb(Re=#U6)` 224 `Rd=memb(Rs+#s11:0)` 224 `Rd=memb(Rs+Rt<<#u2)` 224 `Rd=memb(Rt<<#u2+#U6)` 224 `Rd=memb(Rx++#s4:0:circ(Mu))` 224 `Rd=memb(Rx++#s4:0)` 224 `Rd=memb(Rx++I:circ(Mu))` 224 `Rd=memb(Rx++Mu:brev)` 224 `Rd=memb(Rx++Mu)` 224

```
memb_fifo
```

`Ryy=memb_fifo(Re=#U6)` 228 `Ryy=memb_fifo(Rs)` 228 `Ryy=memb_fifo(Rs+#s11:0)` 228 `Ryy=memb_fifo(Rt<<#u2+#U6)` 228 `Ryy=memb_fifo(Rx++#s4:0:circ(Mu))` 228 `Ryy=memb_fifo(Rx++#s4:0)` 228 `Ryy=memb_fifo(Rx++I:circ(Mu))` 229 `Ryy=memb_fifo(Rx++Mu:brev)` 229 `Ryy=memb_fifo(Rx++Mu)` 229

```
membh
```

`Rd=membh(Re=#U6)` 257 `Rd=membh(Rs)` 257 `Rd=membh(Rs+#s11:1)` 257 `Rd=membh(Rt<<#u2+#U6)` 257 `Rd=membh(Rx++#s4:1:circ(Mu))` 258 `Rd=membh(Rx++#s4:1)` 258 `Rd=membh(Rx++I:circ(Mu))` 258 `Rd=membh(Rx++Mu:brev)` 258 `Rd=membh(Rx++Mu)` 258 `Rdd=membh(Re=#U6)` 260 `Rdd=membh(Rs)` 260 `Rdd=membh(Rs+#s11:2)` 260 `Rdd=membh(Rt<<#u2+#U6)` 260 `Rdd=membh(Rx++#s4:2:circ(Mu))` 260 `Rdd=membh(Rx++#s4:2)` 260 `Rdd=membh(Rx++I:circ(Mu))` 261 `Rdd=membh(Rx++Mu:brev)` 261 `Rdd=membh(Rx++Mu)` 261

```
memd
```

`if ([!]Pt[.new]) Rdd=memd(#u6)` 222 `if ([!]Pt[.new]) Rdd=memd(Rs+#u6:3)` 222 `if ([!]Pt[.new]) Rdd=memd(Rx++#s4:3)` 222 `if ([!]Pv[.new]) memd(#u6)=Rtt` 288 `if ([!]Pv[.new]) memd(Rs+#u6:3)=Rtt` 288 `if ([!]Pv[.new]) memd(Rs+Ru<<#u2)=Rtt` 288 `if ([!]Pv[.new]) memd(Rx++#s4:3)=Rtt` 288 `if ([!]Pv[.new]) Rdd=memd(Rs+Rt<<#u2)` 222 `memd(gp+#u16:3)=Rtt` 285 `memd(Re=#U6)=Rtt` 285 `memd(Rs+#s11:3)=Rtt` 285 `memd(Rs+Ru<<#u2)=Rtt` 285 `memd(Ru<<#u2+#U6)=Rtt` 285 `memd(Rx++#s4:3:circ(Mu))=Rtt` 285 `memd(Rx++#s4:3)=Rtt` 285 `memd(Rx++I:circ(Mu))=Rtt` 285 `memd(Rx++Mu:brev)=Rtt` 285 `memd(Rx++Mu)=Rtt` 285 `Rdd=memd(gp+#u16:3)` 219 `Rdd=memd(Re=#U6)` 219 `Rdd=memd(Rs+#s11:3)` 219 `Rdd=memd(Rs+Rt<<#u2)` 219 `Rdd=memd(Rt<<#u2+#U6)` 219 `Rdd=memd(Rx++#s4:3:circ(Mu))` 219 `Rdd=memd(Rx++#s4:3)` 219 `Rdd=memd(Rx++I:circ(Mu))` 219 `Rdd=memd(Rx++Mu:brev)` 219 `Rdd=memd(Rx++Mu)` 219

```
memd_aq
```

`Rdd=memd_aq(Rs)` 221

```
memd_locked
```

`memd_locked(Rs,Pd)=Rtt` 312 `Rdd=memd_locked(Rs)` 311

```
memd_rl
```

`memd_rl(Rs):at=Rtt` 287 `memd_rl(Rs):st=Rtt` 287

```
memh
```

`if ([!]Pt[.new]) Rd=memh(#u6)` 236 `if ([!]Pt[.new]) Rd=memh(Rs+#u6:1)` 236 `if ([!]Pt[.new]) Rd=memh(Rx++#s4:1)` 236 `if ([!]Pv[.new]) memh(#u6)=Nt.new` 279 `if ([!]Pv[.new]) memh(#u6)=Rt` 298 `if ([!]Pv[.new]) memh(#u6)=Rt.H` 298 `if ([!]Pv[.new]) memh(Rs+#u6:1)=#S6` 298 `if ([!]Pv[.new]) memh(Rs+#u6:1)=Nt.new` 279 `if ([!]Pv[.new]) memh(Rs+#u6:1)=Rt` 298 `if ([!]Pv[.new]) memh(Rs+#u6:1)=Rt.H` 298 `if ([!]Pv[.new]) memh(Rs+Ru<<#u2)=Nt.new` 279 `if ([!]Pv[.new]) memh(Rs+Ru<<#u2)=Rt` 299 `if ([!]Pv[.new]) memh(Rs+Ru<<#u2)=Rt.H` 298 `if ([!]Pv[.new]) memh(Rx++#s4:1)=Nt.new` 279 `if ([!]Pv[.new]) memh(Rx++#s4:1)=Rt` 299 `if ([!]Pv[.new]) memh(Rx++#s4:1)=Rt.H` 299 `if ([!]Pv[.new]) Rd=memh(Rs+Rt<<#u2)` 236 `memh(gp+#u16:1)=Nt.new` 277 `memh(gp+#u16:1)=Rt` 296 `memh(gp+#u16:1)=Rt.H` 296 `memh(Re=#U6)=Nt.new` 277 `memh(Re=#U6)=Rt` 295 `memh(Re=#U6)=Rt.H` 295 `memh(Rs+#s11:1)=Nt.new` 277 `memh(Rs+#s11:1)=Rt` 295 `memh(Rs+#s11:1)=Rt.H` 295 `memh(Rs+#u6:1)[+-]=#U5` 267 `memh(Rs+#u6:1)[+-|&]=Rt` 267 `memh(Rs+#u6:1)=#S8` 295 `memh(Rs+Ru<<#u2)=Nt.new` 277 `memh(Rs+Ru<<#u2)=Rt` 295 `memh(Rs+Ru<<#u2)=Rt.H` 295 `memh(Ru<<#u2+#U6)=Nt.new` 277 `memh(Ru<<#u2+#U6)=Rt` 295 `memh(Ru<<#u2+#U6)=Rt.H` 295 `memh(Rx++#s4:1:circ(Mu))=Nt.new` 277 `memh(Rx++#s4:1:circ(Mu))=Rt` 295 `memh(Rx++#s4:1:circ(Mu))=Rt.H` 295 `memh(Rx++#s4:1)=Nt.new` 277 `memh(Rx++#s4:1)=Rt` 295 `memh(Rx++#s4:1)=Rt.H` 295 `memh(Rx++I:circ(Mu))=Nt.new` 277 `memh(Rx++I:circ(Mu))=Rt` 295 `memh(Rx++I:circ(Mu))=Rt.H` 295 `memh(Rx++Mu:brev)=Nt.new` 277 `memh(Rx++Mu:brev)=Rt` 296 `memh(Rx++Mu:brev)=Rt.H` 296 `memh(Rx++Mu)=Nt.new` 277 `memh(Rx++Mu)=Rt` 296 `memh(Rx++Mu)=Rt.H` 296 `Rd=memh(gp+#u16:1)` 234 `Rd=memh(Re=#U6)` 234 `Rd=memh(Rs+#s11:1)` 234 `Rd=memh(Rs+Rt<<#u2)` 234 `Rd=memh(Rt<<#u2+#U6)` 234 `Rd=memh(Rx++#s4:1:circ(Mu))` 234 `Rd=memh(Rx++#s4:1)` 234 `Rd=memh(Rx++I:circ(Mu))` 234 `Rd=memh(Rx++Mu:brev)` 234 `Rd=memh(Rx++Mu)` 234

```
memh_fifo
```

`Ryy=memh_fifo(Re=#U6)` 231 `Ryy=memh_fifo(Rs)` 231 `Ryy=memh_fifo(Rs+#s11:1)` 231 `Ryy=memh_fifo(Rt<<#u2+#U6)` 231 `Ryy=memh_fifo(Rx++#s4:1:circ(Mu))` 231 `Ryy=memh_fifo(Rx++#s4:1)` 231 `Ryy=memh_fifo(Rx++I:circ(Mu))` 232 `Ryy=memh_fifo(Rx++Mu:brev)` 232 `Ryy=memh_fifo(Rx++Mu)` 232

```
memub
```

`if ([!]Pt[.new]) Rd=memub(#u6)` 242 `if ([!]Pt[.new]) Rd=memub(Rs+#u6:0)` 242 `if ([!]Pt[.new]) Rd=memub(Rx++#s4:0)` 242 `if ([!]Pv[.new]) Rd=memub(Rs+Rt<<#u2)` 242 `Rd=memub(gp+#u16:0)` 240 `Rd=memub(Re=#U6)` 240 `Rd=memub(Rs+#s11:0)` 240 `Rd=memub(Rs+Rt<<#u2)` 240 `Rd=memub(Rt<<#u2+#U6)` 240 `Rd=memub(Rx++#s4:0:circ(Mu))` 240 `Rd=memub(Rx++#s4:0)` 240 `Rd=memub(Rx++I:circ(Mu))` 240 `Rd=memub(Rx++Mu:brev)` 240 `Rd=memub(Rx++Mu)` 240

```
memubh
```

`Rd=memubh(Re=#U6)` 258 `Rd=memubh(Rs+#s11:1)` 259 `Rd=memubh(Rt<<#u2+#U6)` 259 `Rd=memubh(Rx++#s4:1:circ(Mu))` 259 `Rd=memubh(Rx++#s4:1)` 259 `Rd=memubh(Rx++I:circ(Mu))` 259 `Rd=memubh(Rx++Mu:brev)` 260 `Rd=memubh(Rx++Mu)` 259 `Rdd=memubh(Re=#U6)` 261 `Rdd=memubh(Rs+#s11:2)` 261 `Rdd=memubh(Rt<<#u2+#U6)` 261 `Rdd=memubh(Rx++#s4:2:circ(Mu))` 262 `Rdd=memubh(Rx++#s4:2)` 262 `Rdd=memubh(Rx++I:circ(Mu))` 262 `Rdd=memubh(Rx++Mu:brev)` 262 `Rdd=memubh(Rx++Mu)` 262

```
memuh
```

`if ([!]Pt[.new]) Rd=memuh(#u6)` 246 `if ([!]Pt[.new]) Rd=memuh(Rs+#u6:1)` 246 `if ([!]Pt[.new]) Rd=memuh(Rx++#s4:1)` 246 `if ([!]Pv[.new]) Rd=memuh(Rs+Rt<<#u2)` 246 `Rd=memuh(gp+#u16:1)` 244 `Rd=memuh(Re=#U6)` 244 `Rd=memuh(Rs+#s11:1)` 244 `Rd=memuh(Rs+Rt<<#u2)` 244 `Rd=memuh(Rt<<#u2+#U6)` 244 `Rd=memuh(Rx++#s4:1:circ(Mu))` 244 `Rd=memuh(Rx++#s4:1)` 244 `Rd=memuh(Rx++I:circ(Mu))` 244 `Rd=memuh(Rx++Mu:brev)` 244 `Rd=memuh(Rx++Mu)` 244

```
memw
```

`if ([!]Pt[.new]) Rd=memw(#u6)` 251 `if ([!]Pt[.new]) Rd=memw(Rs+#u6:2)` 251 `if ([!]Pt[.new]) Rd=memw(Rx++#s4:2)` 251 `if ([!]Pv[.new]) memw(#u6)=Nt.new` 283 `if ([!]Pv[.new]) memw(#u6)=Rt` 306 `if ([!]Pv[.new]) memw(Rs+#u6:2)=#S6` 306 `if ([!]Pv[.new]) memw(Rs+#u6:2)=Nt.new` 283 `if ([!]Pv[.new]) memw(Rs+#u6:2)=Rt` 306 `if ([!]Pv[.new]) memw(Rs+Ru<<#u2)=Nt.new` 283 `if ([!]Pv[.new]) memw(Rs+Ru<<#u2)=Rt` 306 `if ([!]Pv[.new]) memw(Rx++#s4:2)=Nt.new` 283 `if ([!]Pv[.new]) memw(Rx++#s4:2)=Rt` 306 `if ([!]Pv[.new]) Rd=memw(Rs+Rt<<#u2)` 251 `memw(gp+#u16:2)=Nt.new` 281 `memw(gp+#u16:2)=Rt` 303 `memw(Re=#U6)=Nt.new` 281 `memw(Re=#U6)=Rt` 303 `memw(Rs+#s11:2)=Nt.new` 281 `memw(Rs+#s11:2)=Rt` 303 `memw(Rs+#u6:2)[+-]=#U5` 268 `memw(Rs+#u6:2)[+-|&]=Rt` 268 `memw(Rs+#u6:2)=#S8` 303 `memw(Rs+Ru<<#u2)=Nt.new` 281 `memw(Rs+Ru<<#u2)=Rt` 303 `memw(Ru<<#u2+#U6)=Nt.new` 281 `memw(Ru<<#u2+#U6)=Rt` 303 `memw(Rx++#s4:2:circ(Mu))=Nt.new` 281 `memw(Rx++#s4:2:circ(Mu))=Rt` 303 `memw(Rx++#s4:2)=Nt.new` 281 `memw(Rx++#s4:2)=Rt` 303 `memw(Rx++I:circ(Mu))=Nt.new` 281 `memw(Rx++I:circ(Mu))=Rt` 303 `memw(Rx++Mu:brev)=Nt.new` 281 `memw(Rx++Mu:brev)=Rt` 303 `memw(Rx++Mu)=Nt.new` 281 `memw(Rx++Mu)=Rt` 303 `Rd=memw(gp+#u16:2)` 248 `Rd=memw(Re=#U6)` 248 `Rd=memw(Rs+#s11:2)` 248 `Rd=memw(Rs+Rt<<#u2)` 248 `Rd=memw(Rt<<#u2+#U6)` 248 `Rd=memw(Rx++#s4:2:circ(Mu))` 248 `Rd=memw(Rx++#s4:2)` 248 `Rd=memw(Rx++I:circ(Mu))` 248 `Rd=memw(Rx++Mu:brev)` 248 `Rd=memw(Rx++Mu)` 248

```
memw_aq
```

`Rd=memw_aq(Rs)` 250

```
memw_locked
```

`memw_locked(Rs,Pd)=Rt` 312 `Rd=memw_locked(Rs)` 311

```
memw_rl
```

`memw_rl(Rs):at=Rt` 305 `memw_rl(Rs):st=Rt` 305

```
min
```

`Rd=min(Rt,Rs)` 346 `Rdd=min(Rtt,Rss)` 347

```
minu
```

`Rd=minu(Rt,Rs)` 346 `Rdd=minu(Rtt,Rss)` 347

```
modwrap
```

`Rd=modwrap(Rs,Rt)` 348

```
movlen
```

`Rd=movlen(Rs,Rtt)` 239

```
mpy
```

`Rd=mpy(Rs,Rt.H):<<1:rnd:sat` 507 `Rd=mpy(Rs,Rt.H):<<1:sat` 507 `Rd=mpy(Rs,Rt.L):<<1:rnd:sat` 507 `Rd=mpy(Rs,Rt.L):<<1:sat` 507 `Rd=mpy(Rs,Rt)` 507 `Rd=mpy(Rs,Rt):<<1` 507 `Rd=mpy(Rs,Rt):<<1:sat` 507 `Rd=mpy(Rs,Rt):rnd` 507 `Rd=mpy(Rs.[HL],Rt.[HL])[:<<1][:rnd][:sat]` 491 `Rdd=mpy(Rs,Rt)` 510 `Rdd=mpy(Rs.[HL],Rt.[HL])[:<<1][:rnd]` 491 `Rx+=mpy(Rs,Rt):<<1:sat` 507 `Rx+=mpy(Rs.[HL],Rt.[HL])[:<<1][:sat]` 491 `Rx-=mpy(Rs,Rt):<<1:sat` 507 `Rx-=mpy(Rs.[HL],Rt.[HL])[:<<1][:sat]` 491 `Rxx[+-]=mpy(Rs,Rt)` 510 `Rxx+=mpy(Rs.[HL],Rt.[HL])[:<<1]` 491 `Rxx-=mpy(Rs.[HL],Rt.[HL])[:<<1]` 491

```
mpyi
```

`Rd=+mpyi(Rs,#u8)` 479 `Rd=mpyi(Rs,#m9)` 480 `Rd=-mpyi(Rs,#u8)` 479 `Rd=mpyi(Rs,Rt)` 480 `Rx+=mpyi(Rs,#u8)` 480 `Rx+=mpyi(Rs,Rt)` 480 `Rx-=mpyi(Rs,#u8)` 480 `Rx-=mpyi(Rs,Rt)` 480

```
mpysu
```

`Rd=mpysu(Rs,Rt)` 507

```
mpyu
```

`Rd=mpyu(Rs,Rt)` 507 `Rd=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498 `Rdd=mpyu(Rs,Rt)` 510 `Rdd=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498 `Rx+=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498 `Rx-=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498 `Rxx[+-]=mpyu(Rs,Rt)` 510 `Rxx+=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498 `Rxx-=mpyu(Rs.[HL],Rt.[HL])[:<<1]` 498

```
mpyui
```

`Rd=mpyui(Rs,Rt)` 480

```
mux
```

`Rd=mux(Pu,#s8,#S8)` 171 `Rd=mux(Pu,#s8,Rs)` 171 `Rd=mux(Pu,Rs,#s8)` 171 `Rd=mux(Pu,Rs,Rt)` 171

### N

```
neg
```

`Rd=neg(Rs)` 157 `Rd=neg(Rs):sat` 349 `Rdd=neg(Rss)` 349

```
no mnemonic
```

`Cd=Rs` 202 `Cdd=Rss` 202 `if ([!]Pu[.new]) Rd=#s12` 185 `if ([!]Pu[.new]) Rd=Rs` 185 `if ([!]Pu[.new]) Rdd=Rss` 185 `Pd=Ps` 200 `Pd=Rs` 572 `Rd=#s16` 162 `Rd=Cs` 202 `Rd=Ps` 572 `Rd=Rs` 164 `Rdd=#s8` 162 `Rdd=Css` 202 `Rdd=Rss` 164 `Rx.[HL]=#u16` 162

```
nop
```

`nop` 158

```
normamt
```

`Rd=normamt(Rs)` 404 `Rd=normamt(Rss)` 404

```
not
```

`Pd=not(Ps)` 200 `Rd=not(Rs)` 155 `Rdd=not(Rss)` 339

### O

```
or
```

`if ([!]Pu[.new]) Rd=or(Rs,Rt)` 180 `Pd=and(Ps,or(Pt,[!]Pu))` 200 `Pd=or(Ps,and(Pt,[!]Pu))` 200 `Pd=or(Ps,or(Pt,[!]Pu))` 200 `Pd=or(Pt,[!]Ps)` 200 `Rd=or(Rs,#s10)` 155 `Rd=or(Rs,Rt)` 155 `Rd=or(Rt,~Rs)` 155 `Rdd=or(Rss,Rtt)` 339 `Rdd=or(Rtt,~Rss)` 339 `Rx[&|^]=or(Rs,Rt)` 341 `Rx=or(Ru,and(Rx,#s10))` 341 `Rx|=or(Rs,#s10)` 341

### P

```
packhl
```

`Rdd=packhl(Rs,Rt)` 174

```
parity
```

`Rd=parity(Rs,Rt)` 415 `Rd=parity(Rss,Rtt)` 415

```
pause
```

`pause(#u10)` 324

```
pc
```

`Rd=add(pc,#u6)` 197

```
pmemcpy
```

`Rdd=pmemcpy(Rx,Rtt)` 238, 239

```
pmpyw
```

`Rdd=pmpyw(Rs,Rt)` 503 `Rxx^=pmpyw(Rs,Rt)` 503

```
popcount
```

`Rd=popcount(Rss)` 406

### R

```
release
```

`release(Rs):at` 302 `release(Rs):st` 302

```
rol
```

`Rd=rol(Rs,#u5)` 584 `Rdd=rol(Rss,#u6)` 584 `Rx[&|]=rol(Rs,#u5)` 590 `Rx[+-]=rol(Rs,#u5)` 586 `Rx^=rol(Rs,#u5)` 590 `Rxx[&|]=rol(Rss,#u6)` 591 `Rxx[+-]=rol(Rss,#u6)` 586 `Rxx^=rol(Rss,#u6)` 591

```
round
```

`Rd=round(Rs,#u5)[:sat]` 350 `Rd=round(Rs,Rt)[:sat]` 350 `Rd=round(Rss):sat` 350

### S

```
sat
```

`Rd=sat(Rss)` 537

```
satb
```

`Rd=satb(Rs)` 537

```
sath
```

`Rd=sath(Rs)` 537

```
satub
```

`Rd=satub(Rs)` 537

```
satuh
```

`Rd=satuh(Rs)` 537

```
setbit
```

`memb(Rs+#u6:0)=setbit(#U5)` 265 `memh(Rs+#u6:1)=setbit(#U5)` 267 `memw(Rs+#u6:2)=setbit(#U5)` 268 `Rd=setbit(Rs,#u5)` 417 `Rd=setbit(Rs,Rt)` 417

```
sfadd
```

`Rd=sfadd(Rs,Rt)` 456

```
sfclass
```

`Pd=sfclass(Rs,#u5)` 457

```
sfcmp.eq
```

`Pd=sfcmp.eq(Rs,Rt)` 459

```
sfcmp.ge
```

`Pd=sfcmp.ge(Rs,Rt)` 459

```
sfcmp.gt
```

`Pd=sfcmp.gt(Rs,Rt)` 459

```
sfcmp.uo
```

`Pd=sfcmp.uo(Rs,Rt)` 459

```
sffixupd
```

`Rd=sffixupd(Rs,Rt)` 467

```
sffixupn
```

`Rd=sffixupn(Rs,Rt)` 467

```
sffixupr
```

`Rd=sffixupr(Rs)` 467

```
sfinvsqrta
```

`Rd,Pe=sfinvsqrta(Rs)` 470

```
sfmake
```

`Rd=sfmake(#u10):neg` 473 `Rd=sfmake(#u10):pos` 473

```
sfmax
```

`Rd=sfmax(Rs,Rt)` 474

```
sfmin
```

`Rd=sfmin(Rs,Rt)` 475

```
sfmpy
```

`Rd=sfmpy(Rs,Rt)` 476 `Rx+=sfmpy(Rs,Rt,Pu):scale` 469 `Rx+=sfmpy(Rs,Rt)` 468 `Rx+=sfmpy(Rs,Rt):lib` 471 `Rx-=sfmpy(Rs,Rt)` 468 `Rx-=sfmpy(Rs,Rt):lib` 471

```
sfrecipa
```

`Rd,Pe=sfrecipa(Rs,Rt)` 477

```
sfsub
```

`Rd=sfsub(Rs,Rt)` 478

```
shuffeb
```

`Rdd=shuffeb(Rss,Rtt)` 550

```
shuffeh
```

`Rdd=shuffeh(Rss,Rtt)` 550

```
shuffob
```

`Rdd=shuffob(Rtt,Rss)` 550

```
shuffoh
```

`Rdd=shuffoh(Rtt,Rss)` 550

```
sp1loop0
```

`p3=sp1loop0(#r7:2,#U10)` 198 `p3=sp1loop0(#r7:2,Rs)` 198

```
sp2loop0
```

`p3=sp2loop0(#r7:2,#U10)` 198 `p3=sp2loop0(#r7:2,Rs)` 198

```
sp3loop0
```

`p3=sp3loop0(#r7:2,#U10)` 198 `p3=sp3loop0(#r7:2,Rs)` 198

```
sub
```

`if ([!]Pu[.new]) Rd=sub(Rt,Rs)` 182 `Rd=add(Rs,sub(#s6,Ru))` 331 `Rd=sub(#s10,Rs)` 159 `Rd=sub(Rt,Rs)` 159 `Rd=sub(Rt,Rs):sat` 159 `Rd=sub(Rt,Rs):sat:deprecated` 353 `Rd=sub(Rt.[HL],Rs.[HL])[:sat]:<<16` 355 `Rd=sub(Rt.L,Rs.[HL])[:sat]` 355 `Rdd=sub(Rss,Rtt,Px):carry` 337 `Rdd=sub(Rtt,Rss)` 353 `Rx+=sub(Rt,Rs)` 354

```
swiz
```

`Rd=swiz(Rs)` 539

```
sxtb
```

`if ([!]Pu[.new]) Rd=sxtb(Rs)` 183 `Rd=sxtb(Rs)` 161

```
sxth
```

`if ([!]Pu[.new]) Rd=sxth(Rs)` 183 `Rd=sxth(Rs)` 161

```
sxtw
```

`Rdd=sxtw(Rs)` 357

```
syncht
```

`syncht` 325

### T

```
tableidxb
```

`Rx=tableidxb(Rs,#u4,#S6):raw` 421 `Rx=tableidxb(Rs,#u4,#U5)` 421

```
tableidxd
```

`Rx=tableidxd(Rs,#u4,#S6):raw` 421 `Rx=tableidxd(Rs,#u4,#U5)` 422

```
tableidxh
```

`Rx=tableidxh(Rs,#u4,#S6):raw` 422 `Rx=tableidxh(Rs,#u4,#U5)` 422

```
tableidxw
```

`Rx=tableidxw(Rs,#u4,#S6):raw` 422 `Rx=tableidxw(Rs,#u4,#U5)` 422

```
tlbmatch
```

`Pd=tlbmatch(Rss,Rt)` 571

```
togglebit
```

`Rd=togglebit(Rs,#u5)` 417 `Rd=togglebit(Rs,Rt)` 417

```
trace
```

`trace(Rs)` 326

```
trap0
```

`trap0(#u8)` 327

```
trap1
```

`trap1(#u8)` 327 `trap1(Rx,#u8)` 327

```
tstbit
```

`if ([!]tstbit(Ns.new,#0)) jump:<hint> #r9:2` 270 `p[01]=tstbit(Rs,#0)` 211 `Pd=[!]tstbit(Rs,#u5)` 573 `Pd=[!]tstbit(Rs,Rt)` 573

### U

```
unpause
```

`unpause` 328

### V

```
vabsdiffb
```

`Rdd=vabsdiffb(Rtt,Rss)` 360

```
vabsdiffh
```

`Rdd=vabsdiffh(Rtt,Rss)` 361

```
vabsdiffub
```

`Rdd=vabsdiffub(Rtt,Rss)` 360

```
vabsdiffw
```

`Rdd=vabsdiffw(Rtt,Rss)` 362

```
vabsh
```

`Rdd=vabsh(Rss)` 358 `Rdd=vabsh(Rss):sat` 358

```
vabsw
```

`Rdd=vabsw(Rss)` 359 `Rdd=vabsw(Rss):sat` 359

```
vacsh
```

`Rxx,Pe=vacsh(Rss,Rtt)` 364

```
vaddb
```

`Rdd=vaddb(Rss,Rtt)` 373

```
vaddh
```

`Rd=vaddh(Rs,Rt)[:sat]` 165 `Rdd=vaddh(Rss,Rtt)[:sat]` 366

```
vaddhub
```

`Rd=vaddhub(Rss,Rtt):sat` 368

```
vaddub
```

`Rdd=vaddub(Rss,Rtt)[:sat]` 373

```
vadduh
```

`Rd=vadduh(Rs,Rt):sat` 165 `Rdd=vadduh(Rss,Rtt):sat` 366

```
vaddw
```

`Rdd=vaddw(Rss,Rtt)[:sat]` 374

```
valignb
```

`Rdd=valignb(Rtt,Rss,#u3)` 540 `Rdd=valignb(Rtt,Rss,Pu)` 540

```
vaslh
```

`Rdd=vaslh(Rss,#u4)` 606 `Rdd=vaslh(Rss,Rt)` 610

```
vaslw
```

`Rdd=vaslw(Rss,#u5)` 612 `Rdd=vaslw(Rss,Rt)` 613

```
vasrh
```

`Rdd=vasrh(Rss,#u4)` 606 `Rdd=vasrh(Rss,#u4):raw` 607 `Rdd=vasrh(Rss,#u4):rnd` 607 `Rdd=vasrh(Rss,Rt)` 610

```
vasrhub
```

`Rd=vasrhub(Rss,#u4):raw` 608 `Rd=vasrhub(Rss,#u4):rnd:sat` 608 `Rd=vasrhub(Rss,#u4):sat` 608

```
vasrw
```

`Rd=vasrw(Rss,#u5)` 615 `Rd=vasrw(Rss,Rt)` 615 `Rdd=vasrw(Rss,#u5)` 612 `Rdd=vasrw(Rss,Rt)` 613

```
vavgh
```

`Rd=vavgh(Rs,Rt)` 166 `Rd=vavgh(Rs,Rt):rnd` 166 `Rdd=vavgh(Rss,Rtt)` 375 `Rdd=vavgh(Rss,Rtt):crnd` 375 `Rdd=vavgh(Rss,Rtt):rnd` 375

```
vavgub
```

`Rdd=vavgub(Rss,Rtt)` 377 `Rdd=vavgub(Rss,Rtt):rnd` 377

```
vavguh
```

`Rdd=vavguh(Rss,Rtt)` 375 `Rdd=vavguh(Rss,Rtt):rnd` 375

```
vavguw
```

`Rdd=vavguw(Rss,Rtt)[:rnd]` 378

```
vavgw
```

`Rdd=vavgw(Rss,Rtt):crnd` 378 `Rdd=vavgw(Rss,Rtt)[:rnd]` 378

```
vclip
```

`Rdd=vclip(Rss,#u5)` 380

```
vcmpb.eq
```

`Pd=!any8(vcmpb.eq(Rss,Rtt))` 576 `Pd=any8(vcmpb.eq(Rss,Rtt))` 576 `Pd=vcmpb.eq(Rss,#u8)` 577 `Pd=vcmpb.eq(Rss,Rtt)` 577

```
vcmpb.gt
```

`Pd=vcmpb.gt(Rss,#s8)` 577 `Pd=vcmpb.gt(Rss,Rtt)` 577

```
vcmpb.gtu
```

`Pd=vcmpb.gtu(Rss,#u7)` 577 `Pd=vcmpb.gtu(Rss,Rtt)` 577

```
vcmph.eq
```

`Pd=vcmph.eq(Rss,#s8)` 574 `Pd=vcmph.eq(Rss,Rtt)` 574

```
vcmph.gt
```

`Pd=vcmph.gt(Rss,#s8)` 574 `Pd=vcmph.gt(Rss,Rtt)` 574

```
vcmph.gtu
```

`Pd=vcmph.gtu(Rss,#u7)` 574 `Pd=vcmph.gtu(Rss,Rtt)` 574

```
vcmpw.eq
```

`Pd=vcmpw.eq(Rss,#s8)` 579 `Pd=vcmpw.eq(Rss,Rtt)` 579

```
vcmpw.gt
```

`Pd=vcmpw.gt(Rss,#s8)` 579 `Pd=vcmpw.gt(Rss,Rtt)` 579

```
vcmpw.gtu
```

`Pd=vcmpw.gtu(Rss,#u7)` 579 `Pd=vcmpw.gtu(Rss,Rtt)` 579

```
vcmpyi
```

`Rdd=vcmpyi(Rss,Rtt)[:<<1]:sat` 442 `Rxx+=vcmpyi(Rss,Rtt):sat` 443

```
vcmpyr
```

`Rdd=vcmpyr(Rss,Rtt)[:<<1]:sat` 442 `Rxx+=vcmpyr(Rss,Rtt):sat` 443

```
vcnegh
```

`Rdd=vcnegh(Rss,Rt)` 381

```
vconj
```

`Rdd=vconj(Rss):sat` 445

```
vcrotate
```

`Rdd=vcrotate(Rss,Rt)` 446

```
vdmpy
```

`Rd=vdmpy(Rss,Rtt)[:<<1]:rnd:sat` 515 `Rdd=vdmpy(Rss,Rtt):<<1:sat` 512 `Rdd=vdmpy(Rss,Rtt):sat` 512 `Rxx+=vdmpy(Rss,Rtt):<<1:sat` 513 `Rxx+=vdmpy(Rss,Rtt):sat` 513

```
vdmpybsu
```

`Rdd=vdmpybsu(Rss,Rtt):sat` 519 `Rxx+=vdmpybsu(Rss,Rtt):sat` 519

```
vitpack
```

`Rd=vitpack(Ps,Pt)` 581

```
vlslh
```

`Rdd=vlslh(Rss,Rt)` 610

```
vlslw
```

`Rdd=vlslw(Rss,Rt)` 613

```
vlsrh
```

`Rdd=vlsrh(Rss,#u4)` 606 `Rdd=vlsrh(Rss,Rt)` 610

```
vlsrw
```

`Rdd=vlsrw(Rss,#u5)` 612 `Rdd=vlsrw(Rss,Rt)` 613

```
vmaxb
```

`Rdd=vmaxb(Rtt,Rss)` 383

```
vmaxh
```

`Rdd=vmaxh(Rtt,Rss)` 384

```
vmaxub
```

`Rdd=vmaxub(Rtt,Rss)` 383

```
vmaxuh
```

`Rdd=vmaxuh(Rtt,Rss)` 384

```
vmaxuw
```

`Rdd=vmaxuw(Rtt,Rss)` 389

```
vmaxw
```

`Rdd=vmaxw(Rtt,Rss)` 389

```
vminb
```

`Rdd=vminb(Rtt,Rss)` 390

```
vminh
```

`Rdd=vminh(Rtt,Rss)` 392

```
vminub
```

`Rdd,Pe=vminub(Rtt,Rss)` 390 `Rdd=vminub(Rtt,Rss)` 390

```
vminuh
```

`Rdd=vminuh(Rtt,Rss)` 392

```
vminuw
```

`Rdd=vminuw(Rtt,Rss)` 397

```
vminw
```

`Rdd=vminw(Rtt,Rss)` 397

```
vmpybsu
```

`Rdd=vmpybsu(Rs,Rt)` 531 `Rxx+=vmpybsu(Rs,Rt)` 531

```
vmpybu
```

`Rdd=vmpybu(Rs,Rt)` 531 `Rxx+=vmpybu(Rs,Rt)` 531

```
vmpyeh
```

`Rdd=vmpyeh(Rss,Rtt):<<1:sat` 521 `Rdd=vmpyeh(Rss,Rtt):sat` 521 `Rxx+=vmpyeh(Rss,Rtt)` 521 `Rxx+=vmpyeh(Rss,Rtt):<<1:sat` 521 `Rxx+=vmpyeh(Rss,Rtt):sat` 521

```
vmpyh
```

`Rd=vmpyh(Rs,Rt)[:<<1]:rnd:sat` 525 `Rdd=vmpyh(Rs,Rt)[:<<1]:sat` 523 `Rxx+=vmpyh(Rs,Rt)` 523 `Rxx+=vmpyh(Rs,Rt)[:<<1]:sat` 523

```
vmpyhsu
```

`Rdd=vmpyhsu(Rs,Rt)[:<<1]:sat` 527 `Rxx+=vmpyhsu(Rs,Rt)[:<<1]:sat` 527

```
vmpyweh
```

`Rdd=vmpyweh(Rss,Rtt)[:<<1]:rnd:sat` 483 `Rdd=vmpyweh(Rss,Rtt)[:<<1]:sat` 484 `Rxx+=vmpyweh(Rss,Rtt)[:<<1]:rnd:sat` 484 `Rxx+=vmpyweh(Rss,Rtt)[:<<1]:sat` 484

```
vmpyweuh
```

`Rdd=vmpyweuh(Rss,Rtt)[:<<1]:rnd:sat` 487 `Rdd=vmpyweuh(Rss,Rtt)[:<<1]:sat` 488 `Rxx+=vmpyweuh(Rss,Rtt)[:<<1]:rnd:sat` 488 `Rxx+=vmpyweuh(Rss,Rtt)[:<<1]:sat` 488

```
vmpywoh
```

`Rdd=vmpywoh(Rss,Rtt)[:<<1]:rnd:sat` 484 `Rdd=vmpywoh(Rss,Rtt)[:<<1]:sat` 484 `Rxx+=vmpywoh(Rss,Rtt)[:<<1]:rnd:sat` 484 `Rxx+=vmpywoh(Rss,Rtt)[:<<1]:sat` 484

```
vmpywouh
```

`Rdd=vmpywouh(Rss,Rtt)[:<<1]:rnd:sat` 488 `Rdd=vmpywouh(Rss,Rtt)[:<<1]:sat` 488 `Rxx+=vmpywouh(Rss,Rtt)[:<<1]:rnd:sat` 488 `Rxx+=vmpywouh(Rss,Rtt)[:<<1]:sat` 488

```
vmux
```

`Rdd=vmux(Pu,Rss,Rtt)` 582

```
vnavgh
```

`Rd=vnavgh(Rt,Rs)` 166 `Rdd=vnavgh(Rtt,Rss)` 375 `Rdd=vnavgh(Rtt,Rss):crnd:sat` 375 `Rdd=vnavgh(Rtt,Rss):rnd:sat` 375

```
vnavgw
```

`Rdd=vnavgw(Rtt,Rss)` 378 `Rdd=vnavgw(Rtt,Rss):crnd:sat` 378 `Rdd=vnavgw(Rtt,Rss):rnd:sat` 378

```
vpmpyh
```

`Rdd=vpmpyh(Rs,Rt)` 533 `Rxx^=vpmpyh(Rs,Rt)` 534

```
vraddh
```

`Rd=vraddh(Rss,Rtt)` 371

```
vraddub
```

`Rdd=vraddub(Rss,Rtt)` 369 `Rxx+=vraddub(Rss,Rtt)` 369

```
vradduh
```

`Rd=vradduh(Rss,Rtt)` 371

```
vrcmpys
```

`Rd=vrcmpys(Rss,Rt):<<1:rnd:sat` 451 `Rd=vrcmpys(Rss,Rtt):<<1:rnd:sat:raw:hi` 451 `Rd=vrcmpys(Rss,Rtt):<<1:rnd:sat:raw:lo` 452 `Rdd=vrcmpys(Rss,Rt):<<1:sat` 448 `Rdd=vrcmpys(Rss,Rtt):<<1:sat:raw:hi` 448 `Rdd=vrcmpys(Rss,Rtt):<<1:sat:raw:lo` 449 `Rxx+=vrcmpys(Rss,Rt):<<1:sat` 449 `Rxx+=vrcmpys(Rss,Rtt):<<1:sat:raw:hi` 449 `Rxx+=vrcmpys(Rss,Rtt):<<1:sat:raw:lo` 449

```
vrcnegh
```

`Rxx+=vrcnegh(Rss,Rt)` 381

```
vrcrotate
```

`Rdd=vrcrotate(Rss,Rt,#u2)` 454 `Rxx+=vrcrotate(Rss,Rt,#u2)` 454

```
vrmaxh
```

`Rxx=vrmaxh(Rss,Ru)` 385

```
vrmaxuh
```

`Rxx=vrmaxuh(Rss,Ru)` 385

```
vrmaxuw
```

`Rxx=vrmaxuw(Rss,Ru)` 387

```
vrmaxw
```

`Rxx=vrmaxw(Rss,Ru)` 387

```
vrminh
```

`Rxx=vrminh(Rss,Ru)` 393

```
vrminuh
```

`Rxx=vrminuh(Rss,Ru)` 393

```
vrminuw
```

`Rxx=vrminuw(Rss,Ru)` 395

```
vrminw
```

`Rxx=vrminw(Rss,Ru)` 395

```
vrmpybsu
```

`Rdd=vrmpybsu(Rss,Rtt)` 517 `Rxx+=vrmpybsu(Rss,Rtt)` 517

```
vrmpybu
```

`Rdd=vrmpybu(Rss,Rtt)` 517 `Rxx+=vrmpybu(Rss,Rtt)` 517

```
vrmpyh
```

`Rdd=vrmpyh(Rss,Rtt)` 529 `Rxx+=vrmpyh(Rss,Rtt)` 529

```
vrmpyweh
```

`Rdd=vrmpyweh(Rss,Rtt)[:<<1]` 505 `Rxx+=vrmpyweh(Rss,Rtt)[:<<1]` 505

```
vrmpywoh
```

`Rdd=vrmpywoh(Rss,Rtt)[:<<1]` 505 `Rxx+=vrmpywoh(Rss,Rtt)[:<<1]` 505

```
vrndwh
```

`Rd=vrndwh(Rss)` 542 `Rd=vrndwh(Rss):sat` 542

```
vrsadub
```

`Rdd=vrsadub(Rss,Rtt)` 398 `Rxx+=vrsadub(Rss,Rtt)` 398

```
vsathb
```

`Rd=vsathb(Rs)` 545 `Rd=vsathb(Rss)` 545 `Rdd=vsathb(Rss)` 548

```
vsathub
```

`Rd=vsathub(Rs)` 545 `Rd=vsathub(Rss)` 545 `Rdd=vsathub(Rss)` 548

```
vsatwh
```

`Rd=vsatwh(Rss)` 545 `Rdd=vsatwh(Rss)` 548

```
vsatwuh
```

`Rd=vsatwuh(Rss)` 545 `Rdd=vsatwuh(Rss)` 548

```
vsplatb
```

`Rd=vsplatb(Rs)` 552 `Rdd=vsplatb(Rs)` 552

```
vsplath
```

`Rdd=vsplath(Rs)` 553

```
vspliceb
```

`Rdd=vspliceb(Rss,Rtt,#u3)` 554 `Rdd=vspliceb(Rss,Rtt,Pu)` 554

```
vsubb
```

`Rdd=vsubb(Rss,Rtt)` 402

```
vsubh
```

`Rd=vsubh(Rt,Rs)[:sat]` 167 `Rdd=vsubh(Rtt,Rss)[:sat]` 400

```
vsubub
```

`Rdd=vsubub(Rtt,Rss)[:sat]` 402

```
vsubuh
```

`Rd=vsubuh(Rt,Rs):sat` 167 `Rdd=vsubuh(Rtt,Rss):sat` 400

```
vsubw
```

`Rdd=vsubw(Rtt,Rss)[:sat]` 403

```
vsxtbh
```

`Rdd=vsxtbh(Rs)` 556

```
vsxthw
```

`Rdd=vsxthw(Rs)` 556

```
vtrunehb
```

`Rd=vtrunehb(Rss)` 558 `Rdd=vtrunehb(Rss,Rtt)` 558

```
vtrunewh
```

`Rdd=vtrunewh(Rss,Rtt)` 558

```
vtrunohb
```

`Rd=vtrunohb(Rss)` 558 `Rdd=vtrunohb(Rss,Rtt)` 558

```
vtrunowh
```

`Rdd=vtrunowh(Rss,Rtt)` 559

```
vxaddsubh
```

`Rdd=vxaddsubh(Rss,Rtt):rnd:>>1:sat` 424 `Rdd=vxaddsubh(Rss,Rtt):sat` 424

```
vxaddsubw
```

`Rdd=vxaddsubw(Rss,Rtt):sat` 426

```
vxsubaddh
```

`Rdd=vxsubaddh(Rss,Rtt):rnd:>>1:sat` 424 `Rdd=vxsubaddh(Rss,Rtt):sat` 424

```
vxsubaddw
```

`Rdd=vxsubaddw(Rss,Rtt):sat` 426

```
vzxtbh
```

`Rdd=vzxtbh(Rs)` 560

```
vzxthw
```

`Rdd=vzxthw(Rs)` 560

### X

```
xor
```

`if ([!]Pu[.new]) Rd=xor(Rs,Rt)` 180 `Pd=xor(Ps,Pt)` 200 `Rd=xor(Rs,Rt)` 155 `Rdd=xor(Rss,Rtt)` 339 `Rx[&|^]=xor(Rs,Rt)` 341 `Rxx^=xor(Rss,Rtt)` 340

### Z

```
zxtb
```

`if ([!]Pu[.new]) Rd=zxtb(Rs)` 186 `Rd=zxtb(Rs)` 168

```
zxth
```

`if ([!]Pu[.new]) Rd=zxth(Rs)` 186 `Rd=zxth(Rs)` 168
