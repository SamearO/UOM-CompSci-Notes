# Floating Point Representations

## Advantages of Floating Point Representations
* Larger range than `fixed point numbers` (putting a decimal point in between a series of bits)
* Has a `sliding window of precision` that reduces loss of precision when 2 large numbers are divided.

## Normalised floating point form 
* Provides a unique representation for a number and allows the maximum possible precision given a number of bits.
* The normalised version of a `positive fractional` number has no leading zeroes after the binary point, thus always starts as `0.1`.
* The opposite is true for `negative numbers` which start with `1.0`.
* Then the mantissa contains the significant bits of the number.
* Hence the normalised version would allow for `n-1` bits to be used after the binary point if `n` is the number of bits available for the mantissa.
* Hence `-0.046875` is represented as `1.01* 2^-4`. If not normalised, `1.101 * 2^-3` and `1.1101 * 2^-2` would be valid.

## IEEE 754 Form
* With 32 bits, the first bit is the sign bit, 0 for positive, 1 for negative.
* The next 8 bits are the exponent.
* The final 23 bits are the mantissa.
* Thus the number = `(-1)^sign * (1.mantissa) * 2^(exponent-127)`
* The mantissa is appended to a 1 as 0 cannot be at the left of the decimal in scientific notation, leaving it to always be 1. 
* The exponent has 127 subtracted from it to allow the exponent to cover positive and negative exponents.

## Multiplying floating point numbers
* Mantissas are multiplied, usually needing rounding.
* Exponents are added, care needs to be taken for overflows.
* Sign bits are XORd.
* Normalisation of the result may be required.

## Adding floating point numbers
* Shift the smaller number's mantissa right until exponents are equal.
* Add or subtract the new mantissas.
* Renormalise.
* Floating point arithmetic is `not associative` hence the order of adding/ subtracting is important.