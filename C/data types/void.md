The void type specifies that no value is available.

It is used in three kinds of situations:

- Function returns as void: There are various functions in C which do not return any value or you can say they return void. A function with no return value has the return type as void.
	- For example, `void exit (int status);`

- Function arguments as void: There are various functions in C which do not accept any parameter. A function with no parameter can accept a void.
	- For example, `int rand(void);`

- Pointers to void: A pointer of type `void *` represents the address of an object, but not its type. For example, a memory allocation function `void *malloc( size_t size );` returns a pointer to void which can be casted to any data type.