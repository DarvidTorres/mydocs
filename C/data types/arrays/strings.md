- A string is an array of type `char`.
- [[types#characters|characters]] in C are enclosed within a single quote for example, 'a', 'b', 'c'.
- To create a string in C, create an array and store characters on it.
- A string in C always ends with a null character (`\0`)
	- the null character is always the last character in the array.

To store a string in an array, we need to declare a one-dimensional array. The characters in the string can be set at the time of array declaration or later by accessing individual indexes

```C
char <array_name>[<array_size>] = {<char0>, <char1>, .....};
// OR
char <array_name>[<array_size>];
<array_name>[0] = '<char0>';
<array_name>[1] = '<char1>';
...
```

Example:

```C
#include <stdio.h>

int main()
{
    char str[7] = {'S', 't', 'r', 'i', 'c', 'g', '\0'}; // Stricg
    str[4] = 'n'; // Stricg becomes String
    printf("%s", str);

    return 0;
}
```

The `str` array is of size 7 (one more than characters) to store an extra null `\0` character, so the value of our `str` array is "String\0". We don't have to explicitly add a null character in the string as the compiler automatically adds it.

The compiler automatically adds an extra null character at the end of the string if it is not mentioned explicitly. Example:

```C
char str1[7] = "String"; /* \0 not explicitly mentioned */
// OR
char str2[7] = "String\0";
```

If a string doesn’t have a null character, the compiler will still let the program pass without any error. A string is simply a collection of characters, and we need `\0` only to identify the end of the string.

Having no terminator in your c-string will result in functions on the string not being able to determine the end of the string, which will cause some undefined behavior.

```C
char foo[3] = {'f', 'o', 'o'};
```

# pointers to strings

We can declare first a pointer, and then, define it:
```C
int a; // declare variable
int *p; // declare pointer

p = &a; // Assing the address of `a` to `p` (define pointer)
```

Or we can also create a pointer and define it at once:




Given that strings are arrays and that the name of arrays are pointers to the starting element of the array.

Pointers to strings in C can point to the starting address of the array that is the first character in the array.

![pointer to string|400](https://i.imgur.com/FX1Q0zj.png)
`str` is a character array containing the string "WORD" and `ptr` is a character pointer pointing to the address of the first character in the array (that is 'W').

When we create an array, the variable name points to the address of the first element of the array.

```C
// character array storing the string 'String'
char str[7] = "String";
// pointer storing the starting address of the 
// character array str
char *ptr = str;
```



A string literal is a sequence of characters enclosed in double quotation marks.

```C
/* string literal */
char *string_literal = "This is a string literal."
```
