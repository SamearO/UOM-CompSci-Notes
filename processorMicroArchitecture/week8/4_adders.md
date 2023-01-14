# Adders

## Ripple Carry Adders
* Are made of full adders that have the `carry out` of the previous bit become the `carry in` of the next bit.
* This is a simple design however the critical path is very long as the carry is calculated from the least significant bit to the most significant bit and each full adder needs to wait for the result of the previous one.

## Carry Look Ahead Adders
* Uses parallelism to speed up the process.
* It is more complex but has a shorter critical path.
* Uses the following principle:
    * Before a carry can be determined, the `carry state` of each bit being added can be one of 3:
        * `Kill`: inputs are both 0 so carry is not propogated
        * `Propogate`: inputs are different so carry is propogated
        * `Generate`: inputs are both 1 so carry out must be 1
    * This quickly generated info can be used to make bits ready to propogate a carry across the entire width with a single gate rather than rippling.

## Spintronics based adders
* Uses nanomagnetism instead of CMOS
* They are `non volatile`, `low power` and `thermally stable`. 