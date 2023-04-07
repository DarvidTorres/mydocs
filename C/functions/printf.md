# puts() vs printf()


```c
#include <stdio.h>

int main() {
  printf("Hello World!");
  printf("I am learning C.");
  return 0;
}
```
There's no new line between outputs.

when you have only one char in the `printf()` the compiler turns it into a `putchar()`

```c
#include <stdio.h>
int main()
{
    puts("Geeksfor");
    puts("Geeks");
 
    getchar();
    return 0;
}
```

Program that prints exactly "Programming is like building a multilingual puzzle:

```C
#include <stdio.h>
int main(void)
{
puts("\"Programming is like building a multilingual puzzle");
return (0);
}
```

`puts` appends a new line to the end of output, while `fputs` and `printf` do not:

```C
/* Need to escape a new line */
#include<stdio.h>
int main(void)
{
printf("with proper grammar, but the outcome is a piece of art,\n");
return (0);
}
```
