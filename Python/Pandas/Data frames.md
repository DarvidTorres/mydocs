- We can think of a `DataFrame` as a sequence of [[Series|Series]] objects that share the same index.
- Where a [[Dictionaries|dictionary]] maps a key to a value, a `DataFrame` maps a column name to a `Series` of column data.

Example:
```Python
pop_dict = {'California': 38332521,
                   'Texas': 26448193,
                   'New York': 19651127,
                   'Florida': 19552860,
                   'Illinois': 12882135}

area_dict = {'California': 423967,
			 'Texas': 695662,
			 'New York': 141297,
             'Florida': 170312,
             'Illinois': 149995}

population = pd.Series(pop_dict)
area = pd.Series(area_dict)

states = pd.DataFrame({'population': population,
                       'area': area})

states
```

A `DataFrame` is a collection of [[Series]] objects, and a single-column `DataFrame` can be constructed from a single `Series`:

```Python
pd.DataFrame(population, columns = ['population'])
```

In a `Series` object, dictionary keys are passed as the index; in a `DataFrame` dictionary keys are passed as variables (column names):
```Python
pd.DataFrame([{'Foo': 1, 'Bar': 2},
			 {'Foo': 3, 'Baz': 4}])
```
Note: Even if some keys in the dictionary are missing, Pandas will fill them in with NaN (i.e., "not a number").

