##### _shallow_ vs _deep_ copy

A _shallow_ copy is just a copy of the vector of column pointers (corresponding to the columns in a _data.frame_ or _data.table_). The actual data is not physically copied in memory.

A _deep_ copy on the other hand copies the entire data to another location in memory.

When subsetting a _data.table_ using `i` (e.g., `DT[1:10]`), a _deep_ copy is made. However, when `i` is not provided or equals `TRUE`, a _shallow_ copy is made.
# :=

`:=` modifies the input object by reference.
The `:=` operator updates _data.table_ columns _in-place_ (by reference).

```R
DT = data.table(x = 1L, y = 2L)
DT_n = names(DT)
DT_n
# [1] "x" "y"

## add a new column by reference
DT[, z := 3L]

## DT_n also gets updated
DT_n
# [1] "x" "y" "z"

## use `copy()`
DT_n = copy(names(DT))
DT[, w := 4L]

## DT_n doesn't get updated
DT_n
# [1] "x" "y" "z"
```

# copy

The `copy()` function deep copies the input object and therefore any subsequent update by reference operations performed on the copied object will not affect the original object.

