# 8 Program Flow

The Hexagon processor supports the following program flow facilities.

## 8.1 Conditional instructions

Many Hexagon processor instructions can conditionally execute. For example:

```
if (P0) R0 = memw(R2)    // Conditionally load word if P0
if (!P1) jump label      // Conditionally jump if not P1
```

The following instructions can be specified as conditional:

- Jumps and calls
- Many load and store instructions
- Logical instructions (including AND/OR/XOR)
- Shift halfword
- 32-bit add/subtract by register or short immediate
- Sign and zero extend
- 32-bit register transfer and 64-bit combine word
- Register transfer immediate
- Deallocate frame and return

For more information, see Section 5.9 and Chapter 6.

## 8.2 Hardware loops

The Hexagon processor includes hardware loop instructions that perform loop branches with zero overhead. For example:

```
  loop0(start,#3)           // loop 3 times
start:
    { R0 = mpyi(R0,R0) } :endloop0
```

Two sets of hardware loop instructions are provided – loop0 and loop1 – to nest hardware loops one level deep. For example:

```
// Sum the rows of a 100x200 matrix.
```

```
  loop1(outer_start,#100)
outer_start:
    R0 = #0
    loop0(inner_start,#200)
inner_start:
      R3 = memw(R1++#4)
      { R0 = add(R0,R3) }:endloop0
    { memw(R2++#4) = R0 }:endloop1
```

Use the hardware loop instructions as follows:

- For non-nested loops, loop0 is used.
- For nested loops, loop0 is used for the inner loop, and loop1 for the outer loop.

NOTE: If a program must create loops nested more than one level deep, the two innermost loops can be implemented as hardware loops, with the remaining outer loops implemented as software branches.

Each hardware loop is associated with a pair of dedicated loop registers:

- The loop start address register SAn is set to the address of the first instruction in the loop (which is typically expressed in assembly language as a label).
- The loop count register LCn is set to a 32-bit unsigned value that specifies the number of loop iterations to perform. When the PC reaches the end of the loop, LCn is examined to determine whether to repeat or exit the loop.

The hardware loop setup instruction sets both of these registers at once – typically there is no need to set them individually. However, because the loop registers completely specify the hardware loop state, saving and restoring the registers (either automatically by a processor interrupt or manually by the programmer) enables a suspended hardware loop to resume normally once its loop registers are reloaded with the saved values.

The Hexagon processor provides two sets of loop registers for the two hardware loops:

- SA0 and LC0 are used by loop0
- SA1 and LC1 are used by loop1

**Table 8-1  Hardware loop instructions**

| Syntax | Description |
|---|---|
| `loopN(start, Rs) ` | Hardware loop with register loop count.<br>Set registers SAn and LCn for hardware loop N:<br> SAn is assigned the specified start address of the loop.<br> LCn is assigned the value of general register Rs.<br>NOTE: The loop start operand is encoded as a PC-relative immediate value. |
| `loopN(start, `<br>`#count) ` | Hardware loop with immediate loop count.<br>Set registers SAn and LCn for hardware loop N:<br> SAn is assigned the specified start address of the loop.<br> LCn is assigned the specified immediate value (0 to 1023).<br>NOTE: The loop start operand is encoded as a PC-relative immediate value. |
| `:endloopN` | Hardware loop end instruction.<br>Performs the following operation:<br>`if (LCn > 1) {PC = SAn; LCn = LCn-1}`<br>NOTE: This instruction appears in assembly as a suffix appended to the last packet in the loop. It is encoded in the last packet. |
| `SAn = Rs` | Set loop start address to general register Rs |
| `LCn = Rs` | Set loop count to general register Rs |

NOTE: The loop instructions are assigned to instruction class CR.

### 8.2.1 Loop setup

To set up a hardware loop, the loop registers SAn and LCn must be set to the proper values. This is done in two ways:

- A loopN instruction
- Register transfers to SAn and LCn

The loopN instruction performs all the work of setting SAn and LCn. For example:

```
  loop0(start,#3)           // SA0=&start, LC0=3
start:
    { R0 = mpyi(R0,R0) } :endloop0
```

In this example, the hardware loop (consisting of a single multiply instruction) executes three times. The loop0 instruction sets register SA0 to the address value of label start, and LC0 to 3.

