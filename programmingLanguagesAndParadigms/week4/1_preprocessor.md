# The C Pre-Processor

* The pre-processor runs before the compilation step to perform textual transformations in the code.

## Including Headers
* Files can have `#include <header.h>` to use foreign code.
* The header files themselves only contain declarations that are implemented in C files.
* The pre-processor essentially copies the code of the header file specified into the file with the `include` statement.

## Macro Expansions
* Compile-time defined constants can be defined to save on space for variables.
* These `macros` are textual replacements that are replaced when the compilation takes place.
* Since they are just text replacements, parenthesis should be used when arithmetic is going to be done on them.
```C
# define ARRAY_SIZE 10
# define SIZE_2 20
# define OTHER_SIZE (ARRAY_SIZE + SIZE_2)

int main() {
    int array[ARRAY_SIZE]; // ARRAY_SIZE gets replaced with 10
}
```

## Conditional Compilation
* Code can conditionally be included in the compiled release to facilitate debug builds/ sped up release builds.
```C
#define DEBUG_MODE
#define VERBOSITY_LEVEL 4

int main() {
#ifdef DEBUG_MODE
    debug_function();
#endif
    return 0;
}

#if VERBOSITY_LEVEL > 3
    printf("additional function");
#endif
```