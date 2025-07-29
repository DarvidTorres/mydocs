Reference count is the number of references ([[identifiers|identifiers]]) that a value has.

```python
import ctypes
def ref_count(address: int):
	return ctypes.c_long.from_address(address).value

ref_count(id(a))

a = [1, 2, 3]
print(hex(id(a)))
b = a
print(hex(id(a)))
```