Loop counts are limited to the range 0 to1023 when they are expressed as immediate values in loopN. If the intended loop count exceeds this range, it must be specified as a register value. For example:

Using loopN:

```
  R1 = #20000;
  loop0(start,R1)          // LC0=20000, SA0=&start
start:
    { R0 = mpyi(R0,R0) } :endloop0
```

Using register transfers:

```
  R1 = #20000
  LC0 = R1                 // LC0=20000
  R1 = #start
  SA0 = R1                 // SA0=&start
start:
    { R0 = mpyi(R0,R0) } :endloop0
```

If a loopN instruction is located too far from its loop start address, the PC-relative offset value that specifies the start address can exceed the maximum range of the start-address operand of the instruction. When this occurs, either move the loopN instruction closer to the loop start, or specify the loop start address as a 32-bit constant (Section 10.9).

For example, using 32-bit constants:

```
  R1 = #20000;
  loop0(##start,R1)        // LC0=20000, SA0=&start
  ...
```

### 8.2.2 Loop end

The loop end instruction indicates the last packet in a hardware loop. The loop end instruction is expressed in assembly language by appending the packet with the symbol `:endloopN`, where `N` specifies the hardware loop (0 or 1). For example:

```
  loop0(start,#3)
start:
    { R0 = mpyi(R0,R0) } :endloop0  // last packet in loop
```

The last instruction in the loop must always be expressed in assembly language as a packet (using curly braces), even if it is the only instruction in the packet.

Nested hardware loops can specify the same instruction as the end of both the inner and outer loops. For example:

```
// Sum the rows of a 100x200 matrix.
// Software pipeline the outer loop.
```

```
     p0 = cmp.gt(R0,R0)              // p0 = false
     loop1(outer_start,#100)
outer_start:
     { if (p0) memw(R2++#4) = R0
       p0 = cmp.eq(R0,R0)            // p0 = true
       R0 = #0
       loop0(inner_start,#200) }
inner_start:
     R3 = memw(R1++#4)
     { R0 = add(R0,R3) }:endloop0:endloop1
     memw(R2++#4) = R0
```

Though endloopN behaves like a regular instruction (by implementing the loop test and branch), it does not execute in any instruction slot, and does not count as an instruction in the packet. Therefore a single instruction packet that is marked as a loop end can perform up to six operations:

- Four regular instructions (the normal limit for an instruction packet)
- The `endloop0` test and branch
- The `endloop1` test and branch

NOTE: The endloopN instruction is encoded in the instruction packet (Section 10.6).

### 8.2.3 Loop execution

After a hardware loop is set up, the loop body always executes at least once regardless of the specified loop count (because the loop count is not examined until the last instruction in the loop). Therefore, if a loop must be optionally executed zero times, it must be preceded with an explicit conditional branch. For example:

```
  loop0(start,R1)
  P0 = cmp.eq(R1,#0)
  if (P0) jump skip
start:
    { R0 = mpyi(R0,R0) } :endloop0
skip:
```

In this example, a hardware loop is set up with the loop count in R1, but if the value in R1 is zero a software branch skips over the loop body.

After the loop end instruction of a hardware loop is executed, the Hexagon processor examines the value in the corresponding loop count register:

- If the value is greater than 1, the processor decrements the loop count register and performs a zero-cycle branch to the loop start address.
- If the value is less than or equal to 1, the processor resumes program execution at the instruction immediately following the loop end instruction.

NOTE: Because nested hardware loops can share a loop end instruction, the processor can examine both loop count registers in a single operation.

### 8.2.4 Pipelined hardware loops

Software pipelined loops are common for VLIW architectures such as the Hexagon processor. They offer increased code performance in loops by overlapping multiple loop iterations.

A software pipeline has three sections:

- A prologue in which the loop is primed
- A kernel (or steady-state) portion
- An epilogue that drains the pipeline

A simple example is shown in Table 8-2.

**Table 8-2  Software pipelined loop**

```
int foo(int *A, int *result)
{
    int i;
    for (i=0;i<100;i++) {
        result[i]= A[i]*A[i];
    }
}
```

