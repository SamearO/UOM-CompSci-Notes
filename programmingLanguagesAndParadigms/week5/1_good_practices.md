# C Good Practices

## Compiler Warnings

* GCC Compiler flags such as `-Wall`, `-Wextra` and `-pedantic` can be used to highlight issues in the code.

## Dynamic Analysis tools
* Tools like `Valgrind` and `ASAN` can be used to check for memory leaks during runtime.

## Overflows
* Using functions like `sizeof()` to keep track of sizes instead of hardcoding them.
* Signed and unsigned overflows are different. Hence wider types and casting should be used.

## Using safe functions
* use `strncpy` instead of `strcpy`.
* `strncpy` does not add `\0` at the end of target buffers hence a check needs to be made for that.

## Dynamic Memory allocation
* After calling `free`, the pointer is invalid hence it cannot be dereferenced or used.
* `realloc` returns null but does not free the pointer when it fails. 