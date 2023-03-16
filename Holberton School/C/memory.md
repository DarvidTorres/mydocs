RAM: Random-access memory.

Memory is a (list) sequence of locations to store data (numbers).
- Bytes of memory are assigned unique memory addresses.

The Stack and the Heap are two memory areas located in the computer’s RAM.

## stack

The stack is the sequence (oredered list) of memory:
* it is a contiguous (continuous, in a row) block of memory.
- Data on the stack has a [[data types|fixed size]]
- Arrays have the [[data types#size|size]] of their type multiplied by the number of elements
	- float a\[10\] = 4 bytes x 10 elements = 40 bytes

- Variables are stored in memory at some memory address.
	- The size of memory to be allocated is known to the compiler
	- When a [[functions|function]] is called, it's local variables are placed on the stack
	- When the [[functions|function]] is returned (the function call is over), the variables are removed (the memory for the variables is de-allocated).

Stack memory allocation happens using some predefined routines in the compiler. A programmer does not have to worry about memory allocation and de-allocation of stack variables.

-   It’s a temporary memory allocation scheme where the data members are accessible only if the method( ) that contained them is currently running.
-   It allocates or de-allocates the memory automatically as soon as the corresponding method completes its execution.

you can think of the Stack as a pile of boxes, one on top of the other. You cannot directly put a box in the middle of the stack, just like you cannot take a box without crashing the whole pile. Whenever we add a box, we add it at the top end of the pile, and only there, and same when we take a box – we only take them one by one, starting from the top end alone.

## heap

The heap is for dynamic allocation of memory.

- Pile of memory space available to programmers to allocate and de-allocate.
	- Memory is allocated during the execution of instructions written by programmers. 
	- Manual memory management
- Memory leak occurs when programmers create a memory in heap and forget to delete it.

## stack vs heap

- stack is a sequence (ordered list), while heap is a pile of memory (unordered)
- Blocks of data on the heap can be different sizes, and are not necessarily in order.
- Stack accesses local variables only while Heap allows you to access variables globally.
- Stack variables can’t be resized whereas Heap variables can be resized.
- Stack memory allocation is considered safer as compared to heap memory allocation because the data stored can only be accessed by the owner thread.
- Memory allocation and de-allocation are faster as compared to Heap-memory allocation.
- Stack memory has less storage space as compared to Heap-memory.

![stack vs heap | 300](https://i.imgur.com/8KoJ9JE.png)

# dynamic memory allocation

## dynamic memory allocation

Dynamic Memory Allocation can be defined as a procedure in which the size of a data structure (like [[arrays]]) is changed during the runtime.

There are 4 library functions provided by C defined under `<stdlib.h>` header file to facilitate dynamic memory allocation in C programming: 
- malloc()
- calloc()
- free()
- realloc()

## malloc

malloc: memory allocation.

The `malloc` function is used to allocate a certain amount of memory during the execution of a program. It will request a block of memory from the heap. If the request is granted, the operating system will reserve the requested amount of memory and `malloc` will return a pointer to the reserved space.

`malloc()`: function to request a block of heap memory. It returns a pointer of type void which can be cast into a pointer of any form.

The `malloc` function allocates a specific number of bytes in memory and returns a pointer to the allocated memory. This memory will have read and write permissions.

Prototype: `<type> *p = void *malloc(size_t <bytes>);`
- `void *` means it is a pointer to the type of your choice
- `size_t` is a speciall type that is simillar to `unsigned int` but only allows for positive values
- `<bytes>`: a number that indicates how much memory in bytes we need
* `malloc(size_t <bytes>)`: is the memory allocated in heap
* `p` is the pointer that stores the memory allocated
- If space is insufficient, allocation fails and returns a NULL pointer.

When the amount of memory is not needed anymore, you must return it to the operating system by calling the function `free`.

Example:
```C
#include <stdio.h> // for printf
#include <stdlib.h> // for malloc

int main(void)
{
int *a = malloc(sizeof(int) * 10); // a points to address of dimension 20 bytes, that was
									// reserved by malloc in heap memory

for (int i = 0; i < 10; i++)
{
a[i] = 10 - i; // create an array defined by for loop
}
for (int i = 0; i < 10; i++)
{
printf("a[%d] = %d\n", i, a[i]);
}
printf("\n");

free(a); // free memory at a

return (0); 
}
```

## memory leaks

- Ocurrs when we fail to free dynamically allocated memory
- The space is no longer available (because it's in use)
- If the pointer referencing to leaked memory no longer exists, we can lose access to it

we can free memory areas to be realocated with `free()` (makes the memory space available) but it doesn't delete the data contained in those directions. We can use `calloc()`to set to `0` (delete de data) when freeing.

we can do `sudo apt install vagrind` in linux
`valgrind ./main.out`: to check for memory leaks
`valgrind --leak-check=full ./main.out`: to get more information
`valgrind -s --leak-check=full --show-leak-kinds=all --track-origins=yes ./main.out`: to get full details
