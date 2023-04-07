Logical Operators return either 0 (false) or 1 (true).

# NOT

| `p`   | `!p`  |
| --- | --- |
| 0   | 1   |
| 1   | 0   |


# AND

| `p`   | `q`   |`p&&q`  |
| --- | --- | ---- |
| 1   | 1   | 1    |
| 1   | 0   | 0    |
| 0   | 1   | 0    |
| 0   | 0   | 0    |


Syntax:

```C
(<condition_1> && <condition_2>)
```

Example:

```C
int main()
{
int a = 10, b = 20;

if (a > 0 && b > 0)
{
	printf("Both values are greater than 0\n");
}
else
{
	printf("Both values are less than 0\n");
}
return 0;
}

```

# OR

- Behaves as an inclusive or.

| `p` | `q` | p\|\|q |
| --- | --- | ------ |
| 1   | 1   | 1      |
| 1   | 0   | 1      |
| 0   | 1   | 1      |
| 0   | 0   | 0      |

Syntax:

```C
(condition_1 || condition_2)
```



