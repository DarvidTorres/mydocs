A type qualifier is a keyword that is applied to a type, resulting in a qualified type.

C supports:
- `const`
- `restrict`
- `volatile`
- `_Atomic`

# const

- `const` declares a [[variables|variable]] to be nonmodifiable.
- Prevents changes to defined variables.
- If we try to modify a `const` variable, the compiler will terminate with an error.

Example:

```C
#include <stdio.h>
void main()
{
    const int i = 5;
    i = 10;
    i++;
}
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