```
foo:
{       R3 = R1
        loop0(.kernel,#98)        // Decrease loop count by 2
}
        R1 = memw(R0++#4)         // First prologue stage
{       R1 = memw(R0++#4)         // Second prologue stage
        R2 = mpyi(R1,R1)
}
        .falign
.kernel:
{       R1 = memw(R0++#4)         // Kernel
        R2 = mpyi(R1,R1)
        memw(R3++#4) = R2
}:endloop0
{       R2 = mpyi(R1,R1)          // First epilogue stage
        memw(R3++#4) = R2
}
        memw(R3++#4) = R2         // Second epilogue stage
        jumpr lr
```

In Table 8-2, the kernel section of the pipelined loop performs three iterations of the loop in parallel:

- The load for iteration N+2
- The multiply for iteration N+1
- The store for iteration N

One drawback to software pipelining is the extra code necessary for the prologue and epilogue sections of a pipelined loop.

To address this issue, the Hexagon processor provides the spNloop0 instruction, where the “`N`” in the instruction name indicates a digit in the range 1 to 3. For example:

```
  P3 = sp2loop0(start,#10)     // Set up pipelined loop
```

The spNloop0 instruction is a variant of the loop0 instruction: it sets up a normal hardware loop using SA0 and LC0, but also performs the following additional operations:

- When the spNloop0 instruction executes, it assigns the truth value false to the predicate register P3.
- After the associated loop executes N times, P3 is automatically set to true.

This feature (known as automatic predicate control) enables the store instructions in the kernel section of a pipelined loop to conditionally execute by P3 and thus – because of the way spNloop0 controls P3 – not execute during the pipeline warm-up. This can reduce the code size of software pipelined loops by eliminating the need for prologue code.

The spNloop0 instruction cannot be used to eliminate the epilogue code from a pipelined loop; however, in some cases it is possible to do this by using programming techniques.

Typically, load safety is the issue that affects the removal of epilogue code. If the kernel section of a pipelined loop can safely access past the end of its arrays – either because it is known as safe, or because the arrays have been padded at the end – epilogue code is unnecessary. However, if load safety cannot be ensured, explicit epilogue code is required to drain the software pipeline.

Table 8-3 shows how spNloop0 and load safety simplify the code shown in Table 8-2.

**Table 8-3  Software pipelined loop (using spNloop0)**

```
int foo(int *A, int *result)
{
    int i;
    for (i=0;i<100;i++) {
        result[i]= A[i]*A[i];
    }
}
```

```
foo:
{ // load safety assumed
        P3 = sp2loop0(.kernel,#102)    // Set up pipelined loop
        R3 = R1
}
.falign
.kernel:
{       R1 = memw(R0++#4)              // Kernel
        R2 = mpyi(R1,R1)
        if (P3) memw(R3++#4) = R2
}:endloop0
```

```
        jumpr lr
```

NOTE: The count value that `spNloop0` uses to control the P3 setting is stored in the user status register USR.LPCFG.

### 8.2.5 Loop restrictions

Hardware loops have the following restrictions:

- The loop setup packet in loopN or spNloop0 (Section 8.2.4) cannot contain a speculative indirect jump, new-value compare jump, or dealloc_return.
- The last packet in a hardware loop cannot contain any program flow instructions (including jumps or calls).
- The loop end packet in loop0 cannot contain any instruction that changes SA0 or LC0. Similarly, the loop end packet in loop1 cannot contain any instruction that changes SA1 or LC1.
- The loop end packet in spNloop0 cannot contain any instruction that changes P3.

NOTE: SA1 and LC1 can be changed at the end of loop0 while SA0 and LC0 can be changed at the end of loop1.

## 8.3 Software branches

Unlike hardware loops, software branches use an explicit instruction to perform a branch operation. Software branches include jumps, calls, and returns.

The target address for branch instructions is specified as register indirect or PC-relative offsets. PC-relative offsets are normally less than 32 bits, but can be specified as 32 bits by using the appropriate syntax in the target operand (Section 8.3.4).

Branch instructions are unconditional or conditional, with the execution of conditional instructions controlled by a predicate expression.

**Table 8-4  Software branch instructions**

