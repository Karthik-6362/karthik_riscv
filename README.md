## Karthik_riscv

<details>
  <summary> DAY_3 :- Digital Logic with TL-Verilog and Makerchip :- </summary>
  
### Digital Logic with TL-Verilog and Makerchip:- 

<details>
  <summary>Combinational logic in TL-Verilog using Makerchip:- </summary>

BASIC LOGIC GATES :- 
![BASIC GATES](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/a1188279-9c8a-4b6c-89be-33b8f568f561)

COMBINATIONAL LOGIC OF FULL ADDER :- 
![Full adder comb logic](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/68c59ac6-46dc-44e7-a575-1aa6d1a35ed6)
This can be used in sequence to get a n-bit adder.

BOOLEAN OPERATORS IN VERILOG :- 
![Boolean operators in verilog](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/c98e4987-5637-4347-985c-0008af380a5c)

MULTIPLEXER(MUX) :- 
A simple multiplexer (mux) is a digital logic device with multiple data inputs, one output, and a set of control inputs. It selects one of the data inputs to be transmitted to the output based on the binary values present on the control inputs. The selected input is then forwarded to the output, effectively allowing data from a single source to be sent to the output.

``` verilog
Syntax:- condition ? expression_if_true : expression_if_false
assign f = s ? X1 : X2;   // using a ternary operator
```
![mux logic](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/7d58b063-b882-4c79-9458-9ed854217e88)
The code `assign f = s ? X1 : X2;` represents a one-line Verilog description of a multiplexer (mux) operation, where the output `f` is assigned the value of `X1` when the select signal `s` is true, and the value of `X2` when the select signal is false. 

CHAINING TERNARY OPERATOR:- 

Mux with a 3 bit select input:- 
![Chaining ternary operator](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/d7115cca-3a5f-4887-be1f-13a99e4c525d)

Equivalent realization:- 
![Chaining ternary operator equivalent](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/1c2a113e-bf5d-4ac2-be0b-f5604f9d2d8c)

```TL-Verilog
assign f =
  sel[0]
    ? a
    : (sel[1]
      ? b
      : (sel[2]
        ? c
        : d
        )
  );
```

INTRODUCTION TO MAKERCHIP:- 
Makerchip IDE is a web-based integrated development environment used for digital system and chip design, supporting SystemVerilog, code editing, simulation, debugging, and it's widely used in education and FPGA design.
[Makerchip IDE](https://makerchip.com/sandbox/)
LABS FOR COMBINATIONAL LOGIC :- 

Getting familiar with Makerchip:- 
1. Reproduce this screenshot:
2. Open “Tutorials” “Validity Tutorial”.
3. In tutorial, click ```Load pythagorean example```
4. Split panes and move tabs.
5. Zoom/pan in Diagram w/ mouse wheel and drag.
6. Zoom Waveform w/ “Zoom In” button.
7. Click $bb_sq to highlight.
![USING MAKERCHIP ](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/5a4497cb-2764-430c-9dad-7271b946840a)


A) Inverter :-

```TL-Verilog
\TLV
   $reset = *reset;
   
   $out = ! $in1;
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```
Execution in makerchip:- 
![Inverter in makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/bb09ba96-fb84-4eb3-b269-af99cb0cd0a3)

NOTE:-
- There was no need to declare $out and $in1 (unlike Verilog).
- There was no need to assign $in1. Random stimulus is provided, and a warning is produced.

B) Or gate :- 
```TL-Verilog
\TLV
   $reset = *reset;
   
   $out = $in1 | $in2;
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule

```

Execution in makerchip:- 
![or in makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/bb2b762f-de42-4bfc-a109-7fc01e185f66)


C) Explicitly adding the only 4 bits of the inputs using + :- 

```TL-Verilog
\TLV
   $reset = *reset;
   
   $out[4:0] = $in1[3:0] + $in2[3:0];
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```

Execution in makerchip:- 
![add in makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/b0608c75-c475-4835-8374-6f849684f3dc)


D) Mux with 1-bit inputs:-
```TL-Verilog
\TLV
   $reset = *reset;
   
   $out = $sel ? $in1 : $in2;
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```

Execution in makerchip:- 
![mux in makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/26e42752-ca40-40e3-b02d-4313467efdc0)


E) Mux with 8-bit inputs:- 
```TL-Verilog
\TLV
   $reset = *reset;
   
   $out[7:0] = $sel ? $in1[7:0] : $in2[7:0];
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```
Execution in makerchip:- 
![mux with 8bit ip in makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/56ab2534-30d4-428b-9306-a785437e7c1c)

