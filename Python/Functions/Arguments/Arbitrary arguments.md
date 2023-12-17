- We can define a function that is able to accept arbitrary or variable number of arguments.
- The arbitrary number of arguments might be [[Positional-only or keyword-only|positional]] or [[keyword arguments|keyword]] arguments.

Use: 
- An argument prefixed with a single asterisk `*` for arbitrary positional arguments.
- An argument prefixed with two asterisks `**` for arbitrary keyword arguments.

## \*args

Using the formal parameter `*<sequence_identifier>` the function will receive (when called) positional (comma separated) arguments without having to define how many.

Example:
```Python
def var_args(*args):
	"""Print passed args"""
	for i in args:
		print(i)

var_args('Foo', 'Bar')
var_args('Baz')
```
Notice that the pass arguments aren't tuples or lists, but comma separated arguments:
```Python
def var_args(*args):
	"""Print passed args"""
	for i in args:
		print(i)

x = ('a', 'b')
y = ('c', 'd')
var_args(y, x)
```
What get's printed are not the components of the tuples `x` and `y` but the tuples themselves.

Before the variable number of arguments, zero or more normal arguments may occur.

Normally, these _variadic_ arguments will be last in the list of formal parameters, because they scoop up all remaining input arguments that are passed to the function. Any formal parameters which occur after the `*args` parameter are ‘keyword-only’ arguments, meaning that they can only be used as keywords rather than positional arguments.

```Python
def product(*args, sci = False):
    """Return multiplication of args.
    
    Keyword arguments:
    sci -- scientific notation (default False)
    """
    x = 1
    for i in args:
    	x *= i
    if sci == True:
        print(f"{x:e}")
    else:
        print(x)

product(0.2, 0.3)
product(0.2, 0.3, sci = True)
product(0.2, 0.3, 0.5)
product(0.2, 0.3, 0.5, sci = True)
```

## \*\*kwargs

Using the formal parameter `**<sequence_identifier>` the function will receive (when called) keyword arguments without defining how many.

Example:
```Python
def keyword_args(**kwargs):
    """Print keyword and values passed"""
    for keyword, value in kwargs.items():
        print(f"{keyword}: {value}")
 
keyword_args(foo = 'foo', bar = 'bar')
keyword_args(foo = 'foo', bar = 'bar', baz = 'baz')
```