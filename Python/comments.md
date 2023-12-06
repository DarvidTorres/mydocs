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

* We use triple quotation marks for multi-line strings.

Since Python will ignore string literals that are not assigned to a variable, you can add a multiline string (triple quotes) in your code, and place your comment inside it:

```Python
'''
I am a
multi-line comment!
'''

"""
This is a comment
written in
more than just one line
"""

print("Hello, World!")
```

# docstrings

Python docstrings are the string literals that appear right after the definition of a function, method, class, or module.