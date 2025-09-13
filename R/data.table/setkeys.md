### `setkey` and `setkeyv` in **data.table**

In **data.table**, a *key* is like a rowname: it defines one or more columns that are used for fast row lookups, joins, and grouping.

`setkey()` and `setkeyv()` modify the input data.table by reference. They return the result invisibly.

#### What happens when you set a key

1. **Sorting the rows**
   * The table is sorted in ascending order by the key columns.
   * Example:
     ```r
     DT <- data.table(A = c(3,1,2), B = c("c","a","b"))
     DT
     setkey(DT, A)
     DT
     # Rows are now ordered by A: (1, 2, 3)
     ```

1. **Marking the column(s) as the key**
   * Internally, `data.table` records which columns are the key (rowname).
   * You can now look up rows directly:

     ```r
     DT[.(2)]      # returns the row where A == 2
     ```

#### One vs multiple columns

* If you key on **one column**, that column behaves like rownames in base R, but faster and more flexible.
* If you key on **multiple columns**, the key is an *ordered tuple*.

  * Example:
    ```r
    DT <- data.table(A = c(1,1,2,2), B = c("x","y","x","y"), val = 1:4)
    DT
    setkey(DT, A, B)
    DT
    DT[.(2, "x")]
    #    A B val
    # 1: 2 x   3
    ```
  * The lookup `(2,"x")` finds the row where both `A=2` and `B="x"`.

#### `setkey` vs `setkeyv`

* `setkey(DT, A, B)` → columns are given **unquoted**.
* `setkeyv(DT, c("A","B"))` → columns are given as a **character vector** (useful if column names are stored in a variable).

Both functions do the same thing; only the input style differs.

#### Behavior with missing matches

* If a key value does not exist, `data.table` still returns a row but with `NA`s in the other columns:

  ```r
  DT[.(5)]
  #    A    B
  # 1: 5 <NA>
  ```
* To drop non-matches completely, use `nomatch=0L`:

  ```r
  DT[.(5), nomatch=0L]
  # Empty data.table (0 rows)
  ```

#### Helper functions

- `key(<DT>)` returns the data.table's key if it exists; NULL if none exists.
- `haskey(<DT>)` returns TRUE/FALSE if the data.table has a key.