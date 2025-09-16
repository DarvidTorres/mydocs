```R
flights_small <- data.table(
  year = c(2014, 2014, 2014, 2014, 2014, 2014),
  month = c(1, 1, 6, 6, 6, 6),
  origin = c("JFK", "JFK", "JFK", "LGA", "EWR", "JFK"),
  dest = c("LAX", "SFO", "LAX", "ORD", "MIA", "ORD"),
  arr_delay = c(13, -5, 0, 20, -2, 8),
  dep_delay = c(14, -3, -6, 25, -1, 10)
)
```
# melt (unpivot columns)

**`melt()`**: takes **wide data** (many columns) and reshapes it into **long form** (fewer columns, more rows). Think: “stack columns into rows.”

General form:

```R
melt(
  <data>,
  id.vars,
  measure.vars,
  variable.name = "variable",
  value.name = "value"
)
```

- **`data`** → your data.table (e.g. `flights_small`).
- **`id.vars`** →  “what stays fixed”. If missing, all non-measure columns will be assigned to it.
- **`measure.vars`** → the columns you want to reshape. These become values in a single column.  We can also specify column _positions_ instead of _names_.
- **`variable.name`** → the column name that will contain the _names_ of the melted variables. By default, variable column is of type factor. Set variable.factor argument to FALSE if you’d like to return a character vector instead.
- **`value.name`** → the column name that will contain the _values_ of those variables.
- By default, the molten columns are automatically named variable and value.

```R
melted <- melt(
  flights_small,
  id.vars = c("year", "month", "origin", "dest"),
  measure.vars = c("arr_delay", "dep_delay"),
  variable.name = "delay_type",
  value.name = "delay"
)
```


# dcast (pivot columns)

**`dcast()`**: does the reverse — takes long data and spreads it back to wide. Think: “unstack rows into columns.”

