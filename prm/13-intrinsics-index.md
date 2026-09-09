[← Contents](README.md)

# Intrinsics Index

### A

```
abs
   Rd=abs(Rs)
```

`Word32 Q6_R_abs_R(Word32 Rs)` 330

```
Rd=abs(Rs):sat
```

`Word32 Q6_R_abs_R_sat(Word32 Rs)` 330

```
Rdd=abs(Rss)
```

`Word64 Q6_P_abs_P(Word64 Rss)` 329

```
add
   Rd=add(#u6,mpyi(Rs,#U6))
```

`Word32 Q6_R_add_mpyi_IRI(Word32 Iu6, Word32 Rs, Word32 IU6)` 481

```
Rd=add(#u6,mpyi(Rs,Rt))
```

`Word32 Q6_R_add_mpyi_IRR(Word32 Iu6, Word32 Rs, Word32 Rt)` 481

```
Rd=add(Rs,#s16)
```

`Word32 Q6_R_add_RI(Word32 Rs, Word32 Is16)` 153

```
Rd=add(Rs,add(Ru,#s6))
```

`Word32 Q6_R_add_add_RRI(Word32 Rs, Word32 Ru, Word32 Is6)` 331

```
Rd=add(Rs,Rt)
```

`Word32 Q6_R_add_RR(Word32 Rs, Word32 Rt)` 153

```
Rd=add(Rs,Rt):sat
```

`Word32 Q6_R_add_RR_sat(Word32 Rs, Word32 Rt)` 153

```
Rd=add(Rt.H,Rs.H):<<16
```

`Word32 Q6_R_add_RhRh_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.H,Rs.H):sat:<<16
```

`Word32 Q6_R_add_RhRh_sat_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.H,Rs.L):<<16
```

`Word32 Q6_R_add_RhRl_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.H,Rs.L):sat:<<16
```

`Word32 Q6_R_add_RhRl_sat_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.H)
```

`Word32 Q6_R_add_RlRh(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.H):<<16
```

`Word32 Q6_R_add_RlRh_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.H):sat
```

`Word32 Q6_R_add_RlRh_sat(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.H):sat:<<16
```

`Word32 Q6_R_add_RlRh_sat_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.L)
```

`Word32 Q6_R_add_RlRl(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.L):<<16
```

`Word32 Q6_R_add_RlRl_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.L):sat
```

`Word32 Q6_R_add_RlRl_sat(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Rt.L,Rs.L):sat:<<16
```

`Word32 Q6_R_add_RlRl_sat_s16(Word32 Rt, Word32 Rs)` 336

```
Rd=add(Ru,mpyi(#u6:2,Rs))
```

`Word32 Q6_R_add_mpyi_RIR(Word32 Ru, Word32 Iu6_2, Word32 Rs)` 481

```
Rd=add(Ru,mpyi(Rs,#u6))
```

`Word32 Q6_R_add_mpyi_RRI(Word32 Ru, Word32 Rs, Word32 Iu6)` 481

```
Rdd=add(Rs,Rtt)
```

`Word64 Q6_P_add_RP(Word32 Rs, Word64 Rtt)` 334

```
Rdd=add(Rss,Rtt)
```

`Word64 Q6_P_add_PP(Word64 Rss, Word64 Rtt)` 334

```
Rdd=add(Rss,Rtt):sat
```

`Word64 Q6_P_add_PP_sat(Word64 Rss, Word64 Rtt)` 334

```
Rx+=add(Rs,#s8)
```

`Word32 Q6_R_addacc_RI(Word32 Rx, Word32 Rs, Word32 Is8)` 331

```
Rx+=add(Rs,Rt)
```

