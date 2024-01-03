To construct a multiply indexed `Series` or `DataFrame` is to simply pass a list of two or more index arrays to the constructor.

Example:
```Python
my_matrix = np.random.rand(4, 2)
my_matrix
my_data = pd.DataFrame(my_matrix,
				 index = [['a', 'a', 'b', 'b'], [1, 2, 1, 2]],
				 columns = ['data1', 'data2'])
my_data
```

The `unstack()` method converts a `MultiIndex` into a `DataFrame`.
The `stack()` method converts a `DataFrame` into a `MultiInex`
```Python
my_data2 = my_data.unstack()
my_data2
my_data2.stack()
```
