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
# melt

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
melted_data <- melt(
  flights_small,
  measure.vars = c("arr_delay", "dep_delay"),
  variable.name = "delay_type", # Assing column name
  value.name = "delay_time"     # Assign column name
)
melted_data
#     year month origin   dest delay_type delay_time
#    <num> <num> <char> <char>     <fctr>      <num>
# 1:  2014     1    JFK    LAX  arr_delay         13
# 2:  2014     1    JFK    SFO  arr_delay         -5
# 3:  2014     6    JFK    LAX  arr_delay          0
# 4:  2014     6    LGA    ORD  arr_delay         20
# 5:  2014     6    EWR    MIA  arr_delay         -2
# 6:  2014     6    JFK    ORD  arr_delay          8
# 7:  2014     1    JFK    LAX  dep_delay         14
# 8:  2014     1    JFK    SFO  dep_delay         -3
# 9:  2014     6    JFK    LAX  dep_delay         -6
#10:  2014     6    LGA    ORD  dep_delay         25
#11:  2014     6    EWR    MIA  dep_delay         -1
#12:  2014     6    JFK    ORD  dep_delay         10
```
# dcast

**`dcast()`**: does the reverse — takes long data and spreads it back to wide. Think: “unstack rows into columns.”

General form:
```R
dcast(
  data,
  formula,
  value.var,
  fun.aggregate
)
```

- **`data`** → your long-format data (usually the result of `melt()`).
- **`formula`** → the core instruction:
    - LHS (left-hand side): the identifiers you want as rows.
    - RHS (right-hand side): the identifiers you want as columns.  
        Example: `year + month + origin + dest ~ delay_type` means rows are grouped by year+month+origin+dest, and columns spread out by `delay_type`.
- **`value.var`** → which column contains the values to fill into the table (often the one you created with `value.name` in `melt()`).
- **`fun.aggregate`** → optional function for when multiple values land in the same cell (like `mean`, `sum`, `length`). If you don’t supply it, but multiple values exist, `dcast()` will complain.
- If each cell is guaranteed to hold just **one value**, no `fun.aggregate` is needed.
- If multiple rows could collapse into the same cell, you _must_ tell `dcast()` how to combine them using `fun.aggregate`.

```R
dcast(
  melted_data,
  year + month + origin + dest ~ delay_type,
  value.var = "delay_time"
)
```
- **Left-hand side (before `~`)** = the **row identifiers** you want to keep as rows.  
    → here: `year + month + origin + dest`
- **Right-hand side (after `~`)** = what you want to become **new columns**.  
    → here: `delay_type` (which has 2 levels: `arr_delay`, `dep_delay`)
- **value.var** = which column has the numbers to fill those new cells.  
    → here: `delay_time`
### What happens

1. Look at one row in your melted data:
    `2014 1 JFK LAX arr_delay 13`
    Another row says:
    `2014 1 JFK LAX dep_delay 14`
    They have the **same identifiers** (year, month, origin, dest), but different `delay_type`.
2. `dcast()` will take those two rows and **spread them into columns**:
```R
year month origin dest arr_delay dep_delay
2014     1   JFK   LAX        13        14
```
3. Doing this for all flights gives you back your original wide format.
### Use `"..."` in the formula

In **data.table**, `dcast()` lets you say:
```R
dcast(
  melted_data,
  ... ~ delay_type,
  value.var = "delay_time"
)
```
Here, `"..."` means **all the remaining columns except the one(s) on the right-hand side**.  
So in the example, `...` expands to `year + month + origin + dest`.
### fun.aggregate

The **`fun.aggregate`** argument tells `dcast()` what to do if more than one row ends up in the same “cell.”
```R
dt <- data.table(
  year = c(2014, 2014, 2014),
  month = c(1),
  origin = c("JFK"),
  dest = c("LAX"),
  delay_type = c("arr_delay", "arr_delay", "dep_delay"),
  delay_time = c(13, 20, 14)
)
dt
#    year month origin   dest delay_type delay_time
#   <num> <num> <char> <char>     <char>      <num>
#1:  2014     1    JFK    LAX  arr_delay         13 # delay_type = arr_delay 
#2:  2014     1    JFK    LAX  arr_delay         20 # delay_type = arr_delay
#3:  2014     1    JFK    LAX  dep_delay         14
```
Notice:
- Both row 1 and row 2 are **arr_delay** for the same identifiers.
- Row 3 is `dep_delay` for the same identifiers.
### Step 2: Try `dcast()` **without** `fun.aggregate`

```R
dcast(
  dt,
  ... ~ delay_type,
  value.var = "delay_time"
)
```
- This will **error** because there are _two values_ for `arr_delay` (13 and 20), and `dcast` doesn’t know which to pick.
- Default aggregation = length (with a warning).
### Step 3: Try `dcast()` **with** `fun.aggregate = mean`

```R
dcast(
  dt,
  ... ~ delay_type,
  value.var = "delay_time",
  fun.aggregate = mean
)
```
- The two arrival delays (13 and 20) are averaged into 16.5.
### Step 4: Try `fun.aggregate = sum`
```R
dcast(
  dt,
  ... ~ delay_type,
  value.var = "delay_time",
  fun.aggregate = sum
)
```