`Word32 Q6_R_addacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 331

```
Rx-=add(Rs,#s8)
```

`Word32 Q6_R_addnac_RI(Word32 Rx, Word32 Rs, Word32 Is8)` 331

```
Rx-=add(Rs,Rt)
```

`Word32 Q6_R_addnac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 331

```
Ry=add(Ru,mpyi(Ry,Rs))
```

`Word32 Q6_R_add_mpyi_RRR(Word32 Ru, Word32 Ry, Word32 Rs)` 481

```
addasl
   Rd=addasl(Rt,Rs,#u3)
```

`Word32 Q6_R_addasl_RRI(Word32 Rt, Word32 Rs, Word32 Iu3)` 589

```
all8
   Pd=all8(Ps)
```

`Byte Q6_p_all8_p(Byte Ps)` 194

```
and
   Pd=and(Ps,and(Pt,!Pu))
```

`Byte Q6_p_and_and_ppnp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=and(Ps,and(Pt,Pu))
```

`Byte Q6_p_and_and_ppp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=and(Pt,!Ps)
```

`Byte Q6_p_and_pnp(Byte Pt, Byte Ps)` 200

```
Pd=and(Pt,Ps)
```

`Byte Q6_p_and_pp(Byte Pt, Byte Ps)` 200

```
Rd=and(Rs,#s10)
```

`Word32 Q6_R_and_RI(Word32 Rs, Word32 Is10)` 155

```
Rd=and(Rs,Rt)
```

`Word32 Q6_R_and_RR(Word32 Rs, Word32 Rt)` 155

```
Rd=and(Rt,~Rs)
```

`Word32 Q6_R_and_RnR(Word32 Rt, Word32 Rs)` 155

```
Rdd=and(Rss,Rtt)
```

`Word64 Q6_P_and_PP(Word64 Rss, Word64 Rtt)` 339

```
Rdd=and(Rtt,~Rss)
```

`Word64 Q6_P_and_PnP(Word64 Rtt, Word64 Rss)` 339

```
Rx&=and(Rs,~Rt)
```

`Word32 Q6_R_andand_RnR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx&=and(Rs,Rt)
```

`Word32 Q6_R_andand_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx^=and(Rs,~Rt)
```

`Word32 Q6_R_andxacc_RnR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx^=and(Rs,Rt)
```

`Word32 Q6_R_andxacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx|=and(Rs,#s10)
```

`Word32 Q6_R_andor_RI(Word32 Rx, Word32 Rs, Word32 Is10)` 342

```
Rx|=and(Rs,~Rt)
```

`Word32 Q6_R_andor_RnR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx|=and(Rs,Rt)
```

`Word32 Q6_R_andor_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
any8
   Pd=any8(Ps)
```

`Byte Q6_p_any8_p(Byte Ps)` 194

```
asl
   Rd=asl(Rs,#u5)
```

`Word32 Q6_R_asl_RI(Word32 Rs, Word32 Iu5)` 584

```
Rd=asl(Rs,#u5):sat
```

`Word32 Q6_R_asl_RI_sat(Word32 Rs, Word32 Iu5)` 595

```
Rd=asl(Rs,Rt)
```

`Word32 Q6_R_asl_RR(Word32 Rs, Word32 Rt)` 597

```
Rd=asl(Rs,Rt):sat
```

`Word32 Q6_R_asl_RR_sat(Word32 Rs, Word32 Rt)` 605

```
Rdd=asl(Rss,#u6)
```

`Word64 Q6_P_asl_PI(Word64 Rss, Word32 Iu6)` 585

```
Rdd=asl(Rss,Rt)
```

`Word64 Q6_P_asl_PR(Word64 Rss, Word32 Rt)` 597

```
Rx&=asl(Rs,#u5)
```

`Word32 Q6_R_asland_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx&=asl(Rs,Rt)
```

`Word32 Q6_R_asland_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rx^=asl(Rs,#u5)
```

`Word32 Q6_R_aslxacc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx+=asl(Rs,#u5)
```

`Word32 Q6_R_aslacc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx+=asl(Rs,Rt)
```

`Word32 Q6_R_aslacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx=add(#u8,asl(Rx,#U5))
```

`Word32 Q6_R_add_asl_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 587

```
Rx=and(#u8,asl(Rx,#U5))
```

`Word32 Q6_R_and_asl_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 591

```
Rx-=asl(Rs,#u5)
```

`Word32 Q6_R_aslnac_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx-=asl(Rs,Rt)
```

`Word32 Q6_R_aslnac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx=or(#u8,asl(Rx,#U5))
```

`Word32 Q6_R_or_asl_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 591

```
Rx=sub(#u8,asl(Rx,#U5))
```

`Word32 Q6_R_sub_asl_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 587

```
Rx|=asl(Rs,#u5)
```

`Word32 Q6_R_aslor_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx|=asl(Rs,Rt)
```

`Word32 Q6_R_aslor_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rxx&=asl(Rss,#u6)
```

`Word64 Q6_P_asland_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx&=asl(Rss,Rt)
```

`Word64 Q6_P_asland_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx^=asl(Rss,#u6)
```

`Word64 Q6_P_aslxacc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx^=asl(Rss,Rt)
```

`Word64 Q6_P_aslxacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx+=asl(Rss,#u6)
```

`Word64 Q6_P_aslacc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx+=asl(Rss,Rt)
```

`Word64 Q6_P_aslacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx-=asl(Rss,#u6)
```

`Word64 Q6_P_aslnac_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx-=asl(Rss,Rt)
```

`Word64 Q6_P_aslnac_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx|=asl(Rss,#u6)
```

`Word64 Q6_P_aslor_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 592

```
Rxx|=asl(Rss,Rt)
```

`Word64 Q6_P_aslor_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 604

```
aslh
   Rd=aslh(Rs)
```

`Word32 Q6_R_aslh_R(Word32 Rs)` 173

```
asr
   Rd=asr(Rs,#u5)
```

`Word32 Q6_R_asr_RI(Word32 Rs, Word32 Iu5)` 584

```
Rd=asr(Rs,#u5):rnd
```

`Word32 Q6_R_asr_RI_rnd(Word32 Rs, Word32 Iu5)` 594

```
Rd=asr(Rs,Rt)
```

`Word32 Q6_R_asr_RR(Word32 Rs, Word32 Rt)` 597

```
Rd=asr(Rs,Rt):sat
```

`Word32 Q6_R_asr_RR_sat(Word32 Rs, Word32 Rt)` 605

```
Rdd=asr(Rss,#u6)
```

`Word64 Q6_P_asr_PI(Word64 Rss, Word32 Iu6)` 585

```
Rdd=asr(Rss,#u6):rnd
```

`Word64 Q6_P_asr_PI_rnd(Word64 Rss, Word32 Iu6)` 594

```
Rdd=asr(Rss,Rt)
```

`Word64 Q6_P_asr_PR(Word64 Rss, Word32 Rt)` 597

```
Rx&=asr(Rs,#u5)
```

`Word32 Q6_R_asrand_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx&=asr(Rs,Rt)
```

`Word32 Q6_R_asrand_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rx+=asr(Rs,#u5)
```

`Word32 Q6_R_asracc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx+=asr(Rs,Rt)
```

`Word32 Q6_R_asracc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx-=asr(Rs,#u5)
```

`Word32 Q6_R_asrnac_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx-=asr(Rs,Rt)
```

`Word32 Q6_R_asrnac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx|=asr(Rs,#u5)
```

`Word32 Q6_R_asror_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx|=asr(Rs,Rt)
```

`Word32 Q6_R_asror_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rxx&=asr(Rss,#u6)
```

`Word64 Q6_P_asrand_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx&=asr(Rss,Rt)
```

`Word64 Q6_P_asrand_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx^=asr(Rss,Rt)
```

`Word64 Q6_P_asrxacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx+=asr(Rss,#u6)
```

`Word64 Q6_P_asracc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx+=asr(Rss,Rt)
```

`Word64 Q6_P_asracc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx-=asr(Rss,#u6)
```

`Word64 Q6_P_asrnac_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx-=asr(Rss,Rt)
```

`Word64 Q6_P_asrnac_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx|=asr(Rss,#u6)
```

`Word64 Q6_P_asror_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 592

```
Rxx|=asr(Rss,Rt)
```

`Word64 Q6_P_asror_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 604

```
asrh
   Rd=asrh(Rs)
```

`Word32 Q6_R_asrh_R(Word32 Rs)` 173

```
asrrnd
   Rd=asrrnd(Rs,#u5)
```

`Word32 Q6_R_asrrnd_RI(Word32 Rs, Word32 Iu5)` 594

```
Rdd=asrrnd(Rss,#u6)
```

`Word64 Q6_P_asrrnd_PI(Word64 Rss, Word32 Iu6)` 594

### B

```
bitsclr
   Pd=!bitsclr(Rs,#u6)
```

`Byte Q6_p_not_bitsclr_RI(Word32 Rs, Word32 Iu6)` 569

```
Pd=!bitsclr(Rs,Rt)
```

`Byte Q6_p_not_bitsclr_RR(Word32 Rs, Word32 Rt)` 569

```
Pd=bitsclr(Rs,#u6)
```

`Byte Q6_p_bitsclr_RI(Word32 Rs, Word32 Iu6)` 569

```
Pd=bitsclr(Rs,Rt)
```

`Byte Q6_p_bitsclr_RR(Word32 Rs, Word32 Rt)` 569

```
bitsplit
   Rdd=bitsplit(Rs,#u5)
```

`Word64 Q6_P_bitsplit_RI(Word32 Rs, Word32 Iu5)` 419

```
Rdd=bitsplit(Rs,Rt)
```

`Word64 Q6_P_bitsplit_RR(Word32 Rs, Word32 Rt)` 419

```
bitsset
   Pd=!bitsset(Rs,Rt)
```

`Byte Q6_p_not_bitsset_RR(Word32 Rs, Word32 Rt)` 569

```
Pd=bitsset(Rs,Rt)
```

`Byte Q6_p_bitsset_RR(Word32 Rs, Word32 Rt)` 569

```
boundscheck
   Pd=boundscheck(Rs,Rtt)
```

`Byte Q6_p_boundscheck_RP(Word32 Rs, Word64 Rtt)` 562

```
brev
   Rd=brev(Rs)
```

`Word32 Q6_R_brev_R(Word32 Rs)` 416

```
Rdd=brev(Rss)
```

`Word64 Q6_P_brev_P(Word64 Rss)` 416

### C

```
cl0
   Rd=cl0(Rs)
```

`Word32 Q6_R_cl0_R(Word32 Rs)` 405

```
Rd=cl0(Rss)
```

`Word32 Q6_R_cl0_P(Word64 Rss)` 405

```
cl1
   Rd=cl1(Rs)
```

`Word32 Q6_R_cl1_R(Word32 Rs)` 405

```
Rd=cl1(Rss)
```

`Word32 Q6_R_cl1_P(Word64 Rss)` 405

```
clb
   Rd=add(clb(Rs),#s6)
```

`Word32 Q6_R_add_clb_RI(Word32 Rs, Word32 Is6)` 405

```
Rd=add(clb(Rss),#s6)
```

`Word32 Q6_R_add_clb_PI(Word64 Rss, Word32 Is6)` 405

```
Rd=clb(Rs)
```

`Word32 Q6_R_clb_R(Word32 Rs)` 405

```
Rd=clb(Rss)
```

`Word32 Q6_R_clb_P(Word64 Rss)` 405

```
clip
   Rd=clip(Rs,#u5)
```

`Word32 Q6_R_clip_RI(Word32 Rs, Word32 Iu5)` 338

```
clrbit
   Rd=clrbit(Rs,#u5)
```

`Word32 Q6_R_clrbit_RI(Word32 Rs, Word32 Iu5)` 417

```
Rd=clrbit(Rs,Rt)
```

`Word32 Q6_R_clrbit_RR(Word32 Rs, Word32 Rt)` 417

```
cmp.eq
   Pd=!cmp.eq(Rs,#s10)
```

`Byte Q6_p_not_cmp_eq_RI(Word32 Rs, Word32 Is10)` 188

```
Pd=!cmp.eq(Rs,Rt)
```

`Byte Q6_p_not_cmp_eq_RR(Word32 Rs, Word32 Rt)` 188

```
Pd=cmp.eq(Rs,#s10)
```

`Byte Q6_p_cmp_eq_RI(Word32 Rs, Word32 Is10)` 188

```
Pd=cmp.eq(Rs,Rt)
```

`Byte Q6_p_cmp_eq_RR(Word32 Rs, Word32 Rt)` 188

```
Pd=cmp.eq(Rss,Rtt)
```

`Byte Q6_p_cmp_eq_PP(Word64 Rss, Word64 Rtt)` 568

```
Rd=!cmp.eq(Rs,#s8)
```

`Word32 Q6_R_not_cmp_eq_RI(Word32 Rs, Word32 Is8)` 190

```
Rd=!cmp.eq(Rs,Rt)
```

`Word32 Q6_R_not_cmp_eq_RR(Word32 Rs, Word32 Rt)` 190

```
Rd=cmp.eq(Rs,#s8)
```

`Word32 Q6_R_cmp_eq_RI(Word32 Rs, Word32 Is8)` 190

```
Rd=cmp.eq(Rs,Rt)
```

`Word32 Q6_R_cmp_eq_RR(Word32 Rs, Word32 Rt)` 190

```
cmp.ge
   Pd=cmp.ge(Rs,#s8)
```

`Byte Q6_p_cmp_ge_RI(Word32 Rs, Word32 Is8)` 188

```
cmp.geu
   Pd=cmp.geu(Rs,#u8)
```

`Byte Q6_p_cmp_geu_RI(Word32 Rs, Word32 Iu8)` 188

```
cmp.gt
   Pd=!cmp.gt(Rs,#s10)
```

`Byte Q6_p_not_cmp_gt_RI(Word32 Rs, Word32 Is10)` 188

```
Pd=!cmp.gt(Rs,Rt)
```

`Byte Q6_p_not_cmp_gt_RR(Word32 Rs, Word32 Rt)` 188

```
Pd=cmp.gt(Rs,#s10)
```

`Byte Q6_p_cmp_gt_RI(Word32 Rs, Word32 Is10)` 189

```
Pd=cmp.gt(Rs,Rt)
```

`Byte Q6_p_cmp_gt_RR(Word32 Rs, Word32 Rt)` 189

```
Pd=cmp.gt(Rss,Rtt)
```

`Byte Q6_p_cmp_gt_PP(Word64 Rss, Word64 Rtt)` 568

```
cmp.gtu
   Pd=!cmp.gtu(Rs,#u9)
```

`Byte Q6_p_not_cmp_gtu_RI(Word32 Rs, Word32 Iu9)` 188

```
Pd=!cmp.gtu(Rs,Rt)
```

`Byte Q6_p_not_cmp_gtu_RR(Word32 Rs, Word32 Rt)` 188

```
Pd=cmp.gtu(Rs,#u9)
```

`Byte Q6_p_cmp_gtu_RI(Word32 Rs, Word32 Iu9)` 189

```
Pd=cmp.gtu(Rs,Rt)
```

`Byte Q6_p_cmp_gtu_RR(Word32 Rs, Word32 Rt)` 189

```
Pd=cmp.gtu(Rss,Rtt)
```

`Byte Q6_p_cmp_gtu_PP(Word64 Rss, Word64 Rtt)` 568

```
cmp.lt
   Pd=cmp.lt(Rs,Rt)
```

`Byte Q6_p_cmp_lt_RR(Word32 Rs, Word32 Rt)` 189

```
cmp.ltu
   Pd=cmp.ltu(Rs,Rt)
```

`Byte Q6_p_cmp_ltu_RR(Word32 Rs, Word32 Rt)` 189

```
cmpb.eq
   Pd=cmpb.eq(Rs,#u8)
```

`Byte Q6_p_cmpb_eq_RI(Word32 Rs, Word32 Iu8)` 564

```
Pd=cmpb.eq(Rs,Rt)
```

`Byte Q6_p_cmpb_eq_RR(Word32 Rs, Word32 Rt)` 564

```
cmpb.gt
   Pd=cmpb.gt(Rs,#s8)
```

`Byte Q6_p_cmpb_gt_RI(Word32 Rs, Word32 Is8)` 564

```
Pd=cmpb.gt(Rs,Rt)
```

`Byte Q6_p_cmpb_gt_RR(Word32 Rs, Word32 Rt)` 564

```
cmpb.gtu
   Pd=cmpb.gtu(Rs,#u7)
```

`Byte Q6_p_cmpb_gtu_RI(Word32 Rs, Word32 Iu7)` 564

```
Pd=cmpb.gtu(Rs,Rt)
```

`Byte Q6_p_cmpb_gtu_RR(Word32 Rs, Word32 Rt)` 564

```
cmph.eq
   Pd=cmph.eq(Rs,#s8)
```

`Byte Q6_p_cmph_eq_RI(Word32 Rs, Word32 Is8)` 566

```
Pd=cmph.eq(Rs,Rt)
```

`Byte Q6_p_cmph_eq_RR(Word32 Rs, Word32 Rt)` 566

```
cmph.gt
   Pd=cmph.gt(Rs,#s8)
```

`Byte Q6_p_cmph_gt_RI(Word32 Rs, Word32 Is8)` 566

```
Pd=cmph.gt(Rs,Rt)
```

`Byte Q6_p_cmph_gt_RR(Word32 Rs, Word32 Rt)` 566

```
cmph.gtu
   Pd=cmph.gtu(Rs,#u7)
```

`Byte Q6_p_cmph_gtu_RI(Word32 Rs, Word32 Iu7)` 566

```
Pd=cmph.gtu(Rs,Rt)
```

`Byte Q6_p_cmph_gtu_RR(Word32 Rs, Word32 Rt)` 566

```
cmpy
   Rd=cmpy(Rs,Rt):<<1:rnd:sat
```

`Word32 Q6_R_cmpy_RR_s1_rnd_sat(Word32 Rs, Word32 Rt)` 435

```
Rd=cmpy(Rs,Rt):rnd:sat
```

`Word32 Q6_R_cmpy_RR_rnd_sat(Word32 Rs, Word32 Rt)` 435

```
Rd=cmpy(Rs,Rt*):<<1:rnd:sat
```

`Word32 Q6_R_cmpy_RR_conj_s1_rnd_sat(Word32 Rs, Word32 Rt)` 435

```
Rd=cmpy(Rs,Rt*):rnd:sat
```

`Word32 Q6_R_cmpy_RR_conj_rnd_sat(Word32 Rs, Word32 Rt)` 435

```
Rdd=cmpy(Rs,Rt):<<1:sat
```

`Word64 Q6_P_cmpy_RR_s1_sat(Word32 Rs, Word32 Rt)` 430

```
Rdd=cmpy(Rs,Rt):sat
```

`Word64 Q6_P_cmpy_RR_sat(Word32 Rs, Word32 Rt)` 430

```
Rdd=cmpy(Rs,Rt*):<<1:sat
```

`Word64 Q6_P_cmpy_RR_conj_s1_sat(Word32 Rs, Word32 Rt)` 430

```
Rdd=cmpy(Rs,Rt*):sat
```

`Word64 Q6_P_cmpy_RR_conj_sat(Word32 Rs, Word32 Rt)` 430

```
Rxx+=cmpy(Rs,Rt):<<1:sat
```

`Word64 Q6_P_cmpyacc_RR_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx+=cmpy(Rs,Rt):sat
```

`Word64 Q6_P_cmpyacc_RR_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx+=cmpy(Rs,Rt*):<<1:sat
```

`Word64 Q6_P_cmpyacc_RR_conj_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx+=cmpy(Rs,Rt*):sat
```

`Word64 Q6_P_cmpyacc_RR_conj_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx-=cmpy(Rs,Rt):<<1:sat
```

`Word64 Q6_P_cmpynac_RR_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx-=cmpy(Rs,Rt):sat
```

`Word64 Q6_P_cmpynac_RR_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx-=cmpy(Rs,Rt*):<<1:sat
```

`Word64 Q6_P_cmpynac_RR_conj_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
Rxx-=cmpy(Rs,Rt*):sat
```

`Word64 Q6_P_cmpynac_RR_conj_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 430

```
cmpyi
   Rdd=cmpyi(Rs,Rt)
```

`Word64 Q6_P_cmpyi_RR(Word32 Rs, Word32 Rt)` 433

```
Rxx+=cmpyi(Rs,Rt)
```

`Word64 Q6_P_cmpyiacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 433

```
cmpyiw
   Rd=cmpyiw(Rss,Rtt):<<1:rnd:sat
```

`Word32 Q6_R_cmpyiw_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyiw(Rss,Rtt):<<1:sat
```

`Word32 Q6_R_cmpyiw_PP_s1_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyiw(Rss,Rtt*):<<1:rnd:sat
```

`Word32 Q6_R_cmpyiw_PP_conj_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyiw(Rss,Rtt*):<<1:sat
```

`Word32 Q6_R_cmpyiw_PP_conj_s1_sat(Word64 Rss, Word64 Rtt)` 440

```
Rdd=cmpyiw(Rss,Rtt)
```

`Word64 Q6_P_cmpyiw_PP(Word64 Rss, Word64 Rtt)` 440

```
Rdd=cmpyiw(Rss,Rtt*)
```

`Word64 Q6_P_cmpyiw_PP_conj(Word64 Rss, Word64 Rtt)` 440

```
Rxx+=cmpyiw(Rss,Rtt)
```

`Word64 Q6_P_cmpyiwacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 440

```
Rxx+=cmpyiw(Rss,Rtt*)
```

`Word64 Q6_P_cmpyiwacc_PP_conj(Word64 Rxx, Word64 Rss, Word64 Rtt)` 440

```
cmpyiwh
   Rd=cmpyiwh(Rss,Rt):<<1:rnd:sat
```

`Word32 Q6_R_cmpyiwh_PR_s1_rnd_sat(Word64 Rss, Word32 Rt)` 437

```
Rd=cmpyiwh(Rss,Rt*):<<1:rnd:sat
```

`Word32 Q6_R_cmpyiwh_PR_conj_s1_rnd_sat(Word64 Rss, Word32 Rt)` 437

```
cmpyr
   Rdd=cmpyr(Rs,Rt)
```

`Word64 Q6_P_cmpyr_RR(Word32 Rs, Word32 Rt)` 433

```
Rxx+=cmpyr(Rs,Rt)
```

`Word64 Q6_P_cmpyracc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 433

```
cmpyrw
   Rd=cmpyrw(Rss,Rtt):<<1:rnd:sat
```

`Word32 Q6_R_cmpyrw_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyrw(Rss,Rtt):<<1:sat
```

`Word32 Q6_R_cmpyrw_PP_s1_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyrw(Rss,Rtt*):<<1:rnd:sat
```

`Word32 Q6_R_cmpyrw_PP_conj_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 440

```
Rd=cmpyrw(Rss,Rtt*):<<1:sat
```

`Word32 Q6_R_cmpyrw_PP_conj_s1_sat(Word64 Rss, Word64 Rtt)` 440

```
Rdd=cmpyrw(Rss,Rtt)
```

`Word64 Q6_P_cmpyrw_PP(Word64 Rss, Word64 Rtt)` 440

```
Rdd=cmpyrw(Rss,Rtt*)
```

`Word64 Q6_P_cmpyrw_PP_conj(Word64 Rss, Word64 Rtt)` 440

```
Rxx+=cmpyrw(Rss,Rtt)
```

`Word64 Q6_P_cmpyrwacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 440

```
Rxx+=cmpyrw(Rss,Rtt*)
```

`Word64 Q6_P_cmpyrwacc_PP_conj(Word64 Rxx, Word64 Rss, Word64 Rtt)` 440

```
cmpyrwh
   Rd=cmpyrwh(Rss,Rt):<<1:rnd:sat
```

`Word32 Q6_R_cmpyrwh_PR_s1_rnd_sat(Word64 Rss, Word32 Rt)` 437

```
Rd=cmpyrwh(Rss,Rt*):<<1:rnd:sat
```

`Word32 Q6_R_cmpyrwh_PR_conj_s1_rnd_sat(Word64 Rss, Word32 Rt)` 437

```
combine
   Rd=combine(Rt.H,Rs.H)
```

`Word32 Q6_R_combine_RhRh(Word32 Rt, Word32 Rs)` 170

```
Rd=combine(Rt.H,Rs.L)
```

`Word32 Q6_R_combine_RhRl(Word32 Rt, Word32 Rs)` 170

```
Rd=combine(Rt.L,Rs.H)
```

`Word32 Q6_R_combine_RlRh(Word32 Rt, Word32 Rs)` 170

```
Rd=combine(Rt.L,Rs.L)
```

`Word32 Q6_R_combine_RlRl(Word32 Rt, Word32 Rs)` 170

```
Rdd=combine(#s8,#S8)
```

`Word64 Q6_P_combine_II(Word32 Is8, Word32 IS8)` 170

```
Rdd=combine(#s8,Rs)
```

`Word64 Q6_P_combine_IR(Word32 Is8, Word32 Rs)` 170

```
Rdd=combine(Rs,#s8)
```

`Word64 Q6_P_combine_RI(Word32 Rs, Word32 Is8)` 170

```
Rdd=combine(Rs,Rt)
```

`Word64 Q6_P_combine_RR(Word32 Rs, Word32 Rt)` 170

```
convert_d2df
   Rdd=convert_d2df(Rss)
```

`Word64 Q6_P_convert_d2df_P(Word64 Rss)` 462

```
convert_d2sf
   Rd=convert_d2sf(Rss)
```

`Word32 Q6_R_convert_d2sf_P(Word64 Rss)` 462

```
convert_df2d
   Rdd=convert_df2d(Rss)
```

`Word64 Q6_P_convert_df2d_P(Word64 Rss)` 465

```
Rdd=convert_df2d(Rss):chop
```

`Word64 Q6_P_convert_df2d_P_chop(Word64 Rss)` 465

```
convert_df2sf
   Rd=convert_df2sf(Rss)
```

`Word32 Q6_R_convert_df2sf_P(Word64 Rss)` 461

```
convert_df2ud
   Rdd=convert_df2ud(Rss)
```

`Word64 Q6_P_convert_df2ud_P(Word64 Rss)` 465

```
Rdd=convert_df2ud(Rss):chop
```

`Word64 Q6_P_convert_df2ud_P_chop(Word64 Rss)` 465

```
convert_df2uw
   Rd=convert_df2uw(Rss)
```

`Word32 Q6_R_convert_df2uw_P(Word64 Rss)` 465

```
Rd=convert_df2uw(Rss):chop
```

`Word32 Q6_R_convert_df2uw_P_chop(Word64 Rss)` 465

```
convert_df2w
   Rd=convert_df2w(Rss)
```

`Word32 Q6_R_convert_df2w_P(Word64 Rss)` 465

```
Rd=convert_df2w(Rss):chop
```

`Word32 Q6_R_convert_df2w_P_chop(Word64 Rss)` 465

```
convert_sf2d
   Rdd=convert_sf2d(Rs)
```

`Word64 Q6_P_convert_sf2d_R(Word32 Rs)` 465

```
Rdd=convert_sf2d(Rs):chop
```

`Word64 Q6_P_convert_sf2d_R_chop(Word32 Rs)` 465

```
convert_sf2df
   Rdd=convert_sf2df(Rs)
```

`Word64 Q6_P_convert_sf2df_R(Word32 Rs)` 461

```
convert_sf2ud
   Rdd=convert_sf2ud(Rs)
```

`Word64 Q6_P_convert_sf2ud_R(Word32 Rs)` 465

```
Rdd=convert_sf2ud(Rs):chop
```

`Word64 Q6_P_convert_sf2ud_R_chop(Word32 Rs)` 465

```
convert_sf2uw
   Rd=convert_sf2uw(Rs)
```

`Word32 Q6_R_convert_sf2uw_R(Word32 Rs)` 465

```
Rd=convert_sf2uw(Rs):chop
```

`Word32 Q6_R_convert_sf2uw_R_chop(Word32 Rs)` 465

```
convert_sf2w
   Rd=convert_sf2w(Rs)
```

`Word32 Q6_R_convert_sf2w_R(Word32 Rs)` 465

```
Rd=convert_sf2w(Rs):chop
```

`Word32 Q6_R_convert_sf2w_R_chop(Word32 Rs)` 465

```
convert_ud2df
   Rdd=convert_ud2df(Rss)
```

`Word64 Q6_P_convert_ud2df_P(Word64 Rss)` 462

```
convert_ud2sf
   Rd=convert_ud2sf(Rss)
```

`Word32 Q6_R_convert_ud2sf_P(Word64 Rss)` 462

```
convert_uw2df
   Rdd=convert_uw2df(Rs)
```

`Word64 Q6_P_convert_uw2df_R(Word32 Rs)` 462

```
convert_uw2sf
   Rd=convert_uw2sf(Rs)
```

`Word32 Q6_R_convert_uw2sf_R(Word32 Rs)` 462

```
convert_w2df
   Rdd=convert_w2df(Rs)
```

`Word64 Q6_P_convert_w2df_R(Word32 Rs)` 462

```
convert_w2sf
   Rd=convert_w2sf(Rs)
```

`Word32 Q6_R_convert_w2sf_R(Word32 Rs)` 462

```
cround
   Rd=cround(Rs,#u5)
```

`Word32 Q6_R_cround_RI(Word32 Rs, Word32 Iu5)` 352

```
Rd=cround(Rs,Rt)
```

`Word32 Q6_R_cround_RR(Word32 Rs, Word32 Rt)` 352

```
Rdd=cround(Rss,#u6)
```

`Word64 Q6_P_cround_PI(Word64 Rss, Word32 Iu6)` 352

```
Rdd=cround(Rss,Rt)
```

`Word64 Q6_P_cround_PR(Word64 Rss, Word32 Rt)` 352

```
ct0
   Rd=ct0(Rs)
```

`Word32 Q6_R_ct0_R(Word32 Rs)` 407

```
Rd=ct0(Rss)
```

`Word32 Q6_R_ct0_P(Word64 Rss)` 407

```
ct1
   Rd=ct1(Rs)
```

`Word32 Q6_R_ct1_R(Word32 Rs)` 407

```
Rd=ct1(Rss)
```

`Word32 Q6_R_ct1_P(Word64 Rss)` 407

### D

```
dccleana
   dccleana(Rs)
```

`void Q6_dccleana_A(Address a)` 317

```
dccleaninva
   dccleaninva(Rs)
```

`void Q6_dccleaninva_A(Address a)` 317

```
dcfetch
   dcfetch(Rs)
```

`void Q6_dcfetch_A(Address a)` 316

```
dcinva
   dcinva(Rs)
```

`void Q6_dcinva_A(Address a)` 317

```
dczeroa
   dczeroa(Rs)
```

`void Q6_dczeroa_A(Address a)` 313

```
deinterleave
   Rdd=deinterleave(Rss)
```

`Word64 Q6_P_deinterleave_P(Word64 Rss)` 413

```
dfadd
   Rdd=dfadd(Rss,Rtt)
```

`Word64 Q6_P_dfadd_PP(Word64 Rss, Word64 Rtt)` 456

```
dfclass
   Pd=dfclass(Rss,#u5)
```

`Byte Q6_p_dfclass_PI(Word64 Rss, Word32 Iu5)` 457

```
dfcmp.eq
   Pd=dfcmp.eq(Rss,Rtt)
```

`Byte Q6_p_dfcmp_eq_PP(Word64 Rss, Word64 Rtt)` 459

```
dfcmp.ge
   Pd=dfcmp.ge(Rss,Rtt)
```

`Byte Q6_p_dfcmp_ge_PP(Word64 Rss, Word64 Rtt)` 459

```
dfcmp.gt
   Pd=dfcmp.gt(Rss,Rtt)
```

`Byte Q6_p_dfcmp_gt_PP(Word64 Rss, Word64 Rtt)` 459

```
dfcmp.uo
   Pd=dfcmp.uo(Rss,Rtt)
```

`Byte Q6_p_dfcmp_uo_PP(Word64 Rss, Word64 Rtt)` 459

```
dfmake
   Rdd=dfmake(#u10):neg
```

`Word64 Q6_P_dfmake_I_neg(Word32 Iu10)` 473

```
Rdd=dfmake(#u10):pos
```

`Word64 Q6_P_dfmake_I_pos(Word32 Iu10)` 473

```
dfmax
   Rdd=dfmax(Rss,Rtt)
```

`Word64 Q6_P_dfmax_PP(Word64 Rss, Word64 Rtt)` 474

```
dfmin
   Rdd=dfmin(Rss,Rtt)
```

`Word64 Q6_P_dfmin_PP(Word64 Rss, Word64 Rtt)` 475

```
dfmpyfix
   Rdd=dfmpyfix(Rss,Rtt)
```

`Word64 Q6_P_dfmpyfix_PP(Word64 Rss, Word64 Rtt)` 476

```
dfmpyhh
   Rxx+=dfmpyhh(Rss,Rtt)
```

`Word64 Q6_P_dfmpyhhacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 468

```
dfmpylh
   Rxx+=dfmpylh(Rss,Rtt)
```

`Word64 Q6_P_dfmpylhacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 468

```
dfmpyll
   Rdd=dfmpyll(Rss,Rtt)
```

`Word64 Q6_P_dfmpyll_PP(Word64 Rss, Word64 Rtt)` 476

```
dfsub
   Rdd=dfsub(Rss,Rtt)
```

`Word64 Q6_P_dfsub_PP(Word64 Rss, Word64 Rtt)` 478

```
dmsyncht
   Rd=dmsyncht
```

`Word32 Q6_R_dmsyncht()` 325

### E

```
extract
   Rd=extract(Rs,#u5,#U5)
```

`Word32 Q6_R_extract_RII(Word32 Rs, Word32 Iu5, Word32 IU5)` 409

```
Rd=extract(Rs,Rtt)
```

`Word32 Q6_R_extract_RP(Word32 Rs, Word64 Rtt)` 409

```
Rdd=extract(Rss,#u6,#U6)
```

`Word64 Q6_P_extract_PII(Word64 Rss, Word32 Iu6, Word32 IU6)` 409

```
Rdd=extract(Rss,Rtt)
```

`Word64 Q6_P_extract_PP(Word64 Rss, Word64 Rtt)` 409

```
extractu
   Rd=extractu(Rs,#u5,#U5)
```

`Word32 Q6_R_extractu_RII(Word32 Rs, Word32 Iu5, Word32 IU5)` 409

```
Rd=extractu(Rs,Rtt)
```

`Word32 Q6_R_extractu_RP(Word32 Rs, Word64 Rtt)` 409

```
Rdd=extractu(Rss,#u6,#U6)
```

`Word64 Q6_P_extractu_PII(Word64 Rss, Word32 Iu6, Word32 IU6)` 409

```
Rdd=extractu(Rss,Rtt)
```

`Word64 Q6_P_extractu_PP(Word64 Rss, Word64 Rtt)` 409

### F

```
fastcorner9
   Pd=!fastcorner9(Ps,Pt)
```

`Byte Q6_p_not_fastcorner9_pp(Byte Ps, Byte Pt)` 193

```
Pd=fastcorner9(Ps,Pt)
```

`Byte Q6_p_fastcorner9_pp(Byte Ps, Byte Pt)` 193

### I

```
insert
   Rx=insert(Rs,#u5,#U5)
```

`Word32 Q6_R_insert_RII(Word32 Rx, Word32 Rs, Word32 Iu5, Word32 IU5)` 412

```
Rx=insert(Rs,Rtt)
```

`Word32 Q6_R_insert_RP(Word32 Rx, Word32 Rs, Word64 Rtt)` 412

```
Rxx=insert(Rss,#u6,#U6)
```

`Word64 Q6_P_insert_PII(Word64 Rxx, Word64 Rss, Word32 Iu6, Word32 IU6)` 412

```
Rxx=insert(Rss,Rtt)
```

`Word64 Q6_P_insert_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 412

```
interleave
   Rdd=interleave(Rss)
```

`Word64 Q6_P_interleave_P(Word64 Rss)` 413

### L

```
l2fetch
   l2fetch(Rs,Rt)
```

`void Q6_l2fetch_AR(Address a, Word32 Rt)` 323

```
l2fetch(Rs,Rtt)
```

`void Q6_l2fetch_AP(Address a, Word64 Rtt)` 323

```
lfs
   Rdd=lfs(Rss,Rtt)
```

`Word64 Q6_P_lfs_PP(Word64 Rss, Word64 Rtt)` 414

```
lsl
   Rd=lsl(#s6,Rt)
```

`Word32 Q6_R_lsl_IR(Word32 Is6, Word32 Rt)` 597

```
Rd=lsl(Rs,Rt)
```

`Word32 Q6_R_lsl_RR(Word32 Rs, Word32 Rt)` 597

```
Rdd=lsl(Rss,Rt)
```

`Word64 Q6_P_lsl_PR(Word64 Rss, Word32 Rt)` 597

```
Rx&=lsl(Rs,Rt)
```

`Word32 Q6_R_lsland_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rx+=lsl(Rs,Rt)
```

`Word32 Q6_R_lslacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx-=lsl(Rs,Rt)
```

`Word32 Q6_R_lslnac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx|=lsl(Rs,Rt)
```

`Word32 Q6_R_lslor_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rxx&=lsl(Rss,Rt)
```

`Word64 Q6_P_lsland_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx^=lsl(Rss,Rt)
```

`Word64 Q6_P_lslxacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx+=lsl(Rss,Rt)
```

`Word64 Q6_P_lslacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx-=lsl(Rss,Rt)
```

`Word64 Q6_P_lslnac_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx|=lsl(Rss,Rt)
```

`Word64 Q6_P_lslor_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 604

```
lsr
   Rd=lsr(Rs,#u5)
```

`Word32 Q6_R_lsr_RI(Word32 Rs, Word32 Iu5)` 584

```
Rd=lsr(Rs,Rt)
```

`Word32 Q6_R_lsr_RR(Word32 Rs, Word32 Rt)` 597

```
Rdd=lsr(Rss,#u6)
```

`Word64 Q6_P_lsr_PI(Word64 Rss, Word32 Iu6)` 585

```
Rdd=lsr(Rss,Rt)
```

`Word64 Q6_P_lsr_PR(Word64 Rss, Word32 Rt)` 597

```
Rx&=lsr(Rs,#u5)
```

`Word32 Q6_R_lsrand_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx&=lsr(Rs,Rt)
```

`Word32 Q6_R_lsrand_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rx^=lsr(Rs,#u5)
```

`Word32 Q6_R_lsrxacc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx+=lsr(Rs,#u5)
```

`Word32 Q6_R_lsracc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx+=lsr(Rs,Rt)
```

`Word32 Q6_R_lsracc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx=add(#u8,lsr(Rx,#U5))
```

`Word32 Q6_R_add_lsr_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 587

```
Rx=and(#u8,lsr(Rx,#U5))
```

`Word32 Q6_R_and_lsr_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 591

```
Rx-=lsr(Rs,#u5)
```

`Word32 Q6_R_lsrnac_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx-=lsr(Rs,Rt)
```

`Word32 Q6_R_lsrnac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 600

```
Rx=or(#u8,lsr(Rx,#U5))
```

`Word32 Q6_R_or_lsr_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 591

```
Rx=sub(#u8,lsr(Rx,#U5))
```

`Word32 Q6_R_sub_lsr_IRI(Word32 Iu8, Word32 Rx, Word32 IU5)` 587

```
Rx|=lsr(Rs,#u5)
```

`Word32 Q6_R_lsror_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx|=lsr(Rs,Rt)
```

`Word32 Q6_R_lsror_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 603

```
Rxx&=lsr(Rss,#u6)
```

`Word64 Q6_P_lsrand_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx&=lsr(Rss,Rt)
```

`Word64 Q6_P_lsrand_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 603

```
Rxx^=lsr(Rss,#u6)
```

`Word64 Q6_P_lsrxacc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx^=lsr(Rss,Rt)
```

`Word64 Q6_P_lsrxacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 604

```
Rxx+=lsr(Rss,#u6)
```

`Word64 Q6_P_lsracc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx+=lsr(Rss,Rt)
```

`Word64 Q6_P_lsracc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx-=lsr(Rss,#u6)
```

`Word64 Q6_P_lsrnac_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx-=lsr(Rss,Rt)
```

`Word64 Q6_P_lsrnac_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 600

```
Rxx|=lsr(Rss,#u6)
```

`Word64 Q6_P_lsror_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 592

```
Rxx|=lsr(Rss,Rt)
```

`Word64 Q6_P_lsror_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 604

### M

```
mask
   Rd=mask(#u5,#U5)
```

`Word32 Q6_R_mask_II(Word32 Iu5, Word32 IU5)` 583

```
Rdd=mask(Pt)
```

`Word64 Q6_P_mask_p(Byte Pt)` 570

```
max
   Rd=max(Rs,Rt)
```

`Word32 Q6_R_max_RR(Word32 Rs, Word32 Rt)` 344

```
Rdd=max(Rss,Rtt)
```

`Word64 Q6_P_max_PP(Word64 Rss, Word64 Rtt)` 345

```
maxu
   Rd=maxu(Rs,Rt)
```

`UWord32 Q6_R_maxu_RR(Word32 Rs, Word32 Rt)` 344

```
Rdd=maxu(Rss,Rtt)
```

`UWord64 Q6_P_maxu_PP(Word64 Rss, Word64 Rtt)` 345

```
memb
   memb(Rx++#s4:0:circ(Mu))=Rt
       void Q6_memb_IMR_circ(void** StartAddress, Word32 Is4_0, Word32 Mu, Word32
```

`Rt, void* BaseAddress)` 290

```
memb(Rx++I:circ(Mu))=Rt
   void Q6_memb_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void*
```

`BaseAddress)` 290

```
Rd=memb(Rx++#s4:0:circ(Mu))
   Word32 Q6_R_memb_IM_circ(void** StartAddress, Word32 Is4_0, Word32 Mu,
```

`void* BaseAddress)` 224

```
Rd=memb(Rx++I:circ(Mu))
   Word32 Q6_R_memb_M_circ(void** StartAddress, Word32 Mu, void* BaseAddress)
```

224

```
memd
   memd(Rx++#s4:3:circ(Mu))=Rtt
       void Q6_memd_IMP_circ(void** StartAddress, Word32 Is4_3, Word32 Mu, Word64
```

`Rtt, void* BaseAddress)` 286

```
memd(Rx++I:circ(Mu))=Rtt
   void Q6_memd_MP_circ(void** StartAddress, Word32 Mu, Word64 Rtt, void*
```

`BaseAddress)` 286

```
Rdd=memd(Rx++#s4:3:circ(Mu))
   Word32 Q6_R_memd_IM_circ(void** StartAddress, Word32 Is4_3, Word32 Mu,
```

`void* BaseAddress)` 220

```
Rdd=memd(Rx++I:circ(Mu))
   Word32 Q6_R_memd_M_circ(void** StartAddress, Word32 Mu, void* BaseAddress)
```

220

```
memh
   memh(Rx++#s4:1:circ(Mu))=Rt
       void Q6_memh_IMR_circ(void** StartAddress, Word32 Is4_1, Word32 Mu, Word32
```

`Rt, void* BaseAddress)` 296

```
memh(Rx++#s4:1:circ(Mu))=Rt.H
   void Q6_memh_IMRh_circ(void** StartAddress, Word32 Is4_1, Word32 Mu, Word32
```

`Rt, void* BaseAddress)` 296

```
memh(Rx++I:circ(Mu))=Rt
   void Q6_memh_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void*
```

`BaseAddress)` 296

```
memh(Rx++I:circ(Mu))=Rt.H
   void Q6_memh_MRh_circ(void** StartAddress, Word32 Mu, Word32 Rt, void*
```

`BaseAddress)` 296

```
Rd=memh(Rx++#s4:1:circ(Mu))
   Word32 Q6_R_memh_IM_circ(void** StartAddress, Word32 Is4_1, Word32 Mu,
```

`void* BaseAddress)` 234

```
Rd=memh(Rx++I:circ(Mu))
   Word32 Q6_R_memh_M_circ(void** StartAddress, Word32 Mu, void* BaseAddress)
```

234

```
memub
   Rd=memub(Rx++#s4:0:circ(Mu))
       Word32 Q6_R_memub_IM_circ(void** StartAddress, Word32 Is4_0, Word32 Mu,
```

`void* BaseAddress)` 240

```
Rd=memub(Rx++I:circ(Mu))
   Word32 Q6_R_memub_M_circ(void** StartAddress, Word32 Mu, void*
```

`BaseAddress)` 240

```
memuh
   Rd=memuh(Rx++#s4:1:circ(Mu))
       Word32 Q6_R_memuh_IM_circ(void** StartAddress, Word32 Is4_1, Word32 Mu,
```

`void* BaseAddress)` 244

```
Rd=memuh(Rx++I:circ(Mu))
   Word32 Q6_R_memuh_M_circ(void** StartAddress, Word32 Mu, void*
```

`BaseAddress)` 244

```
memw
   memw(Rx++#s4:2:circ(Mu))=Rt
       void Q6_memw_IMR_circ(void** StartAddress, Word32 Is4_2, Word32 Mu, Word32
```

`Rt, void* BaseAddress)` 303

```
memw(Rx++I:circ(Mu))=Rt
   void Q6_memw_MR_circ(void** StartAddress, Word32 Mu, Word32 Rt, void*
```

`BaseAddress)` 303

```
Rd=memw(Rx++#s4:2:circ(Mu))
   Word32 Q6_R_memw_IM_circ(void** StartAddress, Word32 Is4_2, Word32 Mu,
```

`void* BaseAddress)` 248

```
Rd=memw(Rx++I:circ(Mu))
   Word32 Q6_R_memw_M_circ(void** StartAddress, Word32 Mu, void* BaseAddress)
```

248

```
min
   Rd=min(Rt,Rs)
```

`Word32 Q6_R_min_RR(Word32 Rt, Word32 Rs)` 346

```
Rdd=min(Rtt,Rss)
```

`Word64 Q6_P_min_PP(Word64 Rtt, Word64 Rss)` 347

```
minu
   Rd=minu(Rt,Rs)
```

`UWord32 Q6_R_minu_RR(Word32 Rt, Word32 Rs)` 346

```
Rdd=minu(Rtt,Rss)
```

`UWord64 Q6_P_minu_PP(Word64 Rtt, Word64 Rss)` 347

```
modwrap
   Rd=modwrap(Rs,Rt)
```

`Word32 Q6_R_modwrap_RR(Word32 Rs, Word32 Rt)` 348

```
mpy
   Rd=mpy(Rs,Rt.H):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RRh_s1_rnd_sat(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt.H):<<1:sat
```

`Word32 Q6_R_mpy_RRh_s1_sat(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt.L):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RRl_s1_rnd_sat(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt.L):<<1:sat
```

`Word32 Q6_R_mpy_RRl_s1_sat(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt)
```

`Word32 Q6_R_mpy_RR(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt):<<1
```

`Word32 Q6_R_mpy_RR_s1(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt):<<1:sat
```

`Word32 Q6_R_mpy_RR_s1_sat(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs,Rt):rnd
```

`Word32 Q6_R_mpy_RR_rnd(Word32 Rs, Word32 Rt)` 508

```
Rd=mpy(Rs.H,Rt.H)
```

`Word32 Q6_R_mpy_RhRh(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):<<1
```

`Word32 Q6_R_mpy_RhRh_s1(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):<<1:rnd
```

`Word32 Q6_R_mpy_RhRh_s1_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RhRh_s1_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):<<1:sat
```

`Word32 Q6_R_mpy_RhRh_s1_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):rnd
```

`Word32 Q6_R_mpy_RhRh_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):rnd:sat
```

`Word32 Q6_R_mpy_RhRh_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.H):sat
```

`Word32 Q6_R_mpy_RhRh_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L)
```

`Word32 Q6_R_mpy_RhRl(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):<<1
```

`Word32 Q6_R_mpy_RhRl_s1(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):<<1:rnd
```

`Word32 Q6_R_mpy_RhRl_s1_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RhRl_s1_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):<<1:sat
```

`Word32 Q6_R_mpy_RhRl_s1_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):rnd
```

`Word32 Q6_R_mpy_RhRl_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):rnd:sat
```

`Word32 Q6_R_mpy_RhRl_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.H,Rt.L):sat
```

`Word32 Q6_R_mpy_RhRl_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H)
```

`Word32 Q6_R_mpy_RlRh(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):<<1
```

`Word32 Q6_R_mpy_RlRh_s1(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):<<1:rnd
```

`Word32 Q6_R_mpy_RlRh_s1_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RlRh_s1_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):<<1:sat
```

`Word32 Q6_R_mpy_RlRh_s1_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):rnd
```

`Word32 Q6_R_mpy_RlRh_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):rnd:sat
```

`Word32 Q6_R_mpy_RlRh_rnd_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.H):sat
```

`Word32 Q6_R_mpy_RlRh_sat(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.L)
```

`Word32 Q6_R_mpy_RlRl(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.L):<<1
```

`Word32 Q6_R_mpy_RlRl_s1(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.L):<<1:rnd
```

`Word32 Q6_R_mpy_RlRl_s1_rnd(Word32 Rs, Word32 Rt)` 492

```
Rd=mpy(Rs.L,Rt.L):<<1:rnd:sat
```

`Word32 Q6_R_mpy_RlRl_s1_rnd_sat(Word32 Rs, Word32 Rt)` 493

```
Rd=mpy(Rs.L,Rt.L):<<1:sat
```

`Word32 Q6_R_mpy_RlRl_s1_sat(Word32 Rs, Word32 Rt)` 493

```
Rd=mpy(Rs.L,Rt.L):rnd
```

`Word32 Q6_R_mpy_RlRl_rnd(Word32 Rs, Word32 Rt)` 493

```
Rd=mpy(Rs.L,Rt.L):rnd:sat
```

`Word32 Q6_R_mpy_RlRl_rnd_sat(Word32 Rs, Word32 Rt)` 493

```
Rd=mpy(Rs.L,Rt.L):sat
```

`Word32 Q6_R_mpy_RlRl_sat(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs,Rt)
```

`Word64 Q6_P_mpy_RR(Word32 Rs, Word32 Rt)` 510

```
Rdd=mpy(Rs.H,Rt.H)
```

`Word64 Q6_P_mpy_RhRh(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.H):<<1
```

`Word64 Q6_P_mpy_RhRh_s1(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.H):<<1:rnd
```

`Word64 Q6_P_mpy_RhRh_s1_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.H):rnd
```

`Word64 Q6_P_mpy_RhRh_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.L)
```

`Word64 Q6_P_mpy_RhRl(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.L):<<1
```

`Word64 Q6_P_mpy_RhRl_s1(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.L):<<1:rnd
```

`Word64 Q6_P_mpy_RhRl_s1_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.H,Rt.L):rnd
```

`Word64 Q6_P_mpy_RhRl_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.H)
```

`Word64 Q6_P_mpy_RlRh(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.H):<<1
```

`Word64 Q6_P_mpy_RlRh_s1(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.H):<<1:rnd
```

`Word64 Q6_P_mpy_RlRh_s1_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.H):rnd
```

`Word64 Q6_P_mpy_RlRh_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.L)
```

`Word64 Q6_P_mpy_RlRl(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.L):<<1
```

`Word64 Q6_P_mpy_RlRl_s1(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.L):<<1:rnd
```

`Word64 Q6_P_mpy_RlRl_s1_rnd(Word32 Rs, Word32 Rt)` 493

```
Rdd=mpy(Rs.L,Rt.L):rnd
```

`Word64 Q6_P_mpy_RlRl_rnd(Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs,Rt):<<1:sat
```

`Word32 Q6_R_mpyacc_RR_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 508

```
Rx+=mpy(Rs.H,Rt.H)
```

`Word32 Q6_R_mpyacc_RhRh(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.H):<<1
```

`Word32 Q6_R_mpyacc_RhRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.H):<<1:sat
```

`Word32 Q6_R_mpyacc_RhRh_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.H):sat
```

`Word32 Q6_R_mpyacc_RhRh_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.L)
```

`Word32 Q6_R_mpyacc_RhRl(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.L):<<1
```

`Word32 Q6_R_mpyacc_RhRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.L):<<1:sat
```

`Word32 Q6_R_mpyacc_RhRl_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.H,Rt.L):sat
```

`Word32 Q6_R_mpyacc_RhRl_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.L,Rt.H)
```

`Word32 Q6_R_mpyacc_RlRh(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.L,Rt.H):<<1
```

`Word32 Q6_R_mpyacc_RlRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 493

```
Rx+=mpy(Rs.L,Rt.H):<<1:sat
```

`Word32 Q6_R_mpyacc_RlRh_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx+=mpy(Rs.L,Rt.H):sat
```

`Word32 Q6_R_mpyacc_RlRh_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx+=mpy(Rs.L,Rt.L)
```

`Word32 Q6_R_mpyacc_RlRl(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx+=mpy(Rs.L,Rt.L):<<1
```

`Word32 Q6_R_mpyacc_RlRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx+=mpy(Rs.L,Rt.L):<<1:sat
```

`Word32 Q6_R_mpyacc_RlRl_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx+=mpy(Rs.L,Rt.L):sat
```

`Word32 Q6_R_mpyacc_RlRl_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs,Rt):<<1:sat
```

`Word32 Q6_R_mpynac_RR_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 508

```
Rx-=mpy(Rs.H,Rt.H)
```

`Word32 Q6_R_mpynac_RhRh(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.H):<<1
```

`Word32 Q6_R_mpynac_RhRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.H):<<1:sat
```

`Word32 Q6_R_mpynac_RhRh_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.H):sat
```

`Word32 Q6_R_mpynac_RhRh_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.L)
```

`Word32 Q6_R_mpynac_RhRl(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.L):<<1
```

`Word32 Q6_R_mpynac_RhRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.L):<<1:sat
```

`Word32 Q6_R_mpynac_RhRl_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.H,Rt.L):sat
```

`Word32 Q6_R_mpynac_RhRl_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.H)
```

`Word32 Q6_R_mpynac_RlRh(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.H):<<1
```

`Word32 Q6_R_mpynac_RlRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.H):<<1:sat
```

`Word32 Q6_R_mpynac_RlRh_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.H):sat
```

`Word32 Q6_R_mpynac_RlRh_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.L)
```

`Word32 Q6_R_mpynac_RlRl(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.L):<<1
```

`Word32 Q6_R_mpynac_RlRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.L):<<1:sat
```

`Word32 Q6_R_mpynac_RlRl_s1_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rx-=mpy(Rs.L,Rt.L):sat
```

`Word32 Q6_R_mpynac_RlRl_sat(Word32 Rx, Word32 Rs, Word32 Rt)` 494

```
Rxx+=mpy(Rs,Rt)
```

`Word64 Q6_P_mpyacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 510

