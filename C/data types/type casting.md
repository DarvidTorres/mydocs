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

