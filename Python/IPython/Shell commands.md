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
type(dir)
```