</details>


<details>
  <summary> Sequential Logic:- </summary>

## D-Flipflop :- 
A D flip-flop is a digital circuit element that stores and outputs a binary value (0 or 1) based on the input data (D), a clock signal (clk), and an optional reset signal, allowing the stored value to be changed on the rising or falling edge of the clock and reset to a predefined state when the reset signal is active.

```TL-Verilog 
\TLV
   $reset = *reset;
   
   $out = $reset ? 0 : $data_in;
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```
Execution in makerchip:-  
![d flipflop makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/e7a56bb8-9bc0-4062-bbee-9d3c6b337b67)

## Fibonacci Series:- 
The Fibonacci series is a sequence of numbers where each number is the sum of the two preceding ones, usually starting with 0 and 1.
![eg- Fibonacci Series](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/07ddba11-3adf-4cf9-b2f7-4179e5c17a2a)

```TL-Verilog
\TLV
   $reset = *reset;
   
   $num[31:0] = $reset ? 1 : (>>1$num + >>2$num);
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
```
Execution in makerchip:- 
![Fibonacci Series makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/c9616d00-78d8-4164-9b29-7cc52d621658)

## Lab:- Counter 

```TL-Verilog
\TLV
   $reset = *reset;
   
   $cnt[1:0] = $reset ? (0) : (>>1$cnt[1:0] + 1) ;
```
Execution in makerchip:- 
![counter](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/0ef32ff0-3620-48f7-8a35-5e4c76cf90b9)


## Representations of constants in verilog:- 

'0: All 0s (width based on context).
'X: All DONT-CARE bits.
16’d5: 16-bit decimal 5.
5'b00XX1: 5-bit value with DONT-CARE bits.
1: 32-bit (signed) 1.

Our simulator configuration:
● will zero-extend or truncate when widths are mismatched (without
warning)
● uses 2-state simulation (no X’s)

## Sequential Calculator:- 

```TL-Verilog 
\TLV
   $reset = *reset;
   
   $val1[31:0] = >>1$out;
   $val2[31:0] = $rand1[3:0];
   $sum = $val1 + $val2;
   $diff = $val1 - $val2;
   $prod = $val1 * $val2;
   $quot = $val1 / $val2;
   
   $out = $reset ? ( $op[1]?($op[0] ? $quot : $prod):($op[0] ? $diff : $sum) ) : 0;
   // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
   
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
```
Execution in makerchip:- 
![Sequential Calculator](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/484a78e5-59b1-4009-a20c-90bbd2a7f196)


</details>

<details>
  <summary> Pipelined logic :-  </summary>

A Simple Pipeline Pythagoras's Theorem :-

