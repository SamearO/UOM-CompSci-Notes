# Verilog 

## Modules

* Takes input signals and generates some output signals based on some behaviours.
* Has inputs and outputs defined as either `wire` or `reg`.
* Inputs are always `wire`.
* Outputs are `wire` if the `assign` keyword is used and the module uses structural verilog.
* Outputs are `reg` when either blocking or non-blocking assignments are used.

## Module Implementations

### Behavioral verilog

```verilog
module mux_2to1(input wire d0, d1, sel, output wire q);
    assign q = (sel) ? d1 : d0;
endmodule
```

### Structural verilog
```verilog
module mux_2to1(input wire d0, d1, sel, output wire q);
    always @ (*)
        case (sel)
            1'b0: q = d0;
            1'b1: q = d1;
        endcase
endmodule
```

## Sequential Verilog

* Using always statements can be used for implementing sequential verilog.
* If a reset signal is supposed to be asynchronous, then it should be in the sensitivity list of the always statement
```verilog
// Does stuff every time the posedge of the clock is turned on
always @ (posedge clk) // posedge is the rising edge, negedge is the nedgative edge
```

```verilog
// async reset
always @ (posedge clk, posedge reset)
```

## Named Variables

Instead of memorizing variable positions, variables can be passed explicitly.

```verilog
wire parameter_that_gets_passed;
object module_being_referrenced(.argument(parameter_that_gets_passed))

```