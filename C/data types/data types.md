Data type specifies the size and type of information the variable will store.

| type           | size (bytes) |
| -------------- | ------------ |
| chat           | 1            |
| unsigned char  | 1            |
| signed char    | 1            |
| int            | 2 or 4       |
| unsigned int   | 2 or 4       |
| short          | 2            |
| unsigned short | 2            |
| long           | 8            |
| unsigned long  | 8             |

## size

| type        | size (bytes) | precision |
| ----------- | ------------ | --------- |
| float       | 4            | 6         |
| double      | 8            | 15        |
| long double | 10           | 19          |

Example

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

The following programm outputs the following:

julien@ubuntu:~/c/$ ./size64
Size of a char: 1 byte(s)
Size of an int: 4 byte(s)
Size of a long int: 8 byte(s)
Size of a long long int: 8 byte(s)
Size of a float: 4 byte(s)

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

# integers

There are:
- `ints` plain base
- signed `int`
- unsigned `int`: non negative values

# characters

In C programming language, a character variable does not contain a character value itself rather the [ASCII value](https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html) of the character variable. The ascii value represents the character variable in numbers, and each character variable is assigned with some number range from 0 to 127. For example, the ascii value of 'A' is 65.

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

