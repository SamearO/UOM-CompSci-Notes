# Specialised Processing Architectures

* Specific applications demand particular types of processing that can be accelerated with specific hardware that takes advantage of parallelism or other techniques.
* Thus co-processors can be used to transparently improve the performance in specific applications.
* They use reserved space in the instruction set as needed, however if the coprocessor is not present/ the instruction is not taken, the CPU treats it as an illegal instruction thus creating an exception.
* This exception can be detected by the operating system (`emulator trap`) to run the instruction in software instead.

## Floating Point Unit Coprocessors
* They have hardware for arithmetic operations on floating points as well as bit shifting and square roots.
* Floats are good for representing very large and very small values economically.
* If FP operations are used a lot, it justifies the large size of the FPU.

## Intergrating co processors into the CPU
* The demand for coprocessed instructions has increased (eg in Digital Signal Processing).
* Hence general purpose CPUs are now coming with extended ISAs to target these instructions as well as technologies like `SIMD` wherein the CPU can process more than 1 instruction per clock cycle.
* Superscalar extensions can be used to break up 32 bit registers into smaller `vectors` to increase throughput on smaller numbers using existing hardware. (adding 4 8 bit numbers at once, with a gate to prevent carries)
* `Very long instruction words` can be used to explicitly specify which instructions should be executed in parallel (done by the compiler) to allow for zero overhead loops.