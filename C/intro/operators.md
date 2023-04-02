
- Operators in C are special symbols used to perform specific functions
- Variables on which the operators are applied are known as operands.

## Arithmetic Operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| +        | Adds two operands.                                           |
| −        | Subtracts second operand from the first.                     |
| *        | Multiplies both operands.                                    |
| /        | Divides numerator by de-numerator.                           |
| %        | Modulus Operator and remainder of after an integer division. |
| ++       | Increment operator increases the integer value by one.       |
| --       | Decrement operator decreases the integer value by one.       |

Examples:

```C
#include <stdio.h>

int main() {

   int a = 2;
   int b = 3;
   int c ;
   
   printf("Value of a is %d\n", a);
   printf("Value of b is %d\n", b);

   c = a + b;
   printf("Value of a + b is %d\n", c);
	
   c = a - b;
   printf("Value of a - b is %d\n", c);
	
   c = a * b;
   printf("Value of a * b is %d\n", c);
	
   c = a / b;
   printf("Value of a / b is %d\n", c);
	
   c = a % b;
   printf("Value of a %% b is %d\n", c);
   
   c = ++a;
   printf("Value of ++a is %d\n", c);
	
   c = a++;
   printf("Value of a++ is %d\n", c);
   
   c = --a; 
   printf("Value of --a is %d\n", c);
	
   c = a--; 
   printf("Value of a-- is %d\n", c);
   
   return (0);
}
```

Relational Operators
- Logical Operators
- Bitwise Operators
- Assignment Operators
- Misc Operator