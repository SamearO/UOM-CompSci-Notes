# Modular Compilation

* Code can be broken down into modules to separate code into different files.
* Furthermore it can improve compile times by only compiling files that have been changed.
* Files are compiled to object files before being linked into an executable by a `linker`.

## Implementing Modular Compilation

* A header file is used to define the functions that are shared from one file to another.
* A separate C file implements these functions.
* The second C file is then able to call the functions that were defined in the header.

### Library.h 
```C
#ifndef NETWORK_H
#define NETWORK_H
// shared structs are defined in headers
typedef struct {
    int id;
    char content[128];
} my_struct;

void my_shared_function();
```

### Library.c
```C
#include "Library.h"

static void private_function() {
    // Static functions cannot be accessed by other files.
}

void my_shared_function() {
    //Code here
}
```

### calling.c
```C
#include "Library.h"

int main() {
    my_shared_function();
}
```