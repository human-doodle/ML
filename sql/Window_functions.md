# Window Functions:
Used when we want aggregate and non aggregatye values both.

Syntax:
```
function_name() OVER (PARTITION BY partition_expression ORDER BY sort_expression [window_frame_specification])
```
1. PARTITION BY: The PARTITION BY clause divides the result set into partitions or groups based on the specified column(s). The window function is then applied independently to each partition.
Example: Calculate the total sales for each product:
```
SELECT product_name, sale_date, sale_amount, SUM(sale_amount) OVER(PARTITIONBY product_name) AStotal_sales_per_product FROM sales;
```
2. ORDER BY: The ORDER BY clause determines the order in which the rows are considered for the window function within each partition.
Example: Calculate the running total of sales for each product sorted by sale date:
```
SELECT product_name, sale_date, sale_amount, SUM(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date) ASrunning_total FROMsales;
```
3. ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW: The ROWS BETWEEN clause defines the set of rows within the partition that the function operates on. The example below uses the ROWS BETWEEN clause to calculate the cumulative sum of sales for each product from the beginning to the current row.
Example: Calculate the cumulative sum of sales for each product:
```
SELECT product_name, sale_date, sale_amount, SUM(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date ROWSBETWEENUNBOUNDED PRECEDING ANDCURRENTROW) AScumulative_sales FROMsales;
```
4. ROWS BETWEEN n PRECEDING AND m FOLLOWING: The ROWS BETWEEN clause can also specify a range of rows relative to the current row. For example, ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING includes the current row and the rows immediately preceding and following it.
Example: Calculate the moving average of sales for each product over a window of 2 days:
```
SELECT product_name, sale_date, sale_amount, AVG(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date ROWSBETWEEN1PRECEDING AND1FOLLOWING) ASmoving_average FROMsales;
```
5. LEAD() and LAG(): The LEAD() and LAG() functions allow you to access data from the next or previous rows within the same partition.
Example: Calculate the difference in sales amount from the previous day for each product:
```
SELECTproduct_name, sale_date, sale_amount, sale_amount -LAG(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date) ASsales_difference_from_previous_day FROMsales;
```
6. FIRST_VALUE() and LAST_VALUE(): The FIRST_VALUE() and LAST_VALUE() functions retrieve the first and last values in a window of rows within each partition.
Example: Show the first and last sale amount for each product:
```
SELECTproduct_name, sale_date, sale_amount, FIRST_VALUE(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date) ASfirst_sale_amount, LAST_VALUE(sale_amount) OVER(PARTITIONBYproduct_name ORDERBYsale_date) ASlast_sale_amount FROMsales;
```
7.i RANK(): The RANK() function assigns a unique rank to each distinct row in the result set based on the specified ordering criteria. If two or more rows have the same values for the sort_expression, they receive the same rank, and the next rank is skipped. The following rank is determined by adding the number of tied rows to the current rank.
Example:
```
SELECT
    student_name,
    subject,
    score,
    RANK() OVER (PARTITION BY subject ORDER BY score DESC) AS rank
FROM exam_scores;
```
ii. DENSE_RANK(): The DENSE_RANK() function assigns a unique rank to each distinct row in the result set, similar to RANK(). However, if there are ties (rows with the same values for the sort_expression), all tied rows receive the same rank, and the next rank is not skipped. The following rank is determined without considering the number of tied rows.
Example:
```
SELECT
    student_name,
    subject,
    score,
    DENSE_RANK() OVER (PARTITION BY subject ORDER BY score DESC) AS dense_rank
FROM exam_scores;
```
iii. ROW_NUMBER(): The ROW_NUMBER() function assigns a unique sequential number to each row in the result set, starting from 1 for the first row. Unlike RANK() and DENSE_RANK(), ROW_NUMBER() does not consider ties. Each row receives a distinct number based on the order specified.
Example:
```
SELECT
    student_name,
    subject,
    score,
    ROW_NUMBER() OVER (PARTITION BY subject ORDER BY score DESC) AS row_number
FROM exam_scores;
```
Let's use the exam_scores table to demonstrate these different types of ranks:
```
student_id | student_name | subject  | score
---------------------------------------------
1          | Alice        | Math     | 85
2          | Bob          | Math     | 78
3          | Alice        | Science  | 92
4          | Bob          | Science  | 88
5          | Alice        | English  | 90
6          | Bob          | English  | 85
```

i. Result using RANK():
```
student_name | subject  | score | rank
---------------------------------------
Alice        | Science  | 92    | 1
Bob          | Science  | 88    | 2
Alice        | Math     | 85    | 3
Bob          | Math     | 78    | 4
Alice        | English  | 90    | 1
Bob          | English  | 85    | 2
```
ii. Result using DENSE_RANK():
```
student_name | subject  | score | dense_rank
--------------------------------------------
Alice        | Science  | 92    | 1
Bob          | Science  | 88    | 2
Alice        | Math     | 85    | 3
Bob          | Math     | 78    | 4
Alice        | English  | 90    | 1
Bob          | English  | 85    | 2
```
iii. Result using ROW_NUMBER():
```
student_name | subject  | score | row_number
--------------------------------------------
Alice        | Science  | 92    | 1
Bob          | Science  | 88    | 2
Alice        | Math     | 85    | 1
Bob          | Math     | 78    | 2
Alice        | English  | 90    | 1
Bob          | English  | 85    | 2
```