| Syntax | Operation |
|---|---|
| `[if (pred_expr)] jump label`<br>`[if (pred_expr)] jumpr Rs` | Branch to the address specified by register Rs or PC-relative offset. Can be conditionally executed. |
| `[if (pred_expr)] call label`<br>`[if (pred_expr)] callr Rs` | Branch to the address specified by register Rs or PC-relative offset. Store the subroutine return address in link register LR. Can be conditionally executed. |
| `[if (pred_expr)] jumpr LR` | Branch to the subroutine return address contained in link register LR. Can be conditionally executed. |

### 8.3.1 Jumps

Jump instructions change the program flow to a target address, which is specified by either a register or a PC-relative immediate value. Jump instructions can be conditional based on the value of a predicate expression.

**Table 8-5  Jump instructions**

| Syntax | Operation |
|---|---|
| `jump label` | Direct jump. Branch to the address specified by label.<br>Label is encoded as PC-relative signed immediate value. |
| `jumpr Rs` | Indirect jump. Branch to the address contained in general register Rs. |
| `if ([!]Ps) jump label`<br>`if ([!]Ps) jumpr Rs` | Conditional jump. Perform jump if the predicate expression is TRUE. |

NOTE: Conditional jumps can be specified as speculative (Section 8.4).

### 8.3.2 Calls

Call instructions jump to subroutines. The instruction performs a jump to the target address and also stores the return address in the link register LR.

The forms of call are functionally similar to jump instructions and include both PC-relative and register indirect in both unconditional and conditional forms.

**Table 8-6  Call instructions**

| Syntax | Operation |
|---|---|
| `call label` | Direct subroutine call. Branch to the address specified by label, and store the return address in register LR. Label is encoded as PC-relative signed immediate value. |
| `callr Rs` | Indirect subroutine call. Branch to the address contained in general register Rs, and store the return address in register LR. |
| `if ([!]Ps) call label`<br>`if ([!]Ps) callr Rs` | Conditional call. If the predicate expression is TRUE, perform a subroutine call to the specified target address. |

### 8.3.3 Returns

Return instructions return from a subroutine. The instruction performs an indirect jump to the subroutine return address stored in link register LR.

Returns are implemented as jump register indirect instructions, and support both unconditional and conditional forms.

**Table 8-7  Return instructions**

| Syntax | Operation |
|---|---|
| ` jumpr LR` | Subroutine return. Branch to the subroutine return address contained in link register LR. |
| `if ([!]Ps) jumpr LR` | Conditional subroutine return. If the predicate expression is TRUE, perform a subroutine return to the specified target address. |
| `dealloc_return` | Subroutine return with stack frame deallocate. Perform a deallocframe operation (Section 7.5) and then perform a subroutine return to the target address loaded by deallocframe from the link register. |
| `if ([!]Ps) `<br>`dealloc_return` | Conditional subroutine return with stack frame deallocate. If the predicate expression is TRUE, perform deallocframe and subroutine return to the target address loaded by deallocframe from the link register. |

NOTE: The link register LR is an alias of the R31 general register. Therefore subroutine returns can be performed with the jumpr R31 instruction.

The conditional subroutine returns (including dealloc_return) can be specified as speculative (Section 8.4).

### 8.3.4 Extended branches

When a jump or call instruction specifies a PC-relative offset as the branch target, the offset value is normally encoded in significantly less than 32 bits. This can limit the ability for programs to specify “long” branches, which span a large range of the memory address space of the processor.

To support long branches, the jump and call instructions have special versions that encode a full 32-bit value as the PC-relative offset.

NOTE: Such instructions use an extra word to store the 32-bit offset (Section 10.9).

The size of a PC-relative branch offset is expressed in assembly language by optionally prefixing the target label with the symbol “`##`” or “`#`”:

- “`##`” specifies that the assembler must use a 32-bit offset
- “`#`” specifies that the assembler must not use a 32-bit offset
- No “`#`” specifies that the assembler use a 32-bit offset only if necessary

For example:

```
jump ##label   // 32-bit offset
call #label    // Non 32-bit offset
jump label     // Offset size determined by assembler
```

### 8.3.5 Branches to and from packets