```
Rxx+=mpy(Rs.H,Rt.H)
```

`Word64 Q6_P_mpyacc_RhRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 494

```
Rxx+=mpy(Rs.H,Rt.H):<<1
```

`Word64 Q6_P_mpyacc_RhRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.H,Rt.L)
```

`Word64 Q6_P_mpyacc_RhRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.H,Rt.L):<<1
```

`Word64 Q6_P_mpyacc_RhRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.L,Rt.H)
```

`Word64 Q6_P_mpyacc_RlRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.L,Rt.H):<<1
```

`Word64 Q6_P_mpyacc_RlRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.L,Rt.L)
```

`Word64 Q6_P_mpyacc_RlRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx+=mpy(Rs.L,Rt.L):<<1
```

`Word64 Q6_P_mpyacc_RlRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs,Rt)
```

`Word64 Q6_P_mpynac_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 510

```
Rxx-=mpy(Rs.H,Rt.H)
```

`Word64 Q6_P_mpynac_RhRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.H,Rt.H):<<1
```

`Word64 Q6_P_mpynac_RhRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.H,Rt.L)
```

`Word64 Q6_P_mpynac_RhRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.H,Rt.L):<<1
```

`Word64 Q6_P_mpynac_RhRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.L,Rt.H)
```

`Word64 Q6_P_mpynac_RlRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.L,Rt.H):<<1
```

