# SM Charts

## SM chart elements

### State box

* The state box represents a state in the FSM and can have multiple inputs and outputs.
* It also has a name and a list of state (Moore) outputs that turn on concurrently when entering the state.
* Represented as a rectangle.

### Decision box

* Contains a boolean expression that has 2 output paths for True and False that can lead to State Boxes, other Decision boxes or output boxes.
* Represented as a diamond or a hexagon. 

### Output Boxes

* They have only 1 input and 1 output and the input must be from a decision block as it is meant to go high as a result of a decision.
* Mealy as the outputs are dependant on the state and the status of any input signals. 
* Represented as an oval.

## The SM Block

* The SM block describes the operation when residing in a particular state.
* All actions in the SM block occur concurrently hence there is no serial operation.
* All paths through the SM block must be valid.