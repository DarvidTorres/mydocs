# multiline comments
Python does not really have a syntax for multiline comments.
To add a multiline comment you could insert a `#` for each line:

```Python
#This is a comment
#written in
#more than just one line

print("Hello, World!")
```

- If we do not assign strings to any variable, they act as comments.

```Python
"I am a single-line comment"

print("Hello World")
```

* We use triple quotation marks for [[multiline strings]].
* The line length should be limited to 72 characters.

Since Python will ignore string literals that are not assigned to a variable, you can add a multiline string (triple quotes) in your code, and place your comment inside it:

```Python
"""
This is a comment
written in
more than just one line
"""

print("Hello, World!")
```

[[multiline strings]] are not comments, although they can be used as such, especially with special comments called [[docstrings]].
