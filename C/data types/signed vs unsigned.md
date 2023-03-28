- `signed` indicates that a variable can hold negative and positive values.
- `unsigned`indicates a variable that can hold only positive numbers.
- `unsigned` is short for no signed (positive only).
- The property can be applied to most of the numeric data types including `int`, `char`, `short` and `long`.
- `signed` and  `unsigned` can standalone type specifiers, but they're used alone, they default to `int`.
- Objects of type `long` can be declared as `signed long` or `unsigned long`. `signed long` is the same as `long` because signed is the default. The same applies to short.​

# integers

- An `int` type in C, C++, and C# is `signed` by default.
- If negative numbers are involved, the `int` must be `signed`
- An `unsigned int` cannot represent a negative number.

# characters

- In the case of `char`s, which are only 1 byte, the range of an `unsigned char` is 0 to 256, while the range of a `signed char` is -127 to 127.