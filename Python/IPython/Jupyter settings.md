In Jupyter notebooks you do not see the output of every expression of a cell by default.
The `ast_node_interactivity` setting modifies which results are shown as outputs.
Options:
- `last_expr` only print the last statement if it is an expression (default).
- `none` print nothing.
- `last` prints the last expression, even if it is in a loop, without a newline character.
- `last_expr_or_assign` print the last expression or assignment. Only for simple variables, e.g. doesn't work when you assign a value to a position in an array.
- `all` prints all expressions without a newline character.

Example:
```IPython
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = 'all'
```

## Google Colab

Install IPython

# Error messages

`%xmode` takes a single argument, the mode, and there are three possibilities: `Plain`, `Context`, and `Verbose`. The default is `Context`, and gives output like that just shown before. `Plain` is more compact and gives less information:

```Python
%xmode Plain
```