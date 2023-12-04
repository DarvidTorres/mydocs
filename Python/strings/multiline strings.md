# multiline strings

String literals can span multiple lines using triple-quotes:

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