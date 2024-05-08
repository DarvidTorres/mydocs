
| Operator | Name           |
| -------- | -------------- |
| `+`      | Addition       |
| `-`      | Subtraction    |
| `*`      | Multiplication |
| `/`      | Division       |
| `%`      | Modulus        |
| `**`     | Exponent       |
| `//`     | Floor Division |

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

## Modulus and Floor division
The quotient $q$ and the remainder $r$ of $a$ divided by $n$ satisfy the following:

$$
q \in \mathbb{Z}, \quad a = nq+r, \quad |r|<|n|
$$
Example:
$$
\frac{7}{3} \Longrightarrow 7 = (3) \underbrace{(2)}_{\text{quotient}} + \underbrace{1}_{\text{reminder}} \approx 2.\overline{3}
$$
In Python, to obtain:
- the quotient, use the **Floor division**: `//`
- the remainder, use the **Modulus**: `%`

Example:
```Python
Numerator = 7
Denominator = 3
quotient = Numerator // Denominator # Floor division
print(quotient)
remainder = Numerator % Denominator # Modulo
print(remainder)
```