## Basic Left Join with Assignment

```R
# Setup
customers <- data.table(cust_id = 1:5, name = c("Alice", "Bob", "Carol", "Dan", "Eve"))
purchases <- data.table(cust_id = c(2, 4, 6), amount = c(100, 200, 300))

customers; purchases
```
Result:
```
   cust_id   name
     <int> <char>
1:       1  Alice
2:       2    Bob
3:       3  Carol
4:       4    Dan
5:       5    Eve
   cust_id amount
     <num>  <num>
1:       2    100
2:       4    200
3:       6    300
```

```R
# Left join - add purchase amount to customers
customers[purchases, purchase_amt := i.amount, on = .(cust_id)]

customers
```
Result:
```
   cust_id   name purchase_amt
     <int> <char>        <num>
1:       1  Alice           NA
2:       2    Bob          100
3:       3  Carol           NA
4:       4    Dan          200
5:       5    Eve           NA
```

### Different Column Names
```R
sales <- data.table(soldto = c(100, 200, 300), revenue = c(1000, 2000, 3000))
customers <- data.table(customer_num = c(200, 400), segment = c("A", "B"))

sales; customers
```
Result:
```
   soldto revenue
    <num>   <num>
1:    100    1000
2:    200    2000
3:    300    3000
   customer_num segment
          <num>  <char>
1:          200       A
2:          400       B
```
Join when column names differ
```R
sales[customers, segment := i.segment, on = .(soldto = customer_num)]

sales
```
Result:
```
   soldto revenue segment
    <num>   <num>  <char>
1:    100    1000    <NA>
2:    200    2000       A
3:    300    3000    <NA>
```

### Multiple Columns from Join

```R
customers <- data.table(cust_id = 1:3)
details <- data.table(cust_id = 2:4, age = c(25, 30, 35), city = c("NYC", "LA", "SF"))

customers; details
```
Result:
```
   cust_id
     <int>
1:       1
2:       2
3:       3
   cust_id   age   city
     <int> <num> <char>
1:       2    25    NYC
2:       3    30     LA
3:       4    35     SF
```

```R
customers[details, `:=`(age = i.age, city = i.city), on = .(cust_id)]
# OR
customers[details, c("age", "city") := .(i.age, i.city), on = .(cust_id)]
```
Result:
```
   cust_id   age   city
     <int> <num> <char>
1:       1    NA   <NA>
2:       2    25    NYC
3:       3    30     LA
```

### Computed Values During Join
```R
orders <- data.table(order_id = 1:4, quantity = c(10, 20, 30, 40))
prices <- data.table(order_id = c(2, 3, 5), unit_price = c(5, 10, 15))

orders; prices
```
Result:
```
   order_id quantity
      <int>    <num>
1:        1       10
2:        2       20
3:        3       30
4:        4       40
   order_id unit_price
      <num>      <num>
1:        2          5
2:        3         10
3:        5         15
```
Calculate total during join
```R
orders[prices, total := quantity * i.unit_price, on = .(order_id)]
orders
```
Result:
```
   order_id quantity total
      <int>    <num> <num>
1:        1       10    NA
2:        2       20   100
3:        3       30   300
4:        4       40    NA
```

## Important Notes

### 1. **Modification by Reference**
```r
# := modifies the original table
DT[lookup, col := i.val, on = .(id)]
# DT is changed, no need to reassign

# If you want to keep original, copy first
DT_new <- copy(DT)
DT_new[lookup, col := i.val, on = .(id)]
```

### 2. **NA for Non-Matches**
```r
# Unmatched rows automatically get NA
DT[lookup, new_col := i.value, on = .(id)]
# Rows with no match will have NA in new_col
```

### 3. **Right Table Rows Not in Left Are Ignored**
```r
left <- data.table(id = 1:3)
right <- data.table(id = 2:5, val = c(100, 200, 300, 400))

left[right, new_val := i.val, on = .(id)]
# Only id 2 and 3 matched
# id 4 and 5 from 'right' are NOT added to 'left'
```

### 4. **Multiple Matches**
```r
# If lookup has multiple rows with same key
orders <- data.table(order_id = c(1, 1, 2), item = c("A", "B", "C"))
customers <- data.table(order_id = 1:2, cust = c("Alice", "Bob"))

orders[customers, customer := i.cust, on = .(order_id)]
# Both rows with order_id=1 get customer="Alice"
```

---

## Common Patterns

### Pattern 1: Fill Missing Values from Lookup
```r
# Fill NAs in main table from lookup
DT[is.na(column), column := lookup[.SD, value, on = .(id)]]
```

### Pattern 2: Conditional Assignment During Join
```r
DT[lookup, new_col := iff(condition, i.value1, i.value2), on = .(id)]
```

### Pattern 3: Join and Aggregate
```r
# Add count of matches
DT[lookup[, .N, by = id], count := i.N, on = .(id)]
```

### Pattern 4: Chain Multiple Joins
```r
DT[lookup1, col1 := i.val1, on = .(id)][
  lookup2, col2 := i.val2, on = .(id)][
  lookup3, col3 := i.val3, on = .(id)]
```

---

## Your Original Example Explained

```r
result[tot_attys, attorney_count_tot := i.attorney_count, on = .(soldtocustno = customer_number)]
```

**Step-by-step:**
1. Take `result` table (36,844 rows)
2. For each row, look up `result$soldtocustno` in `tot_attys$customer_number`
3. If match found: copy `tot_attys$attorney_count` value
4. If no match: put `NA`
5. Store result in new column `attorney_count_tot`
6. Keep all 36,844 rows from `result`
7. Modify `result` in place (no copy made)

---

This should serve as a comprehensive reference for data.table join syntax with assignment!