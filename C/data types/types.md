A data type is a set of *data values* associated to a set of allowed operations on these values.

The type of a [[variables|variable]] determines how much space it occupies in [[memory|storage]] and how the *bit pattern* stored is interpreted.

- Basic Types: Arithmetic types and are further classified into:
	- integer types
	- floating-point types
- Enumerated types: Arithmetic types used to define variables that can only assign certain discrete integer values throughout the program.
- The type [[void]]: The type specifier void indicates that no value is available.
- Derived types:
	- Pointer types
	- Array types
	- Structure types
	- Union types
	- Function types

# range

1 byte consists of 8 bits of [[memory]].

Consider a byte as a sequence of 8 place-holders (bits), where each bit can hold either 0 or 1 (as each memory bit can only be set to an *on* or *off* state). There are $2^8$ or 256 distinct combinations of 0's and 1's in 8 bits of memory, and we can use each 8-bit combination to represent a different *value*.

Example:

Take the first of the 256 combinations to represent a 0, and the final combination as 255:
| byte            | value |
| --------------- | ----- |
| 0 0 0 0 0 0 0 0 | 0     |
| 0 0 0 0 0 0 0 1 | 1     |
| ...             | ...   |
| 1 1 1 1 1 1 1 0 | 254   |
| 1 1 1 1 1 1 1 1 | 255   |

The range is the difference between the max and min values a data type can hold. For this data type, the range is from 0 to 255. This example type is generally called an unsigned byte, as the values it can represent are positive numbers.

In the same 8-bits, we could define a way to represent a range of numbers from `-128` to `127`.

| byte            | value |
| --------------- | ----- |
| 0 1 1 1 1 1 1 1 | 127   |
| 0 1 1 1 1 1 1 0 | 126   |
| ...             | ...   |
| 0 0 0 0 0 0 0 1 | 0     |
| 0 0 0 0 0 0 0 0 | 0     |
| 1 1 1 1 1 1 1 1 | -1    |
| ...             | ...   |
| 1 0 0 0 0 0 0 1 | -127  |
| 1 0 0 0 0 0 0 0 | -128      |

This representation is generally called a `signed byte`, because it is a `byte` type that can have both positive and negative representations of the number.

In comparing `unsigned byte` and `signed byte`, their ranges are different:
| type          | value range |
| ------------- | ----------- |
| unsigned byte | 0 to 255    |
| signed byte   | -128 to 127 |

However, they are both have 256 possible combinations of values they can represent. They only differ by the _range_ of values they can represent. That's the range of a data type.
| Type           | Storage size                      | Value range                                          |
| -------------- | --------------------------------- | ---------------------------------------------------- |
| char           | 1 byte                            | -128 to 127 or 0 to 255                              |
| unsigned char  | 1 byte                            | 0 to 255                                             |
| signed char    | 1 byte                            | -128 to 127                                          |
| int            | 2 or 4 bytes                      | -32,768 to 32,767 or -2,147,483,648 to 2,147,483,647 |
| unsigned int   | 2 or 4 bytes                      | 0 to 65,535 or 0 to 4,294,967,295                    |
| short          | 2 bytes                           | -32,768 to 32,767                                    |
| unsigned short | 2 bytes                           | 0 to 65,535                                          |
| long           | 8 bytes or (4bytes for 32 bit OS) | -9223372036854775808 to 9223372036854775807          |
| unsigned long  | 8 bytes                           | 0 to 18446744073709551615                            |

The actual number of bits for each type, such as `int` and `long` can be implementation- and architecture-dependent, so the above chart is not necessarily true.

If you want to know the actual minimum and maximum values an implementation uses they are defined in the `limits.h` header file. It defines various constants like SCHAR_MIN, SCHAR_MAX, etc. that give the values for this implementation of C. The following example shows the limits of this implementation:

```C
#include <stdio.h>
    #include <limits.h>
 
   void main()
   {
          printf("Signed char minimum value: %d\n", SCHAR_MIN );
          printf("Signed char maximum value: %d\n", SCHAR_MAX );
          printf("Unsigned char minimum value: %d\n", 0 );
          printf("Unsigned char maximum value: %d\n", UCHAR_MAX );
          printf("Char minimum value: %d\n", CHAR_MIN );
          printf("Char maximum value: %d\n", CHAR_MAX );
          printf("Signed short minimum value: %d\n", SHRT_MIN );
          printf("Signed short maximum value: %d\n", SHRT_MAX );
          printf("Unsigned short minimum value: %d\n", 0 );
          printf("Unsigned short maximum value: %d\n", USHRT_MAX );
          printf("Signed int minimum value: %d\n", INT_MIN );
          printf("Signed int maximum value: %d\n", INT_MAX );
          printf("Unsigned int minimum value: %u\n", 0 );
          printf("Unsigned int maximum value: %u\n", UINT_MAX );
          printf("Signed long minimum value: %ld\n", LONG_MIN );
          printf("Signed long maximum value: %ld\n", LONG_MAX );
          printf("Unsigned long minimum value: %lu\n", 0 );
          printf("Unsigned long maximum value: %lu\n", ULONG_MAX );
          printf("Signed long long minimum value: %lld\n", LLONG_MIN );
          printf("Signed long long maximum value: %lld\n", LLONG_MAX );
          printf("Unsigned long long minimum value: %lu\n", 0 );
          printf("Unsigned long long maximum value: %llu\n", ULLONG_MAX );
  }
```

## size

Data type specifies the size and type of information the variable will store. [[Overview#C standards|The C standard]] usually does not specify exact sizes for the native types, preferring to set a basic minimum that all conforming implementations of C must meet. Implementations are free to go above these minimum requirements.

This means that different implementations can have different sizes for the same type.

| type           | size (bytes) |
| -------------- | ------------ |
| char           | 1            |
| unsigned char  | 1            |
| signed char    | 1            |
| int            | 2 or 4       |
| unsigned int   | 2 or 4       |
| short          | 2            |
| unsigned short | 2            |
| long           | 8            |
| unsigned long  | 8             |
| float       | 4            | 6         |
| double      | 8            | 15        |
| long double | 10           | 19          |

Example:

```c
#include <stdio.h>
int main()
{
    printf("%lu\n", sizeof(char));
    printf("%lu\n", sizeof(int));
    printf("%lu\n", sizeof(float));
    printf("%lu", sizeof(double));
    return 0;
}
```

Example:

```C
#include<stdio.h>
int main(void)
{
printf("Size of a char: %ld byte(s)\n", sizeof(char));
printf("Size of an int: %ld byte(s)\n", sizeof(int));
printf("Size of a long int: %ld byte(s)\n", sizeof(long int));
printf("Size of a long long int: %ld byte(s)\n", sizeof(double));
printf("Size of a float: %ld byte(s)\n", sizeof(float));
return (0);
}
```
