
String [[literals]] can span multiple lines using triple-quotes:

```python
print(
    '''This is a
    multi-line
    string
    '''
)

print("Single-line string")
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

