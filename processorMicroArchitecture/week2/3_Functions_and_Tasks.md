# Functions and Tasks

`Functions` and `tasks` are used to break down behavioral descriptions into more manageable chunks that can be called from `modules`.

## Tasks vs Functions
* Tasks can have `any number` of inputs and outputs, whereas functions must have at least 1 input and only `1 output`.
* Tasks can model both `combinatorial` and `sequential` logic whereas functions can only model `combinatorial` logic. This is because tasks can contain timing and event control systems as well as run concurrently as they are separate procedures.
* Tasks can call other `functions` or `tasks`, `functions` can only call other `functions`.
* Functions must compute a value to return that are assigned to a variable when called.
* Both tasks and functions have their inputs and outputs (except functions don't have declared outputs) declared after their headers.
* Functions must reside within a module but tasks can be included from other files.
* Tasks are calls to separate procedural statements hence they cannot be called from an `assign`. Functions can be called from `=`, `<=` or `assign`.
* Tasks don't return values to expressions however they can change the state of the inputs and outputs passed to it. Functions return a single value to the expression where it was called.

## Tasks
* Begin with the keyword `task` and end with the keyword `endtask`.

```verilog
// Example module to create task
module example_module(input wire [7:0] in, output reg [7:0] out);
    always @ (*)
        example_task(in, out);

    // Task defined within the module
    task example_task;
        input [7:0] to_multiply;
        output [7:0] mult_out;

    begin
        mult_out = to_multiply * 2;
    end

    endtask

endmodule
```

## Functions
* Begin with `function` and end with the keyword `endfunction`.
* The output name is the name of the function.

```verilog
// Example module to create task
module example_module(input wire a, b, output wire c);

assign c = example_function(a,b)

function example_function;
    input a, b;

begin
    // output is the name of the function.
    example_function = a + b

endfunction
endmodule

```