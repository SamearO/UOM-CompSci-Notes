# Improving Search with Inference

## Forward Checking
* Arc consistency can be used during a search to speed it up. The speedup will not be realised if arc consistency has already been applied to the entire network.
* After assigning a variable x_1, find all x_2 that are unassigned and have a constraint relating it to x_1.
* For each x_2, reduce its domain to values that are consistent with the value chosen for x_1 (arc consistency with respect to a variable).

## Intelligent Backtracking
* DFS backtracks one step when a dead end is reached. This wastes time in a CSP when the problem could stem from multiple steps prior.
* Hence, backtracking must be done to a variable x_1 which reduced the available values for the variable x_2 where the failure occured.
* The set of values that are in conflict are known as the conflict set and backjumping jumps to the most recent of the conflict set.
* Backjumping is never used/ not required when forward checking is done as forward checking prevents the search from ever reaching a node where backjumping is required.