Instruction packets are atomic: even if they contain multiple instructions, they are only referenced by the address of the first instruction in the packet. Therefore, branches to a packet can target only the first instruction of a packet.

Packets can contain up to two branches (Section 8.7). The branch destination can target the current packet or the beginning of another packet.

A branch does not interrupt the execution of the current packet: all of the instructions in the packet execute, even if they appear in the assembly source after the branch instruction.

If a packet is at the end of a hardware loop, it cannot contain a branch instruction.

## 8.4 Speculative jumps

Conditional instructions normally depend on predicates that are generated in a previous instruction packet. However, Dot-new predicates enable conditional instructions to use a predicate generated in the same packet that contains the conditional instruction.

When dot-new predicates are used with a conditional jump, the resulting instruction is called a speculative jump. For example:

```
{
   P0 = cmp.eq(R9,#16)        // single-packet compare-and-jump
   IF (P0.new) jumpr:t R11    // ... enabled by use of P0.new
}
```

Speculative jumps require the programmer to specify a direction hint in the jump instruction, indicating whether the conditional jump is expected.

The hint initializes the dynamic branch predictor of the Hexagon processor. Whenever the predictor is wrong, the speculative jump instruction takes two cycles to execute instead of one (due to a pipeline stall).

Hints can improve program performance by indicating how speculative jumps are expected to execute over the course of a program: the more often the specified hint indicates how the instruction actually executes, the better the performance.

Hints are expressed in assembly language by appending the suffix “`:t`” or “`:nt`” to the jump instruction symbol. For example:

- jump:t – The jump instruction is most often taken
- jump:nt – The jump instruction is most often not taken

In addition to dot-new predicates, speculative jumps also accept conditional arithmetic expressions (=0, !=0, >=0, <=0) involving the general register Rs.

**Table 8-8  Speculative jump instructions**

| Syntax | Operation |
|---|---|
| `if ([!]Ps.new) jump:t label`<br>`if ([!]Ps.new) jump:nt label` | Speculative direct jump. If the predicate expression is TRUE, jump to the address specified by label. |
| `if ([!]Ps.new) jumpr:t Rs`<br>`if ([!]Ps.new) jumpr:nt Rs` | Speculative indirect jump. If the predicate expression is TRUE, jump to the address in register Rs. |
| `if (Rs == #0) jump:t label`<br>`if (Rs == #0) jump:nt label` | Speculative direct jump. If the predicate Rs = 0 is TRUE, jump to address specified by label. |
| `if (Rs != #0) jump:t label`<br>`if (Rs != #0) jump:nt label` | Speculative direct jump. If the predicate Rs != 0 is TRUE, jump to the address specified by label. |

**Table 8-8  Speculative jump instructions (cont.)**

| Syntax | Operation |
|---|---|
| `if (Rs >= #0) jump:t label`<br>`if (Rs >= #0) jump:nt label` | Speculative direct jump. If the predicate Rs >= 0 is TRUE, jump to the address specified by label. |
| `if (Rs <= #0) jump:t label`<br>`if (Rs <= #0) jump:nt label` | Speculative direct jump. If the predicate Rs <= 0 is TRUE, jump to the address specified by label. |

NOTE: The hints `:t` and `:nt` interact with the predicate value to determine the instruction cycle count.

Speculative indirect jumps are not supported with register Rs predicates.

## 8.5 Compare jumps

To reduce code size, the Hexagon processor supports a compound instruction that combines a compare with a speculative jump in a single 32-bit instruction.

For example:

```
{
   p0 = cmp.eq (R2,R5)           // Single-instr compare-and-jump
   if (p0.new) jump:nt target    // Enabled by compound instr
}
```

The register operands used in a compare jump are limited to R0 through R7 or R16 through R23 (Table 10-3).

The compare and jump instructions that are used in a compare jump are limited to the instructions listed in Table 8-9. The compare can use predicate P0 or P1 while the jump must specify the same predicate that is set in the compare.

A compare jump instruction is expressed in assembly source as two independent compare and jump instructions in a packet. The assembler translates the two instructions into a single compound instruction.

**Table 8-9  Compare jump instructions**

