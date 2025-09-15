The general form of `data.table` syntax is: `DT[i, j, by]`.
- **`i`** → rows (subset, reorder)
- **`j`** → columns (select, rename, compute)
- **`by`** → groups (summarize within groups)

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

### Using `i` (rows):

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
### Using `j` (columns)

- Return a **vector**: `DT[, arr_delay]`
- Return a **data.table**: `DT[, .(arr_delay)]`
- Multiple columns: `DT[, .(arr_delay, dep_delay)]`
- Rename columns:


As long as `j` returns a `list`, each element of the list will become a column in the resulting `data.table`.