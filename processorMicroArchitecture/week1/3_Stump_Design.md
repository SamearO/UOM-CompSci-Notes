# Stump Design

## Internal Sizes

* 16 Bit architecture hence:
    * The IR is 16 bits.
    * The address bus is 16 bits.
    * Each Memory location stores 16 bits.
* There are 8 registers, R0 is always 0 and does not change, R7 is the PC.

## Instruction Format

| 15-13        |       12-11        |             10 - 0 |
| ------------ | :----------------: | -----------------: |
| 3 bit opcode | 2 Bit Extra (TODO) | 11 Bit Instruction |

# Instruction Types

## Type 1
* Available for all Instructions except for Branching
* Destination Register and 2 Source Registers.
* If it is a Load/Store, bit 11 is used to say if it is a load/ store. Otherwise it is used to indicate if flags should be set.

| 15-13        |             12              |      11 | 10-8    | 7-5   | 4-2   | 1-0   |
| ------------ | :-------------------------: | ------: | ------- | ----- | ----- | ----- |
| 3 bit opcode | Always 0 to indicate Type 1 | Special | DST reg | Src A | SRC B | Shift |


## Type 2

* Destination Register, 1 Source Register, 1 Immediate Value
* For the immediate, to convert to 16 bits, the sign bit is extended to all the unknown bits.
* For LD/ST, 11 set to 1 

| 15-13        |             12              | 11      |  10 - 8 | 7 - 5 | 4 - 0     |
| ------------ | :-------------------------: | ------- | ------: | ----- | --------- |
| 3 bit opcode | Always 1 to indicate Type 2 | Special | DST Reg | SRC A | Immediate |

## Type 3
* Used for Branch Instructions
* Offset is added to the PC

| 15-12  |       11-8        |     7 - 0 |
| ------ | :---------------: | --------: |
| All 1s | Branch Conditions | PC Offset |

# Stump Addressing modes and Instructions

## Immediate Addressing (Type 2) 
* Instruction and Operand, operand is used directly.

## Register Addressing (Type 1 and Type 2)
* Register numbers are specified and are used directly

## Register Indirect Addressing (Type 2)
* Used in Load/ Store operations, the register is in the instruction.
* The register points to an address which points to the operand in memory.

## Immediate Offset Addressing (Type 2)
* Used in Load/ Store Type 2 operations.
* Register and offset are in the instruction
* Register has an address which is added to the offset to get the operand in Memory.

## Register Offset Addressing (Type 1)
* 2 registers in the instruction who's values are added to get the address of a value in memory.

## PC Offset Addressing (Type 3)
* 1 Offset in the instruction, which is added to the PC and is saved to the PC. 
* Used in branch instructions.
