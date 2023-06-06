1. ```DATEADD (datepart , number , date ) ```
This function adds a number (a signed integer) to a datepart of an input date, and returns a modified date/time value. For example, you can use this function to find the date that is 7000 minutes from today: number = 7000, datepart = minute, date = today.
For datepart info and other information see:
https://learn.microsoft.com/en-us/sql/t-sql/functions/dateadd-transact-sql?view=sql-server-ver16 

Some Common dateparts:
year	yy, yyyy
quarter	qq, q
month	mm, m
dayofyear	dy, y
day	dd, d
week	wk, ww
weekday	dw, w
hour	hh
minute	mi, n
second	ss, s
millisecond	ms
microsecond	mcs
nanosecond	ns

Eg Qs : https://leetcode.com/problems/rising-temperature/solutions/3218996/91-with-inner-join-sql-server/?envType=study-plan-v2&envId=top-sql-50

