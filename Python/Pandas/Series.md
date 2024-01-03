A Pandas `Series` is a one-dimensional array of indexed data.

syntax:
```HTML
pd.Series[<data>, index = <index>]
```
Note: index is an optional argument that defaults to an integer sequence.

Example:
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

Example:
```Python
data = pd.Series([0.25, 0.5, 0.75, 1.0],
				index = [3, 'd', '1', 'a'])
data
data['a']
```

We can use a [[Dictionaries|dictionary]] to define a `Series` with values and indexes (as dict. keys):
```Python
population_dict = {'California': 38332521,
                   'Texas': 26448193,
                   'New York': 19651127,
                   'Florida': 19552860,
                   'Illinois': 12882135}
population = pd.Series(population_dict)
population
```

Unlike a dictionary, the `Series` data type also supports array-style operations such as [[Python/NumPy/Slicing|Slicing]]:
```Python
population['California': 'Illinois']
population['California': 'Florida':2]
```

If we pass a dictionary to a Series, the index defaults to the sorted dictionary keys.

Example:
```Python
pd.Series({2:'Foo', 1:'Bar', 3:'Baz'})
pd.Series({'a':5, 'b':2, 'c': 3})
```

The index can be explicitly set:
```Python
pd.Series({2:'Foo', 1:'Bar', 3:'Baz'}, index = [3, 1, 2])
pd.Series({'a':5, 'b':2, 'c': 3}, index = ['c', 'a', 'b'])
```

Or we can populate the `Series` with the explicitly defined keys:
```Python
pd.Series({2:'Foo', 1:'Bar', 3:'Baz'}, index = [3, 2])
pd.Series({'a':5, 'b':2, 'c': 3}, index = ['c', 'b'])
```

