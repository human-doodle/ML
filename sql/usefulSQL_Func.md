## 1. CAST() function in SQL and its usage in various scenarios:

Data Type Conversion: The primary purpose of the CAST() function is to convert data from one data type to another. It can be used to convert numeric types, string types, date and time types, etc.
Example: Convert a string representation of a number to an actual numeric data type.
```
SELECT
    '42' AS string_number,
    CAST('42' AS INT) AS integer_number;

```
Result:
```
string_number | integer_number
------------------------------
42           | 42
```
Preserving Precision: When converting data types with decimals, you may need to preserve the precision. For example, converting a FLOAT to DECIMAL or vice versa.
Example: Convert a FLOAT to DECIMAL with a specific precision and scale.
```
SELECT
    3.14159 AS float_value,
    CAST(3.14159 AS DECIMAL(5, 2)) AS decimal_value;
```
Result:
```
float_value | decimal_value
---------------------------
3.14159    |  3.14
```
Date and Time Operations: The CAST() function is handy when performing date and time operations, such as truncating timestamps to dates or converting date strings to actual date values.
Example: Convert a date string to a DATE data type.
```
SELECT
    '2023-07-23' AS string_date,
    CAST('2023-07-23' AS DATE) AS actual_date;
```
Result:
```
string_date  | actual_date
---------------------------
2023-07-23   | 2023-07-23
```
Alias for Readability: The CAST() function is often used to provide a more descriptive alias for a column, making the result set easier to read and understand.
Example: Convert a numeric value to a string and provide a meaningful alias.
```
SELECT
    42 AS age,
    CAST(42 AS VARCHAR(10)) AS age_string;
```
Result:
```
age | age_string
---------------
42  | 42
```
Handling NULL Values: The CAST() function can be useful for handling NULL values in certain expressions or when converting NULLs to specific data types.
Example: Convert NULL to a default value when converting to a numeric data type.
```
SELECT
    NULL AS null_value,
    COALESCE(CAST(NULL AS INT), 0) AS default_value;
```
Result:
```
null_value | default_value
--------------------------
(null)     | 0
```


## 2. FILTER (PostgreSQL)
  FILTER() function is a non-standard feature found in some database systems like PostgreSQL. It is an extension to aggregate functions introduced to enable more complex filtering of data within an aggregate function.

In PostgreSQL, the FILTER() function allows us to specify a condition to filter the rows included in an aggregate function's calculation. This is particularly useful when you want to perform an aggregate function only on a subset of rows that meet specific conditions.
```
aggregate_function(expression) FILTER (WHERE condition)
```
Example: Calculate the sum of order amounts for customer_id 101 using the FILTER() function in PostgreSQL.

```
SELECT
    customer_id,
    SUM(order_amount) FILTER (WHERE customer_id = 101) AS total_amount_for_customer_101
FROM orders
GROUP BY customer_id;
```
Result:

```
customer_id | total_amount_for_customer_101
-------------------------------------------
101         | 220.00
102         | 171.25
103         | 50.25
```

In T-SQL, we can achieve similar functionality using conditional aggregation or subqueries to filter data before performing aggregate functions.

1. Conditional Aggregation: With conditional aggregation, you can use the CASE statement within aggregate functions to specify conditions for including or excluding rows in the aggregation.
Example: Calculate the sum of order amounts for customer_id 101 using conditional aggregation in T-SQL.

```
SELECT
    customer_id,
    SUM(CASE WHEN customer_id = 101 THEN order_amount ELSE 0 END) AS total_amount_for_customer_101
FROM orders
GROUP BY customer_id;
```

2. Subqueries: Another approach is to use subqueries to filter the data before performing the aggregate function.
Example: Calculate the sum of order amounts for customer_id 101 using a subquery in T-SQL.

```
SELECT
    customer_id,
    SUM(order_amount) AS total_amount_for_customer_101
FROM (
    SELECT customer_id, order_amount
    FROM orders
    WHERE customer_id = 101
) AS filtered_orders
GROUP BY customer_id;
```

## DATE_PART (PosgreSQL)
In PostgreSQL, the DATE_PART() function is used to extract specific components or parts (such as year, month, day, etc.) from a date, timestamp, or interval value. It is a powerful function that allows you to retrieve individual elements from a date or time value for further analysis or formatting.

The basic syntax of the DATE_PART() function is as follows:
```
DATE_PART(unit, source)
```


unit: The unit or part that you want to extract, represented as a string. The valid units are:
```
'years' or 'year' or 'y'
'months' or 'month' or 'mon'
'days' or 'day' or 'd'
'hours' or 'hour' or 'h'
'minutes' or 'minute' or 'min'
'seconds' or 'second' or 'sec'
'milliseconds' or 'millisecond' or 'millisec' or 'ms'
'microseconds' or 'microsecond' or 'microsec' or 'us'
```
source: The date, timestamp, or interval value from which you want to extract the specified unit.

Extract the year from a date:
```
SELECT DATE_PART('YEAR', '2023-07-23') AS year;
```
Result: '2023'

Extract the month from a timestamp:
```
SELECT DATE_PART('MONTH', TIMESTAMP '2023-07-23 15:30:00') AS month;
```
Result: '7'

Extract the day from an interval:
```
SELECT DATE_PART('DAY', INTERVAL '5 days 12 hours') AS days;
```
Result: '5'

Extract the milliseconds from a timestamp:
```
SELECT DATE_PART('MILLISECOND', TIMESTAMP '2023-07-23 15:30:00.123456') AS milliseconds;
```
Result: '123'


