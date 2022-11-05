# Sequential Systems

The outputs of a sequential circuit depend upon their input values as well as the current state which was derived from previous inputs and the processing done on them.

## RTL Datapath

The `RTL datapath` model is where in each clock cycle, data passes from one register to another through some combinatorial logic. As the data moves through this datapath, the control block monitors the data and signals the datapath as to how the data should be manipulated/ flow.

The generally sequential control block is a `finite state machine` that moves between states depending on the state of the datapath and any input signals.

## Finite State Machines

Finite state machines use combinatorial logic to take the current state and a set of inputs to determine the next state. They have finitely many states.

### Mealy Machine

* Determines next state based on present state and current inputs. Hence changes are `asynchronous`.
* Has an `always @ (*)` to define the value of the next state as a function of the current state and any inputs.
* Has an `always @ (posedge clock)` to assign the next state to the current state and perform synchronous reset actions.
* Has an `always @ (*)` to define the state of the outputs based on the value of the current state.
    
### Moore machine
* Determines next state based only on present state. Hence changes are `synchronous`.
* Has an `always @ (*)` to define the state of the FSM's next state based on the current state.
* Has an `always @ (posedge clk, posedge rst)` to Assign the output, asynchronously reset and assign the state based on the next state.
