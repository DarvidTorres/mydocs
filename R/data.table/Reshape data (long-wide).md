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
- **`variable.name`** → the column name that will contain the _names_ of the melted variables. By default, variable column is of type factor. Set `variable.factor` argument to FALSE if you’d like to return a character vector instead.
- **`value.name`** → the column name that will contain the _values_ of those variables.

```R
melt(
  flights_small,
  measure.vars = c("arr_delay", "dep_delay")
)
#     year month origin   dest  variable value
#    <num> <num> <char> <char>    <fctr> <num>
# 1:  2014     1    JFK    LAX arr_delay    13
# 2:  2014     1    JFK    SFO arr_delay    -5
# 3:  2014     6    JFK    LAX arr_delay     0
# 4:  2014     6    LGA    ORD arr_delay    20
# 5:  2014     6    EWR    MIA arr_delay    -2
# 6:  2014     6    JFK    ORD arr_delay     8
# 7:  2014     1    JFK    LAX dep_delay    14
# 8:  2014     1    JFK    SFO dep_delay    -3
# 9:  2014     6    JFK    LAX dep_delay    -6
#10:  2014     6    LGA    ORD dep_delay    25
#11:  2014     6    EWR    MIA dep_delay    -1
#12:  2014     6    JFK    ORD dep_delay    10
```
- By default, the molten columns are automatically named variable and value.

```R
melt(
  flights_small,
  measure.vars = c("arr_delay", "dep_delay"),
  variable.name = "delay_type",
  value.name = "delay_time"
)
```

# dcast (pivot columns)

**`dcast()`**: does the reverse — takes long data and spreads it back to wide. Think: “unstack rows into columns.”

