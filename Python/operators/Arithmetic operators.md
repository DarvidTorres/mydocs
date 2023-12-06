| Operator | Name           | Example      |
| -------- | -------------- | ------------ |
| `+`      | Addition       | `a + b = 30` |
| `-`      | Subtraction    | `a – b = -10` |
| `*`      | Multiplication | `a * b = 200` |
| `/`      | Division       | `b / a = 2` |
| `%`      | Modulus        | `b % a = 0` |
| `**`     | Exponent       | `a**b =10**20` |
| `//`     | Floor Division | `9//2 = 4` |

- Addition of `integer` and `float` results in a `float`. See [[type_casting#Implicit casting]]
```Python
type(a := 10)
type(b := 20.5)
print(type(a+b))
```

- Subtraction of an integer and a float follows the same principle.
```Python
print(type(a := 10))
print(type(b := 20.5))
print(type(a-b))
```

- In multiplication, a `float` operand may have a standard decimal point notation, or a scientific notation.
```Python
print(type(a := 10)) # int
print(type(b := 20.5)) # float
print(type(c := 6.75E-3)) # float (scientific notation)
print(type(a * b))
print(type(a * c))
```

