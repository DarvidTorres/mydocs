`None` is a Python singleton object that cannot be used in any arbitrary Numpy/Pandas array, but only in arrays with data type `object`.

Example:
```Python
import numpy as np
np.array([1, None, 3, 4])
```

The type `object` means that the best common type representation that Numpy could infer for the contents of the array is that they are Python objects. Any operations on the data will be done at the Python level, with much more overhead than the typically fast operations seen for arrays with native types:
```Python
%timeit np.arange(1E6, dtype = object).sum()
%timeit np.arange(1E6, dtype = int).sum()
```

# Not A Number

`NaN` is a special floating-point value recognized by all systems that use the standard [IEEE](https://en.wikipedia.org/wiki/IEEE_754) floating-point representation:
```Python
my_array = np.array([1, np.nan, 3, 4])
my_array.dtype
```

`NaN` is specifically a floating-point value; there is no equivalent NaN value for integers, strings, or other types.

Regardless of the operation, the result of arithmetic with `NaN` will be another `NaN`:
```Python
1 + np.nan
1 * np.nan
my_array.sum()
```

NumPy provides special aggregations that will ignore these missing values:
```Python
np.nansum(my_array)
np.nanmin(my_array)
np.nanmax(my_array)
```

Pandas automatically type-casts to floating-point values when `NaN` values are present:
```Python
pd.Series([1, np.nan])
```

Pandas converts `NaN` and `None` where appropriate:
```Python
pd.Series([0, np.nan, None])
```
In addition to casting the integer array to floating point, Pandas automatically converts the None to a NaN value.

There are several useful methods for detecting, removing, and replacing null values in Pandas data structures.
- `isnull()`: Generate a boolean mask indicating missing values
- `notnull()`: Opposite of `isnull()`
- `dropna()`: Return a filtered version of the data
- `fillna()`: Return a copy of the data with missing values filled or imputed

By default, `dropna()` will drop all rows in which any null value is present:
```Python
df = pd.DataFrame([[1,      np.nan, 2],
                   [2,      3,      5],
                   [np.nan, 4,      6]])
df
df.dropna()
```

Argument `axis` drops specified columns with NA values:
```Python
df.columns
df.dropna(axis='columns')
```

The argument `how` specifies which columns to drop. By default `how=any` will drop any 