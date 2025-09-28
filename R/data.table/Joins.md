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
