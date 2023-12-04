# f-strings

formatted string literals (f-strings).

- To create an f-string, prefix the string with the letter `f` or the uppercase `F`.

Example: 

```Python
f'foo bar baz'

F'qux quux'
```

Just like with any other type of string, you can use single, double, or triple quotes to define an f-string:

```Python
f'foo'
f"bar"
f'''baz'''
```

## f-string expressions

Any portion of an f-string that’s enclosed in curly braces ``{}`` is treated as an "f-string expression". The expression is evaluated and converted to string representation, and the result is interpolated into the original string in that location:

```Python
s = 'bar'
print(f'foo {s}')
```

An f-string expression can’t be empty:

```Python
f'foo{}bar'
SyntaxError: f-string: empty expression not allowed
```

An f-string expression (what's inside the curly brackets) cannot include a backslash `\`. Among other things, that means you can’t use a backslash escape sequence in an f-string expression:

```Python
f"newline: {'\n'}"
# SyntaxError: f-string expression part cannot include a backslash
```

but we can put the backslash into a variable as a workaround:

```Python
a = '\n'
print(f'New line: {a}')
```

The interpreter treats the remainder of the f-string—anything not inside curly braces—just as it would an ordinary string. For example, backlash (escape sequences) are processed as expected:

```Python
s = 'bar'
print(f'foo\n{s}')
```

We can escape curly braces using double curly braces ``{{}}``:

```Python
print(f'{{}}')
```

A single quote is escaped with a backslash character.

```Python
print(f'This was a \'great\' film')
```

You may prefix an f-string with 'r' or 'R' to indicate that it is a raw f-string. In that case, backslash sequences are left intact, just like with an ordinary string. You can specify the `'r'` first and then the `'f'`, or vice-versa.

```Python
print(rf'foo\n')
print(fr'bar\n')
```

F-string also makes debugging easier too. Instead of printing the variable name and its value, we only need to write the variable inside the f-string `{variable_name=}`:

```Python
a = 10
print(f'{a = }')
```

We can do arithmetic operations inside f-string expressions:

```Python
x = 2
print(f'{x} cubed is {x**3}')
```

We can also call functions in f-strings.

```Python
def mymax(x, y):

    return x if x > y else y

a = 3
b = 4

print(f'Max of {a} and {b} is {mymax(a, b)}')
```

we can make explicit the definition of variables

```Python
a = [1, 2 ,3]
b = {'foo': 1, 'bar': 2}
print(f'{a}')
print(f'{b}')
```

# Format Specification Mini-Language

To format f-string expressions use the following syntax:

```Python
f'{<value>:[[fill]align][sign][width][grouping_option]["." precision][type]}'

#You need to specify precision only in case of floating point numbers
```

In a more simplistic way:

```Python
f'{<value>:<formatting_options>}'
```

Since formatting applies to the f-string expression, everything comes inside the curly brackets, and we use the `:` to separate the value we want to format from the formatting options that follow.
## Width and alignment

For width and alignment we use the syntax:

```Python
{<value>:[[fill]align][width]}
```

Where `align` is one of the following:

| Option | Meaning                                                                                                                                                                                                                                                                            |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<`    | Forces the field to be left-aligned within the available space (this is the default for most objects).                                                                                                                                                                             |
| `>`    | Forces the field to be right-aligned within the available space (this is the default for numbers).                                                                                                                                                                                 |
|`^`|Forces the field to be centered within the available space.|
| `=`    | Forces the padding to be placed after the sign (if any) but before the digits. This is used for printing fields in the form ‘+000000120’. This alignment option is only valid for numeric types. It becomes the default for numbers when ‘0’ immediately precedes the field width. |

`width` is input as a number defining the size (number of characters) we want the output string to have. `width` is a decimal integer defining the minimum total field width, including any formatting characters. If not specified, then the field width will be determined by the content.

Example:

```Python
a = 3
print(f'{a:>5}')
```

In the example above, the align option `>` forces the output to be a string of size five, where the value `a` is at the rightmost position, and the rest (four) characters (to the left of `a`) are spaces (by default). We can define which character will pad (`fill`) the string:

```Python
a = 3
print(f'{a:>5}')
print(f'{a:#>5}')
print(f'{a:$>5}')
print(f'{a:%>5}')
print(f'{a:_>5}')
```

The same applies for `<`:

```Python
a = 3
print(f'{a:<5}')
print(f'{a:#<5}')
print(f'{a:$<5}')
print(f'{a:%<5}')
print(f'{a:_<5}')
```

The same also applies to `^`, but the center positioning will depend on how long the input value is (how many digits or characters it has) and how large we define the string to be:

```Python
a = 3
b = 11
print(f'{a:^5}')
print(f'{a:#^5}')
print(f'{a:$^5}')
print(f'{a:%^5}')
print(f'{a:_^5}')

print("\n")

print(f'{b:^5}')
print(f'{b:#^5}')
print(f'{b:$^5}')
print(f'{b:%^5}')
print(f'{b:_^5}')
```

Finally we have three options for `=`:

|Option|Meaning|
|---|---|
|`'+'`|indicates that a sign should be used for both positive as well as negative numbers.|
|`'-'`|indicates that a sign should be used only for negative numbers (this is the default behavior).|
|space|indicates that a leading space should be used on positive numbers, and a minus sign on negative numbers.|

The option `=` has two sign options (see table above): `+` and `-` (as default), both of which align the input value to the right most position and:

* The default option `-` displays the sign at the left most position only for negative values:

```Python
a = 3
c = -2

print(f'{a:=5}')
print(f'{a:#=5}')
print(f'{a:$=5}')
print(f'{a:%=5}')
print(f'{a:_=5}')

print("\n")

print(f'{c:=5}')
print(f'{c:#=5}')
print(f'{c:$=5}')
print(f'{c:%=5}')
print(f'{c:_=5}')
```

* The option `+` displays the sign at the left most position for both, positive and negative values:

```Python
a = 3
c = -2

print(f'{a:=+5}')
print(f'{a:#=+5}')
print(f'{a:$=+5}')
print(f'{a:%=+5}')
print(f'{a:_=+5}')

print("\n")

print(f'{c:=+5}')
print(f'{c:#=+5}')
print(f'{c:$=+5}')
print(f'{c:%=+5}')
print(f'{c:_=+5}')
```

The `=` option also has a space variant which will add a space at the leftmost position for positive values, but a negative sign for negative values.

```Python
a = 3
c = -2

print(f'{a:= 5}')
print(f'{a:#= 5}')
print(f'{a:$= 5}')
print(f'{a:%= 5}')
print(f'{a:_= 5}')

print("\n")

print(f'{c:= 5}')
print(f'{c:#= 5}')
print(f'{c:$= 5}')
print(f'{c:%= 5}')
print(f'{c:_= 5}')
```

Finally, sign options can be used with all alignment options:

```Python
a = 3
c = -2

print(f'{a:=+5}')
print(f'{a:#<+5}')
print(f'{a:$>+5}')
print(f'{a:%^+5}')
print(f'{a:&>-5}')
print(f'{a:0> 5}')

print("\n")

print(f'{c:=+5}')
print(f'{c:#<+5}')
print(f'{c:$>+5}')
print(f'{c:%^+5}')
print(f'{c:&>-5}')
print(f'{c:0> 5}')
```

The option 

## Grouping option

We use the syntax: 

```Python
f'{<value>:[[fill]align][sign][width][grouping_option]}'
```

We can ad either `,` or `_` for a thousand separator.

Example:

```Python
x = 12400
print(f'{x:,}')
print(f'{x:_}')
```

## Types

The type determines how the data should be presented.

Syntax:
```Python
f'{<value>:[[fill]align][sign][width][grouping_option][type]}'
```

The available integer presentation types are:

|Type|Meaning|
|---|---|
|`'b'`|Binary format. Outputs the number in base 2.|
|`'c'`|Character. Converts the integer to the corresponding unicode character before printing.|
|`'d'`|Decimal Integer. Outputs the number in base 10.|
|`'o'`|Octal format. Outputs the number in base 8.|
|`'x'`|Hex format. Outputs the number in base 16, using lower-case letters for the digits above 9.|
|`'X'`|Hex format. Outputs the number in base 16, using upper-case letters for the digits above 9. In case `'#'` is specified, the prefix `'0x'` will be upper-cased to `'0X'` as well.|

Example:

```Python
x = 35
print(f"x is of {type(x)}")
print(f'{x} in binary is {35:b}')
print(f'Unicode character {35} is {35:c}')
print(f'{x} decimal integer is {35:d}')
print(f'{x} in octal format is {35:o}')
print(f'{x} in hex format is {35:x}')
```

In addition to the above presentation types, integers can be formatted with the floating point presentation types listed below (except 'n' and None). When doing so, float() is used to convert the integer to a floating point number before formatting.

The available presentation types for float and Decimal values are

|Type|Meaning|
|---|---|
|`'e'`|Scientific notation. For a given precision `p`, formats the number in scientific notation with the letter ‘e’ separating the coefficient from the exponent. The coefficient has one digit before and `p` digits after the decimal point, for a total of `p + 1` significant digits. With no precision given, uses a precision of `6` digits after the decimal point for [`float`](https://docs.python.org/3/library/functions.html#float "float"), and shows all coefficient digits for [`Decimal`](https://docs.python.org/3/library/decimal.html#decimal.Decimal "decimal.Decimal"). If no digits follow the decimal point, the decimal point is also removed unless the `#` option is used.|
|`'E'`|Scientific notation. Same as `'e'` except it uses an upper case ‘E’ as the separator character.|
|`'f'`|Fixed-point notation. For a given precision `p`, formats the number as a decimal number with exactly `p` digits following the decimal point. With no precision given, uses a precision of `6` digits after the decimal point for [`float`](https://docs.python.org/3/library/functions.html#float "float"), and uses a precision large enough to show all coefficient digits for [`Decimal`](https://docs.python.org/3/library/decimal.html#decimal.Decimal "decimal.Decimal"). If no digits follow the decimal point, the decimal point is also removed unless the `#` option is used.|
|`'F'`|Fixed-point notation. Same as `'f'`, but converts `nan` to `NAN` and `inf` to `INF`.|
|`'g'`|General format. For a given precision `p >= 1`, this rounds the number to `p` significant digits and then formats the result in either fixed-point format or in scientific notation, depending on its magnitude. A precision of `0` is treated as equivalent to a precision of `1`.<br><br>The precise rules are as follows: suppose that the result formatted with presentation type `'e'` and precision `p-1` would have exponent `exp`. Then, if `m <= exp < p`, where `m` is -4 for floats and -6 for [`Decimals`](https://docs.python.org/3/library/decimal.html#decimal.Decimal "decimal.Decimal"), the number is formatted with presentation type `'f'` and precision `p-1-exp`. Otherwise, the number is formatted with presentation type `'e'` and precision `p-1`. In both cases insignificant trailing zeros are removed from the significand, and the decimal point is also removed if there are no remaining digits following it, unless the `'#'` option is used.<br><br>With no precision given, uses a precision of `6` significant digits for [`float`](https://docs.python.org/3/library/functions.html#float "float"). For [`Decimal`](https://docs.python.org/3/library/decimal.html#decimal.Decimal "decimal.Decimal"), the coefficient of the result is formed from the coefficient digits of the value; scientific notation is used for values smaller than `1e-6` in absolute value and values where the place value of the least significant digit is larger than 1, and fixed-point notation is used otherwise.<br><br>Positive and negative infinity, positive and negative zero, and nans, are formatted as `inf`, `-inf`, `0`, `-0` and `nan` respectively, regardless of the precision.|
|`'G'`|General format. Same as `'g'` except switches to `'E'` if the number gets too large. The representations of infinity and NaN are uppercased, too.|
|`'%'`|Percentage. Multiplies the number by 100 and displays in fixed (`'f'`) format, followed by a percent sign.|

Example:

```Python
x = 35.23
print(f'{x:.3e}')
print(f'{x:.3f}')
print(f'{x:.3g}')
print(f'{x:.3%}')
```
## Precision

The precision is a decimal integer indicating how many digits should be displayed after the decimal point for presentation floating presentation types.

Syntax:
```Python
f'{<value>:[[fill]align][sign][width][grouping_option]["." precision][type]}'

#You need to specify precision only in case of floating point numbers
```

Example:

```Python
x = 35.23
print(f'{x:.3e}')
print(f'{x:.3f}')
print(f'{x:.3g}')
print(f'{x:.3%}')
```


