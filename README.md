# karthik_riscv

## Digital Logic with TL-Verilog and Makerchip:- 

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

```tlverilog
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

``` tlverilog
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
``` tlverilog
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

``` tlverilog
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
```tlverilog
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
```tlverilog
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

```tlverilog 
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

``` tlverilog
\TLV
   $reset = *reset;
   
   $num[31:0] = $reset ? 1 : (>>1$num + >>2$num);
   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
```
Execution in makerchip:- 
![Fibonacci Series makerchip](https://github.com/Karthik-6362/karthik_riscv/assets/137412032/c9616d00-78d8-4164-9b29-7cc52d621658)


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

``` tlverilog 
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
![Uploading Sequential Calculator.png…]()




</details>




























