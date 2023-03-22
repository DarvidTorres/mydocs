Recursion let us define a function in terms of itself:

```c
void recursion() {
   recursion(); /* function calls itself */
}

int main() {
   recursion();
}
```

we need to define an exit condition from the function, otherwise it will go into an infinite loop. The exit conditino is usually called base case.

The following is a classic factorial definition example:

```c
#include <stdio.h>

unsigned long long int factorial(unsigned int i) {

   if(i <= 1) {
      return 1; // base case
   }
   return i * factorial(i - 1);
}

int  main() {
   int i = 12;
   printf("Factorial of %d is %d\n", i, factorial(i));
   return 0;
}
```