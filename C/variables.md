- Variables are names given to [[memory]] locations for storing [[types#value range|data values]].
- Name variables are called identifiers.
- Variables have [[types|type]].

To create a variable declare type, give name and add [[types#value range|value]]:
```C
<type> <name> = <value>;
```

Example:

```C
int myVar = 15;
```

Create a variable called myVar of type int and store the value 15 in the variable's memory location.

You can declare a variable without assigning the value, and assign the value later:

```C
// Declare a variable
int myNum; // identifier: myNum
myNum = 15; // Assign a value to the variable
```

# format 

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

# constants

the `const` keyword prevents changes to defined variables.

```c
const int myNum = 15;  // myNum will always be 15
myNum = 10;  // error: assignment of read-only variable 'myNum'
```

Constants must be defined with value:

```c
const int minutesPerHour;
minutesPerHour = 60; // error
```

it is considered good practice to declare them with uppercase. It is not required, but useful for code readability and common for C programmers:

```c
const int BIRTHYEAR = 1980;
```

# scope

## local scope

The scope of a variable is the block of code in the entire program where the variable is declared, used, and can be modified.

```c
{
	/*BLOCK 1*/
    // contents of BLOCK 2 cannot be accessed here
}

{
	/*BLOCK 2*/
    // contents of BLOCK 1 cannot be accessed here
}
```

```c
{
	/*OUTER BLOCK*/
    
	{    /*INNER BLOCK*/
        //contents of the outer block just before the start of this block
        //CAN be accessed here
      }
    
       //contents of the inner block are NOT accessible here
 }
```

## global scope

```c
/*all global variables are declared here */

function1()
	{
    // all global variables can be accessed inside function1
    }
    
function2()
	{
    // all global variables can be accessed inside function2
    }
```

