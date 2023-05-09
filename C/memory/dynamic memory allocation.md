# dynamic memory allocation

Dynamic Memory Allocation can be defined as a procedure in which the size of a data structure (like [[arrays]]) is changed during the runtime.

There are 4 library functions provided by C defined under `<stdlib.h>` header file to facilitate dynamic memory allocation in C programming: 
- malloc()
- calloc()
- free()
- realloc()

# malloc

malloc: memory allocation.

The `malloc` function is used to allocate a certain amount of memory during the execution of a program. It will request a block of memory from the heap. If the request is granted, the operating system will reserve the requested amount of memory and `malloc` will return a pointer to the reserved space.

`malloc()`: function to request a block of heap memory. It returns a pointer of type void which can be cast into a pointer of any form.

The `malloc` function allocates a specific number of bytes in memory and returns a pointer to the allocated memory. This memory will have read and write permissions.

Prototype: `<type> *p = void *malloc(size_t <bytes>);`
- `void *` means it is a pointer to the type of your choice
- `size_t` is a special type that is simillar to `unsigned int` but only allows for positive values
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

[c - Do I cast the result of malloc? - Stack Overflow](https://stackoverflow.com/questions/605845/do-i-cast-the-result-of-malloc)

## memory leaks

- Ocurrs when we fail to free dynamically allocated memory
- The space is no longer available (because it's in use)
- If the pointer referencing to leaked memory no longer exists, we can lose access to it

we can free memory areas to be realocated with `free()` (makes the memory space available) but it doesn't delete the data contained in those directions. We can use `calloc()`to set to `0` (delete de data) when freeing.

we can do `sudo apt install vagrind` in linux
`valgrind ./main.out`: to check for memory leaks
`valgrind --leak-check=full ./main.out`: to get more information
`valgrind -s --leak-check=full --show-leak-kinds=all --track-origins=yes ./main.out`: to get full details
