- Variables are names given to [[memory]] locations for storing [[types#value range|data values]].
- Name variables are called identifiers.
- Variables have [[types|type]].

To create a variable declare type and name:

```C
<type> <varName>;
```

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // variable declaration
    
    return (0);
}
```

To assign (or store) a [[types#value range|value]] in a variable, use the `=` operator:

```C
<type> <varName> = <value>;
```

We call this operation variable definition or initialization.

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // variable declaration
    myVar = 3; // variable definition / initialization
    
    return (0);
}
```

To display the value of variables in the terminal use [[format specifiers]].

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // variable declaration
    myVar = 3; // variable definition
    printf("myVar value is %d", myVar);
    
    return (0);
}
```


You can declare a variable without assigning the value, and assign the value later:

```C
// Declare a variable
int myNum; // identifier: myNum
myNum = 15; // Assign a value to the variable
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

