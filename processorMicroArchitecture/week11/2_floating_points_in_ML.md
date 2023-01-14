# Floating Points in Machine Learning

* Lower precision floats can be used to reduce the time and space taken to train models.
* The extra space and time taken saved can increase the size of the model to improve the model's accuracy.

## BFloat16
* Has the same number of exponent bits as `float32` but 7 bits for the mantissa as opposed to 23.
* Thus where lower precision is required like in the activations and gradients, `bfloat16` can be used and `fp32` can be used for weights where the accuracy is required.

## Microsoft Floating Point
* Uses a shared exponent to achieve dynamic range but the exponent is shared between multiple floats.
