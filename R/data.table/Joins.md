### One-to-many join in `data.table`

The general form of a join is:

```r
x[i, on = "col", nomatch = ...]
```

- `x` = secondary table (left-side)
- `i` = primary table (inside `[ ]`), **all rows from `i` are preserved**. 
- `on` = column(s) to match by
- `nomatch` = controls what happens when no match is found
	- default is `NA` → unmatched rows in `i` are kept, with `NA` filled in from `x`
	- if set to `FALSE` → unmatched rows are dropped
	
In the standard `x[i]` join, all rows from i (the table in the brackets) are preserved, but only the matching rows from x are kept. This is known as a right join because it keeps everything from the table on the right side of the expression.

---

### Example tables

```r
library(data.table)

# Customers table (each customer appears once)
customers <- data.table(
  cust_id = c(1, 2, 3),
  name = c("Alice", "Bob", "Carol")
)
customers
#    cust_id   name
#      <num> <char>
# 1:       1  Alice
# 2:       2    Bob
# 3:       3  Carol

# Orders table (customers can appear many times if they place multiple orders)
orders <- data.table(
  order_id = c(101, 102, 103, 104, 105),
  cust_id  = c(1,   1,   2,   3,   3),
  product  = c("Book", "Pen", "Bag", "Shoes", "Hat")
)
orders
#    order_id cust_id product
#       <num>   <num>  <char>
# 1:      101       1    Book
# 2:      102       1     Pen
# 3:      103       2     Bag
# 4:      104       3   Shoes
# 5:      105       3     Hat
```

### Case 1: Every customer has at least one order

```r
orders[customers, on = "cust_id"]
```

Result:
```
   order_id cust_id product   name
      <num>   <num>  <char> <char>
1:      101       1    Book  Alice
2:      102       1     Pen  Alice
3:      103       2     Bag    Bob
4:      104       3   Shoes  Carol
5:      105       3     Hat  Carol
```

- All **customers** (`i`) are present.
- If a customer has multiple orders, their row is repeated.
- This is a classic **one-to-many join**.

### Case 2: Some customers have no orders

Suppose we didn't have Bob’s order:

```r
orders <- data.table(
  order_id = c(101, 102, 104, 105),
  cust_id  = c(1,   1,   3,   3),
  product  = c("Book", "Pen", "Shoes", "Hat")
)
orders
#    order_id cust_id product
#       <num>   <num>  <char>
# 1:      101       1    Book
# 2:      102       1     Pen
# 3:      104       3   Shoes
# 4:      105       3     Hat

orders[customers, on = "cust_id"]
```

Result:

```
   order_id cust_id product   name
      <num>   <num>  <char> <char>
1:      101       1    Book  Alice
2:      102       1     Pen  Alice
3:       NA       2    <NA>    Bob
4:      104       3   Shoes  Carol
5:      105       3     Hat  Carol
```

- Bob (`cust_id = 2`) is **still present**, because all rows from `customers` must be kept.
- But since there is no matching row in `orders`, the new columns (`order_id`, `product`) are filled with `NA`.
### Dropping unmatched rows

`orders[customers, on = "cust_id", nomatch = FALSE]`

Result:
```
   order_id cust_id product   name
      <num>   <num>  <char> <char>
1:      101       1    Book  Alice
2:      102       1     Pen  Alice
3:      104       3   Shoes  Carol
4:      105       3     Hat  Carol
```

---
### Key rule to remember

👉 In `x[i, on=..., nomatch=...]`:
- **Rows from `i` (inside `[ ]`) are preserved** by default, even if unmatched (with `NA`).
- Use `nomatch = FALSE` to exclude unmatched rows instead.

Absolutely — let’s put together a **comprehensive note** you can keep for reference on `data.table` joins, `.EACHI`, and `on` usage. I’ll organize it step by step with examples and key takeaways.

---

# **Data.table Joins, `on`, and `.EACHI` — Notes**

### 1. **Basic x[i] join structure**

```r
x[i, j, by, on]
```

- **x** → primary table (before `[ ]`)
- **i** → secondary table (inside `[ ]`)
- **on** → specifies which columns to match (`x` columns = `i` columns)
- **j** → expressions to compute or columns to return
- **by** → groups for aggregation

---

### 2. **The `on` argument**

`on = .(x_col = i_col)`
- Left of = → column in x (the table before [ ])
- Right of = → column in i (the table inside [ ])
**Syntax:**

```r
x[i, on = .(x_col = i_col)]
```

- **Left-hand side (`x_col`)** → column in `x`
- **Right-hand side (`i_col`)** → column in `i`

---
### 3. **`by = .EACHI`**

- **Definition:** Run `j` **once for each row of `i`** (the lookup table).
- Groups are formed **per row in `i`**, not per unique key.

**Example with toy data:**

```r
Products_Toy <- data.table(
  id = c(1, 2),
  name = c("banana", "carrots"),
  price = c(0.5, 1.0)
)

ProductReceived_Toy <- data.table(
  product_id = c(1, 1, 2),
  count = c(10, 20, 5)
)

ProductReceived_Toy[
  Products_Toy,
  on = c(product_id = "id"),
  by = .EACHI,
  j = .(total_value_received = sum(price * count))
]
```

