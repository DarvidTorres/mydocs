### 🔍 **`separate_wider_*` functions**

- **Purpose:** Split a single column into **multiple wider columns**.
- You end up with **more columns** (data is spread wider).
- Two main variants:
    - `separate_wider_delim()` → split by a delimiter (like `-`, `,`, `/`)
    - `separate_wider_position()` → split by character positions
- Typical use: Breaking a `YYYY-MM-DD` date string into `year`, `month`, `day` columns.
Example:
```r
library(tidyr)
df <- tibble(date = c("2025-08-27", "2024-12-05"))

df |> 
  separate_wider_delim(date, delim = "-", 
                       names = c("year", "month", "day"))
```

**Result:**

|year|month|day|
|---|---|---|
|2025|08|27|
|2024|12|05|

---

### 🔍 **`separate_longer_*` functions**

- **Purpose:** Split a single column into **multiple longer rows**.
    
- You end up with **more rows** (data is stacked longer).
    
- Two main variants:
    
    - `separate_longer_delim()` → split by a delimiter into multiple rows
        
    - `separate_longer_position()` → split by fixed character positions into rows
        
- Typical use: Splitting a comma-separated list into multiple observations.
    

Example:

```r
df2 <- tibble(id = 1:2, pets = c("dog,cat", "fish,bird"))

df2 |> 
  separate_longer_delim(pets, delim = ",")
```

**Result:**

|id|pets|
|---|---|
|1|dog|
|1|cat|
|2|fish|
|2|bird|

---

### TL;DR

|Function Family|What It Does|Shape Change|
|---|---|---|
|`separate_wider_*()`|Split into **more columns** (wider data)|Columns increase|
|`separate_longer_*()`|Split into **more rows** (longer data)|Rows increase|

---

For your `intake_date`, you’d want `**separate_wider_delim()`** because you’re splitting one date column into separate **year** and **month** columns.

---

Would you like me to show how to **do the same thing with `separate_longer_delim()`** just so you see the contrast?