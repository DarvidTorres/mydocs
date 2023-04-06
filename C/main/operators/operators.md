# Arithmetic Operators

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

# Relational Operators

| Operator | Description                                                                                                                         |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| ==       | Checks if the values of two operands are equal or not. If yes, then the condition becomes true                                      |
| !=       | Checks if the values of two operands are equal or not. If the values are not equal, then the condition becomes true                 |
| >        | Checks if the value of left operand is greater than the value of right operand. If yes, then the condition becomes true             |
| <        | Checks if the value of left operand is less than the value of right operand. If yes, then the condition becomes true                |
| >=       | Checks if the value of left operand is greater than or equal to the value of right operand. If yes, then the condition becomes true |
| <=       | Checks if the value of left operand is less than or equal to the value of right operand. If yes, then the condition becomes true.   |

Examples:

```C
#include <stdio.h>

int main() {

   int a = 2;
   int b = 3;

   if( a == b ) {
      printf("a is equal to b\n" );
   } else {
      printf("a is not equal to b\n" );
   }
	
   if ( a < b ) {
      printf("a is less than b\n" );
   } else {
      printf("a is not less than b\n" );
   }
	
   if ( a > b ) {
      printf("a is greater than b\n" );
   } else {
      printf("a is not greater than b\n" );
   }
   
   if ( a <= b ) {
      printf("a is either less than or equal to  b\n" );
   } else {
      printf("a is neither less than nor equal to b\n");
   }
	
   if ( a >= b ) {
      printf("a is either greater than or equal to b\n" );
   } else {
      printf("a is neither greater than nor equal to b\n");
   }
   
   return (0);
}
```

# Logical Operators

| Operator | Description                                                                                                                                                | 
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| &&       | Called Logical AND operator. If both the operands are non-zero, then the condition becomes true                                                            |
| \|\|     | Called Logical OR Operator. If any of the two operands is non-zero, then the condition becomes true                                                        |
| !        | Called Logical NOT Operator. It is used to reverse the logical state of its operand. If a condition is true, then Logical NOT operator will make it false. |

Examples:

```C
#include <stdio.h>
#include <stdbool.h> // Header-file for boolean data-type.

int main() {

   bool a = false;
   bool b = true;
   
   printf("a is %s", a ? "true\n" : "false\n");
   printf("b is %s", b ? "true\n" : "false\n");
   
    if ( !a ) {
      printf("!a is true\n" );
   } else {
      printf("!a is false\n" );
   }
   
   if ( !b ) {
      printf("!b is true\n" );
   } else {
      printf("!b is false\n" );
   }

   if ( a && b ) {
      printf("a && b is true\n" );
   } else {
      printf("a && b is false\n" );
   }
	
   if ( a || b ) {
      printf("a || b is true\n" );
   } else {
      printf("a || b is false\n" );
   }
   
   return (0);
}
```

# Bitwise Operators

In the C programming language, operations can be performed on a bit level using bitwise operators.

| p   | q   | p & q | p \| q | p ^ q |
| --- | --- | ----- | ------ | ----- |
| 0   | 0   | 0     | 0      | 0     |
| 0   | 1   | 0     | 1      | 1     |
| 1   | 1   | 1     | 1      | 0     |
| 1   | 0   | 0     | 1      | 1     |

[Bitwise operations in C - Wikipedia](https://en.wikipedia.org/wiki/Bitwise_operations_in_C)

# Assignment Operators

| Operator | Description                                                                                                                        |  
| -------- | ---------------------------------------------------------------------------------------------------------------------------------- | 
| =        | Simple assignment operator. Assigns values from right side operands to left side operand                                           | 
| +=       | Add AND assignment operator. It adds the right operand to the left operand and assign the result to the left operand               | 
| -=       | Subtract AND assignment operator. It subtracts the right operand from the left operand and assigns the result to the left operand  | 
| \*=       | Multiply AND assignment operator. It multiplies the right operand with the left operand and assigns the result to the left operand|
| \/=      | Divide AND assignment operator. It divides the left operand with the right operand and assigns the result to the left operand      | 
| \%=      | Modulus AND assignment operator. It takes modulus using two operands and assigns the result to the left operand                    | 
| <<=      | Bitwise left shift assignment                                                                                                 | 
| >>=      | Bitwise right shift assignment                                                                                                | 
| &=       | Bitwise AND assignment operator                                                                                                    | 
| ^=       | Bitwise exclusive OR and assignment operator                                                                                       | 
| \|=      | Bitwise inclusive OR and assignment operator.                                                                                      | 

# Misc Operator

| Operator | Description                       | 
| -------- | --------------------------------- |
| sizeof() | Returns the [[types#storage size\|size]] of a variable    |
| &        | Returns the [[address]] of a variable |
| *        | [[pointers\|Pointer]] to a variable             |
| ? :      | [[if else#Ternary or Conditional operator\|Ternary or Conditional operator]].           |

