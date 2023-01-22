# Debugging

## Types of Bugs
* `Syntactical Errors`: The language used to write the code is incorrect, usually caught by IDEs.
* `Conceptual Errors`: The code works but works in an unintended manner.

## Systemic Approach to Fixing Bugs

### Isolate the problem
* Find a way to reliably replicate the problem.
* Narrow down the problem to a precise statement.
* Using test cases can help.

### Isolate the source of the problem
* `Brute force`: Work through the code till something odd is found.
* `Back tracking`: Start where the problem is detected and work backwards.
* `Binary search`: Approach the middle of the execution flow and find the problem.
* `Cause elimination`: Identify as many possible causes of the problem and work through them systematically.

### Implementing the fix
* Fix the problem
* Write unit tests for the fix and the code that was fixed.
