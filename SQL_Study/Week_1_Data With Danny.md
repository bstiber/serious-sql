# Week 1 notes

## Notes SELECT

Using  SELECT

```sql
SELECT
  column_name_1,
  column_name_2
FROM schema_name.table_name
```

✅ No comma after the last column in the SELECT list.

`SELECT` is what you use to choose what `Data` you want to `retrieve` from the `table.` The `specific` section of the table.

## Purpose
Specifies what columns or column you want to retrieve from a table.

## Important
SELECT doesn't decide where the data comes from -- that's FROM.

## Row filtering 
Is handled by using `WHERE`.

`FROM` is used to choose which table (and schema, if needed) the data will come from.


# EXAMPLE
You are in a grocery store, you want to `SELECT`(data) oranges `FROM`(location) the fruit stand, inside the store.

## Wildcard example
SELECT `*` is used to choose everything from the table. Not a specific item such as all `fruit` not just `oranges`.

```SQL
SELECT *
FROM schema_name.table_name;
```

### Analogy
SELECT = I want oranges, apples, bananas (Specific `columns`)
FROM = From the product section (table)
WHERE = Only if they are ripe (filter rows)

```SQL
SELECT name, age
FROM employees
WHERE department = 'Sales';
```

# Notes WHERE

WHERE using in SQL

`WHERE` is used for filtering the `FROM` 

## Purpose
to filter rows in a table based on a condition

## Example

```SQL
SELECT badge_number
FROM LA_County
WHERE department = 'fire_department';
```

## Analogy
SELECT = I want oranges (Specific columns)
FROM = From the produce section (table)
WHERE = Only if they are ripe (filter rows)

# LIMIT

### Purpose: 
To `limit` the number of lines displayed on the computer.

### Syntax: 
LIMIT 10 = means only show 10 lines of text.

### Example: 
```sql
SELECT *
FROM dvd_rentals.actor
LIMIT 10;
```

### Analogy: 
Only show 10 DVD rentals not the whole list of rentals.

### Trap: 

# NEXT TO EXPLAIN
`ORDER BY`
`category`
`desc` - Ascending & Descending

   Which category had the lowest total_sales value according to the sales_by_film_category table? What was the total_sales value?

## Category example
```sql
SELECT
  category,
  total_sales
FROM dvd_rentals.sales_by_film_category
ORDER BY total_sales
LIMIT 1;
```
# EXERCISES
### 1: What is the name of the category with the highest category_id in the dvd_rentals.category table?

```SQL
SELECT 
  name,
  category_id
FROM
  dvd_rentals.category
order by category_id DESC
limit 1; /*or remove the limit to see all 16 in descending order*/
```
### 2: For the films with the longest length, what is the title of the “R” rated film with the lowest replacement_cost in dvd_rentals.film table?

```SQL
SELECT 
  title, replacement_cost, length, rating
FROM dvd_rentals.film
WHERE rating = 'R'
ORDER BY length DESC, replacement_cost ASC
LIMIT 10;
```
### 3: Who was the manager of the store with the highest total_sales in the dvd_rentals.sales_by_store table?

```SQL
SELECT 
  store, 
  manager, 
  total_sales
FROM dvd_rentals.sales_by_store
ORDER BY total_sales DESC
Limit 10;
```
### 4: What is the postal_code of the city with the 5th highest city_id in the dvd_rentals.address table?

```SQL
SELECT 
  city_id,
  postal_code 
FROM dvd_rentals.address 
ORDER BY city_id DESC
LIMIT 10;
```
# Find the number of records in your dataset

## Using `COUNT`

How many rows are there in the film_list table?

```SQL
SELECT 
 COUNT(*) AS row_count 
FROM dvd_rentals.film_list;
```
### Column Aliases
AS `row_count` (above) just means the result column will show up labeled as “row_count” instead of whatever default name SQL would give it.*/

### Show Unique Column Values

What are the unique values for the rating column in the film table?

Using `DISTINCT`

```SQL
SELECT DISTINCT
 rating
FROM dvd_rentals.film_list;
```

`DISTINCT` makes SQL only show one of each thing, so you don’t get repeats in your results.

---------------
# Record Counts & Distinct Values

