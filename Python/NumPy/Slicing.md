Each array has three attributes:
1.  `ndim`: number of dimensions
2. `shape`: size of each dimension
3. `size`: total size of the array

```Python
x3 = np.random.randint(10, size = (3, 4, 5)) # Three-dimensional array
print(f"x3 ndim: {x3.ndim}")
print(f"x3 shape: {x3.shape}")
print(f"x3 size: {x3.size}")
print(f"dtype: {x3.dtype}")
```

NumPy slicing syntax follows the standard Python list slicing:
`<list_identifier>[start = 0:stop = size of dimension:step = 1]`

```Python
x = np.arange(10)
x[::2]
x[1::2]
```

A potentially confusing case is when the step value is negative. In this case, the defaults for **start** and **stop** are swapped. This becomes a convenient way to reverse an array:

```Python
x = np.arange(10)
x[::-1] # all elements are reversed
x[5::-2] # reversed every other from index 5
```

Multi-dimensional slices work in the same way, with multiple slices separated by commas.

```Python
x2 = np.random.randint(10, size = (3, 4)) # Two-dimensional array
x2[:2, :3] # two rows, three columns
x2[:3, ::2] # three rows, every other column
x2[::-1, ::-1]
```

Access single rows or columns of an array by combining indexing and slicing.

```Python
x2 = np.random.randint(10, size = (3, 4)) # Two-dimensional array
x2[:, 0]
x2[:, 0:2]
x2[0, :]
x2[0]
```

Array slices return *views* rather than copies of array data. If we modify a subarray the original is also modified

```Python
x2 = np.random.randint(10, size = (3, 4)) # Two-dimensional array
x2_sub = x2[:2, :2]
x2_sub
x2_sub[0, 0] = 99
x2_sub
x2
```

Copy the data within an array with the `copy()` method, this will avoid modifying the original array

```Python
x2_sub_copy = x2[:2, :2].copy()
x2_sub_copy
x2_sub_copy[0, 0] = 42
x2_sub_copy
x2
```

```Python
grid = np.arange(1, 10)
grid
grid.reshape((3,3))
grid
```

```Python
x = np.array([1, 2, 3])
x
x.reshape((1, 3))
x.reshape((3, 1))
```