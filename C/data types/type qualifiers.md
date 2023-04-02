A type qualifier is a keyword that is applied to a type, resulting in a qualified type.

C supports:
- `const`
- `restrict`
- `volatile`
- `_Atomic`

# const

- `const` declares a [[variables|variable]] to be a [[tokens#constants|constant]] (unmodifiable variable).
- Prevents changes to defined variables.
- variables declared with `const` will default to $0$.

Example:

```C
#include <stdio.h>

int main() 
{
	const int a;
	printf("%d", a);
	
	return 0;
}
```

* Since `const` variables can't be modified, we must assign value at declaration or we'll get unmodifiable default value.

Example:

```c
#include <stdio.h>
int main() {
    const int a = 3;

	return (0);
}
```

- If we try to modify a `const` variable, the compiler will terminate with an error.

Example:

```C
#include <stdio.h>
int main()
{
    const int i = 5;
    i++;

	return (0);
}
```

It is considered good practice uppercase `const` variables. It is not required, but useful for code readability and common for C programmers:

```c
const int BIRTHYEAR = 1980;
```

# volatile