**Output:**
```
   id  total_value_received
1:  1                   15
2:  2                    5
```
**Explanation:**
- Row 1 of `Products_Toy` → `id = 1` → matches rows with `product_id = 1` → sum `price * count`.
- Row 2 of `Products_Toy` → `id = 2` → matches `product_id = 2` → sum `price * count`.

---
### 4. **Difference vs `by = "id"`**

- `.EACHI` → group **per row of `i`**, keeps duplicates separate.
- `by = "id"` → group **by unique values** of a column in the joined result.
**Example with duplicate rows in `i`:**
```r
Products_Toy <- data.table(
  id = c(1, 1, 2),
  name = c("banana", "banana_alt", "carrots"),
  price = c(0.5, 0.6, 1.0)
)

ProductReceived_Toy[
  Products_Toy,
  on = c(product_id = "id"),
  by = .EACHI,
  j = .(total_value_received = sum(price * count))
]
```

**Output (`.EACHI`):**
```
   id total_value_received
1:  1                   15   # 0.5*(10+20)
2:  1                   18   # 0.6*(10+20)
3:  2                    5
```

**Output (`by = "id"` after join):**
```
   id total_value_received
1:  1                   33   # 15 + 18
2:  2                    5
```

> **Key difference:** `.EACHI` preserves the row-level grouping of `i`; `by = "id"` collapses duplicates.

---
### 5. **Why use `.EACHI`**

- When you want **row-level aggregation** relative to the lookup table (`i`).
- Saves you a separate step: join first, then group.
- Often used for “per-key aggregations” while preserving the structure of `i`.

---
### 6. **Alternative two-step approach**

```r
ProductReceived[
  Products_Toy,
  on = c(product_id = "id")
][, .(total_value_received = sum(price * count)), by = "product_id"]
```
- Join first, then group by the join key.
- Equivalent to `.EACHI` **if `i` has unique join keys**.

---
# **Multi-Column Joins in data.table**

```R
Products = rowwiseDT(
  id = ,
  name = ,
  price = ,
  unit = ,
  type = ,
  1L,
  "banana",
  0.63,
  "unit",
  "natural",
  2L,
  "carrots",
  0.89,
  "lb",
  "natural",
  3L,
  "popcorn",
  2.99,
  "unit",
  "processed",
  4L,
  "soda",
  1.49,
  "ounce",
  "processed",
  NA,
  "toothpaste",
  2.99,
  "unit",
  "processed"
)

NewTax = data.table(
  unit = c("unit", "ounce"),
  type = "processed",
  tax_prop = c(0.65, 0.20)
)
```

### 1. **Purpose**

- Sometimes you need to join tables based on **more than one column**, e.g., a combination of `unit` and `type`.
- This is common when **the key is composite** (e.g., tax rates depend on both `unit` and `type`).

---
### 2. **Syntax**

```r
x[i, on = c("col1", "col2", ...)]
```

- Each column name in the character vector `on` is used to match between `x` and `i`.
- By default, `data.table` matches columns with the **same name** in both tables.
- If names differ, use `on = .(x_col1 = i_col1, x_col2 = i_col2, ...)` or `c(x_col1 = "i_col1")`.

---
### 3. **Example: Adding tax_prop to Products**

```r
NewTax[Products, on = c("unit", "type")]
```

**Explanation of arguments:**

- `x = NewTax` → table providing `tax_prop`
- `i = Products` → table we want to update / add info to
- `on = c("unit", "type")` → match rows where both `unit` **and** `type` are equal

**Result:**
```
      unit      type tax_prop    id       name price
1:   unit   natural       NA     1     banana  0.63
2:     lb   natural       NA     2    carrots  0.89
3:   unit processed     0.65     3    popcorn  2.99
4:  ounce processed     0.20     4       soda  1.49
5:   unit processed     0.65    NA toothpaste  2.99
```

---

### 4. **Notes on the output**

- `tax_prop` is added from `NewTax` for matching rows.
    
- Rows in `Products` with no match in `NewTax` (e.g., `unit = "unit", type = "natural"`) get `NA`.
    
- Rows in `NewTax` that don’t match any row in `Products` are **ignored** because this is a **right join** (driven by `i`).
    

---

### 5. **Key points / tips**

1. Multi-column joins work like single-column joins — just provide all relevant columns in `on`.
    
2. Column names must match by default; otherwise, use `.(x_col = i_col)` notation.
    
3. The order of columns in `on` matters if your tables have multiple rows per key — it defines the matching logic.
    
4. You can combine with `.EACHI` and `j` for **aggregations per group of keys**.
    

---

✅ **Summary:**

- Multi-column joins allow precise matching using composite keys.
    
- Syntax is simple: `on = c("col1", "col2", ...)` or `on = .(x_col = i_col, ...)`.
    
- Useful for cases like adding tax rates, price adjustments, or any lookup table that depends on several attributes.
    

---

If you want, I can also add a **diagram showing which columns are matched in `x` vs `i` for multi-column joins** — it makes it really easy to remember for notes.

Do you want me to do that?