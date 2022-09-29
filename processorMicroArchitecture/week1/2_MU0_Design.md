# MU0 Design

## Internal Sizes
Addresses are 12 bits and each address contains 16 bits worth of information hence:
* The PC is 12 bits wide.
* The IR is 16 bits, 4 of which are the instruction OPCode
* The Accumulator is 16 bits
* The Address bus is 12 bits.
* The Data bus is 16 bits.

## MU0 Instructions

### LDA and STA
* Contains an address who's contents are stored on the accumulator/ moved from the accumulator to the address

### ADD and SUB
* Contains an address who's contents are added/ subtracted from the accumulator
* Flags are always set.

### JMP JGE and JNE
* Contains an address where if the instruction is taken, the PC is replaced by the address.
* JMP: Always Jumps
* JGE: Accumulator >= 0
* JNE: Accumulator != 0

### STP
* Stops the processor and turns the Halt signal on.