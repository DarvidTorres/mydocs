The general form of `data.table` syntax is: `DT[i, j, by]`.
- **`i`** → rows (subset, reorder)
- **`j`** → columns (select, compute, name)
- **`by`** → groups (summarize within groups)

#### Using `i` (rows):

- We can subset rows similar to a `data.frame`- except you don’t have to use `DT$` repetitively since columns within the frame of a `data.table` are seen as if they are _variables_.
- Works like row filtering in `data.frame`, but columns are seen as variables.
- Examples:
    - Condition: `DT[origin == "JFK" & month == 6L]`
    - Row numbers: `DT[1:2]`
    - Ordering: `DT[order(origin, -dest)]`
👉 No need to write `DT$origin` — just `origin`.

```R
library(data.table)

# Create example data.table
DT <- data.table(
  ID = c("a", "b", "a", "b", "c", "c"),
  Category = c("X", "X", "Y", "Y", "X", "Y"),
  Value1 = c(10, 15, 10, 20, 15, 25),
  Value2 = c(100, 200, 150, 120, 180, 130)
)

DT
```



As long as `j` returns a `list`, each element of the list will become a column in the resulting `data.table`.