| Compare Instruction | Jump Instruction |
|---|---|
| `Pd = cmp.eq (Rs, Rt)`<br>`Pd = cmp.gt (Rs, Rt)`<br>`Pd = cmp.gtu (Rs, Rt)`<br>`Pd = cmp.eq (Rs,#U5)`<br>`Pd = cmp.gt (Rs,#U5)`<br>`Pd = cmp.gtu (Rs,#U5)`<br>`Pd = cmp.eq (Rs,#-1)`<br>`Pd = cmp.gt (Rs,#-1)`<br>`Pd = tstbit (Rs, #0)` | `IF (Pd.new) jump:t label`<br>`IF (Pd.new) jump:nt label`<br>`IF (!Pd.new) jump:t label`<br>`IF (!Pd.new) jump:nt label` |

### 8.5.1 New-value compare jumps

A compare jump instruction can access a register that is assigned a new value in the same instruction packet (Section 3.3). This feature is expressed in assembly language by the following changes:

- Appending the suffix “`.new`” to the new-value register in the compare
- Rewriting the compare jump so its constituent compare and jump operations appear as a single conditional instruction

For example:

```
// load-compare-and-jump packet enabled by new-value compare jump
```

```
{
   R0 = memw(R2+#8)
   if (cmp.eq(R0.new,#0)) jump:nt target
}
```

New-value compare jump instructions have the following restrictions:

- They are limited to the instruction forms listed in Table 8-10.
- They cannot be combined with another jump instruction in the same packet.
- If an instruction produces a 64-bit result or performs a floating-point operation, its result registers cannot be used as the new-value register.
- If an instruction uses auto-increment or absolute-set addressing mode (Section 5.8), its address register cannot be used as the new-value register.
- If the instruction that sets a new-value register is conditional (Section 6.1.2), it must always execute.

If the specified jump direction hint is wrong (Section 8.4), a new-value compare jump takes three cycles to execute instead of one. While this penalty is one cycle longer than in a regular speculative jump, the overall performance is still better than using a regular speculative jump (which must execute an extra packet in all cases).

NOTE: New-value compare jump instructions are assigned to instruction class NV, which can execute only in Slot 0. The instruction that assigns the new value must execute in Slot 1, 2, or 3.

**Table 8-10  New-value compare jump instructions**

```
if ([!]cmp.eq (Rs.new, Rt)) jump:[hint] label
if ([!]cmp.gt (Rs.new, Rt)) jump:[hint] label
if ([!]cmp.gtu (Rs.new, Rt)) jump:[hint] label
```

```
if ([!]cmp.gt (Rs, Rt.new)) jump:[hint] label
if ([!]cmp.gtu (Rs, Rt.new)) jump:[hint] label
if ([!]cmp.eq (Rs.new,  #u5)) jump:[hint] label
if ([!]cmp.gt (Rs.new, #u5)) jump:[hint] label
if ([!]cmp.gtu (Rs.new ,#u5)) jump:[hint] label
```

```
if ([!]cmp.eq (Rs.new,  #-1)) jump:[hint] label
if ([!]cmp.gt (Rs.new, #-1)) jump:[hint] label
```

```
if ([!]tstbit (Rs.new, #0)) jump:[hint] label
```

## 8.6 Register transfer jumps

To reduce code size, the Hexagon processor supports a compound instruction that combines a register transfer with an unconditional jump in a single 32-bit instruction.

For example:

```
{
   jump target    // Jump to label “target”
   R1 = R2        // Assign contents of reg R2 to R1
}
```

The source and target register operands in the register transfer are limited to R0 through R7 or R16 through R23 (Table 10-3).

The target address in the jump is a scaled 9-bit PC-relative address value (as opposed to the 22-bit value in the regular unconditional jump instruction).

A register transfer jump instruction is expressed in assembly source as two independent instructions in a packet. The assembler translates the instructions into a single compound instruction.

**Table 8-11  Register transfer jump instructions**

| Syntax | Operation |
|---|---|
| `jump label; `<br>`Rd=Rs` | Register transfer jump.<br>Perform register transfer and branch to address specified by label. Label is encoded as PC-relative 9-bit signed immediate value. |
| `jump label; `<br>`Rd=#u6` | Register transfer immediate jump.<br>Perform register transfer (of 6-bit unsigned immediate value) and branch to address specified by label.<br>Label is encoded as PC-relative 9-bit signed immediate value. |

