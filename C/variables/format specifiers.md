- Format specifiers in C are used to take inputs and print the output of a type.
- To declare a format specifier use the `%` operator.
- Format specifiers tell the [[compilation]] about the [[C/data types/types|type of data]] that must be given or input and the type of data that must be printed on the screen.

The Most commonly used format specifiers are given below:
| Format Specifiers | Type of Output                      |
| ----------------- | ----------------------------------- |
| %d or %i          | A decimal integer or signed integer |
| %c                | Signed character                    |
| %f                | Signed float                        |
|%e |A floating-point number|
|%s  |A string or sequence of character |
|%lf |double|
|%Lf |Long double |
|%o |Octal integer |
|%u |Short unsigned integer|
|%ld  |Long decimal integer|
|%x |Hexadecimal integer|
|%p |Print memory address in the hexadecimal form|

Examples:

- `%d` (Decimal [[int|Integer]]):

```C
#include <stdio.h>

int main() {
    int a = 50;
    printf("The integer value of a is %d", a);

    return 0;
}
```

- `%c` ([[char|Character]]):

```C
#include <stdio.h>

int main() {
    char a = 51;
    printf("The character is: %c", a);

    return 0;
}
```

- `%f` ([[floats|Floating Point]]):

```C
#include <stdio.h>

int main() {
    float a = 3;
    printf("The floating point of a: %f", a);

    return 0;
}
```

- `%e` ([[floats|Floating Pointer Number]]):

```C
#include <stdio.h>

int main() {
    float a = 12.5;
    printf("The floating-point of a: %e", a);

    return 0;
}
```

- `%s` ([[C/data structures/arrays/strings|String]]):

```C
#include <stdio.h>

int main() {
    char s[]="this is a string";
    printf("The string value of s is: %s \n", s);

    return 0;
}
```

- `%lf` (Double):

```C
#include <stdio.h>

int main() {
    double d = 12.5;
    printf("The double value of d is %lf \n", d);

    return 0;
}
```

- `%o` (octal integer):

```C
#include <stdio.h>

int main() {
    int oct = 11;
    printf("The octal integer value of oct is %o \n", oct);

    return 0;
}
```

- `%x` (Hexadecimal Integer):

```C
#include <stdio.h>

int main() {
    int h = 14;
    printf("The hexadecimal value of h is %x \n", h);

    return 0;
}
```

- `%p` (Prints Memory Address):

```C
#include <stdio.h>

int main() {
    int sum = 0;
    printf("The memory address of sum is %p \n", &sum);

    return 0;
}
```





Names are case sensitive (`myVar` and `myvar` are different variables)

To set decimal precision for `float`s do:

```c
float myFloatNum = 3.5;

printf("%f\n", myFloatNum); // Default will show 6 digits after the decimal point
printf("%.1f\n", myFloatNum); // Only show 1 digit
printf("%.2f\n", myFloatNum); // Only show 2 digits
printf("%.4f", myFloatNum);   // Only show 4 digits
```

we can convert types:

```c
// Automatic conversion: float to int
int myInt = 9.99;

printf("%d", myInt); // 9
```

the example below will print 2.000 because we convert the varable, which stored 2

```c
float sum = 5 / 2;

printf("%f", sum); // 2.000000
```

To get the correct float we need to convert before storing:

```c
// Manual conversion: int to float
float sum = (float) 5 / 2;

printf("%f", sum); // 2.500000
```

`%ls`type:

```c
    printf("4\n");          // Print narrow string of characters with a narrow function
    printf("%s\n", "5");    // Print narrow string of characters with a narrow function
    printf("%ls\n",L"6");   // Print wide string of characters with a narrow function
```
