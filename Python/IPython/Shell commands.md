- Any command that works at the command-line can be used in IPython by prefixing it with `!`.

Example:
```IPython
!ls
!pwd
!echo "Printing from the shell"
```
Note: these results are not returned as lists or strings.

```IPython
dir = !pwd
# type(!pwd) this will fail
type(dir)
```

we can pass Python variables into the shell using `{<var>}`:
```IPython
foo = 'bar'
!echo {foo}
```

