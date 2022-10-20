# Arrays, Strings and Command Line args

## Arrays
* Are stored contiguously.
```C
// Single dimensional array
int array[4]; 
array[0] = 10;
int x = array[3];

// 2D array
int 2d_arr[3][2]; // 3 arrays with 2 vars each
2d_arr[0][1] = 0;

//static initialisation
int static_array[][2] = {{1,2}, {3, 4}} // The dimensions of the inner arrays needs to be specified.
```

## Strings
* Strings are arrays of chars.
* End of array byte is added automatically by the compiler
```C
char[] hello = "Hello World";
```

## Command line arguments
```C
int main(int argc, char** argv) {
    // argv is a list of list of chars (list of strings)
}
```