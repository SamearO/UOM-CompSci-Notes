# Pointers

* The address of a variable can be accessed with `&variable`.
* This address can be stored in a pointer which stores the address of the variable.
```C
int my_var = 42;
int *ptr = &my_var; // variable ptr contains the address of my_var
printf("pointer value: 0x%lx\n", ptr) // 0xF123 (Address of my_var)
printf("pointed value: %d\n", *ptr) // Dereferencing the pointer to get the value pointed by the pointer
```
* Elements of structs can be accessed with `->` where `my_struct->a` is equivalent to `(*my_struct).a`

# Uses of Pointers

## Functions changing their parameters

* Values are usually passed to functions by copying them. Hence if the variable is changed in the function, the value remains the same in the external context.
* This can be changed by passing the pointer to the function and modifying the value of the pointer.
* Thus the value is changed in the outer context too.

```C
void change_variable(int *param) {
    *param++;
}

int main() {
    int param = 5;
    change_variable(&param);
    printf("%d\n", param);  // param is now 6
}
```

## Functions returning more than 1 item
* Memory addresses can be passed to the function that the function modifies to return more than 1 result.
* The function can then return a code that signifies the function status. (If it failed or not).

## Functions efficiently updating large structs
* It can be very expensive to pass variables by copy to functions.
* Hence structs can be passed to functions with their pointers.

## Pointer Chains
* Pointers are themselves variables hence can be pointed to.
```C
int value = 42;
int *ptr1 = &value;
int **ptr2 = &ptr1; // ptr2 contains the address of ptr1 and *ptr2 contains the value of ptr1 (the address of value)
int ***ptr3 = &ptr2;
```