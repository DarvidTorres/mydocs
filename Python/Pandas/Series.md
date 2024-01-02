A Pandas `Series` is a one-dimensional array of indexed data. It can be created from a list or array as follows:

```Python
data = pd.Series([0.25, 0.5, 0.75, 1.0])
data
```

The `Series` wraps both a sequence of values and a sequence of indices.

```Python
data.values
data.index
```

While the [[Python/NumPy/Arrays|Numpy Array]] has an implicitly defined integer index used to access the values, the Pandas Series has an explicitly defined index associated with the values.

This explicit index definition gives the Series object additional capabilities. For example, the index need not be an integer, but can consist of values of any desired type.
