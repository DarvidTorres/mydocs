Pointers store addresses, not values, of variables. But we can access the variable's address via the pointer using the asterisk operator (`*`); this operation is called dereferencing.

Example:

```C
#include <stdio.h>

int main() {
    int myVar = 3;
    int * myPtr = &myVar;
    printf("Value at &myVar is %d", *myPtr);
    
    return (0);
}
```

We can change the variable's value by dereferencing:

```c
#include <stdio.h>

int main() {
    int a = 10;
    int * p = &a;
    printf("a = %d\n", a); // print value of a
    *p = 12; // dereferencing
    printf("a = %d\n", a); // print modified value of a
    
    return (0);
}
```

Another example:

```c
#include <stdio.h>

int main() {
    int a; // declare variable
    int d; // declare another variable
    int * p; // declare pointer
    
    p = &a; // Assing the address of `a` to `p` (define pointer)
    a = 5; // define variable a
    
    printf("%p\n", p); // return stored address in pointer p
    printf("%p\n", &a); // return variable a address
    printf("%p\n", &p); // return pointer p address
    printf("%d\n", *p); // return value at &a
    
    d = 10; // define variable d
    *p = d; // redefine value at address (dereferencing)
    printf("%d\n", a); // returns 10 (as value at address was redefined)
    
    return (0);
}
```

# pointer to pointer

As pointers reference to value at address using `*`, to point to a value in a pointer, we need to use `**`, and to point to a value in a pointer that points to a pointer, we need to use `***`

Example:

```c
#include <stdio.h>
int main()
{
int x = 5;
int* p = &x; // p contains address of x
printf("%d\n", *p); // value at (address of x) = value of x
int** q = &p; // store address of p in q pointer
printf("%ls\n", *q); // value at (address of p) = address of x
printf("%d\n", *(*q)); // value at (value at (address of p)) = value of x
int*** r = &q; // store address of q
printf("%ls\n", *(*r)); // value at (value at (address of q (address of p))) = address of x
printf("%d\n", *(*(*r))); // value at (value at (value at (address of q))) = value at x
return (0);
}
```

