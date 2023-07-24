The CASE statement in SQL is a powerful and flexible way to perform conditional logic within your queries. It allows you to define conditions and return different values based on those conditions. The basic syntax of the CASE statement is as follows:

```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE default_result
END
```

Using CASE with an aggregate function to calculate bonus based on department:

```
SELECT
    department,
    AVG(age) AS average_age,
    CASE
        WHEN department = 'HR' THEN AVG(age) * 1.1
        WHEN department = 'IT' THEN AVG(age) * 1.15
        ELSE AVG(age)
    END AS bonus
FROM employees
GROUP BY department;
```
