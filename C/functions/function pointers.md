- [[functions|function definitions]] are stored in [[memory]], so they have an address.
- A function pointer is a [[pointer]] that stores a [[functions|function's definition]] address.
- You cannot perform pointer arithmetic on function pointers.
- A function name without parentheses is a pointer to the function's definition, just as the name of an [[arrays|array]] by itself is a pointer to its 0th element

Example:

```C
#include <stdio.h>

void my_function() {
   printf("Hello World");
}

int main() {
   printf("The address of my_function is: %p\n", my_function);
   printf("The address of the main function is: %p\n", main);
}
```

A function pointer declaration looks like a function declaration, except that the function name is wrapped in parentheses and preceded by an asterisk.

Example:

```C

```

