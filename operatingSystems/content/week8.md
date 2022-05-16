# File Systems II

## Disk Defragmentation
* Reading and writing from files that are not in a contiguous chunk can take longer than files that are in a contiguous chunk. 
* After many read and write operations, files can be broken up into many chunks across the hard drive. 
* Defragmentation uses an algorithm to move data such that all the files are stored in contiguous chunks. 
* Defragmentation is only done on hard drives as hard drives need to physically move the read head to access data hence it is slow when data is broken up. SSDs act more like RAM so it is not necessary. 

## Virtual File Indexes 
* Because the file index is written to and read more times than usual files, it is usually `virtual` hence it is moved around the drive periodically to prevent wear on a specific area.

## Writing files with space constraints
* The operating system is used by multiple processes. 
* When starting to write a file, the space that the file had to write with may be used by another process, thus it can fail mid-operation. There are 2 solutions:
    * Reserve the space required before starting the write. 
    * Have error handling code for when the file write fails after starting.

## UNIX quirks
* In UNIX systems, everything including peripheral devices are considered `files`. Thus a keyboard is a file that can only be read from etc.
* `/dev/null` in UNIX is a file that has no content, any data sent to it is deleted.
* `/dev/random` in UNIX is a file that outputs a stream of random bytes.

## Caching
* When writing to a hard drive, sometimes a RAM cache is used to speed up the operation and allow the process to continue while the file is being written. 
* If a power cut occurs while a file is being written from RAM, it can lead to data loss or corruption. 
* When writing data from RAM, previous data in the RAM can be changed by the process hence when writing data, a check needs to be done that each specific byte is in its latest state.