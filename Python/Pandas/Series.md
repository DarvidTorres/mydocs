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

# Data selection in Series

Like a [[Dictionaries|dictionary]], the `Series` object provides a mapping from a mapping from a collection of keys to a collection of values.

Example:
```Python
import pandas as pd
data = pd.Series([0.25, 0.5, 0.75, 1.0],
				index = ['a', 'b', 'c', 'd'])
data
```

We can use dictionary-like Python expressions and methods to examine the key/indices and values:
```Python
'a' in data
data.keys()
```

`Series` objects can be modified with a dictionary-like syntax:
```Python
data
data['e'] = 1.25
data
```

We can slice `Series` as [[Python/NumPy/Arrays|Arrays]];
```Python
data['a':'c'] # slicing by explicit index
data[0:2] # slicing by implicit integer index
```
Note: when slicing with an explicit index, the final index is included in the slice, while when slicing with an implicit index, the final index is excluded from the slice.

```Python
data[(data > 0.3) & (data < 0.8)] # masking
data[['a', 'e']] # fancy indexing
```

If a `Series` has an explicit integer index, an indexing operation as `data[1]` will use the explicit indices:
```Python
data[1] # explicit index when indexing
data[1:3] # explicit index when slicing
```
Because of this potential confusion in the case of integer indexes, we have the `loc` attribute.

The `loc` attribute allows indexing and slicing that always references the explicit index:
```Python
data.loc[1]
data.loc[1:3]
```

The `iloc` attribute allows indexing and slicing that always references the implicit index:
```Python
data.iloc[1]
data.iloc[1:3]
```

One guiding principle of Python code is that "explicit is better than implicit."

```Python
import this
```

