# Planning

## Representing Planning problems

* Planning problems can be represented in the same way as constraint satisfaction problems.
* There is a list of fluents in a state that hold true.
* Actions can take one state to another given that the previous state has the precondition fluents the action requires.
* The goal state is the state where all the state fluents are as required by the goal state.

## Forward (progression) state search

* Searching from the start state to the goal state by expanding the graph of states and the actions between them.
* Can use any search method from Constraint Satisfaction Problems
* The problem graph gets very big very fast hence this is often unrealistic to use without a heuristic.

## Backward (regression) state search

* Start at the goal state and apply actions backwards to find the initial state.
* Regressing from one state to another uses `new_state = (old_state - ADD(action))U Precondition(a)`
* Only `relevant` actions are taken in a backwards search hence the search space is smaller.
    * Relevant actions are actions that can be the last step in a plan leading to the current goal state.
* A `relevant action` must contribute to the goal and also not have any effects that contribute negatively to the goal.
    * If the goal is `A and B and C`, an action of `A and B and not C` can not be taken.

## Heuristics for planning

* A relevant heuristic gives an underestimate (or accurate) cost for achieving a task, thus allowing for methods like `A* search` to be used.
* Given that searches are in graphs, a search can become easier by either adding more edges or grouping multiple nodes together.

### Increasing the Edges

* More edges (actions) can be added by ignoring pre-conditions.
    * A naive approach is to ignore all pre-conditions. This however leads to the `set-cover problem` that can be solved with a `greedy search` but leads to a loss in the guarantee of getting a lower bound.
    *  Selected preconditions could be ignored.
* Ignoring delete lists for actions ensures that the work done by one action is not undone by a previous one. Thus increasing the speed at which a lower bound is found.

### Grouping Nodes Together

* Nodes can be grouped together by assuming that the cost of solving a conjunction of sub-nodes is approximated by the cost of solving each subgoal independently.
* This does not give an underestimate in the case where actions undo the progress of other actions.
* This does give an underestimate when actions are redundant eg 1 action can create the same progress as 2 other actions.

# Planning graphs

