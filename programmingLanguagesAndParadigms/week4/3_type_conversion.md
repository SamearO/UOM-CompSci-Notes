# Type Conversion

## Implicit Type Conversion
* When arithmetic is done between variables of different types, C will implicitly try to convert the "smaller" type to the larger type Eg when adding an `int` and a `long`.

## Forced type conversion
* Variables can be casted using the following syntax: `(type)variable`
```C
printf("%lf\n", (float)15/4);
```

## Generic Pointers
* Generic pointers can be used to pass functions variables of different types.
* They are created using `void *`
```C
my_function((void *)&my_var);
```