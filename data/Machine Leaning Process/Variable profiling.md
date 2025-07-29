When  we talk about variables, we might also refer to them as metrics, KPIs, dimensions, or columns. rows, observations and records.
# Check for correct formatting

e.g. zip code as numeric, we won't aggregate (average, sum, etc.)

- Numeric:
	- Character?
	- String?
	- Categorical?
	- Discrete? Integer
	- Continuous? Float (how many decimals)
- String/Character:
	- Numeric?
	- Categorical?
- **Date**:
	- Numeric?
	- Well-formatted

# Empty values

If you can ask the owner (source, where the data was generated from) about the empty values, ask.

- Keep
	- Empty or zero if accurate and meaningful (i.e. no sales of a product on a specific period)
- Remove
	- If you have a large volume of data
	- **Before removing**: confirm that there is no pattern or bias to the missing values (i.e. all sales from a specific product category are missing)
- Impute
	- Substitute empty values if can accurately populate
	- If working with limited data use statistical methods
	- Check against non-impute data vs imputed to see if input generated bias


# Range calculations

