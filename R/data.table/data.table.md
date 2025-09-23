The general form of `data.table` syntax is: `DT[i, j, by]`.
- **`i`** → rows (subset, reorder)
- **`j`** → columns (select, rename, compute)
- **`by`** → groups (do `j` separately within each group)
> Take DT (a data table), subset/reorder rows using `i`, then calculate `j`, grouped by `by`.

```R
library(data.table)

# create a small data.table
flights_small <- data.table(
  year    = c(2014, 2014, 2014, 2014, 2014, 2014),
  month   = c(1, 1, 6, 6, 6, 6),
  origin  = c("JFK", "JFK", "JFK", "LGA", "EWR", "JFK"),
  dest    = c("LAX", "SFO", "LAX", "ORD", "MIA", "ORD"),
  arr_delay = c(13, -5, 0, 20, -2, 8),
  dep_delay = c(14, -3, -6, 25, -1, 10)
)

flights
```

Result:
```
    year month origin   dest arr_delay dep_delay
   <num> <num> <char> <char>     <num>     <num>
1:  2026     1    JFK    LAX        13        14
2:  2026     1    JFK    SFO        -5        -3
3:  2026     6    JFK    LAX         0        -6
4:  2026     6    LGA    ORD        20        25
5:  2026     6    EWR    MIA        -2        -1
6:  2026     6    JFK    ORD         8        10
```

## Using `i` (rows):

- We can subset rows similar to a `data.frame`- except you don’t have to use `DT$` repetitively since columns within the frame of a `data.table` are seen as if they are _variables_.
- Works like row filtering in `data.frame`, but columns are seen as variables.

- Subset with conditions:
    `flights_small[month == 6]`
    → all June flights (rows 3–6).
- Subset with row numbers:
    `flights_small[1:2]`
    → the first two rows.
- Order rows:
    `flights_small[order(origin, -dest)]`
    → sorted by origin ↑, then dest ↓.
- `.N`, number, in row or column:
	Print the penultimate row: `flights_small[.N - 1]`

## Using `j` (columns)

- Return a **vector**: `flights_small[, arr_delay]`
- Return a **data.table**: `flights_small[, .(arr_delay)]`
- Multiple columns: `flights_small[, .(arr_delay, dep_delay)]`

We wrap the variables (column names) within `list()`, which ensures that a data.table is returned. In the case of a single column name, not wrapping with `list()` returns a vector instead. 

data.table also allows wrapping columns with `.()` instead of `list()`. It is an alias to `list()`; they both mean the same.

> As long as j-expression returns a list, each element of the list will be converted to a column in the resulting data.table.

`is.data.table(flights_small[, .(arr_delay)])`

- We can also _deselect_ columns using `-` or `!`. For example:
    ```
    # returns all columns except arr_delay and dep_delay
   flights[, !c("arr_delay", "dep_delay")]
    # or
  flights[, -c("arr_delay", "dep_delay")]
    ```
### Rename columns

Since `.()` is just an alias for `list()`, we can name columns as we would while creating a list
```R
flights_small[, .(delay_arr = arr_delay,
                  delay_dep = dep_delay)]
```

#### Computing in j
data.table’s j can handle more than just selecting columns - it can handle expressions, i.e., computing on columns. This shouldn’t be surprising, as columns can be referred to as if they are variables. Then we should be able to compute by calling functions on those variables. And that’s what precisely happens here.

Examples:
- Total number of early flights (arr+dep delay < 0): 
`flights_small[, sum((arr_delay + dep_delay) < 0)]`
- Average delay in June:
```R
flights_small[month == 6,                 # June month
              .(m_arr = mean(arr_delay),  # Rename and calculate mean
                m_dep = mean(dep_delay))] # Rename and calculate mean
```

- `.N` = number of rows (like `COUNT(*)` in SQL).
```R
flights_small[month == 6, .N]
# how many June flights? → 4
```

### .. prefix

```R
select_cols = c("arr_delay", "dep_delay")
flights[ , ..select_cols]
```
For those familiar with the Unix terminal, the .. prefix should be reminiscent of the “up-one-level” command, which is analogous to what’s happening here – the .. signals to data.table to look for the `select_cols` variable “up-one-level”, i.e., within the global environment in this case.

## by

### Grouping with `.N` (row count)

- Count trips by origin: `flights_small[, .N, by = origin]`
- `.N` = number of rows in each group.
- Count JFK flights in June: `flights_small[origin == "JFK" & month == 6, .N]`
### Grouping by multiple columns

- Count flights by origin–dest pair: `flights_small[, .N, by = .(origin, dest)]`
- Order of `by` variables is preserved in the output.
### Grouping with calculations
Average delays by origin:
```R
flights_small[, .(avg_arr = mean(arr_delay), 
                             avg_dep = mean(dep_delay)),
                             by = origin]
```
- Order of `by` variables is preserved in the output.
### Calculations in `by`

Example: **Count flights per quarter**
`flights_small[, .N, by = .(quarter = ceiling(month / 3))]`
**Explanation using mental model:**
**`by`** → creates a **temporary grouping variable** is created: `quarter = ceiling(month / 3)`
    
    - Conceptually:
        

`year month origin dest arr_delay dep_delay quarter 2014   1  JFK   LAX    13        14        1 2014   1  JFK   SFO    -5        -3        1 2014   6  JFK   LAX     0        -6        2 2014   6  LGA   ORD    20        25        2 2014   6  EWR   MIA    -2        -1        2 2014   6  JFK   ORD     8        10        2`

3. **`j`** → `.N` counts rows **per group**
    

**Result:**

   `quarter N 1:       1 2 2:       2 4`

---

## 2️⃣ **Calculations in both `by` and `j`**

Example: **Average delays per quarter, grouped by origin**

`flights_small[, .(   avg_arr = mean(arr_delay),   avg_dep = mean(dep_delay) ), by = .(quarter = ceiling(month / 3), origin)]`

**Step-by-step mental model:**

1. **`i`** → no filter; all rows included.
    
2. **`by`** → two temporary grouping variables are created:
    
    - `quarter = ceiling(month / 3)`
        
    - `origin` (already exists)
        

Conceptually:

`year month origin dest arr_delay dep_delay quarter 2014   1  JFK   LAX    13        14        1 2014   1  JFK   SFO    -5        -3        1 2014   6  JFK   LAX     0        -6        2 2014   6  LGA   ORD    20        25        2 2014   6  EWR   MIA    -2        -1        2 2014   6  JFK   ORD     8        10        2`

3. **`j`** → compute `mean(arr_delay)` and `mean(dep_delay)` **per group**
    

**Result:**

   `quarter origin avg_arr avg_dep 1:       1  JFK       4       6 2:       2  JFK       4       2 3:       2  LGA      20      25 4:       2  EWR      -2      -1`

---

### ✅ Notes for the mental model

- `i` → filter rows first
    
- `by` → create temporary grouping variables (can include calculations)
    
- `j` → perform computations **within each group**
    
- You can gradually increase complexity in your notes:
    
    1. `by` with calculations only, `j` simple
        
    2. Both `by` and `j` with calculations

Conceptually (it doesn't really happens this way but it's a good mental model):
- When you do `DT[, j, by = some_group]`, `data.table` **creates a temporary grouping variable** for the computation.
- It’s like a new column exists internally.





