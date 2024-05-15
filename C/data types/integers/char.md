- `char` is basically an [[C/data types/integers/int]].
- A `char` does not contain a character value itself rather the [[ASCII]] of the character variable.
- Each character is given a numeric value such as A = 65, B = 66, etc.
- The ASCII value represents the character variable in numbers, and each character variable is assigned with some number range from 0 to 127.
	- For example, the ascii value of 'A' is 65.
- C defines a minimum set of characters that need to be supported on a system where C programs are written and run.
- C does not specify whether a plain ‘char’ refers to a signed or unsigned number – that is implementation defined.
- If you need to be sure your char variable is signed or unsigned, specify it in the declaration like this: `unsigned char c`.
- When a character variable is printed using the `%c` format with `printf`, the appropriate character is output. You can use `%d`, if you like, to see what integer value is used to represent the character.
- Since `char` variables are `int` variables, we can perform arithmetic on them.

Example:

```C
# include <limits.h>
# include <stdio.h>
# include <stdlib.h>

int main(){
      char c;

      c = CHAR_MIN;
      while(c != CHAR_MAX){
              printf("%d\n", c);
              c = c+1;
      }

      exit(EXIT_SUCCESS);
}
```

`CHAR_MIN` and `CHAR_MAX` are constants defined in the `<limits.h>` header file.