- `signed int`s: can hold positive or negative values.
	- An `int` type in C, C++, and C# is `signed` by default.
- If negative numbers are involved, the `int` must be `signed`.
	- `unsigned int`s: can hold positive values only.
	- An `unsigned int` cannot represent a negative number.

- `signed` indicates that a variable can hold negative and positive values.
- `unsigned` indicates a variable that can hold only positive numbers.
- `unsigned` is short for no signed (positive only).
- The property can be applied to most of the numeric data types including `int`, `char`, `short` and `long`.
- `signed` and  `unsigned` can standalone type specifiers, but they're used alone, they default to `int`.
- `signed` is [the default modifier for C](https://stackoverflow.com/questions/18603996/signed-as-default-in-c)
- Objects of type `long` can be declared as `signed long` or `unsigned long`. `signed long` is the same as `long` because signed is the default. The same applies to `short`.​


`Unsigned` types also have the special property of never overflowing in arithmetic. Adding 1 to a `signed` variable that already contains the maximum possible positive number for its type will result in overflow, and the program's behavior becomes undefined. That can never happen with `unsigned` types, because they are defined to work "modulo one greater than the maximum number that they can hold". What this means is best illustrated by example:

```C
#include <stdio.h>
#include <stdlib.h>
main(){
      unsigned int x;
      x = 0;
      while(x >= 0){
              printf("%u\n", x);
              x++;
      }

      exit(EXIT_SUCCESS);
}
```

Assuming that the variable x is stored in 16 bits, then its range of values will be 0–65535 and that sequence will be printed endlessly because the condition `x >= 0` must always be true for an unsigned variable.