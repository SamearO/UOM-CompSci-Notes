# Memory 

## Memory considerations
* What strategy to split up the memory between different processes
    * Best Fit - Fit the memory in the location closest in size to reduce external fragmentation. Requires additional CPU cycles to check every memory location.
    * Worst Fit - Fit the memory in the largest memory location. Requires additional CPU cycles to check every memory location. Can be good as there can be enough leftover space for more processes to put their memory.
    * First Fit - Fit the memory in the first found memory location. Less CPU cycles used. 
* Size per memory location
    * Too large sizes can lead to internal fragmentation.
    * Too small can require too many memory accesses.

## Fragmentation
* Internal - Unused memory within allocated memory due to how structures are packed. 
* External - Enough free memory but not enough in a contigious piece.

