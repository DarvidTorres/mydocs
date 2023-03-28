## size

Data type specifies the size and type of information the variable will store.

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

# range

1 byte consists of 8 bits of memory. Consider a byte as a sequence of 8 place-holders (bits), where each bit can hold either 0 or 1 (as each memory bit can only be set to an *on* or *off* state). There are $2^8$ or 256 distinct combinations of 0's and 1's, and we can use each combination to represent a 

distinct values we can represent from the 8 bits.

Take the first of the 256 combinations to represent a 0, and the final combination as 255:
| byte            | value |
| --------------- | ----- |
| 0 0 0 0 0 0 0 0 | 0     |
| 0 0 0 0 0 0 0 1 | 1     |
| ...             | ...   |
| 1 1 1 1 1 1 1 0 | 254   |
| 1 1 1 1 1 1 1 1 | 255   |

For this data type, the range is from 0 to 255. This type is generally called an unsigned byte, as the values it can represent is unsigned as it has no sign. Basically, it is handled as if it were all positive numbers.




# type casting

Converting one datatype into another is known as type casting or, type-conversion. For example, if you want to store a 'long' value into a simple integer then you can type cast 'long' to 'int'. You can convert the values from one type to another explicitly using the cast operator

```c
(type_name) expression
```

Consider the following program:

```c
#include <stdio.h>

main() {
int sum = 17, count = 5;
double mean;

mean = sum / count;
printf("Value of mean : %f\n", mean);
return (0);
}
```

The output is $3.000000$ and not the expected $3.400000$, this happens because `sum` and `count` are integers, and though `mean` is a double (and thus we get decimal `0`'s), the operation `sum / count` still returns an integer; hence, to get the expected double with the correct result we need to typecast the resul from `sum / count` to `double`, we do this with the cast operator:

```c
#include <stdio.h>

main() {
int sum = 17, count = 5;
double mean;

mean = (double) sum / count; // typecasting
printf("Value of mean : %f\n", mean);
return (0);
}
```

