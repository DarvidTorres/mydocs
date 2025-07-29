- Reusing objects on-demand.
- Optimization strategy given that small integers show up often.
# Integers

At startup, CPython preloads a global list of integers in the range $[-5, 256]$ any time an integer is referenced in that range, Python will use the cached version of that object.

```Python
a = 10 # Python points to the existing reference for 10
a = 257 # A new object is created every time
```
# Strings

- Some string literals may also be automatically interned.
	- Generally, any string that satisfies the identifier naming convention will get interned.
- Force strings to be interned by using `sys.intern()`

