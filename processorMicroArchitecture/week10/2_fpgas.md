# Field Programmable Gate Arrays

* FPGAs are chips that can be reprogramed to host any digital circuits.
* They can be seen as a `target technology` eg an ASIC or a `processing device` like a `CPU`.

## How FPGAs work
* They use `Look Up Tables` that translate input patterns into output patterns. More complex functions are implemented using `LUT Trees`.
* The routing is implemented with `multiplexers` that work as switches.

## FPGA vs ASICs
* Not all blocks are usable and the interconnection network is overhead.
* Compared to ASICs, they are larger, slower and more power hungry.
* Lower costs at lower volumes compared to ASICs.
* Reprogrammability allows for better utilization of the space taken by the FPGA.
* Some structures would be expensive to be implemented using LUTs like `multipliers`.

## FPGAs vs CPUs and GPUs
* FPGAs are best at `stream processing problems` and when pipelining can be applied on large data sets.
* They are better when tight synchronization of processing is required (eg many DSPs can be implemented on one FPGA).
* Better for bit fiddling operations.
* They can be reconfigured on the fly.
* They are worse than CPUs on `control dominated problems` (when there are many if else statements).
* They are worse tham GPUs on `data parallel problems` that need very little control flow and synchronisation.