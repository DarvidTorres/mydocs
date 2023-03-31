- Pointers are [[variables]] that store a variable [[address]].
- Pointers have a [[types|type]].
- Pointer type must match the variable type it *points* to.
- In 64-bit data models, pointer size are always 8 bytes (64 bits).

Pointer declaration syntax:
```C
<varType> <varName>; // variable declaration
<varType> * <ptrName> = &<varName>; // pointer declaration
```

Example:

```C
#include <stdio.h>

int main() {
    int myVar = 3;
    int * myPtr = &myVar;
    printf("Address stored in myPtr is %p", myPtr); 
    
    return (0);
}
```

As pointers are variables, we can declare a pointer without assigning the value, and assign the value later.

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // declare variable
    int * myPtr; // declare pointer
    myPtr = &myVar; // define pointer
    printf("Address stored in myPtr is %p", myPtr);
    
    return (0);
}
```

Note that we don't need to define the variable the pointer *points to*, since the pointer itself only stores the variable's address (not its value).

- Since pointers are variables, they (themselves) have an address.
- Since pointers have an address, they can store their own address.

Example:

```C
#include <stdio.h>

int main() {
    void * my_self; // pointer declaration
    my_self = &my_self; // pointer definition
    printf("Address stored in my_self is %p", my_self);
    
    return (0);
}
```

> Though pointers can point to themselves, only narcissistic pointers do so and other pointers have often enough big problems working with one that does nothing else but look into the mirror all day. So, most people find such pointers not at all useful.



d

```c
int a; // declare variable
int * p; // declare pointer

p = &a; // Assing the address of `a` to `p` (define pointer)
a = 5; // define variable

printf("%ls", p) // returns stored address
printf("%ls", &a) // returns variable address
printf("%ls", &p) // returns pointer address
printf("%ls", *p) // returns value at address

*p = 8; // redefine value at address (dereferencing)
printf(a) // returns 8 (as value at address was redefined)
```



```c
#include <stdio.h>

int main(void)
{
	int a;
	int *ptr_a = &a;
	float *ptr_b = &b;
	char *ptr_c = &c;
	
	//Printing address by using pointers 	
	printf("Address of a: %p\n", ptr_a);
	printf("Address of b: %p\n", ptr_b);
	printf("Address of c: %p\n", ptr_c);

	return 0;
}
```


`char c;`: define a c variable of type `char`
`char *po`: define a pointer of type pointer

```c
#include <stdio.h>
int main() {

int a = 10;
*p = &a;
printf("Address stored in p is %ls", p); // for address of pointer use `%ls` type

return (0);
}
```

we can change the variable's value using the pointer:

```c
#include <stdio.h>
int main()
{
int a;
int* p;
a = 10;
p = &a; // &a address of a
printf("a = %ls\n", a); // print value of a
*p = 12; // dereferencing
printf("a = %ls\n", a); // print modified value of a
}
```

we can redefine the value at address without affecting the pointer's stored address (by doing this we might have several variables (with the same value) stored at the same address):

```c
#include <stdio.h>
int main() {
int a = 10, b = 20, *p = &a;
printf("Address stored in p is %ls\n", p);
printf("Value at address stored in p is %d\n", *p);
*p = b; // redefine value at address
printf("Value at address stored in p now is %d\n", *p);
printf("Value of a now is %d\n", a);
printf("Address of a is %ls\n", &a);
printf("Address of b is %ls\n", &b);
}
```

Pointers can store their own address:
```C
void *my_self = &my_self; 
```

# pointer arithmetic

we can alter what address are stored in pointers (not only the value stored but the address itself):

```c
#include <stdio.h>
int main()
{
int a = 10, *p = &a;
printf("Address stored in p is %ls\n", p);
printf("Value at address p is %d\n", *p);
printf("size of integer is %ld bytes \n", sizeof(int)); // for `sizeof(type)` use `%ld` type
printf("Address p+1 is %ls\n", p+1);
printf("value at address p+1 is %d\n",*(p+1));
}
```

the `p+1` statement is not adding `1` byte to the address, but `1` type unit. For instance, if it's `int` it will add 4 units to address as `int` takes 4 bytes of memory.

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

