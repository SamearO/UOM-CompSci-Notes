# Even More Memory

## Caching
* Caches operate on the principles of locality:
    * Spatial: If an address is used, it is likely that addresses around it are also likely to be used. 
    * Temporal: If an address is used, it is likely to be used again.
* Caching is used to reduce the distance and time between requesting and receiving data.
* There can be multiple layers of caches.
* A cache can be shared between processors.
* There are issues with caches:
    * The information that caches duplicate can change over time so the cache needs to be flushed or somehow updated.
    * Information can be written to a cache hence the information needs to be written to the underlying memory as well.
    * If there is a `cache miss`, the time taken to receive the data is longer than if there was no cache to begin with. This is alleviated by the reduction in time taken when there is a `cache hit`.

## Cache Eviction Strategies
* When a cache is full, old data needs to be removed to add new data, thus there is a decision to be made as to which data should be removed.
* Random Strategy: Remove a random cache item. 
* Least Recently Used: Remove the item that hasn't been used the longest.
* Cyclic: Remove the item that has been in the cache the longest.

## Translation Look Aside Buffer (TLB)
* A `TLB` is used to cache translations between `virtual` and `physical` memory addresses.
* If the `TLB` does not have the translation, then the `page table` is used.

# Swapping and Paging
* The computer's main memory can be seen as a cache for data that can be stored as files on the hard drive/ permanent memory.
* This can be particularly useful when multiple processes use the same physical addresses as data can be `swapped` between the `memory` and `storage`.

## Multiple techniques for swapping
* Standard Swapping: The whole process is moved out to the `backing store`. Can be slower.
* Swapping with Paging: Swap out individual pages within a process. Can be faster and is more used.

## Page Faults
* When the MMU tries to find a physical address that is not in memory. 
* Can be because of bad programming but can also be because an address has been swapped to the `backing store`. 
* Is raised to the `OS` that will handle the fault by moving the swapped data into memory and the process continues.

## Dirty Paging Strategy
* To reduce writing to the `backing store`, an eviction strategy can be used wherein pages that have not been written to can be swapped as it does not require writing to the `backing store first`.
* This requires additional `metadata` storage for the page.
* This can be done with `page monitoring` wherein pages are read only when first read, on the first write, a `page fault` is raised and the permission is changed. 
* If a page is writable then it must have changed so do not evict it. Otherwise it can be overwritten.

# Direct Memory Access (DMA)
* Hardware that facilitates the movement of data from place to place without the CPU.
* Allows the CPU to do other tasks while the data is being transferred.
* DMA Process:
    * CPU sets up a transfer.
    * DMA controller waits for data from I/O device.
    * data gets transferred.
    * DMA controller sends interrupt to CPU to notify it of completion.

# Libraries
* Collections of code that are used in applications.
* Provide interfaces for specific functions.
* Allow code to be platform agnostic. 

## Static Libraries
* Are included in the program executable during compile time. 
* Have to be included in the program hence can take up more space if multiple programs in the system have the same libraries included. 
* Updates to the libraries can be slower as it depends on the individual programs to update libraries. 
* This can lead to security or performance issues.
* They are self contained and have no `O/S`  requirements

## Dynamic Libraries
* Shared libraries that reside on the host's computer
* Needs to be linked on application startup
* Can leverage shared memory as multiple running applications use the library. 