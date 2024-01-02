
- NumPy provides efficient storage of array-based data.
- Unlike Python lists, NumPy is constrained to arrays that all contain the same type.
- If types do not match, NumPy will upcast if possible.

Example:
```Python
import numpy as np
np.array([3.14, 4, 2, 3])
```
Note: integers are up-cast to floating point.

If we want to explicitly set the data type of the resulting array, we can use the `dtype` keyword:

```Python
np.array([1, 2, 3, 4], dtype='float32')
```

- Unlike Python lists, NumPy arrays can explicitly be multi-dimensional.

Example:
```Python
# nested lists result in multi-dimensional arrays
np.array([range(i, i + 3) for i in [2, 4, 6]])
```
