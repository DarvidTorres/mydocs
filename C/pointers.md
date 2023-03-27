Pointers: variables that store address of another variable.
Every time a program is rerunned the address allocation changes.

`p`: address of stored variable
`*p`: value at address
`&a`: address of `a`
`&p`: address of `p` (dereferencing)

In 64-bit data models, pointer sizes are always 64 bits (8 bytes).

variables have a [[data types | type]], and pointers have a *strong type* 

```c
int a; // declare variable
int *p; // declare pointer

p = &a; // Assing the address of `a` to `p` (define pointer)
a = 5; // define variable

printf("%ls", p) // returns stored address
printf("%ls", &a) // returns address
printf("%ls", &p) // returns pointer address
printf("%ls", *p) // returns value at address

*p = 8; // redefine value at address (dereferencing)
printf(a) // returns 8 (as value at address was redefined)
```

To **print the address of a variable**, we use "%p" specifier. There are two ways to get the address of the variable:
1.  By using "address of" (&) operator
```c
#include <stdio.h>

int main(void)
{
	// declare variables 
	int a;
	float b;
	char c;

	printf("Address of a: %p\n", &a);
	printf("Address of b: %p\n", &b);
	printf("Address of c: %p\n", &c);

	return 0;
}
```
2.  By using pointer variable
```c
#include <stdio.h>

int main(void)
{
	// declare variables 
	int a;
	float b;
	char c;
	
	//Declare and Initialize pointers 
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

pointers and variables must match type.

`char c;`: define a c variable of type `char`
`char *po`: define a pointer of type pointer

```c
#include <stdio.h>
int main() {
int a = 10, *p = &a;
printf("Address stored in p is %ls", p); // for address of pointer use `%ls` type
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

