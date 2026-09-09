# 9 PMU Events

The Hexagon processor can collect execution statistics on the applications it executes. The statistics summarize the types of Hexagon processor events that occur while the application runs.

Execution statistics are collected in hardware or software:

- Statistics are collected in hardware with the performance monitor unit (PMU), which is defined as part of the Hexagon processor architecture.
- Statistics are collected in software using the Hexagon simulator. The simulator statistics are presented in the same format used by the PMU.

Execution statistics are expressed in terms of processor events. This chapter defines the event symbols, along with their associated numeric codes.

NOTE: Because the types of execution events vary across the Hexagon processor versions, different types of statistics are collected for each version. This chapter lists the event symbols defined for version V73.

## 9.1 V73 processor event symbols

Table 9-1 defines the symbols that represent processor events for the V73 Hexagon processor.

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x1 | COUNTER0_OVERFLOW | Event detected by counter1 to build an effective 64-bit counter. |
| 0x2 | COUNTER2_OVERFLOW | Event detected by counter3 to build an effective 64-bit counter. |
| 0x3 | COMMITTED_PKT_ANY | Number of packets that are committed by any thread. Packets are executed. |
| 0x4 | COMMITTED_PKT_BSB | Number of packets that are committed two cycles after an earlier packet in the same thread. |
| 0x5 | COUNTER4_OVERFLOW | Event detected by counter5 to build an effective 64-bit counter. |
| 0x6 | COUNTER6_OVERFLOW | Event detected by counter7 to build an effective 64-bit counter. |
| 0x7 | COMMITTED_PKT_B2B | Number of packets that are committed one cycle after the earlier packet in the same thread. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x8 | COMMITTED_PKT_SMT | Number of packets that are committed on the SMT threads. Includes the second, third, and fourth packets that are committed in one cycle. |
| 0xa | CYCLES_5_THREAD_RUNNING | Processor cycles that exactly five threads are running. Running means that the threads are not in the Wait or Stop state. |
| 0xb | CYCLES_6_THREAD_RUNNING | Processor cycles that exactly six threads are running. Running means that the threads are not in the Wait or Stop state. |
| 0xc | COMMITTED_PKT_T0 | Number of packets that are committed by thread 0. Packets are executed. |
| 0xd | COMMITTED_PKT_T1 | Number of packets that are committed by thread 1. Packets are executed. |
| 0xe | COMMITTED_PKT_T2 | Number of packets that are committed by thread 2. Packets are executed. |
| 0xf | COMMITTED_PKT_T3 | Number of packets that are committed by thread 3. Packets are executed. |
| 0x10 | COMMITTED_PKT_T4 | Number of packets that are committed by thread 4. Packets are executed. |
| 0x11 | COMMITTED_PKT_T5 | Number of packets that are committed by thread 5. Packets are executed. |
| 0x12 | ICACHE_DEMAND_MISS | Number of I-cache cacheable demand primary or secondary misses. Includes secondary misses. |
| 0x13 | DCACHE_DEMAND_MISS | Number of D-cache cacheable demand primary or secondary misses. Includes dczero stalls. Excludes uncacheables, prefetches, and no-allocate store misses. |
| 0x14 | DCACHE_STORE_MISS | Number of D-cache cacheable store misses. |
| 0x15 | COMMITTED_PKT_T6 | Thread 6 committed a packet. Packets are executed. |
| 0x16 | COMMITTED_PKT_T7 | Thread 7 committed a packet. Packets are executed. |
| 0x17 | CU_PKT_READY_NOT_DISPATCHED | Packets are ready at the CU scheduler but are not scheduled because either the thread of the scheduler thread is not picked or there is an inter-cluster resource conflict. |
| 0x18 | COMMITTED_PKT_5_THREAD_RUNNING | Number of committed packets with five threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x19 | COMMITTED_PKT_6_THREAD_RUNNING | Number of committed packets with six threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x1a | COMMITTED_PKT_7_THREAD_RUNNING | Number of committed packets with seven threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x1b | COMMITTED_PKT_8_THREAD_RUNNING | Number of committed packets with eight threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x1c | IU_L1S_ACCESS | Number of IU L1S loads. Includes demands or prefetches. |
| 0x1d | IU_L1S_PREFETCH | Number of IU L1S prefetches. |
| 0x1e | IU_L1S_AXIS_STALL | Number of IU L1S stalls due to an AXI slave. |
| 0x1f | IU_L1S_NO_GRANT | IU request to L1S, and no grant from the vector unit. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x20 | ANY_IU_REPLAY | Any IU stall other than an I-cache miss. Includes a jump register stall, fetchcross stall, ITLB miss stall, and so on. Excludes a CU replay. |
| 0x21 | ANY_DU_REPLAY | Any DU replay. Includes a bank conflict, store buffer full, and so on. Excludes a stall due to a cache miss. |
| 0x22 | CYCLES_7_THREAD_RUNNING | Processor cycles that exactly seven threads are running. Running means that the threads are not in Wait or Stop mode. |
| 0x23 | ISSUED_PACKETS | Speculatively issued packets were delivered from an IU. |
| 0x24 | LOOPCACHE_PACKETS | Committed packets were cloned from the packet queue during a pinned hardware loop. |
| 0x25 | COMMITTED_PKT_1_THREAD_RUNNING | Number of committed packets with one thread running. Running means the thread is not in Wait or Stop mode. |
| 0x26 | COMMITTED_PKT_2_THREAD_RUNNING | Number of committed packets with two threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x27 | COMMITTED_PKT_3_THREAD_RUNNING | Number of committed packets with three threads running. Running means that the threads are not in Wait or Stop mode. |
| 0x28 | THREAD_LMH_THROTTLE | For a specific thread, the sustained power exceeds the limits management threshold and limits budget threshold. Results in throttling that is based on thread priority. |
| 0x29 | LMH_THROTTLE | Throttling is based on the value of the peak current that is over the current limits of LMH. |
| 0x2a | COMMITTED_INSTS | Number of committed instructions. Increments by up to eight per cycle. Duplex of two instructions counts as two instructions. Does not include end loops. |
| 0x2b | COMMITTED_TC1_INSTS | Number of committed TC1 class instructions. Increments by up to eight per cycle. Duplex of two TC1 instructions counts as two separate TC1 instructions. Does not include NOP instructions. |
| 0x2c | COMMITTED_PRIVATE_INSTS | Number of committed instructions that have per-cluster (private) execution resources. Increments by up to eight per cycle. Duplex of two private instructions counts as two private instructions. |
| 0x2d | GLOBAL_POWERLIMITS_OVER | Sustained global power that exceeds the overall global limits management threshold and limits the budget threshold. Causes the thread-specific LMH to engage. |
| 0x2e | CYCLES_8_THREAD_RUNNING | Processor cycles that exactly eight threads are running. Running means that the threads are not in Wait or Stop mode. |
| 0x2f | COMMITTED_PKT_4_THREAD_RUNNING | Number of committed packets with four threads running. Running means that the threads are not in Stop or Wait mode. |
| 0x30 | COMMITTED_LOADS | Number of committed load instructions. Includes cached and uncached. Increments by two for dual loads. Excludes prefetches, memory operations, and coprocessor loads. |
| 0x31 | COMMITTED_STORES | Number of committed store instructions. Includes cached and uncached. Increments by two for dual stores. Excludes memory operations and coprocessor stores. |
| 0x32 | COMMITTED_MEMOPS | Number of committed memory operations instructions. Cached or uncached. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x33 | COMMITTED_NOPS | Number of committed NOPs. |
| 0x34 | ISSUED_INSTS | Speculatively issued instructions delivered from the IU. |
| 0x35 | DISPATCHED_PACKETS | Number of packets that the CU dispatched. NOP instructions are squashed. |
| 0x36 | DISPATCHED_INSTS | Number of instructions that the CU dispatched. |
| 0x37 | COMMITTED_PROGRAM_FLOW_INSTS | Number of committed packets that contain a program flow instruction. Includes CR jumps, endloop, J, JR, dealloc_return, system/trap, superset of event 56. Dual jumps count as two jumps. |
| 0x38 | COMMITTED_PKT_CHANGED_FLOW | Number of committed packets that resulted in a change of flow. Any taken jump. Includes endloop and dealloc_return. |
| 0x39 | COMMITTED_PKT_ENDLOOP | Number of committed packets containing an end loop that was taken. |
| 0x3a | PST_USED_P0P1BUSY | Number of times a store port was used when p0 and p1 were both occupied. Only increments when store port is present. |
| 0x3b | CYCLES_1_THREAD_RUNNING | Processor cycles that exactly one thread is running. Running means the thread is not in Wait or Stop mode. |
| 0x3c | CYCLES_2_THREAD_RUNNING | Processor cycles that exactly two threads are running. Running means that the threads are not in Wait or Stop mode. |
| 0x3d | CYCLES_3_THREAD_RUNNING | Processor cycles that exactly three threads are running. Running means that the threads are not in Wait or Stop mode. |
| 0x3e | CYCLES_4_THREAD_RUNNING | Processor cycles that exactly four threads are running. Running means that the threads are not in Wait or Stop mode. |
| 0x3f | AXI_LINE128_READ_REQUEST | Number of 128-byte line read requests issued by the primary AXI master. Includes all interleaved requests. |
| 0x40 | AXI_READ_REQUEST | All read requests issued by the primary AXI master. Includes full lines, partial lines, and all interleaved requests. |
| 0x41 | AXI_LINE32_READ_REQUEST | Number of 32-byte line read requests issued by the primary AXI master. Includes all interleaved requests. |
| 0x42 | AXI_WRITE_REQUEST | All write requests issued by the primary AXI master. Includes full lines, partial lines, and all interleaved requests. |
| 0x43 | AXI_LINE32_WRITE_REQUEST | Number of 32-byte line write requests issued by the primary AXI master. Includes all interleaved requests. All bytes are valid. |
| 0x44 | AHB_READ_REQUEST | Number of read requests issued by the AHB master. |
| 0x45 | AHB_WRITE_REQUEST | Number of write requests issued by the AHB master. |
| 0x46 | AXI_LINE128_WRITE_REQUEST | Number of 128-byte line write requests issued by the primary AXI master. Includes all interleaved requests. All bytes are valid. |
| 0x47 | AXI_SLAVE_MULTI_BEAT_ACCESS | Number of AXI slave multi-beat accesses. |
| 0x48 | AXI_SLAVE_SINGLE_BEAT_ACCESS | Number of AXI slave single-beat accesses. |
| 0x49 | AXI2_READ_REQUEST | All read requests issued by the secondary AXI master. Includes full lines and partial lines. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x4a | AXI2_LINE32_READ_REQUEST | Number of 32-byte line read requests issued by the secondary AXI master. |
| 0x4b | AXI2_WRITE_REQUEST | All write requests issued by the secondary AXI master. Includes full lines and partial lines. |
| 0x4c | AXI2_LINE32_WRITE_REQUEST | Number of 32-byte line write requests issued by the secondary AXI master. |
| 0x4d | AXI2_CONGESTION | Secondary AXI command or data queue is full. An operation is stuck at the head of the secondary AXI master command queue. |
| 0x50 | COMMITTED_FPS | Number of committed floating point instructions. Increments by two for dual floating-point operations. Excludes conversions. |
| 0x51 | REDIRECT_BIMODAL_MISPREDICT | Mispredicted bimodal branch direction caused a control flow redirect. |
| 0x52 | REDIRECT_TARGET_MISPREDICT | Mispredicted branch target caused a control flow redirect. Includes an RAS mispredict, and HintJR mispredict. Excludes indirect jumps and calls other than JUMPR R31 returns. Excludes direction mispredicts. |
| 0x53 | REDIRECT_LOOP_MISPREDICT | Mispredicted hardware loop end caused a control flow redirect. Can only occur when the loop has few packets and the loop count is 2 or less. |
| 0x54 | REDIRECT_MISC | Control flow is redirected for a reason other than events 81, 82, and 83. Includes exceptions, traps, interrupts, non-R31 jumps, multiple initialization loops in flight, and so on. |
| 0x55 | AXI_LINE256_WRITE_REQUEST | Number of 256-byte line write requests issued by the AXI master. All bytes are valid. |
| 0x56 | NUM_PACKET_CRACKED | Number of packets that cracked. |
| 0x58 | JTLB_MISS | Instruction or data address translation request was missed in the JTLB. |
| 0x5a | COMMITTED_PKT_RETURN | Number of committed return instructions. Includes canceled returns. |
| 0x5b | COMMITTED_PKT_INDIRECT_JUMP | Number of committed indirect jumps or call instructions. Includes canceled instructions. Does not include JUMPR R31 returns. |
| 0x5c | COMMITTED_BIMODAL_BRANCH_INSTS | Number of committed bimodal branches. Includes *.old and *.new. Increments by two for dual jumps. |
| 0x5f | VTCM_FIFO_FULL_CYCLES | Cycles cluster can be issued when the VTCM FIFO queue is full. |
| 0x60 | DU_STORE_BUFFER_COALESCED | Number of times an incoming store was coalesced into an existing valid store buffer entry. Each valid store buffer entry is dword-aligned. |
| 0x61 | DU_L1S_LOAD_ACCESS | Number of scalar load accesses to L1S. |
| 0x62 | ICACHE_ACCESS | Number of I-cacheline fetches. |
| 0x63 | BTB_HIT | Number of branch target buffer hits. |
| 0x64 | BTB_MISS | Number of branch target buffer misses. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x65 | IU_DEMAND_SECONDARY_MISS | Number of I-cache secondary misses. |
| 0x67 | FAST_FETCH_KILLED | Number of fast fetches that were killed (after an I-cache access). |
| 0x69 | FETCHED_PACKETS_DROPPED | Number of packets that are dropped because the IU cannot deliver them to the CU. |
| 0x6b | IU_PREFETCHES_SENT_TO_L2 | Number of IU prefetches sent to the L2 cache. Includes cachelines not dropped by the L2 cache. Excludes replayed prefetches and only counts prefetches the L2 accepts. Excludes IU prefetches that are sent to L2 ITCM. |
| 0x6c | ITLB_MISS | Number of ITLB misses that go to JTLB. |
| 0x72 | FETCH_2_CYCLE | Number of two-cycle fetches in an IU (returns, loop end, fall through, BTB). |
| 0x73 | FETCH_3_CYCLE | Number of three-cycle fetches in an IU. |
| 0x75 | L2_IU_SECONDARY_MISS | Number of L2 secondary misses from an IU. |
| 0x76 | L2_IU_ACCESS | Number of L2 cacheable access from an IU. Includes any access to the L2 cache that was the result of an IU command, either demand or L1 prefetch access. Excludes any prefetches generated in the L2 cache. Excludes L2fetch, TCM accesses, and uncacheables. Address must target the primary AXI master. |
| 0x77 | L2_IU_MISS | Number of L2 misses from an IU. Of the events qualified by 0x76, the event that resulted in an L2 miss (demand miss or L1 prefetch miss). An L2 miss is any condition that prevents the immediate return of data to the IU, excluding pipeline conflicts. |
| 0x78 | L2_IU_PREFETCH_ACCESS | Number of prefetches from an IU to the L2 cache. Any IU prefetch access sent to the L2 cache. Access must be L2 cacheable and target the primary AXI. Does not include L2 fetch-generated accesses. |
| 0x79 | L2_IU_PREFETCH_MISS | Number of L2 misses that were IU prefetches. Of the events qualified by 0x78, the events that resulted in an L2 miss. |
| 0x7c | L2_DU_READ_ACCESS | Number of L2 cacheable read accesses from a DU. Any read access from the DU that might cause a lookup in the L2 cache. Includes loads, L1 prefetches, dcfetches. Excludes the initial L2fetch command, uncacheables, TCM accesses, and coprocessor loads. Must target the primary AXI master. |
| 0x7d | L2_DU_READ_MISS | Number of L2 read misses from a DU. Of the events qualified by 0x7C, any event that resulted in an L2 miss (that is, the line is not previously allocated in the L2 cache and is fetched from the backing memory). |
| 0x7e | L2FETCH_ACCESS | Number of L2 fetch accesses from a DU. Any access to the L2 cache from the L2 prefetch engine that was initiated by programming the L2Fetch engine. |
| 0x7f | L2FETCH_MISS | Number of L2 fetch misses from a programmed inquiry. Of the events qualified by 0x7E, the event that resulted in an L2 miss (that is, the line is not previously allocated in the L2 cache and is fetched from the backing memory). |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x81 | L2_ACCESS | Requests to the L2 cache. Does not include internally generated accesses like L2 fetch, however the programming of the L2Fetch engine is counted. All accesses to odd interleave or even interleave are counted. Can be L2 cacheable or TCM. |
| 0x82 | L2_PIPE_CONFLICT_STALL | Request is not taken by the L2 cache due to a pipe conflict. The conflict can be a tag bank, data bank, or other pipeline conflict. |
| 0x83 | L2_TAG_ARRAY_CONFLICT | Of the items in event 130, the items caused by a conflict with the tag array. |
| 0x87 | TCM_DU_ACCESS | Number of TCM accesses from a DU. DU access to the L2 TCM space. Excludes HVX requests. |
| 0x88 | TCM_DU_READ_ACCESS | Number of TCM read accesses from a DU. DU read access to the L2 TCM space. Includes HVX requests. |
| 0x89 | TCM_IU_ACCESS | Number of TCM accesses from an IU. IU access to the L2 TCM space. |
| 0x8a | L2_CASTOUT | L2 cache evicts a dirty line due to an allocation. This event is not triggered on cache operations. |
| 0x8b | L2_DU_STORE_ACCESS | Number of L2 cacheable store access from a DU. Any store access from the DU that might cause a lookup in the L2 cache. Excludes cache operations, uncacheables, TCM, and coprocessor stores. Must target the primary AXI master. |
| 0x8c | L2_DU_STORE_MISS | Number of L2 misses from a DU. Of the events qualified by 0x8B, the events that resulted in a miss. Specifically, the cases where the line is not in the cache or a coalesce buffer. |
| 0x8d | L2_DU_PREFETCH_ACCESS | Number of L2 prefetch accesses from a DU. Of the events qualified by 0x7C, the events that are dcfetch and dhwprefetch. These L2 cacheable events target the primary AXI master. |
| 0x8e | L2_DU_PREFETCH_MISS | Number of L2 prefetch misses from a DU. Of the events qualified by 0x8D, the events that missed the L2 cache. |
| 0x90 | L2_DU_LOAD_SECONDARY_MISS | Number of L2 load secondary misses from a DU. Hit a busy line in the scoreboard, which prevented a return. A busy condition can include pipeline bubbles caused by back-to-back loads, like L1 UC loads. |
| 0x91 | L2FETCH_COMMAND | Number of L2fetch commands. Excludes L2 fetch stop commands. |
| 0x92 | L2FETCH_COMMAND_KILLED | L2 fetch command was killed because a stop command was issued. Increments once for each L2 fetch command that is killed. If multiple commands are queued to the L2Fetch engine, the kill of each command is recorded. |
| 0x93 | L2FETCH_COMMAND_OVERWRITE | L2 fetch command was overwritten. Kills an old L2 fetch command and replaces it with a new command. |
| 0x94 | L2FETCH_ACCESS_CREDIT_FAIL | L2 fetch access cannot get a credit. L2 fetch is blocked due to a missing L2 fetch or L2 evict credit. |
| 0x95 | AXI_SLAVE_READ_BUSY | AXI slave read access hit a busy line. |
| 0x96 | AXI_SLAVE_WRITE_BUSY | AXI slave write access hit a busy line. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x97 | L2_ACCESS_EVEN | Of the events in 0x81, number of accesses made to the even L2 cache. |
| 0x98 | CLADE_HIGH_PRIO_L2_ACCESS | Number of IU or DU requests for a high-priority CLADE region. Not counted for an L2 fetch. |
| 0x99 | CLADE_LOW_PRIO_L2_ACCESS | Number of IU or DU requests for a low-priority CLADE region. Not counted for an L2 fetch. |
| 0x9a | CLADE_HIGH_PRIO_L2_MISS | Number of CLADE high-priority L2 accesses that missed in the L2 cache. |
| 0x9b | CLADE_LOW_PRIO_L2_MISS | Number of CLADE low-priority L2 accesses that missed in the L2 cache. |
| 0x9c | CLADE_HIGH_PRIO_EXCEPTION | CLADE high-priority decode that had an exception. |
| 0x9d | CLADE_LOW_PRIO_EXCEPTION | CLADE low-priority decode that had an exception. |
| 0x9e | AXI2_SLAVE_READ_BUSY | AXI secondary slave read access hit a busy line. |
| 0x9f | AXI2_SLAVE_WRITE_BUSY | AXI secondary slave write access hit a busy line. |
| 0xa0 | ANY_DU_STALL | Any DU stall. Increments once when the thread has a DU stall (D-cache miss or DTLB miss). |
| 0xa1 | DU_BANK_CONFLICT_REPLAY | DU bank conflict replay. Dual memory access to same bank, but different lines. |
| 0xa2 | DU_CREDIT_REPLAY | Number of times a packet took a replay because insufficient QoS DU credits were available. |
| 0xa3 | L2_FIFO_FULL_REPLAY | Number of L2 even or odd FIFO full replays. |
| 0xa4 | DU_STORE_BUFFER_FULL_REPLAY | Number of DU replays because a demand load access hit in the store buffer. |
| 0xa7 | DU_SNOOP_REQUEST | Number of DU snoop requests that were accepted. |
| 0xa8 | DU_FILL_REPLAY | Fill has an index conflict with an instruction from the same thread in the pipeline. Fills and demands might be from different threads if there is a prefetch from the deferral queue, or if a fill has not be acknowledged for very long and forces itself into the pipeline. |
| 0xa9 | PST_3STORETYPE_SBCONF_REPLAY | Number of times a packet on the lower priority cluster had to replay because one cluster had a dual store and the other cluster had a single store or a memop. Only increments when store port is present. |
| 0xac | DU_READ_TO_L2 | Number of DU reads to L2 cache. Total of everything that brings data from the L2 array. Includes prefetches (dcfetch and hwprefetch). Excludes coprocessor loads. |
| 0xad | DU_WRITE_TO_L2 | Number of DU writes to L2 cache. Total of everything that is written out of the DU to the L2 array. Includes dczeroa. Excludes dcclean, dccleaninv, tag writes, and coprocessor stores. |
| 0xae | PST_3LDST_L2FIFOCONF_REPLAY | Number of times a packet on la ower priority cluster had to replay because one cluster had a dual uncacheable loads and the other cluster had a single store or the one cluster had a dual store and other cluster had a load miss. Only increments when the store port is present. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0xaf | DCZERO_COMMITTED | Dczeroa instruction was committed. |
| 0xb0 | L2ITCM_IU_READ | Number of ITCM accesses from an IU. Includes IU demand fetches and IU prefetches. This event is not included in any other L2 events. |
| 0xb1 | L2ITCM_DU_READ | Number of L2 ITCM read accesses from a DU. Includes all demands and prefetches. This event is not included in any other L2 events. |
| 0xb2 | L2ITCM_DU_WRITE | Number of L2 ITCM write accesses from a DU. Includes stores and dczeroa events. Does not include any cache operations. This event is not included in other L2 events. |
| 0xb3 | DTLB_MISS | DTLB miss that goes to JTLB. When both slots miss to different pages, increments by two. When both slots miss to the same page, only count S1 because S1 goes first and fills for S0. |
| 0xb4 | L2ITCM_BIMODAL_WRITES_SUCCESS | Number of successful bimodal writes into L2 ITCM. |
| 0xb6 | STORE_BUFFER_HIT_REPLAY | Store buffer hit is replayed because a packet with two stores is going to the same bank but different cachelines, followed by a load from an address that was pushed into the store buffer. |
| 0xb7 | STORE_BUFFER_FORCE_REPLAY | Store buffer must drain, forcing the current packet to replay. Typically occurs on a cache index match between the current packet and store buffer. Can also store a buffer timeout. |
| 0xb8 | TAG_WRITE_CONFLICT_REPLAY | Number of inter-cluster tag write conflicts. |
| 0xb9 | SMT_BANK_CONFLICT | Number of inter-thread SMT bank conflicts. |
| 0xba | PORT_CONFLICT_REPLAY | Number of all port conflict replays, including the same cluster replays caused by high-priority fills and store buffer force drains. Includes inter-cluster replays. |
| 0xbb | L2ITCM_BIMODAL_WRITES_DROPPED | Number of bimodal writes into L2 ITCM that were dropped. |
| 0xbc | L2ITCM_IU_PREFETCH_READ | Number of ITCM accesses from IU prefetches. Includes only prefetches from an IU. This event is included in event 176. It is not included in any other L2 events. |
| 0xbd | PAGE_CROSS_REPLAY | Page cross from a valid packet that caused a replay. Excludes pdkill packets. Counts twice if both slots cause a page cross. |
| 0xbe | PST_STORE_SENTON_OTHPORT | Number of times a slot 0 store was sent to the other store buffer because the other cluster had a slot 1 store or memop. Only increments when the store port is present. |
| 0xbf | DU_DEMAND_SECONDARY_MISS | Number of DU demand secondary misses. |
| 0xc0 | DU_MISC_REPLAY | DU replays are not counted by other replay events. This event counts every time ANY_DU_REPLAY counts and no other DU replay event counts. |
| 0xc1 | GUARDBUF_SETMATCH_CRACKING_REPLAY | Number of replays taken by a younger access due to an index match with a guard buffer entry. If the younger access hits in D$, only the guard buffer entry of the other thread is checked. Otherwise, an index match with the guard buffer entry of either thread results in this replay. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0xc2 | DU_STATE_REPLAY | Number of times an access replayed because the access one cycle ahead of it was allocating or invalidating a way in the same index. |
| 0xc3 | DCFETCH_COMMITTED | Number of dcfetches that were committed. Includes hits and drops. Does not include convert-to-prefetches. |
| 0xc4 | DCFETCH_HIT | Number of dcfetch hits in D-cache. Includes hitting valid or reserved lines. |
| 0xc5 | DCFETCH_MISS | Number of dcfetches missed in L1 cache. Counts the dcfetches issued to L2 FIFO. |
| 0xc6 | DCACHE_EVICTION_IN_PIPE_REPLAY | Number of replays taken by a packet because an eviction in progress is occupying the pipe. |
| 0xc7 | STBUF_MATCH_PARTIAL_CRACK_REPLAY | Number of replays taken by a partial crack store due to a dword match with an existing store buffer entry. |
| 0xc8 | DU_LOAD_UNCACHEABLE | Load instructions with addresses uncacheable in the L1 cache |
| 0xc9 | DU_DUAL_LOAD_UNCACHEABLE | Packets where both loads have addresses uncacheable in th e L1 cache |
| 0xca | DU_STORE_UNCACHEABLE | Store instructions with addresses uncacheble in the L1 cache |
| 0xcb | DU_STORE_RELEASE_CREDIT_STALL | Stall occurs because there are not enough credits from the store release. |
| 0xcd | AXI_LINE256_READ_REQUEST | Number of 256-byte line read requests issued by the AXI master. All bytes are valid. |
| 0xce | AXI_LINE64_READ_REQUEST | Number of 64-byte line read requests issued by the primary AXI master. Includes all interleaved requests. |
| 0xcf | AXI_LINE64_WRITE_REQUEST | Number of 64-byte line write requests issued by the primary AXI master. Includes all interleaved requests. All bytes are valid. |
| 0xd1 | AHB_8_READ_REQUEST | Number of 8-byte read requests issued by the AHB. |
| 0xd3 | L2FETCH_COMMAND_PAGE_TERMINATION | L2fetch command terminated because it cannot get a page translation from VA to PA. Includes terminations due to permission errors. That is, an address translation can fail because the VA to PA is not in the TLB, or the properties in the translation are not acceptable and the command terminates. |
| 0xd5 | L2_DU_STORE_COALESCE | Number of events from 139 that were coalesced |
| 0xd6 | L2_STORE_LINK | Number of times a new store links to something else in the scoreboard. |
| 0xd7 | L2_SCOREBOARD_70_PERCENT_FULL | Increments by one for every cycle where the L2 scoreboard is at least 70% full. For a 32-entry scoreboard, 23 or more entries are consumed. This event continues to count even if the scoreboard is more than 80% full. For more than one interleave, this event considers only the scoreboard that has the most entries consumed. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0xd8 | L2_SCOREBOARD_80_PERCENT_FULL | Increments by one for every cycle where the L2 scoreboard is at least 80% full. For a 32-entry scoreboard, 26 or more entries are consumed. This event continues to count even if the scoreboard is more than 90% full. For more than one interleave, this event considers only the scoreboard that has the most entries consumed. |
| 0xd9 | L2_SCOREBOARD_90_PERCENT_FULL | Increments by one for every cycle where the L2 scoreboard is at least 90% full. For a 32-entry scoreboard, 29 or more entries are consumed. For more than one interleave, this event considers only the scoreboard that has the most entries consumed. |
| 0xda | L2_SCOREBOARD_FULL_REJECT | L2 scoreboard is too full to accept a selector request, and the selector has a request. |
| 0xdc | L2_EVICTION_BUFFERS_FULL | Counts every cycle when all eviction buffers in any interleave are occupied. |
| 0xdd | AHB_MULTI_BEAT_READ_REQUEST | Number of 32-byte multi-beat read requests issued by the AHB. |
| 0xdf | L2_DU_LOAD_SECONDARY_MISS_ON_SW_PREFETCH | Of the events in 0x90, the events where the primary miss was a DC fetch or L2 fetch. |
| 0xe0 | L2FETCH_DROP | L2 fetch data dropped because a previous eviction has not completed. |
| 0xe5 | THREAD_OFF_PVIEW_CYCLES | Cycles cluster cannot commit because a thread is in the Off or Wait state. |
| 0xe6 | ARCH_LOCK_PVIEW_CYCLES | Cycles cluster cannot commit due to a kernel lock or TLB lock. |
| 0xe7 | REDIRECT_PVIEW_CYCLES | Cycles cluster cannot commit because of redirects such as branch mispredicts. |
| 0xe8 | IU_NO_PKT_PVIEW_CYCLES | Cycles cluster cannot commit because the interrupt queue is empty. |
| 0xe9 | DU_CACHE_MISS_PVIEW_CYCLES | Cycles cluster cannot commit due to a D-cache cacheable miss. |
| 0xea | DU_BUSY_OTHER_PVIEW_CYCLES | Cycles cluster cannot commit due to a DU replay, DU bubble, or DTLB miss. |
| 0xeb | CU_BUSY_PVIEW_CYCLES | Cycles cluster cannot commit due to a register interlock, register port conflict, bubbles due to a timing class such as tc_3stall, no B2B HVX, or HVX FIFO is full. |
| 0xec | SMT_DU_CONFLICT_PVIEW_CYCLES | Cycles cluster cannot commit due to a DU resource conflict. |
| 0xed | COPROC_BUSY_PVIEW_CYCLES | Cycles cluster cannot commit due to a D-cache uncacheable access. |
| 0xee | DU_UNCACHED_PVIEW_CYCLES | Cycles cluster cannot commit due to a DU resource conflict. |
| 0xef | SYSTEM_BUSY_PVIEW_CYCLES | Cycles cluster cannot commit due to system level stalls, including DMA synchronization, ETM is full, QTimer read is not ready, AXI bus is busy, and global cache operations synchronization. |
| 0xf1 | AXI_LINE128_READ_REQUEST_EVEN | Number of 128-byte line read requests issued by the even interleaved AXI master. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0xf2 | AXI_READ_REQUEST_EVEN | All read requests issued by the even interleaved AXI master. |
| 0xf3 | AXI_LINE32_READ_REQUEST_EVEN | Number of 32-byte line read requests issued by the even-interleaved AXI master. |
| 0xf4 | AXI_WRITE_REQUEST_EVEN | Write requests are issued by the even-interleaved AXI master. |
| 0xf5 | AXI_LINE32_WRITE_REQUEST_EVEN | Number of 32-byte line write requests issued by the even-interleaved AXI master. All bytes are valid. |
| 0xf6 | AXI_LINE128_WRITE_REQUEST_EVEN | Number of 128-byte line write requests issued by the even-interleaved AXI master. All bytes are valid. |
| 0xf8 | AXI_LINE64_READ_REQUEST_EVEN | Number of 64-byte line read requests issued by the even-interleaved AXI master. |
| 0xf9 | AXI_LINE64_WRITE_REQUEST_EVEN | Number of 64-byte line write requests issued by the even-interleaved AXI master. All bytes are valid. |
| 0xfa | AXI_WR_CONGESTION_EVEN | Even-interleaved AXI write command or data queue is full, and an operation is stuck at the head of the even interleaved AXI master command queue. |
| 0xfb | AXI_INCOMPLETE_WRITE_REQUEST_EVEN | L2 line-sized write was made to the even-interleaved AXI master, but not all bytes were valid. Includes segmented writes. Excludes WT stores. This event captures the number of writes coalesced at a line level. |
| 0xfc | AXI_LINE256_READ_REQUEST_EVEN | Number of 256-byte line read requests issued by an even-interleaved AXI master. All bytes are valid. |
| 0xfd | AXI_LINE256_WRITE_REQUEST_EVEN | Number of 256-byte line write requests issued by an even-interleaved AXI master. All bytes are valid. |
| 0xfe | CYCLES_3_COPROC_THREADS_ONE_CLUSTER | Number of processor cycles during which a cluster has three threads in Run mode with the coprocessor bit (SSR.XE) enabled. |
| 0x11b | HVXLD_L2_SECONDARY_MISS | Of the events in 0xFB, the events where the load cannot be returned due to the immediately prior access for the line being a pending load or pending L2Fetch |
| 0x2fa | L2_CLEAN_CASTOUT | Number of clean line evictions from L2 cache. Triggers when L2 cache evicts a line due to an allocation. Not triggered on cache operations. |
| 0x2fb | AXI3_READ_REQUEST | All read requests issued by the tertiary AXI master. Includes full lines and partial lines. |
| 0x2fc | AXI3_LINE32_READ_REQUEST | Number of 32-byte line read requests issued by the tertiary AXI master. |
| 0x2fd | AXI3_WRITE_REQUEST | Write requests issued by the tertiary AXI master. Includes full lines and partial lines. |
| 0x2fe | AXI3_LINE32_WRITE_REQUEST | Number of 32-byte line write requests issued by the tertiary AXI master. |
| 0x2ff | AXI3_RD_CONGESTION | Tertiary AXI read command queue is full, and an operation is stuck at the head of the primary AXI master command queue. Includes all interleaved requests. |
| 0x300 | CYCLES_1_PACKET_COMMITTED | Number of cycles when one packet is committed. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x301 | CYCLES_2_PACKET_COMMITTED | Number of cycles when two packets are committed. |
| 0x302 | CYCLES_3_PACKET_COMMITTED | Number of cycles when three packets are committed. |
| 0x303 | CYCLES_4_PACKET_COMMITTED | Number of cycles when four packets are committed. |
| 0x304 | SMT_CLUSTER0 | Number of cycles when more than one packet is committed in cluster 0. |
| 0x305 | SMT_CLUSTER1 | Number of cycles when more than one packet is committed in cluster 1. |
| 0x306 | SMT_INTERCLUSTER | Number of cycles when packets are committed on both clusters. |
| 0x307 | SMT_CONFLICT_FOR_REG_READ_OR_CU_FWD | Number of cases when a packet is SMT-able without slot resource conflicts, but it cannot go due to s0/s1 register read/CU forwarding. |
| 0x308 | COMMITTED_PKT_2_THREAD_RUNNING_2T_PLUS_0T | Number of committed packets with two threads running on the same cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x309 | COMMITTED_PKT_2_THREAD_RUNNING_1T_PLUS_1T | Number of committed packets with two threads running on the different cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30a | COMMITTED_PKT_3_THREAD_RUNNING_3T_PLUS_0T | Number of committed packets with three threads running on the same cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30b | COMMITTED_PKT_3_THREAD_RUNNING_2T_PLUS_1T | Number of committed packets with three threads running, two threads on one cluster and 1 on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30c | COMMITTED_PKT_4_THREAD_RUNNING_4T_PLUS_0T | Number of committed packets with four threads running on the same cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30d | COMMITTED_PKT_4_THREAD_RUNNING_3T_PLUS_1T | Number of committed packets with four threads running, three threads on one cluster and one thread running on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30e | COMMITTED_PKT_4_THREAD_RUNNING_2T_PLUS_2T | Number of committed packets with four threads running, two threads on one cluster and two threads running on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x30f | COMMITTED_PKT_5_THREAD_RUNNING_4T_PLUS_1T | Number of committed packets with 5 threads running, four threads on one cluster and one thread running on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x310 | COMMITTED_PKT_5_THREAD_RUNNING_3T_PLUS_2T | Number of committed packets with 5 threads running, three threads on one cluster and two threads running on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x311 | COMMITTED_PKT_6_THREAD_RUNNING_4T_PLUS_2T | Number of committed packets with six threads running, four threads on one cluster and two threads running on another cluster. Running means that the threads are not in the Wait or Stop state. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x312 | COMMITTED_PKT_6_THREAD_RUNNING_3T_PLUS_3T | Number of committed packets with six threads running, three threads on one cluster and three threads running on another cluster. Running means that the threads are not in the Wait or Stop state. |
| 0x313 | ICACHE_DEMAND_MISS_PREFETCH_MISS | Number of iprfetches initiated on demand misses. |
| 0x314 | SIMPLE_PACKET | Number of committed simple packets, which can be dispatched on in-cluster SMT threads. Includes eligible packets that are committed on both primary and in-cluster SMT threads. |
| 0x315 | AXI3_LINE64_WRITE_REQUEST | Number of 64-byte line write requests issued by the primary AXI3 master. Includes all interleaved requests. All bytes are valid. |
| 0x316 | AXI3_LINE64_READ_REQUEST | Number of 64-byte line read requests issued by the primary AXI3 master. Includes all interleaved requests |
| 0x317 | AXI3_WR_CONGESTION | Tertiary AXI write command or data queue is full, and an operation is stuck at the head of the primary AXI3 master command queue. Includes all interleaved requests. |
| 0x318 | AXI3_INCOMPLETE_WRITE_REQUEST | L2 line-sized write was made to the AXI3 master, but not all bytes were valid. Includes segmented writes. Excludes WT stores. |
| 0x319 | ICACHE_DATA_REPLAY | Number of I-cache data replays due to incorrect way predictions. |
| 0x31c | SMT_PKT_PICKED_BUT_NOT_COMMIT_PVIEW_CYCLES | In-cluster SMT thread is picked but not committed. |
| 0x31d | SMT_PKT_IQ_NO_PKT_PVIEW_CYCLES | In-cluster SMT thread is not picked because no packet is in IQ on the SMT thread. |
| 0x31e | SMT_PKT_NOT_SIMPLE_PVIEW_CYCLES | In-cluster SMT thread is not picked because no simple packet is on the SMT thread. |
| 0x31f | SMT_PKT_NOT_READY_PVIEW_CYCLES | In-cluster SMT thread is not picked because no simple packet is ready for dispatch on the SMT thread. |
| 0x320 | SMT_PKT_SLOT_CONFLICT_PVIEW_CYCLES | In-cluster SMT thread is not picked due to a slot conflict between the primary thread and SMT thread. |
| 0x321 | SMT_PKT_REG_FWD_BLOCK_PVIEW_CYCLES | In-cluster SMT thread is not picked due to a register and forward block on the SMT thread. |
| 0x322 | CLADE2_EB_FULL | CLADE2 can use up to two eviction buffer entries. Indicates that both entries are used and CLADE2 is congested. |
| 0x323 | CLADE2_RD_REQ | Number of L2 cache read requests in the CLADE2 region. |
| 0x324 | CLADE2_RDCACHE_MISS | Number of L2 cache read request misses in the CLADE2 region. |
| 0x325 | CLADE2_WR_REQ | Number of L2 cache write requests in the CLADE2 region. |
| 0x326 | CLADE2_WRCACHE_MISS | Number of L2 cache write request misses in the CLADE2 region. |
| 0x327 | AXI_EWD_REQUEST | L2 cache eviction of clean data to the AXI master bus. |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0x328 | AXI_EWD_REQUEST_EVEN | L2 cache eviction of clean data to the even interleaved AXI master bus. |
| 0x329 | AXI_CMO_REQUEST | Cache maintenance operation request from the QDSP6 core to AXIM. |
| 0x32a | AXI_CMO_REQUEST_EVEN | Cache maintenance operation request from the QDSP6 core to AXIM Interleave0. |
| 0x32b | ICACHE_DEMAND_MISS_PREFETCH_MISS_IU0 | Number of iprfetches initiated on a demand miss in IU0. |
| 0x32c | ICACHE_DEMAND_MISS_PREFETCH_MISS_IU1 | Number of iprfetches initiated on a demand miss in IU1. |
| 0x330 | VMEM_ST_SMT_DU_PORT_CONLICT_REPLAY | Number of times a packet takes a replay because CU did not allocate a port at schedule time and did not arbitrate for the port in DU based on the state bit VMEMSttoVTCM but needed a port as it mapped to L2. |
| 0x333 | DU_SPF_DTLBPGCROSS | Number of stopping prefetching due to page cross. |
| 0x334 | DU_SPF_DCACHE_HIT | Number of prefetch requests hitting in L1D$. |
| 0x335 | DU_SPF_DCACHE_MISS | Number of prefetch requests missing in L1D$. |
| 0x336 | DU_SPF_L2FIFOFULL_RETRY | Number of prefetch retry on L2FIFO queue full. |
| 0x337 | DU_SPF_L2BUFFULL_RETRY | Number of prefetch retry on L2 credits/AQoS busy. |
| 0x338 | DU_SPF_CONFLICT_RETRY | Number of cycles that prefetches losing arbitration. |
| 0x350 | DU_NUM_WAY_PREDICTIONS | Number of times DU did way predictions for loads. |
| 0x351 | DU_WAY_PRED_REPLAYS | Number of times DU replayed due to way misprediction. |
| 0x352 | DU_BANKCONFLICTREPLAY_INVALID | Number of time bank conflict replay was prevented due to way prediction. |
| 0xbbf | DU_CACHE_MISS_L2HIT_PVIEW_CYCLES | Cycles cluster cannot commit due to D-cache cacheable miss hitting in L2. |
| 0xbc0 | DU_CACHE_MISS_TCM_PVIEW_CYCLES | Cycles cluster cannot commit due to D-cache cacheable miss going to TCM. |
| 0xbc1 | DU_CACHE_MISS_AXI_PVIEW_CYCLES | Cycles cluster cannot commit due to D-cache cacheable miss going to AXI. |
| 0xbc2 | DU_CACHE_MISS_AHB_PVIEW_CYCLES | Cycles cluster cannot commit due to D-cache cacheable miss going to AHB. |
| 0xbc3 | DU_CACHE_MISS_AXI2_PVIEW_CYCLES | Cycles cluster cannot commit due to D-cache cacheable miss going to AXI2. |
| 0xbc4 | ICACHE_DEMAND_MISS_L2HIT_PRI | – |
| 0xbc5 | ICACHE_DEMAND_MISS_L2MISS_PRI | – |
| 0xbc6 | ICACHE_DEMAND_MISS_L2TCMHIT_PRI | – |
| 0xbc7 | ICACHE_DEMAND_MISS_L2ITCMHIT_PRI | – |
| 0xbc8 | ICACHE_IPREFETCHES_SENT_L2HIT | – |
| 0xbc9 | ICACHE_IPREFECHES_SENT_L2MISS | – |

**Table 9-1  V73 processor events symbols**

| Event | Symbol | Definition |
|---|---|---|
| 0xbca | ICACHE_IPREFETCHES_SENT_L2TCM | – |
| 0xbcb | ICACHE_IPREFETCHES_SENT_L2ITCM | – |
