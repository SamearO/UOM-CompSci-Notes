# Shifters

* Shifters move the bits a number of places to the left or right.
* They are made by a cascade of flip flops where the output of each flip flop is connected to the data input of the next flip flop in the chain.

## Types of Shifters
* `One place shifter`: Shifts one place in one direction in one cycle.
* `Bidirectional shifter`: Shifts one place left or right in one direction
* `Barrel Shifter`: Shifts arbitrary number of places in one cycle

## Barrel Shifter
* Uses multiplexers to shift the bits, it requires a lot of wiring.
* Used in floating point arithmetic for add or subtract operations wherein the mantissas need to be aligned which requires shifting until the exponents match.
