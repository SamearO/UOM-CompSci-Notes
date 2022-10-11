# Verification and Testing

## Design steps
Fabricating chips and doing testing is expensive, hence multiple steps are used to minimise cost and ensure testing is thorough.

1. Verilog description is created by designer.
2. CAD tools compile the design, syntax errors are caught here.
3. Simulators and test benches are used to test the functionality of the design. If tests fail, return to step 1.
4. Verification testing is run to ensure the design works as expected by the specification.
5. The hardware is finally produced.

## Hierarchical approach

Exhaustive testing is not possible due to time constraints, hence:
1. simple elements are tested individually. 
2. integration tests are run to ensure the design is sound.

# Testbench

Testbenches are used to apply data to inputs of designs and view the resulting outputs.

* In verilog test benches, all signals used including the input and outputs must be declared.
* Inputs are usually defined as `reg` as `=` will be used to assign values to them.
* Outputs will be defined with `wire`.

## Example Testbench
```verilog
module Stump_ALU_test();
//inputs
reg [15:0] input_a;
reg [15:0] input_b;
// output
wire [15:0] result;

// Name followed by the module
Stump_ALU ALU(.input_a(input_a), .input_b(input_b), .result(result));

// test code goes here
initial
begin
//test code 
end

endmodule
```

## Using the Testbenches
* For sequential designs, a clock input must be given to run the test.
```verilog
begin
input_a = 16'h0000
#100 input_b = 16'hFFFF // #100 refers to a delay of 100 ticks. 

// for loops in tests.
integer count
for (count =0; count<10; count = count+1)
    // do stuff

// Sending output to a file for examining test results/ running automated verification
integer file_handler
file_handle = $fopen("file_name");
$fdisplay(file_handler, "Some text\n") // writing to the file
$fdisplay(file_handle, "Output state: %x", result); // writing results to the file
$fclose(file_handler); // closing the file handler

// Setting the clock for sequential circuits
initial clock = 0; 
always #50 clock = ~clock; //Clock changes states every 50 ticks.

end

```