A data type is a set of *data values* associated to a set of allowed operations on these values.

The type of a [[variables|variable]] determines how much space it occupies in [[memory|storage]] and how the *bit pattern* stored is interpreted.

- Basic Types: Arithmetic types and are further classified into:
	- integer types
	- floating-point types
- Enumerated types: Arithmetic types used to define variables that can only assign certain discrete integer values throughout the program.
- The type [[void]]: The type specifier void indicates that no value is available.
- Derived types:
	- Pointer types
	- Aggregate types
		- Array types
		- Structure types
	- Union types
	- Function types
		- The type of a function specifies the type of the function's return value.

# value range

Bit stands for *binary digit*.

1 byte consists of 8 bits of [[memory]].

Consider a byte as a sequence of 8 place-holders (bits), where each bit can hold either 0 or 1 (as each memory bit can only be set to an *on* or *off* state). There are $2^8$ or 256 distinct combinations of 0's and 1's that can be placed in 8 place-holders; then we can use each 8-bit combination to represent a different *value*.

Example:

Take the first of the 256 combinations to represent a 0, and the final combination as 255:
| byte            | value |
| --------------- | ----- |
| 0 0 0 0 0 0 0 0 | 0     |
| 0 0 0 0 0 0 0 1 | 1     |
| ...             | ...   |
| 1 1 1 1 1 1 1 0 | 254   |
| 1 1 1 1 1 1 1 1 | 255   |

The range is the difference between the max and min values a data type can hold. For this data type, the range is from 0 to 255. This type is generally called an unsigned byte, as the values it can represent are positive numbers (no sign).

In the same 8-bits, we could define a way to represent a range of numbers from -128 to 127.
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

This representation is generally called a signed byte, because it is a byte type that can have both positive and negative representations of the number (has a sign).

Comparing the unsigned and signed byte example types, their ranges are different, even though their size is the same:
| type          | size   | value range |
| ------------- | ------ | ----------- |
| unsigned byte | 1 byte | 0 to 255    |
| signed byte   | 1 byte | -128 to 127 |

Both have $2^8$ or 256 possible combinations of values they can represent. They only differ by the _range_ of values they can represent. That's the range of a data type.

Similarly, this can be extended to other types of different size as well. For example, the a 2-byte type will have 16 bits (or 16 place-holders) to store binary units; that's $2^{16}$ or 65536 combinations of values that it can represent, as in the 1-byte type, the range of values can be all positives or split into positive and negatives.

# storage size

The type of a [[variables|variable]] determines how much space it occupies in storage and how the bit pattern stored is interpreted (value range).

The [[Overview#C standards|C standard]] usually does not specify exact sizes for the native types, preferring to set a basic minimum that all conforming implementations of C must meet. Implementations are free to go above these minimum requirements.

This means that different implementations can have different sizes for the same type.

Example data type sizes:

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

Example data types:
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

>The actual number of bits for each type, such as `int` and `long` can be implementation- and architecture-dependent, so the above chart is not necessarily true.