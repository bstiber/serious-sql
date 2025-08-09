# Notes guideline

## Use the following format

### Purpose: 
Filters rows based on a condition  

### Syntax: 
SELECT cols FROM table WHERE condition; 

### Example: 
SELECT * FROM employees WHERE dept='Sales';  

### Analogy: 
Only if they are ripe (filter rows)  

### Trap: 
WHERE filters before aggregation; HAVING is after
   