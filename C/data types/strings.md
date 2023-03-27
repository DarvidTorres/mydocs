# strings as arrays

- String is a data type that stores the sequence of characters in an array.
- Individual characters in C are enclosed within a single quote for example, 'a', 'b', 'c'.
- To store a string in C, we can create an array and store characters on it.
- A string in C always ends with a null character (`\0`)
	- the null character is always the last character in the array.

To store a string in an array, we need to declare a one-dimensional array. The characters in the string can be set at the time of array declaration or later by accessing individual indexes

```C
char <array_name>[<array_size>] = {'a', 'b', .....};
// OR
char <array_name>[<array_size>];
<array_name>[0] = 'a';
<array_name>[1] = 'b';
...
```

# pointers to strings

Pointers to strings in C can point to the starting address of the array that is the first character in the array.

![pointer to string|400](https://i.imgur.com/FX1Q0zj.png)
`str` is a character array containing the string "WORD" and `ptr` is a character pointer pointing to the address of the first character in the array (that is 'W').
