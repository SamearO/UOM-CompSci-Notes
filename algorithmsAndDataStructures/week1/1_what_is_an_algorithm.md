# What is an algorithm

* A computation that takes a specific set of inputs, defines a set of steps that need to be taken to create the specified output.

## Factors that define an algorithm
* Is it correct (does it solve the computational problem).
* How does it perform
    * How much memory does it use
    * How fast is it
    * How does it scale with the available resources
    * How does it change based on the best case/ worst case/ average case scenarios.
* Will it terminate
* Is it deterministic
* Is it secure
* How 'good' is the output

## Comparing algorithms

To take into account differences in performance between computers, the relative speeds of algorithms are compared using `O(n)` notation wherein `n` refers to the amount of inputs. This shows how the time taken to run an algorithm scales with the number of inputs.

## Operations needed in an algorithm
Algorithms can be measured by how many `primitive operations` are required to run them given an input size `n`. The primitive operations are:

* Value assignments 
* Calling a method
* Performing arithmetic
* Comparing 2 elements
* Indexing into an array
* Following an object method
* Returning from a method

Algorithms are compared in the `worst case` scenario given the above. For example:

```python
def arrayMax(arr):
    highest = arr[0]
    for i in range(len(arr)):
        if arr[i] > highest:
            highest = arr[i]
    return highest
```

* 2 Primitive operations for assigning highest.
* 1 for assigning i to 1
* n for assigning checking if i < n  every time the for loop is iterated
* 4 operations for indexing into the array, comparing it to highest, incrementing and assigning i.
* The previous operation would have used 6 if it was higher than highest.
* Thus between 4(n-1) and 6(n-1) for the loop body
* 1 for returning

Thus in total the best case is `5n` and the worst case is `7n-2`.