## 8.7 Dual jumps

Two software branch instructions (referred to here as “jumps”) can appear in the same instruction packet, under the conditions listed in Table 8-12.

The first jump is defined as the jump instruction at the lower address, and the second jump as the jump instruction at the higher address.

Unlike most packetized operations, dual jumps are not executed in parallel (Section 3.3.1). Instead, the two jumps are processed in a well-defined order in a packet:

1. The predicate in the first jump is evaluated.

2. If the first jump is taken, the second jump is ignored.

3. If the first jump is not taken, the second jump is performed.

**Table 8-12  Dual jump instructions**

| Instruction | Description | First jump in packet? | Second jump in packet? |
|---|---|---|---|
| `jump` | Direct jump | No | Yes |
| `if ([!]Ps[.new]) jump` | Conditional jump | Yes | Yes |
| `call`<br>`if ([!]Ps) call` | Direct calls | No | Yes |
| `Pd=cmp.xx ; if ([!]Pd.new) `<br>`jump` | Compare jump | Yes | Yes |
| `if ([!]cmp.xx(Rs.new, Rt)) `<br>`jump` | New-value compare jump | No | No |
| `jumpr`<br>`if ([!]Ps[.new]) jumpr`<br>`callr `<br>`if ([!]Ps) callr`<br>`dealloc_return`<br>`if ([!]Ps[.new]) `<br>`dealloc_return` | Indirect jumps<br>Indirect calls<br>dealloc_return | No | No |
| `endloopN` | Hardware loop end | No | No |

NOTE: If a call is ignored in a dual jump, the link register LR is not changed.

## 8.8 Hint indirect jump target

Because it obtains the jump target address from a register, the jumpr instruction (Section 8.3.1) normally causes the processor to stall for one cycle.

To avoid the stall penalty caused by a jumpr instruction, the Hexagon processor supports the hintjr jump hint instruction, which can be specified before the jumpr instruction.

The hintjr instruction indicates that the program is about to execute a jumpr to the address contained in the specified register.

**Table 8-13  Speculative jump hint instruction**

| Syntax | Operation |
|---|---|
| `hintjr(Rs)` | Informs the processor that the jumpr(Rs) instruction is about to be performed. |

NOTE: To prevent a stall, the hintjr instruction must execute at least 2 packets before the corresponding jumpr instruction.

The hintjr instruction is not needed for jumpr instructions used as returns (Section 8.3.3), because in this case the Hexagon processor automatically predicts the jump targets based on the most recent nested call instructions.

## 8.9 Pauses

Pauses suspend the execution of a program for a period of time, and put it into low-power mode. The program remains suspended for the duration specified in the instruction.

The pause instruction accepts an unsigned 8-bit immediate operand which specifies the pause duration in terms of cycles. The maximum possible duration is 263 cycles (255+8).

Hexagon processor interrupts cause a program to exit the paused state before its specified duration has elapsed.

The pause instruction is useful to implement user-level low-power synchronization operations (such as spin locks).

**Table 8-14  Pause instruction**

| Syntax | Operation |
|---|---|
| `pause(#u8) ` | Suspend the program in low-power mode for the specified cycle duration. |

## 8.10 Exceptions

Exceptions are internally-generated disruptions to the program flow.

The Hexagon processor OS handles fatal exceptions by terminating the execution of the application system. The user is responsible for fixing the problem and recompiling their applications.

The error messages generated by exceptions include the following information:

- Cause code – Hexadecimal value that indicates the type of exception
- User IP – PC value that indicates that the instruction executed when the exception occurred
- Bad VA – Virtual address that indicates the data accessed when the exception occurred

NOTE: The cause code, user IP, and Bad VA values are stored in the Hexagon processor system control registers SSR[7:0], ELR, and BADVA respectively.

If multiple exceptions occur simultaneously, the exception with the lowest error code value has the highest exception priority.

If a packet contains multiple loads or a load and a store and both operations have an exception of any type, all slot 1 exceptions process before any slot 0 exception is processed.

**Table 8-15  V73 exceptions**

