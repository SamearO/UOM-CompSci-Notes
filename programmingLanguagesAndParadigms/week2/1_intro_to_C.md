# Introduction to C

## Why use C
* Speed
* Low memory footprint
* Low level control 
* Nice syntax

## Why not use C
* Large surface for human error

## Declaring Variables
```C
int main() {
    // Declaring and assigning in different lines
    int a;
    a = 12; // before this line, the value of a is garbage

    int b = 13; //same line
    // multiple per line
    int x, y = 10, z = 11;
}
```

## Types
* Compiler checks the validity of operations.
* Defines the amount of space in memory for each variable.

### Type qualifiers
* Architecture specific qualifiers to change the amount of memory assigned to a variable.
```C
int main() {
    short int a; // signed 16 bits minimum
    unsigned int b; // cannot be negative but can have twice as large positive ints
    unsigned long int c; // at least 32 bits
    long long int d; // at least 64 bits
    double e; // double precision float, usually 64 bits as opposed to 32 bits
}
```