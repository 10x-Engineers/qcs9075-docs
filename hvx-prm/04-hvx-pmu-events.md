# 4 HVX PMU events

The Hexagon processor architecture defines a performance monitor unit (PMU) to provide on-target performance tracking.

The PMU allows for easy collection of aggregate performance data like cache performance and instructions per packet. This data is valuable for system planning and architecture purposes because it drives performance and power statistical models.

In V69 and later versions, the PMU event space is expanded to 1024 events. Events 0 to 255 describe core events. Coprocessors use events 384 and above; which are described in the Qualcomm Hexagon V73 Programmer’s Reference Manual (80-N2040-53)

HVX events 256 to 299 are documented in Table 4-1

**Table 4-1  HVX PMU events**

| Event | Name | Description |
|---|---|---|
| 256 | HVX_ACTIVE | VFIFO not empty. |
| 257 | HVX_REG_ORDER | Stall cycles due to interlocks. |
| 258 | HVX_ACC_ORDER | Stall cycles due to accumulator not produced in previous context cycle. |
| 259 | HVX_LD_L2_OUTSTANDING | Stall cycles due to load pending. |
| 260 | HVX_ST_L2_OUTSTANDING | Stall cycles due to store not yet allocated in L2. |
| 261 | HVX_VTCM_OUTSTANDING | Stall cycles due to VTCM transaction pending. |
| 262 | HVX_SCATGATH_FULL | Scatter/gather: network scoreboard not updated. |
| 263 | HVX_SCATGATH_IN_FULL | Scatter/gather input buffer full. |
| 266 | HVX_VOLTAGE_UNDER | Throttling: voltage model exceeds undershoot threshold. |
| 267 | HVX_POWER_OVER | Throttling: sustained power exceeds budget |
| 268 | HVX_PKT_PARTIAL | Stall cycles due to multi-issue packet. |
| 273 | HVX_PKT | Packets with HVX instructions. |
| 274 | HVX_PKT_THREAD | Committed packets on a thread with the XE bit set, whether executed in Q6 or coprocessor. |
| 275 | HVX_CORE_VFIFO_FULL_STALL | Number of cycles a thread stalls due to VFIFO. |
| 277 | CYCLES_1_HVX_CONTEXTS_RUNNING | Cycles one HVX context running. |
| 278 | CYCLES_2_HVX_CONTEXTS_RUNNING | Cycles two HVX contexts that run concurrently. |
| 279 | CYCLES_3_HVX_CONTEXTS_RUNNING | Cycles three HVX contexts that run concurrently. |

**Table 4-1  HVX PMU events**

| Event | Name | Description |
|---|---|---|
| 280 | HVXLD_L2 | L2 cacheable load access from HVX. Any load access from HVX that might cause a lookup in the L2 cache. Excludes cache operations, uncacheables, and scalars. |
| 281 | HVXLD_L2_TCM | TCM load access for HVX. HVX load from the L2 TCM space |
| 290 | HVXST_VTCM_FULL | Write FIFO full. |
| 291 | HVXST_L2 | Vector store to L2. |
| 292 | HVXST_L2_MISS | L2 cacheable miss from HVX store; the cases where the 128-byte-line address is not in the tag or a coalesce buffer. |
| 295 | HVXST_L2_SECODARY_MISS | L2 cacheable secondary miss from HVX store; the cases where the 128-byte-line address is not in the tag or a coalesce buffer. |
| 296 | HVXPIPE_ALU | Executed simple ALU instruction. |
| 297 | HVXPIPE_MPY | Executed multiply or abs-diff instruction. |
| 300 | CYCLES_4_HVX_CONTEXTS_RUNNING | Cycles four HVX contexts that run concurrently |