| Cause code | Event type | Event description | Notes |
|---|---|---|---|
| 0x0 | Reset | Software thread reset. | Non-maskable, highest priority |
| 0x01 | Precise, unrecoverable | Unrecoverable BIU error (bus error, timeout, L2 parity error, and so on). | Non-maskable |
| 0x03 | Precise, unrecoverable | Double exception; the exception occurs while SSR[EX]=1. | Non-maskable |
| 0x11 | Precise | Privilege violation: User/Guest mode execute to page with no execute permissions (X=0). | Non-maskable |
| 0x12 | Precise | Privilege violation: User mode execute to a page with no user permissions (X=1, U=0). | Non-maskable |
| 0x15 | Precise | Invalid packet. | Non-maskable |
| 0x16 | Precise | Illegal execution of coprocessor instruction. | Non-maskable |
| 0x17 | Precise | Instruction cache error. | Non-maskable |
| 0x1A | Precise | Privilege violation: Executing a guest mode instruction in user mode. | Non-maskable |
| 0x1B | Precise | Privilege violation: Executing a supervisor instruction in User/Guest mode. | Non-maskable |
| 0x1D | Precise, unrecoverable | Packet with multiple writes to the same destination register. | Non-maskable |
| 0x1E | Precise, unrecoverable | Program counter values that are not properly aligned. | Non-maskable |
| 0x20 | Precise | Load to misaligned address. | Non-maskable |

**Table 8-15  V73 exceptions (cont.)**

| Cause code | Event type | Event description | Notes |
|---|---|---|---|
| 0x21 | Precise | Store to misaligned address. | Non-maskable |
| 0x22 | Precise | Privilege violation: User/Guest mode read to page with no read permission (R=0). | Non-maskable |
| 0x23 | Precise | Privilege violation: User/Guest mode write to page with no write permissions (W=0). | Non-maskable |
| 0x24 | Precise | Privilege violation: User mode read to page with no user permission (R=1, U=0). | Non-maskable |
| 0x25 | Precise | Privilege violation: User mode write to page with no user permissions (W=1, U=0). | Non-maskable |
| 0x26 | Precise | Coprocessor VMEM address error. | Non-maskable |
| 0x27 | Precise | Stack overflow: Allocframe instruction exceeded FRAMELIMIT. | Non-maskable, |
| 0x42 | Imprecise | Data abort. | Non-maskable |
| 0x43 | Imprecise | NMI. | Non-maskable |
| 0x44 | Imprecise | Multiple TLB match. | Non-maskable |
| 0x45 | Imprecise | Livelock exception. | Non-maskable |
| 0x60 | TLB miss-X | Missing fetch address on PC-page. | Non-maskable |
| 0x61 | TLB miss-X | Missing fetch on the second page from the packet that spans pages. | Non-maskable |
| 0x62 | TLB miss-X | icinva. | Non-maskable |
|  | Reserved |  |  |
| 0x70 | TLB miss-RW | Memory read. | Non-maskable |
| 0x71 | TLB miss-RW | Memory write. | Non-maskable |
|  | Reserved |  |  |
| #u8 | Trap0 | Software Trap0 instruction. | Non-maskable |
| #u8 | Trap1 | Software Trap1 instruction. | Non-maskable |
|  | Reserved |  |  |
| 0x80 | Debug | Single-step debug exception. |  |
|  | Reserved |  |  |
| 0xBF | Floating-point | Execution of floating-point instruction resulted in exception. | Non-maskable |
| 0xC0 | Interrupt0 | General external interrupt. | Maskable, highest priority general interrupt |
| 0xC1 | Interrupt 1 | General external interrupt | Maskable |
| 0xC2 | Interrupt 2 | General external interrupt | VIC0 interface |
| 0xC3 | Interrupt 3 | General external interrupt | VIC1 interface |
| 0xC4 | Interrupt 4 | General external interrupt | VIC2 interface |
| 0xC5 | Interrupt 5 | General external interrupt | VIC3 interface |

**Table 8-15  V73 exceptions (cont.)**

| Cause code | Event type | Event description | Notes |
|---|---|---|---|
| 0xC6 | Interrupt 6 | General external interrupt |  |
| 0xC7 | Interrupt 7 | General external interrupt | Lowest-priority interrupt |
