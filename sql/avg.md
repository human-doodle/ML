AVG is an SQL aggregate function that calcukates the avverage of the selected group of values. 
There are limitaions that need to be taken care of:
1. It can only be used on numerical columns.
2. IT IGNORES NULL COMPLETELY.

So the two queries below will produce the same result:

```
SELECT AVG(column_name)
FROM table_name
WHERE column_name IS NOT NULL;
```

```
SELECT AVG(column_name)
FROM table_name;
```
(Considering column_name has one or more nul values.)

There will be some cases when we'd want to treat null values as 0. Using AVG directly without converting NULL to 0 will give unexpected results.
