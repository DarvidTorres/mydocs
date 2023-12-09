# stack

The stack is the sequence (oredered list) of memory:
* it is a contiguous (continuous, in a row) block of memory.
- Data on the stack has a [[C/data types/types|fixed size]]
- Arrays have the [[C/data types/types#size|size]] of their type multiplied by the number of elements
	- float a\[10\] = 4 bytes x 10 elements = 40 bytes

- Variables are stored in memory at some memory address.
	- The size of memory to be allocated is known to the compiler
	- When a [[C/functions/functions|function]] is called, it's local variables are placed on the stack
	- When the [[C/functions/functions|function]] is returned (the function call is over), the variables are removed (the memory for the variables is de-allocated).

Stack memory allocation happens using some predefined routines in the compiler. A programmer does not have to worry about memory allocation and de-allocation of stack variables.

-   It’s a temporary memory allocation scheme where the data members are accessible only if the method( ) that contained them is currently running.
-   It allocates or de-allocates the memory automatically as soon as the corresponding method completes its execution.

you can think of the Stack as a pile of boxes, one on top of the other. You cannot directly put a box in the middle of the stack, just like you cannot take a box without crashing the whole pile. Whenever we add a box, we add it at the top end of the pile, and only there, and same when we take a box – we only take them one by one, starting from the top end alone.

# heap

The heap is for dynamic allocation of memory.

- Pile of memory space available to programmers to allocate and de-allocate.
	- Memory is allocated during the execution of instructions written by programmers. 
	- Manual memory management
- Memory leak occurs when programmers create a memory in heap and forget to delete it.

# stack vs heap

- stack is a sequence (ordered list), while heap is a pile of memory (unordered)
- Blocks of data on the heap can be different sizes, and are not necessarily in order.
- Stack accesses local variables only while Heap allows you to access variables globally.
- Stack variables can’t be resized whereas Heap variables can be resized.
- Stack memory allocation is considered safer as compared to heap memory allocation because the data stored can only be accessed by the owner thread.
- Memory allocation and de-allocation are faster as compared to Heap-memory allocation.
- Stack memory has less storage space as compared to Heap-memory.
