- [[functions|function definitions]] are stored in [[memory]], so they have an address.
- A function pointer is a [[pointers|pointer]] that stores a [[functions|function's definition]] address.
- You cannot perform [[pointers#pointer arithmetic|pointer arithmetic]] on function pointers.
- A function name without parentheses is a pointer to the function's definition, just as the name of an [[arrays|array]] by itself is a pointer to its 0th element.
- Dereferencing the function pointer yields the referenced function.

Example:

```C
#include <stdio.h>

int my_function() {
   printf("Hello World");
}

int main() {
   printf("The address of my_function is: %p\n", my_function);
   printf("The address of the main function is: %p\n", main);

return (0);
}
```

Though function names are pointers to function definitions.

A function pointer declaration looks like a function declaration, except that the pointer's name is wrapped in parentheses and preceded by an asterisk. As with function declarations, the names of the arguments can be omitted.

```C
<funType> <funName> (int <ptr1> , int <ptr2>); // function declaration
<funType> (*<ptrName>) (int <ptr1> , int <ptr2>); // function pointer declaration
```


