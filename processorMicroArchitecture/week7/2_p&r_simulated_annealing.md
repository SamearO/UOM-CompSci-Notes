# Place and Route with Simulated Annealing

* `Simulated Annealing` is a technique used to do placement and routing.
* It tries to minimise a `cost function` of either:
    * `Manhattan distance`: Sum of x and y distances from sources to destinations.
    * `Euclidian distances`: Square root of the sum of squares of x and y.

## Placement with Simulated Annealing
* Start with an initial placement.
* Randomly swap 2 blocks.
* If the swap was good (minimises cost function), keep with high likelihood otherwise keep with low likelihood.
* Allow long distance and bad swaps at first and slowly reduce this.

## Routing with Simulated Annealing 
* Route all paths individually
* Update the cost function again to assign higher costs to paths that are used the most.
* Run the iteration again over and over until happy.