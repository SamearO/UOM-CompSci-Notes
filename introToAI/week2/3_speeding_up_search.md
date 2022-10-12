> The following notes are from the extended reading. 
# Speeding up Search Algorithms

Search algorithms like Alpha-Beta pruning can be sped up using game-specific optimizations.

## Iterative Deepening search
* Dynamic move ordering schemes can allow for earlier pruning of branches, leading to speed ups.
* Moves that were found to be best in the past can be searched first.
* With iterative deepening search, do a search of 1 depth and record the best path of moves. Then search a ply deeper using the previous result to inform the move ordering.
* This takes more computation but can be made up for with better ordering.

## Transpositions
* The results of previous states can be stored in a dictionary that is queried to see if they are more ideal states.
* This is useful when repeated states can occur in games hence querying the dictionary can allow for not having to calculate the score for a state.

## Forward Pruning

* On each ply, only consider a beam of n possible moves according to the evaluation function of their scores as opposed to considering all possible moves. 
* This makes the algorithm faster but can lead to suboptimal moves being played.

# Improving search algorithms

`AB Pruning` that has to stop at a certain depth and use an evaluation function can lead to moves that are not ideal.

## Quienscence search

An evaluation function can give false confidence in the case where a move seems like a winning move, but if the depth of the iteration was longer, it would show that it is a losing move. 

This can be solved by a `quiescence search` where more iterations are done until the system is confident that wild swings in the value of the evaluation function are minimal.

The search can be limited to searching only certain types of moves like `capture moves` in chess to ensure there is less computation used.