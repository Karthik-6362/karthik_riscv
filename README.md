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

```verilog
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

``` tlv
\m5_TLV_version 1d: tl-x.org
\m5
   
   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================
   
   //use(m5-1.0)   /// uncomment to use M5 macro library.
\SV
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m5_makerchip_module   // (Expanded in Nav-TLV pane.)
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
``` tlv
\m5_TLV_version 1d: tl-x.org
\m5
   
   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================
   
   //use(m5-1.0)   /// uncomment to use M5 macro library.
\SV
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m5_makerchip_module   // (Expanded in Nav-TLV pane.)
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

``` tlv
\m5_TLV_version 1d: tl-x.org
\m5
   
   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================
   
   //use(m5-1.0)   /// uncomment to use M5 macro library.
\SV
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m5_makerchip_module   // (Expanded in Nav-TLV pane.)
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
```tlv
\m5_TLV_version 1d: tl-x.org
\m5
   
   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================
   
   //use(m5-1.0)   /// uncomment to use M5 macro library.
\SV
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m5_makerchip_module   // (Expanded in Nav-TLV pane.)
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
```tlv
\m5_TLV_version 1d: tl-x.org
\m5
   
   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================
   
   //use(m5-1.0)   /// uncomment to use M5 macro library.
\SV
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m5_makerchip_module   // (Expanded in Nav-TLV pane.)
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