`Word64 Q6_P_mpynac_RlRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.L,Rt.L)
```

`Word64 Q6_P_mpynac_RlRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
Rxx-=mpy(Rs.L,Rt.L):<<1
```

`Word64 Q6_P_mpynac_RlRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 495

```
mpyi
   Rd=mpyi(Rs,#m9)
```

`Word32 Q6_R_mpyi_RI(Word32 Rs, Word32 Im9)` 481

```
Rd=mpyi(Rs,Rt)
```

`Word32 Q6_R_mpyi_RR(Word32 Rs, Word32 Rt)` 481

```
Rx+=mpyi(Rs,#u8)
```

`Word32 Q6_R_mpyiacc_RI(Word32 Rx, Word32 Rs, Word32 Iu8)` 481

```
Rx+=mpyi(Rs,Rt)
```

`Word32 Q6_R_mpyiacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 481

```
Rx-=mpyi(Rs,#u8)
```

`Word32 Q6_R_mpyinac_RI(Word32 Rx, Word32 Rs, Word32 Iu8)` 481

```
Rx-=mpyi(Rs,Rt)
```

`Word32 Q6_R_mpyinac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 481

```
mpysu
   Rd=mpysu(Rs,Rt)
```

`Word32 Q6_R_mpysu_RR(Word32 Rs, Word32 Rt)` 508

```
mpyu
   Rd=mpyu(Rs,Rt)
```

`UWord32 Q6_R_mpyu_RR(Word32 Rs, Word32 Rt)` 508

```
Rd=mpyu(Rs.H,Rt.H)
```

`UWord32 Q6_R_mpyu_RhRh(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.H,Rt.H):<<1
```

`UWord32 Q6_R_mpyu_RhRh_s1(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.H,Rt.L)
```

`UWord32 Q6_R_mpyu_RhRl(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.H,Rt.L):<<1
```

`UWord32 Q6_R_mpyu_RhRl_s1(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.L,Rt.H)
```

`UWord32 Q6_R_mpyu_RlRh(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.L,Rt.H):<<1
```

`UWord32 Q6_R_mpyu_RlRh_s1(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.L,Rt.L)
```

`UWord32 Q6_R_mpyu_RlRl(Word32 Rs, Word32 Rt)` 499

```
Rd=mpyu(Rs.L,Rt.L):<<1
```

`UWord32 Q6_R_mpyu_RlRl_s1(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs,Rt)
```

`UWord64 Q6_P_mpyu_RR(Word32 Rs, Word32 Rt)` 510

```
Rdd=mpyu(Rs.H,Rt.H)
```

`UWord64 Q6_P_mpyu_RhRh(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.H,Rt.H):<<1
```

`UWord64 Q6_P_mpyu_RhRh_s1(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.H,Rt.L)
```

`UWord64 Q6_P_mpyu_RhRl(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.H,Rt.L):<<1
```

`UWord64 Q6_P_mpyu_RhRl_s1(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.L,Rt.H)
```

`UWord64 Q6_P_mpyu_RlRh(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.L,Rt.H):<<1
```

`UWord64 Q6_P_mpyu_RlRh_s1(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.L,Rt.L)
```

`UWord64 Q6_P_mpyu_RlRl(Word32 Rs, Word32 Rt)` 499

```
Rdd=mpyu(Rs.L,Rt.L):<<1
```

`UWord64 Q6_P_mpyu_RlRl_s1(Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.H,Rt.H)
```

`Word32 Q6_R_mpyuacc_RhRh(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.H,Rt.H):<<1
```

`Word32 Q6_R_mpyuacc_RhRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.H,Rt.L)
```

`Word32 Q6_R_mpyuacc_RhRl(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.H,Rt.L):<<1
```

`Word32 Q6_R_mpyuacc_RhRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.L,Rt.H)
```

`Word32 Q6_R_mpyuacc_RlRh(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.L,Rt.H):<<1
```

`Word32 Q6_R_mpyuacc_RlRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.L,Rt.L)
```

`Word32 Q6_R_mpyuacc_RlRl(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx+=mpyu(Rs.L,Rt.L):<<1
```

`Word32 Q6_R_mpyuacc_RlRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx-=mpyu(Rs.H,Rt.H)
```

`Word32 Q6_R_mpyunac_RhRh(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx-=mpyu(Rs.H,Rt.H):<<1
```

`Word32 Q6_R_mpyunac_RhRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx-=mpyu(Rs.H,Rt.L)
```

`Word32 Q6_R_mpyunac_RhRl(Word32 Rx, Word32 Rs, Word32 Rt)` 499

```
Rx-=mpyu(Rs.H,Rt.L):<<1
```

`Word32 Q6_R_mpyunac_RhRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 500

```
Rx-=mpyu(Rs.L,Rt.H)
```

`Word32 Q6_R_mpyunac_RlRh(Word32 Rx, Word32 Rs, Word32 Rt)` 500

```
Rx-=mpyu(Rs.L,Rt.H):<<1
```

`Word32 Q6_R_mpyunac_RlRh_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 500

```
Rx-=mpyu(Rs.L,Rt.L)
```

`Word32 Q6_R_mpyunac_RlRl(Word32 Rx, Word32 Rs, Word32 Rt)` 500

```
Rx-=mpyu(Rs.L,Rt.L):<<1
```

`Word32 Q6_R_mpyunac_RlRl_s1(Word32 Rx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs,Rt)
```

`Word64 Q6_P_mpyuacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 510

```
Rxx+=mpyu(Rs.H,Rt.H)
```

`Word64 Q6_P_mpyuacc_RhRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.H,Rt.H):<<1
```

`Word64 Q6_P_mpyuacc_RhRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.H,Rt.L)
```

`Word64 Q6_P_mpyuacc_RhRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.H,Rt.L):<<1
```

`Word64 Q6_P_mpyuacc_RhRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.L,Rt.H)
```

`Word64 Q6_P_mpyuacc_RlRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.L,Rt.H):<<1
```

`Word64 Q6_P_mpyuacc_RlRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.L,Rt.L)
```

`Word64 Q6_P_mpyuacc_RlRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx+=mpyu(Rs.L,Rt.L):<<1
```

`Word64 Q6_P_mpyuacc_RlRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs,Rt)
```

`Word64 Q6_P_mpyunac_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 510

```
Rxx-=mpyu(Rs.H,Rt.H)
```

`Word64 Q6_P_mpyunac_RhRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.H,Rt.H):<<1
```

`Word64 Q6_P_mpyunac_RhRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.H,Rt.L)
```

`Word64 Q6_P_mpyunac_RhRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.H,Rt.L):<<1
```

`Word64 Q6_P_mpyunac_RhRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.L,Rt.H)
```

`Word64 Q6_P_mpyunac_RlRh(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.L,Rt.H):<<1
```

`Word64 Q6_P_mpyunac_RlRh_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.L,Rt.L)
```

`Word64 Q6_P_mpyunac_RlRl(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
Rxx-=mpyu(Rs.L,Rt.L):<<1
```

`Word64 Q6_P_mpyunac_RlRl_s1(Word64 Rxx, Word32 Rs, Word32 Rt)` 500

```
mpyui
   Rd=mpyui(Rs,Rt)
```

`Word32 Q6_R_mpyui_RR(Word32 Rs, Word32 Rt)` 481

```
mux
   Rd=mux(Pu,#s8,#S8)
```

`Word32 Q6_R_mux_pII(Byte Pu, Word32 Is8, Word32 IS8)` 171

```
Rd=mux(Pu,#s8,Rs)
```

`Word32 Q6_R_mux_pIR(Byte Pu, Word32 Is8, Word32 Rs)` 171

```
Rd=mux(Pu,Rs,#s8)
```

`Word32 Q6_R_mux_pRI(Byte Pu, Word32 Rs, Word32 Is8)` 171

```
Rd=mux(Pu,Rs,Rt)
```

`Word32 Q6_R_mux_pRR(Byte Pu, Word32 Rs, Word32 Rt)` 171

### N

```
neg
   Rd=neg(Rs)
```

`Word32 Q6_R_neg_R(Word32 Rs)` 157

```
Rd=neg(Rs):sat
```

`Word32 Q6_R_neg_R_sat(Word32 Rs)` 349

```
Rdd=neg(Rss)
```

`Word64 Q6_P_neg_P(Word64 Rss)` 349

```
no mnemonic
   Pd=Ps
```

`Byte Q6_p_equals_p(Byte Ps)` 200

```
Pd=Rs
```

`Byte Q6_p_equals_R(Word32 Rs)` 572

```
Rd=#s16
```

`Word32 Q6_R_equals_I(Word32 Is16)` 162

```
Rd=Ps
```

`Word32 Q6_R_equals_p(Byte Ps)` 572

```
Rd=Rs
```

`Word32 Q6_R_equals_R(Word32 Rs)` 164

```
Rdd=#s8
```

`Word64 Q6_P_equals_I(Word32 Is8)` 162

```
Rdd=Rss
```

`Word64 Q6_P_equals_P(Word64 Rss)` 164

```
Rx.H=#u16
```

`Word32 Q6_Rh_equals_I(Word32 Rx, Word32 Iu16)` 162

```
Rx.L=#u16
```

`Word32 Q6_Rl_equals_I(Word32 Rx, Word32 Iu16)` 162

```
normamt
   Rd=normamt(Rs)
```

`Word32 Q6_R_normamt_R(Word32 Rs)` 405

```
Rd=normamt(Rss)
```

`Word32 Q6_R_normamt_P(Word64 Rss)` 405

```
not
   Pd=not(Ps)
```

`Byte Q6_p_not_p(Byte Ps)` 200

```
Rd=not(Rs)
```

`Word32 Q6_R_not_R(Word32 Rs)` 155

```
Rdd=not(Rss)
```

`Word64 Q6_P_not_P(Word64 Rss)` 339

### O

```
or
   Pd=and(Ps,or(Pt,!Pu))
```

`Byte Q6_p_and_or_ppnp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=and(Ps,or(Pt,Pu))
```

`Byte Q6_p_and_or_ppp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=or(Ps,and(Pt,!Pu))
```

`Byte Q6_p_or_and_ppnp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=or(Ps,and(Pt,Pu))
```

`Byte Q6_p_or_and_ppp(Byte Ps, Byte Pt, Byte Pu)` 200

```
Pd=or(Ps,or(Pt,!Pu))
```

`Byte Q6_p_or_or_ppnp(Byte Ps, Byte Pt, Byte Pu)` 201

```
Pd=or(Ps,or(Pt,Pu))
```

`Byte Q6_p_or_or_ppp(Byte Ps, Byte Pt, Byte Pu)` 201

```
Pd=or(Pt,!Ps)
```

`Byte Q6_p_or_pnp(Byte Pt, Byte Ps)` 201

```
Pd=or(Pt,Ps)
```

`Byte Q6_p_or_pp(Byte Pt, Byte Ps)` 201

```
Rd=or(Rs,#s10)
```

`Word32 Q6_R_or_RI(Word32 Rs, Word32 Is10)` 155

```
Rd=or(Rs,Rt)
```

`Word32 Q6_R_or_RR(Word32 Rs, Word32 Rt)` 155

```
Rd=or(Rt,~Rs)
```

`Word32 Q6_R_or_RnR(Word32 Rt, Word32 Rs)` 155

```
Rdd=or(Rss,Rtt)
```

`Word64 Q6_P_or_PP(Word64 Rss, Word64 Rtt)` 339

```
Rdd=or(Rtt,~Rss)
```

`Word64 Q6_P_or_PnP(Word64 Rtt, Word64 Rss)` 339

```
Rx&=or(Rs,Rt)
```

`Word32 Q6_R_orand_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx^=or(Rs,Rt)
```

`Word32 Q6_R_orxacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx=or(Ru,and(Rx,#s10))
```

`Word32 Q6_R_or_and_RRI(Word32 Ru, Word32 Rx, Word32 Is10)` 342

```
Rx|=or(Rs,#s10)
```

`Word32 Q6_R_oror_RI(Word32 Rx, Word32 Rs, Word32 Is10)` 342

```
Rx|=or(Rs,Rt)
```

`Word32 Q6_R_oror_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

### P

```
packhl
   Rdd=packhl(Rs,Rt)
```

`Word64 Q6_P_packhl_RR(Word32 Rs, Word32 Rt)` 174

```
parity
   Rd=parity(Rs,Rt)
```

`Word32 Q6_R_parity_RR(Word32 Rs, Word32 Rt)` 415

```
Rd=parity(Rss,Rtt)
```

`Word32 Q6_R_parity_PP(Word64 Rss, Word64 Rtt)` 415

```
pmpyw
   Rdd=pmpyw(Rs,Rt)
```

`Word64 Q6_P_pmpyw_RR(Word32 Rs, Word32 Rt)` 504

```
Rxx^=pmpyw(Rs,Rt)
```

`Word64 Q6_P_pmpywxacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 504

```
popcount
   Rd=popcount(Rss)
```

`Word32 Q6_R_popcount_P(Word64 Rss)` 406

### R

```
rol
   Rd=rol(Rs,#u5)
```

`Word32 Q6_R_rol_RI(Word32 Rs, Word32 Iu5)` 584

```
Rdd=rol(Rss,#u6)
```

`Word64 Q6_P_rol_PI(Word64 Rss, Word32 Iu6)` 585

```
Rx&=rol(Rs,#u5)
```

`Word32 Q6_R_roland_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx^=rol(Rs,#u5)
```

`Word32 Q6_R_rolxacc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rx+=rol(Rs,#u5)
```

`Word32 Q6_R_rolacc_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx-=rol(Rs,#u5)
```

`Word32 Q6_R_rolnac_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 587

```
Rx|=rol(Rs,#u5)
```

`Word32 Q6_R_rolor_RI(Word32 Rx, Word32 Rs, Word32 Iu5)` 591

```
Rxx&=rol(Rss,#u6)
```

`Word64 Q6_P_roland_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 591

```
Rxx^=rol(Rss,#u6)
```

`Word64 Q6_P_rolxacc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 592

```
Rxx+=rol(Rss,#u6)
```

`Word64 Q6_P_rolacc_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx-=rol(Rss,#u6)
```

`Word64 Q6_P_rolnac_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 587

```
Rxx|=rol(Rss,#u6)
```

`Word64 Q6_P_rolor_PI(Word64 Rxx, Word64 Rss, Word32 Iu6)` 592

```
round
   Rd=round(Rs,#u5)
```

`Word32 Q6_R_round_RI(Word32 Rs, Word32 Iu5)` 352

```
Rd=round(Rs,#u5):sat
```

`Word32 Q6_R_round_RI_sat(Word32 Rs, Word32 Iu5)` 352

```
Rd=round(Rs,Rt)
```

`Word32 Q6_R_round_RR(Word32 Rs, Word32 Rt)` 352

```
Rd=round(Rs,Rt):sat
```

`Word32 Q6_R_round_RR_sat(Word32 Rs, Word32 Rt)` 352

```
Rd=round(Rss):sat
```

`Word32 Q6_R_round_P_sat(Word64 Rss)` 352

### S

```
sat
   Rd=sat(Rss)
```

`Word32 Q6_R_sat_P(Word64 Rss)` 537

```
satb
   Rd=satb(Rs)
```

`Word32 Q6_R_satb_R(Word32 Rs)` 537

```
sath
   Rd=sath(Rs)
```

`Word32 Q6_R_sath_R(Word32 Rs)` 537

```
satub
   Rd=satub(Rs)
```

`Word32 Q6_R_satub_R(Word32 Rs)` 537

```
satuh
   Rd=satuh(Rs)
```

`Word32 Q6_R_satuh_R(Word32 Rs)` 537

```
setbit
   Rd=setbit(Rs,#u5)
```

`Word32 Q6_R_setbit_RI(Word32 Rs, Word32 Iu5)` 417

```
Rd=setbit(Rs,Rt)
```

`Word32 Q6_R_setbit_RR(Word32 Rs, Word32 Rt)` 417

```
sfadd
   Rd=sfadd(Rs,Rt)
```

`Word32 Q6_R_sfadd_RR(Word32 Rs, Word32 Rt)` 456

```
sfclass
   Pd=sfclass(Rs,#u5)
```

`Byte Q6_p_sfclass_RI(Word32 Rs, Word32 Iu5)` 457

```
sfcmp.eq
   Pd=sfcmp.eq(Rs,Rt)
```

`Byte Q6_p_sfcmp_eq_RR(Word32 Rs, Word32 Rt)` 459

```
sfcmp.ge
   Pd=sfcmp.ge(Rs,Rt)
```

`Byte Q6_p_sfcmp_ge_RR(Word32 Rs, Word32 Rt)` 459

```
sfcmp.gt
   Pd=sfcmp.gt(Rs,Rt)
```

`Byte Q6_p_sfcmp_gt_RR(Word32 Rs, Word32 Rt)` 459

```
sfcmp.uo
   Pd=sfcmp.uo(Rs,Rt)
```

`Byte Q6_p_sfcmp_uo_RR(Word32 Rs, Word32 Rt)` 459

```
sffixupd
   Rd=sffixupd(Rs,Rt)
```

`Word32 Q6_R_sffixupd_RR(Word32 Rs, Word32 Rt)` 467

```
sffixupn
   Rd=sffixupn(Rs,Rt)
```

`Word32 Q6_R_sffixupn_RR(Word32 Rs, Word32 Rt)` 467

```
sffixupr
   Rd=sffixupr(Rs)
```

`Word32 Q6_R_sffixupr_R(Word32 Rs)` 467

```
sfmake
   Rd=sfmake(#u10):neg
```

`Word32 Q6_R_sfmake_I_neg(Word32 Iu10)` 473

```
Rd=sfmake(#u10):pos
```

`Word32 Q6_R_sfmake_I_pos(Word32 Iu10)` 473

```
sfmax
   Rd=sfmax(Rs,Rt)
```

`Word32 Q6_R_sfmax_RR(Word32 Rs, Word32 Rt)` 474

```
sfmin
   Rd=sfmin(Rs,Rt)
```

`Word32 Q6_R_sfmin_RR(Word32 Rs, Word32 Rt)` 475

```
sfmpy
   Rd=sfmpy(Rs,Rt)
```

`Word32 Q6_R_sfmpy_RR(Word32 Rs, Word32 Rt)` 476

```
Rx+=sfmpy(Rs,Rt,Pu):scale
```

`Word32 Q6_R_sfmpyacc_RRp_scale(Word32 Rx, Word32 Rs, Word32 Rt, Byte Pu)`469

```
Rx+=sfmpy(Rs,Rt)
```

`Word32 Q6_R_sfmpyacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 468

```
Rx+=sfmpy(Rs,Rt):lib
```

`Word32 Q6_R_sfmpyacc_RR_lib(Word32 Rx, Word32 Rs, Word32 Rt)` 471

```
Rx-=sfmpy(Rs,Rt)
```

`Word32 Q6_R_sfmpynac_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 468

```
Rx-=sfmpy(Rs,Rt):lib
```

`Word32 Q6_R_sfmpynac_RR_lib(Word32 Rx, Word32 Rs, Word32 Rt)` 471

```
sfsub
   Rd=sfsub(Rs,Rt)
```

`Word32 Q6_R_sfsub_RR(Word32 Rs, Word32 Rt)` 478

```
shuffeb
   Rdd=shuffeb(Rss,Rtt)
```

`Word64 Q6_P_shuffeb_PP(Word64 Rss, Word64 Rtt)` 551

```
shuffeh
   Rdd=shuffeh(Rss,Rtt)
```

`Word64 Q6_P_shuffeh_PP(Word64 Rss, Word64 Rtt)` 551

```
shuffob
   Rdd=shuffob(Rtt,Rss)
```

`Word64 Q6_P_shuffob_PP(Word64 Rtt, Word64 Rss)` 551

```
shuffoh
   Rdd=shuffoh(Rtt,Rss)
```

`Word64 Q6_P_shuffoh_PP(Word64 Rtt, Word64 Rss)` 551

```
sub
   Rd=add(Rs,sub(#s6,Ru))
```

`Word32 Q6_R_add_sub_RIR(Word32 Rs, Word32 Is6, Word32 Ru)` 331

```
Rd=sub(#s10,Rs)
```

`Word32 Q6_R_sub_IR(Word32 Is10, Word32 Rs)` 159

```
Rd=sub(Rt,Rs)
```

`Word32 Q6_R_sub_RR(Word32 Rt, Word32 Rs)` 159

```
Rd=sub(Rt,Rs):sat
```

`Word32 Q6_R_sub_RR_sat(Word32 Rt, Word32 Rs)` 159

```
Rd=sub(Rt.H,Rs.H):<<16
```

`Word32 Q6_R_sub_RhRh_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.H,Rs.H):sat:<<16
```

`Word32 Q6_R_sub_RhRh_sat_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.H,Rs.L):<<16
```

`Word32 Q6_R_sub_RhRl_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.H,Rs.L):sat:<<16
```

`Word32 Q6_R_sub_RhRl_sat_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.H)
```

`Word32 Q6_R_sub_RlRh(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.H):<<16
```

`Word32 Q6_R_sub_RlRh_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.H):sat
```

`Word32 Q6_R_sub_RlRh_sat(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.H):sat:<<16
```

`Word32 Q6_R_sub_RlRh_sat_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.L)
```

`Word32 Q6_R_sub_RlRl(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.L):<<16
```

`Word32 Q6_R_sub_RlRl_s16(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.L):sat
```

`Word32 Q6_R_sub_RlRl_sat(Word32 Rt, Word32 Rs)` 356

```
Rd=sub(Rt.L,Rs.L):sat:<<16
```

`Word32 Q6_R_sub_RlRl_sat_s16(Word32 Rt, Word32 Rs)` 356

```
Rdd=sub(Rtt,Rss)
```

`Word64 Q6_P_sub_PP(Word64 Rtt, Word64 Rss)` 353

```
Rx+=sub(Rt,Rs)
```

`Word32 Q6_R_subacc_RR(Word32 Rx, Word32 Rt, Word32 Rs)` 354

```
swiz
   Rd=swiz(Rs)
```

`Word32 Q6_R_swiz_R(Word32 Rs)` 539

```
sxtb
   Rd=sxtb(Rs)
```

`Word32 Q6_R_sxtb_R(Word32 Rs)` 161

```
sxth
   Rd=sxth(Rs)
```

`Word32 Q6_R_sxth_R(Word32 Rs)` 161

```
sxtw
   Rdd=sxtw(Rs)
```

`Word64 Q6_P_sxtw_R(Word32 Rs)` 357

### T

```
tableidxb
   Rx=tableidxb(Rs,#u4,#U5)
```

`Word32 Q6_R_tableidxb_RII(Word32 Rx, Word32 Rs, Word32 Iu4, Word32 IU5)` 422

```
tableidxd
   Rx=tableidxd(Rs,#u4,#U5)
```

`Word32 Q6_R_tableidxd_RII(Word32 Rx, Word32 Rs, Word32 Iu4, Word32 IU5)` 422

```
tableidxh
   Rx=tableidxh(Rs,#u4,#U5)
```

`Word32 Q6_R_tableidxh_RII(Word32 Rx, Word32 Rs, Word32 Iu4, Word32 IU5)` 422

```
tableidxw
   Rx=tableidxw(Rs,#u4,#U5)
```

`Word32 Q6_R_tableidxw_RII(Word32 Rx, Word32 Rs, Word32 Iu4, Word32 IU5)` 422

```
tlbmatch
   Pd=tlbmatch(Rss,Rt)
```

`Byte Q6_p_tlbmatch_PR(Word64 Rss, Word32 Rt)` 571

```
togglebit
   Rd=togglebit(Rs,#u5)
```

`Word32 Q6_R_togglebit_RI(Word32 Rs, Word32 Iu5)` 417

```
Rd=togglebit(Rs,Rt)
```

`Word32 Q6_R_togglebit_RR(Word32 Rs, Word32 Rt)` 417

```
tstbit
   Pd=!tstbit(Rs,#u5)
```

`Byte Q6_p_not_tstbit_RI(Word32 Rs, Word32 Iu5)` 573

```
Pd=!tstbit(Rs,Rt)
```

`Byte Q6_p_not_tstbit_RR(Word32 Rs, Word32 Rt)` 573

```
Pd=tstbit(Rs,#u5)
```

`Byte Q6_p_tstbit_RI(Word32 Rs, Word32 Iu5)` 573

```
Pd=tstbit(Rs,Rt)
```

`Byte Q6_p_tstbit_RR(Word32 Rs, Word32 Rt)` 573

### V

```
vabsdiffb
   Rdd=vabsdiffb(Rtt,Rss)
```

`Word64 Q6_P_vabsdiffb_PP(Word64 Rtt, Word64 Rss)` 360

```
vabsdiffh
   Rdd=vabsdiffh(Rtt,Rss)
```

`Word64 Q6_P_vabsdiffh_PP(Word64 Rtt, Word64 Rss)` 361

```
vabsdiffub
   Rdd=vabsdiffub(Rtt,Rss)
```

`Word64 Q6_P_vabsdiffub_PP(Word64 Rtt, Word64 Rss)` 360

```
vabsdiffw
   Rdd=vabsdiffw(Rtt,Rss)
```

`Word64 Q6_P_vabsdiffw_PP(Word64 Rtt, Word64 Rss)` 362

```
vabsh
   Rdd=vabsh(Rss)
```

`Word64 Q6_P_vabsh_P(Word64 Rss)` 358

```
Rdd=vabsh(Rss):sat
```

`Word64 Q6_P_vabsh_P_sat(Word64 Rss)` 358

```
vabsw
   Rdd=vabsw(Rss)
```

`Word64 Q6_P_vabsw_P(Word64 Rss)` 359

```
Rdd=vabsw(Rss):sat
```

`Word64 Q6_P_vabsw_P_sat(Word64 Rss)` 359

```
vaddb
   Rdd=vaddb(Rss,Rtt)
```

`Word64 Q6_P_vaddb_PP(Word64 Rss, Word64 Rtt)` 373

```
vaddh
   Rd=vaddh(Rs,Rt)
```

`Word32 Q6_R_vaddh_RR(Word32 Rs, Word32 Rt)` 165

```
Rd=vaddh(Rs,Rt):sat
```

`Word32 Q6_R_vaddh_RR_sat(Word32 Rs, Word32 Rt)` 165

```
Rdd=vaddh(Rss,Rtt)
```

`Word64 Q6_P_vaddh_PP(Word64 Rss, Word64 Rtt)` 366

```
Rdd=vaddh(Rss,Rtt):sat
```

`Word64 Q6_P_vaddh_PP_sat(Word64 Rss, Word64 Rtt)` 366

```
vaddhub
   Rd=vaddhub(Rss,Rtt):sat
```

`Word32 Q6_R_vaddhub_PP_sat(Word64 Rss, Word64 Rtt)` 368

```
vaddub
   Rdd=vaddub(Rss,Rtt)
```

`Word64 Q6_P_vaddub_PP(Word64 Rss, Word64 Rtt)` 373

```
Rdd=vaddub(Rss,Rtt):sat
```

`Word64 Q6_P_vaddub_PP_sat(Word64 Rss, Word64 Rtt)` 373

```
vadduh
   Rd=vadduh(Rs,Rt):sat
```

`Word32 Q6_R_vadduh_RR_sat(Word32 Rs, Word32 Rt)` 165

```
Rdd=vadduh(Rss,Rtt):sat
```

`Word64 Q6_P_vadduh_PP_sat(Word64 Rss, Word64 Rtt)` 366

```
vaddw
   Rdd=vaddw(Rss,Rtt)
```

`Word64 Q6_P_vaddw_PP(Word64 Rss, Word64 Rtt)` 374

```
Rdd=vaddw(Rss,Rtt):sat
```

`Word64 Q6_P_vaddw_PP_sat(Word64 Rss, Word64 Rtt)` 374

```
valignb
   Rdd=valignb(Rtt,Rss,#u3)
```

`Word64 Q6_P_valignb_PPI(Word64 Rtt, Word64 Rss, Word32 Iu3)` 540

```
Rdd=valignb(Rtt,Rss,Pu)
```

`Word64 Q6_P_valignb_PPp(Word64 Rtt, Word64 Rss, Byte Pu)` 540

```
vaslh
   Rdd=vaslh(Rss,#u4)
```

`Word64 Q6_P_vaslh_PI(Word64 Rss, Word32 Iu4)` 606

```
Rdd=vaslh(Rss,Rt)
```

`Word64 Q6_P_vaslh_PR(Word64 Rss, Word32 Rt)` 611

```
vaslw
   Rdd=vaslw(Rss,#u5)
```

`Word64 Q6_P_vaslw_PI(Word64 Rss, Word32 Iu5)` 612

```
Rdd=vaslw(Rss,Rt)
```

`Word64 Q6_P_vaslw_PR(Word64 Rss, Word32 Rt)` 613

```
vasrh
   Rdd=vasrh(Rss,#u4)
```

`Word64 Q6_P_vasrh_PI(Word64 Rss, Word32 Iu4)` 606

```
Rdd=vasrh(Rss,#u4):rnd
```

`Word64 Q6_P_vasrh_PI_rnd(Word64 Rss, Word32 Iu4)` 607

```
Rdd=vasrh(Rss,Rt)
```

`Word64 Q6_P_vasrh_PR(Word64 Rss, Word32 Rt)` 611

```
vasrhub
   Rd=vasrhub(Rss,#u4):rnd:sat
```

`Word32 Q6_R_vasrhub_PI_rnd_sat(Word64 Rss, Word32 Iu4)` 609

```
Rd=vasrhub(Rss,#u4):sat
```

`Word32 Q6_R_vasrhub_PI_sat(Word64 Rss, Word32 Iu4)` 609

```
vasrw
   Rd=vasrw(Rss,#u5)
```

`Word32 Q6_R_vasrw_PI(Word64 Rss, Word32 Iu5)` 615

```
Rd=vasrw(Rss,Rt)
```

`Word32 Q6_R_vasrw_PR(Word64 Rss, Word32 Rt)` 615

```
Rdd=vasrw(Rss,#u5)
```

`Word64 Q6_P_vasrw_PI(Word64 Rss, Word32 Iu5)` 612

```
Rdd=vasrw(Rss,Rt)
```

`Word64 Q6_P_vasrw_PR(Word64 Rss, Word32 Rt)` 613

```
vavgh
   Rd=vavgh(Rs,Rt)
```

`Word32 Q6_R_vavgh_RR(Word32 Rs, Word32 Rt)` 166

```
Rd=vavgh(Rs,Rt):rnd
```

`Word32 Q6_R_vavgh_RR_rnd(Word32 Rs, Word32 Rt)` 166

```
Rdd=vavgh(Rss,Rtt)
```

`Word64 Q6_P_vavgh_PP(Word64 Rss, Word64 Rtt)` 376

```
Rdd=vavgh(Rss,Rtt):crnd
```

`Word64 Q6_P_vavgh_PP_crnd(Word64 Rss, Word64 Rtt)` 376

```
Rdd=vavgh(Rss,Rtt):rnd
```

`Word64 Q6_P_vavgh_PP_rnd(Word64 Rss, Word64 Rtt)` 376

```
vavgub
   Rdd=vavgub(Rss,Rtt)
```

`Word64 Q6_P_vavgub_PP(Word64 Rss, Word64 Rtt)` 377

```
Rdd=vavgub(Rss,Rtt):rnd
```

`Word64 Q6_P_vavgub_PP_rnd(Word64 Rss, Word64 Rtt)` 377

```
vavguh
   Rdd=vavguh(Rss,Rtt)
```

`Word64 Q6_P_vavguh_PP(Word64 Rss, Word64 Rtt)` 376

```
Rdd=vavguh(Rss,Rtt):rnd
```

`Word64 Q6_P_vavguh_PP_rnd(Word64 Rss, Word64 Rtt)` 376

```
vavguw
   Rdd=vavguw(Rss,Rtt)
```

`Word64 Q6_P_vavguw_PP(Word64 Rss, Word64 Rtt)` 379

```
Rdd=vavguw(Rss,Rtt):rnd
```

`Word64 Q6_P_vavguw_PP_rnd(Word64 Rss, Word64 Rtt)` 379

```
vavgw
   Rdd=vavgw(Rss,Rtt)
```

`Word64 Q6_P_vavgw_PP(Word64 Rss, Word64 Rtt)` 379

```
Rdd=vavgw(Rss,Rtt):crnd
```

`Word64 Q6_P_vavgw_PP_crnd(Word64 Rss, Word64 Rtt)` 379

```
Rdd=vavgw(Rss,Rtt):rnd
```

`Word64 Q6_P_vavgw_PP_rnd(Word64 Rss, Word64 Rtt)` 379

```
vclip
   Rdd=vclip(Rss,#u5)
```

`Word64 Q6_P_vclip_PI(Word64 Rss, Word32 Iu5)` 380

```
vcmpb.eq
   Pd=!any8(vcmpb.eq(Rss,Rtt))
```

`Byte Q6_p_not_any8_vcmpb_eq_PP(Word64 Rss, Word64 Rtt)` 576

```
Pd=any8(vcmpb.eq(Rss,Rtt))
```

`Byte Q6_p_any8_vcmpb_eq_PP(Word64 Rss, Word64 Rtt)` 576

```
Pd=vcmpb.eq(Rss,#u8)
```

`Byte Q6_p_vcmpb_eq_PI(Word64 Rss, Word32 Iu8)` 578

```
Pd=vcmpb.eq(Rss,Rtt)
```

`Byte Q6_p_vcmpb_eq_PP(Word64 Rss, Word64 Rtt)` 578

```
vcmpb.gt
   Pd=vcmpb.gt(Rss,#s8)
```

`Byte Q6_p_vcmpb_gt_PI(Word64 Rss, Word32 Is8)` 578

```
Pd=vcmpb.gt(Rss,Rtt)
```

`Byte Q6_p_vcmpb_gt_PP(Word64 Rss, Word64 Rtt)` 578

```
vcmpb.gtu
   Pd=vcmpb.gtu(Rss,#u7)
```

`Byte Q6_p_vcmpb_gtu_PI(Word64 Rss, Word32 Iu7)` 578

```
Pd=vcmpb.gtu(Rss,Rtt)
```

`Byte Q6_p_vcmpb_gtu_PP(Word64 Rss, Word64 Rtt)` 578

```
vcmph.eq
   Pd=vcmph.eq(Rss,#s8)
```

`Byte Q6_p_vcmph_eq_PI(Word64 Rss, Word32 Is8)` 575

```
Pd=vcmph.eq(Rss,Rtt)
```

`Byte Q6_p_vcmph_eq_PP(Word64 Rss, Word64 Rtt)` 575

```
vcmph.gt
   Pd=vcmph.gt(Rss,#s8)
```

`Byte Q6_p_vcmph_gt_PI(Word64 Rss, Word32 Is8)` 575

```
Pd=vcmph.gt(Rss,Rtt)
```

`Byte Q6_p_vcmph_gt_PP(Word64 Rss, Word64 Rtt)` 575

```
vcmph.gtu
   Pd=vcmph.gtu(Rss,#u7)
```

`Byte Q6_p_vcmph_gtu_PI(Word64 Rss, Word32 Iu7)` 575

```
Pd=vcmph.gtu(Rss,Rtt)
```

`Byte Q6_p_vcmph_gtu_PP(Word64 Rss, Word64 Rtt)` 575

```
vcmpw.eq
   Pd=vcmpw.eq(Rss,#s8)
```

`Byte Q6_p_vcmpw_eq_PI(Word64 Rss, Word32 Is8)` 580

```
Pd=vcmpw.eq(Rss,Rtt)
```

`Byte Q6_p_vcmpw_eq_PP(Word64 Rss, Word64 Rtt)` 580

```
vcmpw.gt
   Pd=vcmpw.gt(Rss,#s8)
```

`Byte Q6_p_vcmpw_gt_PI(Word64 Rss, Word32 Is8)` 580

```
Pd=vcmpw.gt(Rss,Rtt)
```

`Byte Q6_p_vcmpw_gt_PP(Word64 Rss, Word64 Rtt)` 580

```
vcmpw.gtu
   Pd=vcmpw.gtu(Rss,#u7)
```

`Byte Q6_p_vcmpw_gtu_PI(Word64 Rss, Word32 Iu7)` 580

```
Pd=vcmpw.gtu(Rss,Rtt)
```

`Byte Q6_p_vcmpw_gtu_PP(Word64 Rss, Word64 Rtt)` 580

```
vcmpyi
   Rdd=vcmpyi(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vcmpyi_PP_s1_sat(Word64 Rss, Word64 Rtt)` 443

```
Rdd=vcmpyi(Rss,Rtt):sat
```

`Word64 Q6_P_vcmpyi_PP_sat(Word64 Rss, Word64 Rtt)` 443

```
Rxx+=vcmpyi(Rss,Rtt):sat
```

`Word64 Q6_P_vcmpyiacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 443

```
vcmpyr
   Rdd=vcmpyr(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vcmpyr_PP_s1_sat(Word64 Rss, Word64 Rtt)` 443

```
Rdd=vcmpyr(Rss,Rtt):sat
```

`Word64 Q6_P_vcmpyr_PP_sat(Word64 Rss, Word64 Rtt)` 443

```
Rxx+=vcmpyr(Rss,Rtt):sat
```

`Word64 Q6_P_vcmpyracc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 443

```
vcnegh
   Rdd=vcnegh(Rss,Rt)
```

`Word64 Q6_P_vcnegh_PR(Word64 Rss, Word32 Rt)` 381

```
vconj
   Rdd=vconj(Rss):sat
```

`Word64 Q6_P_vconj_P_sat(Word64 Rss)` 445

```
vcrotate
   Rdd=vcrotate(Rss,Rt)
```

`Word64 Q6_P_vcrotate_PR(Word64 Rss, Word32 Rt)` 447

```
vdmpy
   Rd=vdmpy(Rss,Rtt):<<1:rnd:sat
```

`Word32 Q6_R_vdmpy_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 516

```
Rd=vdmpy(Rss,Rtt):rnd:sat
```

`Word32 Q6_R_vdmpy_PP_rnd_sat(Word64 Rss, Word64 Rtt)` 516

```
Rdd=vdmpy(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vdmpy_PP_s1_sat(Word64 Rss, Word64 Rtt)` 513

```
Rdd=vdmpy(Rss,Rtt):sat
```

`Word64 Q6_P_vdmpy_PP_sat(Word64 Rss, Word64 Rtt)` 513

```
Rxx+=vdmpy(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vdmpyacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 513

```
Rxx+=vdmpy(Rss,Rtt):sat
```

`Word64 Q6_P_vdmpyacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 513

```
vdmpybsu
   Rdd=vdmpybsu(Rss,Rtt):sat
```

`Word64 Q6_P_vdmpybsu_PP_sat(Word64 Rss, Word64 Rtt)` 520

```
Rxx+=vdmpybsu(Rss,Rtt):sat
```

`Word64 Q6_P_vdmpybsuacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 520

```
vitpack
   Rd=vitpack(Ps,Pt)
```

`Word32 Q6_R_vitpack_pp(Byte Ps, Byte Pt)` 581

```
vlslh
   Rdd=vlslh(Rss,Rt)
```

`Word64 Q6_P_vlslh_PR(Word64 Rss, Word32 Rt)` 611

```
vlslw
   Rdd=vlslw(Rss,Rt)
```

`Word64 Q6_P_vlslw_PR(Word64 Rss, Word32 Rt)` 613

```
vlsrh
   Rdd=vlsrh(Rss,#u4)
```

`Word64 Q6_P_vlsrh_PI(Word64 Rss, Word32 Iu4)` 606

```
Rdd=vlsrh(Rss,Rt)
```

`Word64 Q6_P_vlsrh_PR(Word64 Rss, Word32 Rt)` 611

```
vlsrw
   Rdd=vlsrw(Rss,#u5)
```

`Word64 Q6_P_vlsrw_PI(Word64 Rss, Word32 Iu5)` 612

```
Rdd=vlsrw(Rss,Rt)
```

`Word64 Q6_P_vlsrw_PR(Word64 Rss, Word32 Rt)` 613

```
vmaxb
   Rdd=vmaxb(Rtt,Rss)
```

`Word64 Q6_P_vmaxb_PP(Word64 Rtt, Word64 Rss)` 383

```
vmaxh
   Rdd=vmaxh(Rtt,Rss)
```

`Word64 Q6_P_vmaxh_PP(Word64 Rtt, Word64 Rss)` 384

```
vmaxub
   Rdd=vmaxub(Rtt,Rss)
```

`Word64 Q6_P_vmaxub_PP(Word64 Rtt, Word64 Rss)` 383

```
vmaxuh
   Rdd=vmaxuh(Rtt,Rss)
```

`Word64 Q6_P_vmaxuh_PP(Word64 Rtt, Word64 Rss)` 384

```
vmaxuw
   Rdd=vmaxuw(Rtt,Rss)
```

`Word64 Q6_P_vmaxuw_PP(Word64 Rtt, Word64 Rss)` 389

```
vmaxw
   Rdd=vmaxw(Rtt,Rss)
```

`Word64 Q6_P_vmaxw_PP(Word64 Rtt, Word64 Rss)` 389

```
vminb
   Rdd=vminb(Rtt,Rss)
```

`Word64 Q6_P_vminb_PP(Word64 Rtt, Word64 Rss)` 390

```
vminh
   Rdd=vminh(Rtt,Rss)
```

`Word64 Q6_P_vminh_PP(Word64 Rtt, Word64 Rss)` 392

```
vminub
   Rdd=vminub(Rtt,Rss)
```

`Word64 Q6_P_vminub_PP(Word64 Rtt, Word64 Rss)` 390

```
vminuh
   Rdd=vminuh(Rtt,Rss)
```

`Word64 Q6_P_vminuh_PP(Word64 Rtt, Word64 Rss)` 392

```
vminuw
   Rdd=vminuw(Rtt,Rss)
```

`Word64 Q6_P_vminuw_PP(Word64 Rtt, Word64 Rss)` 397

```
vminw
   Rdd=vminw(Rtt,Rss)
```

`Word64 Q6_P_vminw_PP(Word64 Rtt, Word64 Rss)` 397

```
vmpybsu
   Rdd=vmpybsu(Rs,Rt)
```

`Word64 Q6_P_vmpybsu_RR(Word32 Rs, Word32 Rt)` 532

```
Rxx+=vmpybsu(Rs,Rt)
```

`Word64 Q6_P_vmpybsuacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 532

```
vmpybu
   Rdd=vmpybu(Rs,Rt)
```

`Word64 Q6_P_vmpybu_RR(Word32 Rs, Word32 Rt)` 532

```
Rxx+=vmpybu(Rs,Rt)
```

`Word64 Q6_P_vmpybuacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 532

```
vmpyeh
   Rdd=vmpyeh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpyeh_PP_s1_sat(Word64 Rss, Word64 Rtt)` 522

```
Rdd=vmpyeh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpyeh_PP_sat(Word64 Rss, Word64 Rtt)` 522

```
Rxx+=vmpyeh(Rss,Rtt)
```

`Word64 Q6_P_vmpyehacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 522

```
Rxx+=vmpyeh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpyehacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 522

```
Rxx+=vmpyeh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpyehacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 522

```
vmpyh
   Rd=vmpyh(Rs,Rt):<<1:rnd:sat
```

`Word32 Q6_R_vmpyh_RR_s1_rnd_sat(Word32 Rs, Word32 Rt)` 526

```
Rd=vmpyh(Rs,Rt):rnd:sat
```

`Word32 Q6_R_vmpyh_RR_rnd_sat(Word32 Rs, Word32 Rt)` 526

```
Rdd=vmpyh(Rs,Rt):<<1:sat
```

`Word64 Q6_P_vmpyh_RR_s1_sat(Word32 Rs, Word32 Rt)` 524

```
Rdd=vmpyh(Rs,Rt):sat
```

`Word64 Q6_P_vmpyh_RR_sat(Word32 Rs, Word32 Rt)` 524

```
Rxx+=vmpyh(Rs,Rt)
```

`Word64 Q6_P_vmpyhacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 524

```
Rxx+=vmpyh(Rs,Rt):<<1:sat
```

`Word64 Q6_P_vmpyhacc_RR_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 524

```
Rxx+=vmpyh(Rs,Rt):sat
```

`Word64 Q6_P_vmpyhacc_RR_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 524

```
vmpyhsu
   Rdd=vmpyhsu(Rs,Rt):<<1:sat
```

`Word64 Q6_P_vmpyhsu_RR_s1_sat(Word32 Rs, Word32 Rt)` 527

```
Rdd=vmpyhsu(Rs,Rt):sat
```

`Word64 Q6_P_vmpyhsu_RR_sat(Word32 Rs, Word32 Rt)` 527

```
Rxx+=vmpyhsu(Rs,Rt):<<1:sat
```

`Word64 Q6_P_vmpyhsuacc_RR_s1_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 527

```
Rxx+=vmpyhsu(Rs,Rt):sat
```

`Word64 Q6_P_vmpyhsuacc_RR_sat(Word64 Rxx, Word32 Rs, Word32 Rt)` 527

```
vmpyweh
   Rdd=vmpyweh(Rss,Rtt):<<1:rnd:sat
```

`Word64 Q6_P_vmpyweh_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 484

```
Rdd=vmpyweh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpyweh_PP_s1_sat(Word64 Rss, Word64 Rtt)` 484

```
Rdd=vmpyweh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpyweh_PP_rnd_sat(Word64 Rss, Word64 Rtt)` 484

```
Rdd=vmpyweh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpyweh_PP_sat(Word64 Rss, Word64 Rtt)` 484

```
Rxx+=vmpyweh(Rss,Rtt):<<1:rnd:sat
   Word64 Q6_P_vmpywehacc_PP_s1_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)
```

485

```
Rxx+=vmpyweh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpywehacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
Rxx+=vmpyweh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpywehacc_PP_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
Rxx+=vmpyweh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpywehacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
vmpyweuh
   Rdd=vmpyweuh(Rss,Rtt):<<1:rnd:sat
```

`Word64 Q6_P_vmpyweuh_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 488

```
Rdd=vmpyweuh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpyweuh_PP_s1_sat(Word64 Rss, Word64 Rtt)` 488

```
Rdd=vmpyweuh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpyweuh_PP_rnd_sat(Word64 Rss, Word64 Rtt)` 488

```
Rdd=vmpyweuh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpyweuh_PP_sat(Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpyweuh(Rss,Rtt):<<1:rnd:sat
   Word64 Q6_P_vmpyweuhacc_PP_s1_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)
```

489

```
Rxx+=vmpyweuh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpyweuhacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpyweuh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpyweuhacc_PP_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpyweuh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpyweuhacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
vmpywoh
   Rdd=vmpywoh(Rss,Rtt):<<1:rnd:sat
```

`Word64 Q6_P_vmpywoh_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 485

```
Rdd=vmpywoh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpywoh_PP_s1_sat(Word64 Rss, Word64 Rtt)` 485

```
Rdd=vmpywoh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpywoh_PP_rnd_sat(Word64 Rss, Word64 Rtt)` 485

```
Rdd=vmpywoh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpywoh_PP_sat(Word64 Rss, Word64 Rtt)` 485

```
Rxx+=vmpywoh(Rss,Rtt):<<1:rnd:sat
   Word64 Q6_P_vmpywohacc_PP_s1_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)
```

485

```
Rxx+=vmpywoh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpywohacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
Rxx+=vmpywoh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpywohacc_PP_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
Rxx+=vmpywoh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpywohacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 485

```
vmpywouh
   Rdd=vmpywouh(Rss,Rtt):<<1:rnd:sat
```

`Word64 Q6_P_vmpywouh_PP_s1_rnd_sat(Word64 Rss, Word64 Rtt)` 489

```
Rdd=vmpywouh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpywouh_PP_s1_sat(Word64 Rss, Word64 Rtt)` 489

```
Rdd=vmpywouh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpywouh_PP_rnd_sat(Word64 Rss, Word64 Rtt)` 489

```
Rdd=vmpywouh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpywouh_PP_sat(Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpywouh(Rss,Rtt):<<1:rnd:sat
   Word64 Q6_P_vmpywouhacc_PP_s1_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)
```

489

```
Rxx+=vmpywouh(Rss,Rtt):<<1:sat
```

`Word64 Q6_P_vmpywouhacc_PP_s1_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpywouh(Rss,Rtt):rnd:sat
```

`Word64 Q6_P_vmpywouhacc_PP_rnd_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
Rxx+=vmpywouh(Rss,Rtt):sat
```

`Word64 Q6_P_vmpywouhacc_PP_sat(Word64 Rxx, Word64 Rss, Word64 Rtt)` 489

```
vmux
   Rdd=vmux(Pu,Rss,Rtt)
```

`Word64 Q6_P_vmux_pPP(Byte Pu, Word64 Rss, Word64 Rtt)` 582

```
vnavgh
   Rd=vnavgh(Rt,Rs)
```

`Word32 Q6_R_vnavgh_RR(Word32 Rt, Word32 Rs)` 166

```
Rdd=vnavgh(Rtt,Rss)
```

`Word64 Q6_P_vnavgh_PP(Word64 Rtt, Word64 Rss)` 376

```
Rdd=vnavgh(Rtt,Rss):crnd:sat
```

`Word64 Q6_P_vnavgh_PP_crnd_sat(Word64 Rtt, Word64 Rss)` 376

```
Rdd=vnavgh(Rtt,Rss):rnd:sat
```

`Word64 Q6_P_vnavgh_PP_rnd_sat(Word64 Rtt, Word64 Rss)` 376

```
vnavgw
   Rdd=vnavgw(Rtt,Rss)
```

`Word64 Q6_P_vnavgw_PP(Word64 Rtt, Word64 Rss)` 379

```
Rdd=vnavgw(Rtt,Rss):crnd:sat
```

`Word64 Q6_P_vnavgw_PP_crnd_sat(Word64 Rtt, Word64 Rss)` 379

```
Rdd=vnavgw(Rtt,Rss):rnd:sat
```

`Word64 Q6_P_vnavgw_PP_rnd_sat(Word64 Rtt, Word64 Rss)` 379

```
vpmpyh
   Rdd=vpmpyh(Rs,Rt)
```

`Word64 Q6_P_vpmpyh_RR(Word32 Rs, Word32 Rt)` 534

```
Rxx^=vpmpyh(Rs,Rt)
```

`Word64 Q6_P_vpmpyhxacc_RR(Word64 Rxx, Word32 Rs, Word32 Rt)` 534

```
vraddh
   Rd=vraddh(Rss,Rtt)
```

`Word32 Q6_R_vraddh_PP(Word64 Rss, Word64 Rtt)` 371

```
vraddub
   Rdd=vraddub(Rss,Rtt)
```

`Word64 Q6_P_vraddub_PP(Word64 Rss, Word64 Rtt)` 369

```
Rxx+=vraddub(Rss,Rtt)
```

`Word64 Q6_P_vraddubacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 369

```
vradduh
   Rd=vradduh(Rss,Rtt)
```

`Word32 Q6_R_vradduh_PP(Word64 Rss, Word64 Rtt)` 371

```
vrcmpys
   Rd=vrcmpys(Rss,Rt):<<1:rnd:sat
```

`Word32 Q6_R_vrcmpys_PR_s1_rnd_sat(Word64 Rss, Word32 Rt)` 452

```
Rdd=vrcmpys(Rss,Rt):<<1:sat
```

`Word64 Q6_P_vrcmpys_PR_s1_sat(Word64 Rss, Word32 Rt)` 449

```
Rxx+=vrcmpys(Rss,Rt):<<1:sat
```

`Word64 Q6_P_vrcmpysacc_PR_s1_sat(Word64 Rxx, Word64 Rss, Word32 Rt)` 449

```
vrcnegh
   Rxx+=vrcnegh(Rss,Rt)
```

`Word64 Q6_P_vrcneghacc_PR(Word64 Rxx, Word64 Rss, Word32 Rt)` 381

```
vrcrotate
   Rdd=vrcrotate(Rss,Rt,#u2)
```

`Word64 Q6_P_vrcrotate_PRI(Word64 Rss, Word32 Rt, Word32 Iu2)` 455

```
Rxx+=vrcrotate(Rss,Rt,#u2)
   Word64 Q6_P_vrcrotateacc_PRI(Word64 Rxx, Word64 Rss, Word32 Rt, Word32 Iu2)
```

455

```
vrmaxh
   Rxx=vrmaxh(Rss,Ru)
```

`Word64 Q6_P_vrmaxh_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 385

```
vrmaxuh
   Rxx=vrmaxuh(Rss,Ru)
```

`Word64 Q6_P_vrmaxuh_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 385

```
vrmaxuw
   Rxx=vrmaxuw(Rss,Ru)
```

`Word64 Q6_P_vrmaxuw_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 387

```
vrmaxw
   Rxx=vrmaxw(Rss,Ru)
```

`Word64 Q6_P_vrmaxw_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 387

```
vrminh
   Rxx=vrminh(Rss,Ru)
```

`Word64 Q6_P_vrminh_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 393

```
vrminuh
   Rxx=vrminuh(Rss,Ru)
```

`Word64 Q6_P_vrminuh_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 393

```
vrminuw
   Rxx=vrminuw(Rss,Ru)
```

`Word64 Q6_P_vrminuw_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 395

```
vrminw
   Rxx=vrminw(Rss,Ru)
```

`Word64 Q6_P_vrminw_PR(Word64 Rxx, Word64 Rss, Word32 Ru)` 395

```
vrmpybsu
   Rdd=vrmpybsu(Rss,Rtt)
```

`Word64 Q6_P_vrmpybsu_PP(Word64 Rss, Word64 Rtt)` 518

```
Rxx+=vrmpybsu(Rss,Rtt)
```

`Word64 Q6_P_vrmpybsuacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 518

```
vrmpybu
   Rdd=vrmpybu(Rss,Rtt)
```

`Word64 Q6_P_vrmpybu_PP(Word64 Rss, Word64 Rtt)` 518

```
Rxx+=vrmpybu(Rss,Rtt)
```

`Word64 Q6_P_vrmpybuacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 518

```
vrmpyh
   Rdd=vrmpyh(Rss,Rtt)
```

`Word64 Q6_P_vrmpyh_PP(Word64 Rss, Word64 Rtt)` 529

```
Rxx+=vrmpyh(Rss,Rtt)
```

`Word64 Q6_P_vrmpyhacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 529

```
vrmpyweh
   Rdd=vrmpyweh(Rss,Rtt)
```

`Word64 Q6_P_vrmpyweh_PP(Word64 Rss, Word64 Rtt)` 506

```
Rdd=vrmpyweh(Rss,Rtt):<<1
```

`Word64 Q6_P_vrmpyweh_PP_s1(Word64 Rss, Word64 Rtt)` 506

```
Rxx+=vrmpyweh(Rss,Rtt)
```

`Word64 Q6_P_vrmpywehacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 506

```
Rxx+=vrmpyweh(Rss,Rtt):<<1
```

`Word64 Q6_P_vrmpywehacc_PP_s1(Word64 Rxx, Word64 Rss, Word64 Rtt)` 506

```
vrmpywoh
   Rdd=vrmpywoh(Rss,Rtt)
```

`Word64 Q6_P_vrmpywoh_PP(Word64 Rss, Word64 Rtt)` 506

```
Rdd=vrmpywoh(Rss,Rtt):<<1
```

`Word64 Q6_P_vrmpywoh_PP_s1(Word64 Rss, Word64 Rtt)` 506

```
Rxx+=vrmpywoh(Rss,Rtt)
```

`Word64 Q6_P_vrmpywohacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 506

```
Rxx+=vrmpywoh(Rss,Rtt):<<1
```

`Word64 Q6_P_vrmpywohacc_PP_s1(Word64 Rxx, Word64 Rss, Word64 Rtt)` 506

```
vrndwh
   Rd=vrndwh(Rss)
```

`Word32 Q6_R_vrndwh_P(Word64 Rss)` 542

```
Rd=vrndwh(Rss):sat
```

`Word32 Q6_R_vrndwh_P_sat(Word64 Rss)` 542

```
vrsadub
   Rdd=vrsadub(Rss,Rtt)
```

`Word64 Q6_P_vrsadub_PP(Word64 Rss, Word64 Rtt)` 399

```
Rxx+=vrsadub(Rss,Rtt)
```

`Word64 Q6_P_vrsadubacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 399

```
vsathb
   Rd=vsathb(Rs)
```

`Word32 Q6_R_vsathb_R(Word32 Rs)` 545

```
Rd=vsathb(Rss)
```

`Word32 Q6_R_vsathb_P(Word64 Rss)` 545

```
Rdd=vsathb(Rss)
```

`Word64 Q6_P_vsathb_P(Word64 Rss)` 548

```
vsathub
   Rd=vsathub(Rs)
```

`Word32 Q6_R_vsathub_R(Word32 Rs)` 545

```
Rd=vsathub(Rss)
```

`Word32 Q6_R_vsathub_P(Word64 Rss)` 545

```
Rdd=vsathub(Rss)
```

`Word64 Q6_P_vsathub_P(Word64 Rss)` 548

```
vsatwh
   Rd=vsatwh(Rss)
```

`Word32 Q6_R_vsatwh_P(Word64 Rss)` 545

```
Rdd=vsatwh(Rss)
```

`Word64 Q6_P_vsatwh_P(Word64 Rss)` 548

```
vsatwuh
   Rd=vsatwuh(Rss)
```

`Word32 Q6_R_vsatwuh_P(Word64 Rss)` 545

```
Rdd=vsatwuh(Rss)
```

`Word64 Q6_P_vsatwuh_P(Word64 Rss)` 548

```
vsplatb
   Rd=vsplatb(Rs)
```

`Word32 Q6_R_vsplatb_R(Word32 Rs)` 552

```
Rdd=vsplatb(Rs)
```

`Word64 Q6_P_vsplatb_R(Word32 Rs)` 552

```
vsplath
   Rdd=vsplath(Rs)
```

`Word64 Q6_P_vsplath_R(Word32 Rs)` 553

```
vspliceb
   Rdd=vspliceb(Rss,Rtt,#u3)
```

`Word64 Q6_P_vspliceb_PPI(Word64 Rss, Word64 Rtt, Word32 Iu3)` 554

```
Rdd=vspliceb(Rss,Rtt,Pu)
```

`Word64 Q6_P_vspliceb_PPp(Word64 Rss, Word64 Rtt, Byte Pu)` 554

```
vsubb
   Rdd=vsubb(Rss,Rtt)
```

`Word64 Q6_P_vsubb_PP(Word64 Rss, Word64 Rtt)` 402

```
vsubh
   Rd=vsubh(Rt,Rs)
```

`Word32 Q6_R_vsubh_RR(Word32 Rt, Word32 Rs)` 167

```
Rd=vsubh(Rt,Rs):sat
```

`Word32 Q6_R_vsubh_RR_sat(Word32 Rt, Word32 Rs)` 167

```
Rdd=vsubh(Rtt,Rss)
```

`Word64 Q6_P_vsubh_PP(Word64 Rtt, Word64 Rss)` 400

```
Rdd=vsubh(Rtt,Rss):sat
```

`Word64 Q6_P_vsubh_PP_sat(Word64 Rtt, Word64 Rss)` 400

```
vsubub
   Rdd=vsubub(Rtt,Rss)
```

`Word64 Q6_P_vsubub_PP(Word64 Rtt, Word64 Rss)` 402

```
Rdd=vsubub(Rtt,Rss):sat
```

`Word64 Q6_P_vsubub_PP_sat(Word64 Rtt, Word64 Rss)` 402

```
vsubuh
   Rd=vsubuh(Rt,Rs):sat
```

`Word32 Q6_R_vsubuh_RR_sat(Word32 Rt, Word32 Rs)` 167

```
Rdd=vsubuh(Rtt,Rss):sat
```

`Word64 Q6_P_vsubuh_PP_sat(Word64 Rtt, Word64 Rss)` 400

```
vsubw
   Rdd=vsubw(Rtt,Rss)
```

`Word64 Q6_P_vsubw_PP(Word64 Rtt, Word64 Rss)` 403

```
Rdd=vsubw(Rtt,Rss):sat
```

`Word64 Q6_P_vsubw_PP_sat(Word64 Rtt, Word64 Rss)` 403

```
vsxtbh
   Rdd=vsxtbh(Rs)
```

`Word64 Q6_P_vsxtbh_R(Word32 Rs)` 556

```
vsxthw
   Rdd=vsxthw(Rs)
```

`Word64 Q6_P_vsxthw_R(Word32 Rs)` 556

```
vtrunehb
   Rd=vtrunehb(Rss)
```

`Word32 Q6_R_vtrunehb_P(Word64 Rss)` 559

```
Rdd=vtrunehb(Rss,Rtt)
```

`Word64 Q6_P_vtrunehb_PP(Word64 Rss, Word64 Rtt)` 559

```
vtrunewh
   Rdd=vtrunewh(Rss,Rtt)
```

`Word64 Q6_P_vtrunewh_PP(Word64 Rss, Word64 Rtt)` 559

```
vtrunohb
   Rd=vtrunohb(Rss)
```

`Word32 Q6_R_vtrunohb_P(Word64 Rss)` 559

```
Rdd=vtrunohb(Rss,Rtt)
```

`Word64 Q6_P_vtrunohb_PP(Word64 Rss, Word64 Rtt)` 559

```
vtrunowh
   Rdd=vtrunowh(Rss,Rtt)
```

`Word64 Q6_P_vtrunowh_PP(Word64 Rss, Word64 Rtt)` 559

```
vxaddsubh
   Rdd=vxaddsubh(Rss,Rtt):rnd:>>1:sat
```

`Word64 Q6_P_vxaddsubh_PP_rnd_rs1_sat(Word64 Rss, Word64 Rtt)` 424

```
Rdd=vxaddsubh(Rss,Rtt):sat
```

`Word64 Q6_P_vxaddsubh_PP_sat(Word64 Rss, Word64 Rtt)` 424

```
vxaddsubw
   Rdd=vxaddsubw(Rss,Rtt):sat
```

`Word64 Q6_P_vxaddsubw_PP_sat(Word64 Rss, Word64 Rtt)` 426

```
vxsubaddh
   Rdd=vxsubaddh(Rss,Rtt):rnd:>>1:sat
```

`Word64 Q6_P_vxsubaddh_PP_rnd_rs1_sat(Word64 Rss, Word64 Rtt)` 424

```
Rdd=vxsubaddh(Rss,Rtt):sat
```

`Word64 Q6_P_vxsubaddh_PP_sat(Word64 Rss, Word64 Rtt)` 424

```
vxsubaddw
   Rdd=vxsubaddw(Rss,Rtt):sat
```

`Word64 Q6_P_vxsubaddw_PP_sat(Word64 Rss, Word64 Rtt)` 426

```
vzxtbh
   Rdd=vzxtbh(Rs)
```

`Word64 Q6_P_vzxtbh_R(Word32 Rs)` 560

```
vzxthw
   Rdd=vzxthw(Rs)
```

`Word64 Q6_P_vzxthw_R(Word32 Rs)` 560

### X

```
xor
   Pd=xor(Ps,Pt)
```

`Byte Q6_p_xor_pp(Byte Ps, Byte Pt)` 201

```
Rd=xor(Rs,Rt)
```

`Word32 Q6_R_xor_RR(Word32 Rs, Word32 Rt)` 155

```
Rdd=xor(Rss,Rtt)
```

`Word64 Q6_P_xor_PP(Word64 Rss, Word64 Rtt)` 339

```
Rx&=xor(Rs,Rt)
```

`Word32 Q6_R_xorand_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx^=xor(Rs,Rt)
```

`Word32 Q6_R_xorxacc_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rx|=xor(Rs,Rt)
```

`Word32 Q6_R_xoror_RR(Word32 Rx, Word32 Rs, Word32 Rt)` 342

```
Rxx^=xor(Rss,Rtt)
```

`Word64 Q6_P_xorxacc_PP(Word64 Rxx, Word64 Rss, Word64 Rtt)` 340

### Z

```
zxtb
   Rd=zxtb(Rs)
```

`Word32 Q6_R_zxtb_R(Word32 Rs)` 168

```
zxth
   Rd=zxth(Rs)
```

`Word32 Q6_R_zxth_R(Word32 Rs)` 168
