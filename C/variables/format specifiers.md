- Format specifiers in C are used to take inputs and print the output of a type.
- To declare a format specifier use the `%` operator.
- Format specifiers tell the compiler about the type of data that must be given or input and the type of data that must be printed on the screen.

In C variables don't work as Python's (we can't print the value by calling the variable):

```C
int myNum = 15;
printf(myNum);  // Nothing happens
```

For doing that we need to specify format:

```c
%d or %i //A decimal integer or signed integer 
%c //Signed character 
%f //Signed float
%e //A floating-point number
%s  //A string or sequence of character 
%lf //double
%Lf //Long double 
%o //Octal integer 
%u // Short unsigned integer
%ld  //Long decimal integer
%x //Hexadecimal integer
%p //Print memory address in the hexadecimal form
```

In this way:

```c
int myNum = 15;
printf("%d", myNum);  // Outputs 15

int myNum = 15;
printf("My favorite number is: %d", myNum); // Outputs My favorite number is 15
```

The specifier is acting as a placeholder:

```c
int myNum = 15;
char myLetter = 'D';
printf("My number is %d and my letter is %c", myNum, myLetter);
```

```c
int x = 5, y = 6, z = 50; // declare multiple variables at once
printf("%d", x + y + z);

int x, y, z;
x = y = z = 50; // declare same value to several variables at once
printf("%d", x + y + z);
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