![Pythagoras's Theorem](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/7c3e6328-888f-49f2-bb31-36894d25609f)

Logic used:- 

![Pythagoras's Theorem logic](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/736a35c5-068c-4d66-b50c-5289b372670a)

The above logic is distributed into 3 stages:- 

![Pythagoras's Theorem logic distribution](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/32b635bc-2d60-42cd-9155-52303d69fd1a)

```TL-Verilog
`include "sqrt32.v";
|calc\
      @1
         $aa_sq[31:0] = $aa * $aa;
         $bb_sq[31:0] = $bb * $bb;
         
      @2
         $cc_sq[31:0] = $aa_sq + $bb_sq;
      @3
         $cc[31:0] = sqrt($cc_sq);
```

Stage1:- The inputs are squared.
Stage2:- The squared numbers are added
Stage3:- Root is taken for the sum.

Execution in makerchip:-
![Pipelining the Pythagoras's Theorem](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/7d9ccfc7-7f4c-410d-947c-7782eab980aa)

Staging is a physical attribute. No impact to behavior:- 
![Staging is a physical attribute  No impact to behavior](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/47d7bb31-c16d-4290-8261-06dbd589140b)

- Retiming changes in system verilog is very bug-prone, so it is easy to make these vhanges in tlverilog.
- In makerchip waveform viewer the output will be captured according to the time, so if there are 3 stages in the logic then the output of the present inputs will be after 2 cycles.

## Pipeline Logic Advantages:-
- In a non-pipelined system, a single operation may span multiple clock cycles, resulting in a relatively slow completion time. However, by introducing pipelining, the operation is divided into distinct stages, each executed in a single clock cycle. This architectural approach not only speeds up individual stages but also allows for concurrent execution of multiple stages. When pipelining is coupled with a higher clock frequency, it leads to a substantial reduction in the overall time required to finish an operation.
- Pipelining enables the parallel execution of various stages within an operation. As each stage is designed to be completed swiftly, the entire operation can be processed more efficiently. This enhanced throughput, when combined with an increased clock frequency, results in the ability to handle a greater number of operations within the same unit of time.

## Language syntax of TLVerilog :- 

Type of an identifier determined by symbol prefix and case/delimitation style.

Based on the first two letters of the variables:- 
- $lower_case: pipe signal
- $CamelCase: state signal (technically, this is “Pascal case”)
- $UPPER_CASE: keyword signal
- ``` >>1 ``` : Ahead by 1.


## Lab:- Pipeline 
```TL-Verilog
\TLV
   $reset = *reset;
   
   |comp
      @1
         $err1 = $bad_input | $illegal_op ;
      @3 
         $err2 = $overflow | $err1 ;
      @6
         $err3 = $err2 || $div_by_zero;
   
   
   
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```
Execution in makerchip:- 
![pipeline lab](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/a6d0981d-e677-4cbd-9a5a-9445e3bfe684)

### Counter and Calculator in Pipeline :- 
```TL-Verilog
\TLV
   
   |calc
      @1
         $reset = *reset;
         $cnt[1:0] = $reset ? (0) : (>>1$cnt[1:0] + 1) ;
         
         $val1[31:0] = >>1$out;
         $val2[31:0] = $rand1[3:0];
         $sum = $val1 + $val2;
         $diff = $val1 - $val2;
         $prod = $val1 * $val2;
         $quot = $val1 / $val2;
         $out = $reset ? ( $op[1]?($op[0] ? $quot : $prod):($op[0] ? $diff : $sum) ) : 0;
   
   // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
```

Execution in makerchip:- 
![Counter and Calculator in Pipeline](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/1068289e-5fbe-41c1-b76e-0fb018aaf577)

### Lab: 2-Cycle Calculator :- 

```TL-Verilog
\TLV
   
   |calc
      @1
         $val1[31:0] = >>2$out;
         $val2[31:0] = $rand1[3:0];
         $sum[31:0] = $val1[31:0] + $val2[31:0];
         $diff[31:0] = $val1[31:0] - $val2[31:0];
         $prod[31:0] = $val1[31:0] * $val2[31:0];
         $quot[31:0] = $val1[31:0] / $val2[31:0];
         

      @2
         $reset = *reset;
         $valid = $reset ? (0) : (>>1$valid + 1) ;
         $op[1:0] = $reset | $valid ;
         $out[32:0] = $op[1] ? ($op[0] ? $quot[31:0] : $prod[31:0]) : ($op[0] ? $diff[31:0] : $sum[31:0]) ;
   // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
   
   
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;

```

Execution in makerchip:- 
![Lab 2-Cycle Calculator](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/1e3a9942-ed26-4006-af1e-d2b6d3555c42)

</details>


<details>
  <summary>Validity :- </summary>

Validity provides:
- Easier debug
- Cleaner design
- Better error checking
- Automated clock gating


## Clock Gating:- 
- Used to save power while transferring clock.
- Clock signals are distributed to EVERY flip-flop.
- Clocks toggle twice per cycle.
- This consumes power.
- Clock gating avoids toggling clock signals.

### File structure in makerchip :-

- \m5_TLV_version 1d: tl-x.org :- Version of makerchip being used and tl-x.org contains tyhe documentation
- m5 :- Macro language used for processsing.
- m5_makerchip_module :- Expands the inputs and outputs in the NAV file.
- \sv  :- The system verilog codes.
- \TLV :- Where tlverilog code is defined.

### Distance Accumulator :- 

- Each valid transaction in the |calc pipeline will represent a valid hop.
- $aa is the forward-facing distance of the hop, and $bb is the lateral distance, so $cc gives us the distance of a hop.
- We add to our pipeline an accumulator accumulating the computed $cc values and providing a running total distance

![Distance Accumulator](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/0742436b-0041-4865-8f7c-60305af26e5b)

Implementing in Makerchip :- 
```TL-Verilog
\SV
`include "sqrt32.v";

\TLV
   $reset = *reset;
   
   |calc
      @1
         $reset = *reset ;
      ?$valid
         @1
            $aa_sq[31:0] = $aa * $aa;
            $bb_sq[31:0] = $bb * $bb;

         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $tot_dst = $reset ? 0 : ($valid ? >>1$tot_dst + $cc : >>1$tot_dst) ;

```

Execution in makerchip:- 
![Total Distance (Makerchip walkthrough)](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/9ed4b7a2-75c7-4cfa-a09d-8fa59bb2f5fb)

## Cycle Calculator with Validity :- 
$valid_or_reset = $valid || $reset; as a when condition for calculation instead of zeroing $out.

```TL-Verilog
\TLV
   $reset = *reset;
   |clac  
      @1
         $reset = *reset ;
      ?$valid
         @1
            
            $val1[31:0] = >>2$out[31:0];
            $sum = $val1 + $val2;
            $diff = $val1 - $val2;
            $prod = $val1 * $val2;
            $quot = $val1 / $val2;
            $valid = >>1$valid +1 ;
            $valid_or_reset = $valid || $reset;
      @2
         $out[31:0] = $valid_or_reset ? ($op[1]?($op[0] ? $quot : $prod) : ($op[0] ? $diff : $sum) ) : 0 ;
  
```
Execution in makerchip :- 
![Cycle Calculator with Validity](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/a8f098aa-ea3f-475b-8c4a-92accca52323)


</details>

<details>
  <summary>Day 3 Wrap-up :- </summary>

##  Hierarchy Concept :- 






</details>



</details>


<details>
<summary>DAY_4 Basic RISC-V CPU micro-architecture :- </summary>

<details>
<summary>Introduction to Simple RISC-V Micro-architecture :- </summary>

## RISC-V Block Diagram :- 
- Instruction Fetch (IF) Unit: This unit fetches instructions from memory.
- Instruction Decode (ID) Unit: It decodes the fetched instructions and determines the required operations.
- Execution Unit (EXU): This unit performs the actual execution of instructions, which may include arithmetic, logical, and data manipulation operations.
- Memory Unit (MEM): The memory unit handles data transfers between the CPU core and memory, including load and store operations.
- Write-back Unit (WB): This unit handles writing the results back to registers.
![RISC-V Block Diagram](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/789e8a0e-6efa-4cb2-b3dc-59326cfb6508)

### Implementation Plan :- 
![Implementation Plan](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/3e5a3e82-9393-4a9e-8afe-e72784f338c3)

### Implementation in  makerchip  :- 
![Implementation in  makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/3297600d-4b41-4287-8615-e970c550abe7)

### Visualization:- 
![Visualization](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/10fc316d-e564-441b-a2c3-99fcdfaaabca)

</details>


<details>
  <summary>Instruction Fetch  :- </summary>

## Instruction Fetch (IF) Unit :-
- The IF unit is responsible for fetching instructions from the memory, typically the program memory or instruction cache.
- During this stage, the IF unit retrieves the instruction at the current program counter (PC) address, increments the PC to point to the next instruction, and passes the fetched instruction to the next stage of the pipeline.


### Lab: Next PC :-
- Reset $pc[31:0] to 0 if previous instruction was a “reset instruction” (>>1$reset).
- Increment by 1 instruction (32’d4 bytes) thereafter.
- We’ll add branch later.
 
```
\TLV
   $reset = *reset;
   
   $pc_out[31:0] = >>1$reset ? (0) : (>>1$pc_prev[31:0] + 32'h4) ;
```
![pc next](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/48e417aa-b36b-4473-a5f1-2cf7844adfe5)


### Lab: Fetch :- 
-Uncomment //m4+imem(@1), and //m4+cpu_viz(@4) compile, and observe log errors.
```tlverilog
\TLV
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         
         $pc[31:0] = >>1$reset ? (0) : (>>1$pc[31:0] + 32'd4) ;
      @1
         $imm_rd_en = !$reset;
         $imm_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         $instr[31:0] = $imem_rd_data[31:0];
         
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;

   |cpu
      m4+imem(@1)    // Args: (read stage)
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   m4+cpu_viz(@4)    // For visualisation
```
![Instruction fetch](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/590ba10a-f389-4000-9734-7311f8ee69bc)

</details>

<details>
  <summary>Instruction Decode :- </summary>


## Decode :- 

- The ID unit follows the IF unit in the pipeline and is responsible for decoding the fetched instructions.
- It determines the required operations based on the instruction's opcode (operation code) and may identify the operands involved in the operation.
- In the ID stage, the CPU examines the instruction, identifies the operation to be performed (e.g., addition, subtraction, load, store), and may also determine which registers or memory locations are involved in the operation.

![Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/a2ce825d-a694-49d3-a32f-307691692e86)

- The opcode fetched from the memory is decoded for the next steps and moved to the appropriate registers.
- Below image shows hoe decode is determining the TYPE OF RISC V instructions set (Various types of Instructions in RV32 are I, R, S, J, U)

## Instruction Types Decode :- 

![Instruction Types Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/285a9a64-8e8f-41ef-8887-6e05e0fd0f02)

``` tlverilog
@1 
         //$pc[31:0] = >>1$reset ? 32'b0 : >>1$taken_br ? >>1$br_tgt_pc : >>1$pc + 32'd4;
         $imem_rd_en = !$reset;
         $instr[31:0] = $imem_rd_data[31:0];
         //$instr[31:0] =  $imem_rd_en ? 32'b0 : >>1$imem_rd_data[$imem_rd_addr];
         $imem_rd_addr[3-1:0] = $pc[3+1:2];
         
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'bxx001;
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         $is_r_instr = $instr[6:2] ==? 5'b01xxx ||
                       $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] ==? 5'bxx100;
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         $is_b_instr = $instr[6:2] ==? 5'b11000;
         $is_j_instr = $instr[6:2] ==? 5'b11011;
```

![Instruction Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/09d88c63-99bf-432b-9a18-427fff53222c)


## Instruction Immediate Decode :- 
![Instruction Immediate Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/cdf7f0ee-818a-4526-a485-f5406f7e31ef)

```
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}}, $instr[30:20] } 
                                  : $is_s_instr ? {{21{$instr[31]}}, $instr[30:25],$instr[11:7]} 
                                  : $is_b_instr ? { {19{$instr[31]}} , $inst[7] , $instr[30:25] , $instr[11:8] ,1'b0}
                                  : $is_u_instr ? { $instr[31] , $instr[30:12], 12'b0 }
                                  : { {12{$instr[31]}} , $instr[20], $instr[30:25], $instr[24:21] ,1'b0 };
         
```

![Instruction Immediate Decode makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/60f9f68f-3fd1-44d7-be10-016b1dc10678)

## Extracting  other instruction fields: $funct7, $funct3, $rs1, $rs2, $rd, $opcode :- 

![Extract other instruction fields](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/57df5eca-c112-4636-8878-718299baaf88)

```
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         $rs1_valid = $is_r_instr ||  $is_i_instr ||$is_s_instr || $is_b_instr;
         $func3_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         $func7_valid = $is_r_instr;
         $rd_valid = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr;
         $opcode_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr || $is_u_instr || $is_j_instr;
```

![Extract other instruction fields Makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/97ddee6b-7ff2-44c0-aa36-19a17b123988)


## Instruction Decode :- 
![Instruction Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/e4fcdaf8-6a7c-4cfc-9833-588a5d5b57f3)

```
      @1
         $dec_bits[10:0] = {$funct7[5],$funct3[2:0],$opcode[6:0]};
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_load = $dec_bits ==? 11'bx_000_0000011;
         //$is_load = $dec_bits ==? 11'bx_001_0000011;
         //$is_load = $dec_bits ==? 11'bx_010_0000011;
         //$is_load = $dec_bits ==? 11'bx_100_0000011;
         //$is_load = $dec_bits ==? 11'bx_100_0000011;
         $is_lui = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr = $dec_bits ==? 11'bx_000_1100111;
         $is_sb = $dec_bits ==? 11'bx_000_0100011;
         $is_sh = $dec_bits ==? 11'bx_001_0100011;
         $is_sw = $dec_bits ==? 11'bx_010_0100011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0010011;
         $is_xori = $dec_bits ==? 11'bx_100_0010011;
         $is_ori = $dec_bits ==? 11'bx_110_0010011;
         $is_andi = $dec_bits ==? 11'bx_111_0010011;
         $is_slli = $dec_bits ==? 11'b0_001_0010011;
         $is_srli = $dec_bits ==? 11'b0_101_0010011;
         $is_srai = $dec_bits ==? 11'b1_001_0010011;
         $is_add = $dec_bits ==? 11'b0_000_0110011;
         $is_sub = $dec_bits ==? 11'b1_000_0110011;
         $is_sll = $dec_bits ==? 11'b0_001_0110011;
         $is_slt = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu = $dec_bits ==? 11'b0_011_0110011;
         $is_xor = $dec_bits ==? 11'b0_100_0110011;
         $is_srl = $dec_bits ==? 11'b0_101_0110011;
         $is_sra = $dec_bits ==? 11'b1_101_0110011;
         $is_or = $dec_bits ==? 11'b0_110_0110011;
         $is_and = $dec_bits ==? 11'b0_111_0110011;
```
![Instruction Decode Makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/92883d4b-17ef-4678-80a1-f95d6d40da07)


</details>



<details>
  <summary>Register File Read :- </summary>

- Register File: This is where the general-purpose registers (GPRs) are stored.
- RISC-V typically has a small number of registers, often 32, which can be used for storing data and addresses.

![Register File Read](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/68567fb4-aa04-4d20-9c41-e47520bd8279)

```
      @2 
         $rf_rd_en1 = $rs1_valid ? $rs1[$rf_rd_index1[4:0]] : 32'b0;
         $rf_rd_en2 = $rs2_valid ? $rs2[$rf_rd_index2[4:0]] : 32'b0;
         
         //$rf_rd_en1 = $rs1_valid ? $rs1[$rf_rd_index1[4:0]] : 32'b0;
         //$rf_rd_en2 = $rs2_valid ? $rs2[$rf_rd_index2[4:0]] : 32'b0;
```
![Register File Read Makerchip ](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/c8505adf-2537-4f7f-a453-993178fbeefd)

## Register File Read (part 2) :- 
- Assign $src1/2_value[31:0] to register file outputs.
```
         //$src1_value[31:0] =  $rf_rd_data1;
         //$src2_value[31:0] =  $rf_rd_data2;
         $src1_value[31:0] = >>2$rf_wr_en && ($rd == $rs1) ? >>1$result : $rf_rd_data1;
         $src2_value[31:0] = >>2$rf_wr_en && ($rd == $rs2) ? >>1$result : $rf_rd_data2; 
```
![Register File Read (part 2) Makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/4b3dc76e-8bb1-479e-bbb3-a37a53aed763)


</details>

<details>
  <summary>ALU ( arithmetic-logic unit)</summary>

- An arithmetic-logic unit (ALU) is the part of the CPU that carries out arithmetic and logic operations.
- Below image shows an ADDI (ADD Immediate) instruction computation.
![ALU](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/3f8bebed-eeb4-494f-919e-281221759e46)
```
         //ALU Implmentation - ADD , ADDI , SUB, OR , AND, XOR PLUS IMMEDIATE
         $result[31:0] = $is_add ?
                         $src1_value[31:0] + $src2_value[31:0] :
                         $is_sub ?
                         $src1_value[31:0] - $src2_value[31:0] :
                         $is_and ?
                         $src1_value[31:0] & $src2_value[31:0] :
                         $is_or ?
                         $src1_value[31:0] | $src2_value[31:0] :
                         $is_xor ?
                         $src1_value[31:0] ^ $src2_value[31:0] :
                         $is_addi ? 
                         $src1_value[31:0] + $imm[31:0] :
                         $is_andi ?
                         $src1_value[31:0] & $imm[31:0] :
                         $is_ori ?
                         $src1_value[31:0] | $imm[31:0] :
                         $is_xori ?
                         $src1_value[31:0] ^ $imm[31:0] :
                         //LOAD AND STORE COMPUTATION
                         $is_load ?
                         $src1_value[31:0] + $imm[31:0] :
                         $is_s_instr ?
                         $src1_value[31:0] + $imm[31:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS SHIFT OPERATIONS
                         $is_slli ?
                         $src1_value[31:0] << $imm[5:0] :
                         $is_srli ?
                         $src1_value[31:0] >> $imm[5:0] :
                         $is_sll ?
                         $src1_value[31:0] << $src2_value[4:0] :
                         $is_srl ?
                         $src1_value[31:0] >> $src2_value[4:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ?
                         {$imm[31:12], 12'b0} :
                         $is_auipc ?
                         $pc + $imm :
                         $is_jal ?
                         $pc + 32'd4 :
                         $is_jalr ?
                         $pc + 32'd4 :
                         $is_srai ?
                         { {32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
                         $is_slt ?
                         ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_slti ?
                         ($src1_value[31] == $imm[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_sra ?
                         { {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
                         32'bx;
         
         $sltu_rslt[31:0]  = $src1_value[31:0] < $src2_value[31:0];
         $sltiu_rslt[31:0] = $src1_value[31:0] < $imm;
```

![ALU makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/32f69060-402f-4072-8faf-56cb340204c6)


</details>


<details>
  <summary>Register File Write :- </summary>

- Register File Write is a stage in a pipelined CPU architecture where the results of an instruction's execution are written back to the processor's register file
-  This is where the general-purpose registers (GPRs) are stored. RISC-V typically has a small number of registers, often 32, which can be used for storing data and addresses.
![Register File Write](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/94be137d-452c-476d-8bbf-fc48b8daeced)


```
         //Register File Write - Considering three cases
         // Will be enabled only when Valid Bit which is helping us construct pipeline is high
         // along with it destination register needs to be valid and destination register cannot
         // be zero as it will be treated as X0 by RISCV ISA standards. 
         $rf_wr_en = ($valid && $rd_valid && $rd != 5'b0) || >>2$valid_load;
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd;
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data : $result;
```

![Register File Write makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/7350b73f-a525-487f-9dbc-51e824ec5fff)

</details>

<details>
  <summary>Branches :- </summary>

![Branches ](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/2372040a-586c-40ff-a50f-19222dbcd3f7)

```
         //Branch Target for Immediate Instruction PC increment
         $br_tgt_pc[31:0] = $pc + $imm;
         
         //Jump Target for Immediate Instruction PC increment
         $jalr_tgt_pc[31:0] = $src1_value + $imm;
         
      @3   
         //BRANCHING Instructions 
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ?($src1_value != $src2_value) :
                     $is_bltu ? ($src1_value <  $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bgeu ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                            1'b0;
         
         //BRANCHING PROBLEM SOLUTION FOR READ AFTER WRITE CADENCE 
         // In the case of read after write with a branch condition in next cycle
         // The valid bit here will help increment the PC every cycle instead of every 3 cycles.
         $valid = !(>>1$valid_taken_br || >>2$valid_taken_br || >>1$valid_load || >>2$valid_load); 
         
         //Valid Signal for branching which feeds into PC so that during pipeline unnecesarily PC doesn't
         //Increment for INVALID CYCLES. 
         $valid_taken_br = $valid && $taken_br;
```

![Branches makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/d6d4d139-aa91-4ce8-84f2-e523afe454ec)

</details>

<details>
  <summary>Lab: Testbench :- </summary>

```
   *passed = |cpu/xreg[17]>>5$value == (1+2+3+4+5+6+7+8+9);
```
Simulation PASSED!!!
![Simulation PASSED!!!](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/e87f282f-0304-4806-b50a-ae6c3b9298a5)

 
</details>

</details>


<details>
  <summary>Day 5 - Complete Pipelined RISC-V CPU micro-architecture :- </summary>

- Converting non-piepleined CPU to pipelined CPU using timing abstract feature of TL-Verilog.
<details>
  <summary>Waterfall Diagram & Hazards :-  </summary>
- "waterfall logic" in pipelining means a sequential and straightforward processing of instructions in a pipeline, with each stage completing its work before passing it to the next stage.
- In a waterfall pipeline, an instruction moves from one stage to the next only when the preceding stage has fully completed its processing.
- This approach ensures that the order of execution of instructions is maintained, and there is no overlap or concurrent execution between different stages of the pipeline.

![Waterfall Logic Diagram](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/ad4c7aad-3e13-4afb-8053-286d493dd608)

- Converting non-piepleined CPU to pipelined CPU using timing abstract feature of TL-Verilog. 

Waterfall Diagram & Hazards :- 

![Waterfall Diagram   Hazards 2](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/39f52acf-0a4c-4ba5-b37e-4c725fc2b891)

![Waterfall Diagram   Hazards 1](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/8811031a-9fed-4692-b7f0-ab9d18c14494)

 Solution :- Pipelining it every 3 cycles 
 ![Waterfall Diagram   Hazards solution](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/1fc776c1-106f-4585-8be0-1f00ce9a09f7)

</details>

<details>
  <summary>Solutions to Pipeline Hazards :- </summary>

Pipelining the CPU
The above single stage Core was enhanced to be staged across 3 stages in a pipeline, Final output where the core is computing Sum of 9 number. Converting non-pipelined CPU to pipelined CPU using timing abstract feature of TL-Verilog. This allows easy retiming wihtout any risk of funcational bugs. More details reagrding Timing Abstract in TL-Verilog can be found in IEEE Paper "Timing-Abstract Circuit Design in Transaction-Level Verilog" by Steven Hoover.

Pipelining helps improve the operating frequency by breaking down the micro-arch ito substages that consume lesser time.But this process intriduces some hazards and dependencies such as
- Data Hazards
- Structural Hazards
- Control Hazards
- Name Dependence
- Anti Dependence
- Output Dependence
```
|<pipe-name>
   @<pipe stage>
      Instructions present in this stage
      
   @<pipe_stage>
      Instructions present in this stage


*passed = |cpu/xreg[17]>>5$value == (1+2+3+4+5+6+7+8+9);
```


- Register file bypass
![Register file bypass](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/2c3e75ab-097c-4098-a9bb-73b8df78f7c1)

- Correct the branch target path :-
```
         $br_tgt_pc = 1>>$pc + $imm; 
         $valid_taken_br = $valid && $taken_br;
         $valid_load = $valid && $is_load;
         //$valid_jump = &valid && $imm;
```
![Correct the branch target path](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/59a2ddec-589e-47c2-9ae7-781d4b1d35ff)

- Complete Instruction Decode :-
```
         $dec_bits[10:0] = {$funct7[5],$funct3[2:0],$opcode[6:0]};
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_load = $dec_bits ==? 11'bx_000_0000011;
         //$is_load = $dec_bits ==? 11'bx_001_0000011;
         //$is_load = $dec_bits ==? 11'bx_010_0000011;
         //$is_load = $dec_bits ==? 11'bx_100_0000011;
         //$is_load = $dec_bits ==? 11'bx_100_0000011;
         $is_lui = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr = $dec_bits ==? 11'bx_000_1100111;
         $is_sb = $dec_bits ==? 11'bx_000_0100011;
         $is_sh = $dec_bits ==? 11'bx_001_0100011;
         $is_sw = $dec_bits ==? 11'bx_010_0100011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0010011;
         $is_xori = $dec_bits ==? 11'bx_100_0010011;
         $is_ori = $dec_bits ==? 11'bx_110_0010011;
         $is_andi = $dec_bits ==? 11'bx_111_0010011;
         $is_slli = $dec_bits ==? 11'b0_001_0010011;
         $is_srli = $dec_bits ==? 11'b0_101_0010011;
         $is_srai = $dec_bits ==? 11'b1_001_0010011;
         $is_add = $dec_bits ==? 11'b0_000_0110011;
         $is_sub = $dec_bits ==? 11'b1_000_0110011;
         $is_sll = $dec_bits ==? 11'b0_001_0110011;
         $is_slt = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu = $dec_bits ==? 11'b0_011_0110011;
         $is_xor = $dec_bits ==? 11'b0_100_0110011;
         $is_srl = $dec_bits ==? 11'b0_101_0110011;
         $is_sra = $dec_bits ==? 11'b1_101_0110011;
         $is_or = $dec_bits ==? 11'b0_110_0110011;
         $is_and = $dec_bits ==? 11'b0_111_0110011;
```
![Complete Instruction Decode](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/5173c48f-3806-43a2-8b8f-e397df8b3632)

- Complete ALU :-
```
 //ALU Implmentation - ADD , ADDI , SUB, OR , AND, XOR PLUS IMMEDIATE
         $result[31:0] = $is_add ?
                         $src1_value[31:0] + $src2_value[31:0] :
                         $is_sub ?
                         $src1_value[31:0] - $src2_value[31:0] :
                         $is_and ?
                         $src1_value[31:0] & $src2_value[31:0] :
                         $is_or ?
                         $src1_value[31:0] | $src2_value[31:0] :
                         $is_xor ?
                         $src1_value[31:0] ^ $src2_value[31:0] :
                         $is_addi ? 
                         $src1_value[31:0] + $imm[31:0] :
                         $is_andi ?
                         $src1_value[31:0] & $imm[31:0] :
                         $is_ori ?
                         $src1_value[31:0] | $imm[31:0] :
                         $is_xori ?
                         $src1_value[31:0] ^ $imm[31:0] :
                         //LOAD AND STORE COMPUTATION
                         $is_load ?
                         $src1_value[31:0] + $imm[31:0] :
                         $is_s_instr ?
                         $src1_value[31:0] + $imm[31:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS SHIFT OPERATIONS
                         $is_slli ?
                         $src1_value[31:0] << $imm[5:0] :
                         $is_srli ?
                         $src1_value[31:0] >> $imm[5:0] :
                         $is_sll ?
                         $src1_value[31:0] << $src2_value[4:0] :
                         $is_srl ?
                         $src1_value[31:0] >> $src2_value[4:0] :
                         //ALU FOR MISCELLANEOUS OPERATIONS
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ?
                         {$imm[31:12], 12'b0} :
                         $is_auipc ?
                         $pc + $imm :
                         $is_jal ?
                         $pc + 32'd4 :
                         $is_jalr ?
                         $pc + 32'd4 :
                         $is_srai ?
                         { {32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
                         $is_slt ?
                         ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_slti ?
                         ($src1_value[31] == $imm[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_sra ?
                         { {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
                         32'bx;
```
  
</details>


<details>
  <summary>Load/Store Instructions and Completing RISC-V CPU :- </summary>

1. Uncomment //m4+dmem(@4).
2. Connect interface signals above using address bits [5:2] to perform load and
store (when valid).

```
m4_asm(SW, r0, r10, 10000)
m4_asm(LW, r17, r0, 10000)
```
![Load Store Instructions and Completing RISC-V CPU](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/352bd6b0-5cbe-452d-ad55-6dacf2dabc96)






</details>





















