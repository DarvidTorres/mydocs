A type qualifier is a keyword that is applied to a type, resulting in a qualified type.

C supports:
- `const`
- `restrict`
- `volatile`
- `_Atomic`

# const

- `const` declares a [[variables|variable]] to be unmodifiable.
- Prevents changes to defined variables.
- If we try to modify a `const` variable, the compiler will terminate with an error.

Example:

```C
#include <stdio.h>
void main()
{
    const int i = 5;
    i++;
}
```

Since `const` variables can't be modified, we must assign value at declaration.

Example:

```c
#include <stdio.h>
void main() {
    const int a;
    a = 3;
}
```

It is considered good practice uppercase `const` variables. It is not required, but useful for code readability and common for C programmers:

```c
const int BIRTHYEAR = 1980;
```

# volatile