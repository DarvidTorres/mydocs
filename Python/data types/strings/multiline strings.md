- For triple-quoted strings, always use double quote characters to be consistent with the [[docstrings|docstring]] convention in PEP 257.
- The line length should be limited to 72 characters.

String [[literals]] can span multiple lines using triple-quotes:

 ```python
 a = '''this
 is a string
 '''
 a
 print(a)
```

Non-visible characters such as newlines, tabs, etc. are actually part of the string.

```Python
print("""a\
b
c
""")

print('''d
e\
f
''')
```

End of lines are automatically included in the string, but it’s possible to prevent this by adding a `\` at the end of the line.

