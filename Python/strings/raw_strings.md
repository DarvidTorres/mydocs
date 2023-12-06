
If you don’t want characters prefaced by `\` to be interpreted as special characters, you can use raw strings by adding an r before the first quote:

```Python
print('C:\some\name')  # here \n means newline!
print(r'C:\some\name')  # note the r before the quote
```
There is one subtle aspect to raw strings: a raw string may not end in an odd number of `\` characters; see the [FAQ](https://docs.python.org/3/faq/programming.html#faq-programming-raw-string-backslash) for more information and workarounds.


