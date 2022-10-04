# The Main Programming Paradigms

Programming languages can be composed of 1 or more programming paradigms. However all programming languages are eventually compiled down to imperative machine code.

## Imperative Programming
* A sequence of steps that manipulate the program state. Eg: `Assembly`.
* Without any structure, the program can be confusing and difficult to debug.

### Imperative Structured
* Advanced control flow is used to make the program more structured Eg: `C`.
    * For loops
    * While loops
    * Conditionals
    * Functions

### Imperative Object Oriented
* Code is encapsulated into data and objects. Eg: `Java`.
* Well suited for problems with a lot of state.
* Easier reasoning about large code bases.
* Can be overkill for small projects.

### Imperative Concurrent 
* Execution threads/ processes are used to describe parallel/ interleaving code. Eg: `C`.
* Usually have methods for exploiting concurrency:
    * Shared memory
    * Message passing
    * Semi-automatic loop parallelization.

## Declarative Programming
* The programmer describes the meaning/ result of the computations. Eg: `HTML`.
* Has a higher level of abstraction.

### Declarative Functional
* Calling and composing functions to describe the program.
* First class functions (functions are treated as variables).
* Loops are implemented using recursion.
* Pure functions have no side effects (They take inputs and give outputs without changing any external state).

### Declarative Concurrent Programming
* Example: `Erlang`
* Does not have state so there is no need for synchronization.
