What are your risk areas? Identify and describe them.

1.Inconsistencies in the Data entry:
Different formats for the same type of data can lead to inaccuracies in the analysis, for example, the date format might be formatted differently in other tables

2. Missing Data:
Empty fields can give us inaccurant results, especially if they're needed in a particular column

3. Duplicate Entries: 
Sometimes the same record might be entered more than once, leading to inflated and a more serious matter, misleading results.

4.Mismatched Data Types:
For example, if a numeric field being entered as a text or string can prevent mathematical operations on that column

5. Foreign Key Mismatches: 
If tables are related, we're going to need a foreign key to recieve information on that table. The absence of corresponding records in a linked table can cause issues, in that case making your own foreign key maybe best to link the tables.

6.Outliers: 
Extremely high or low values that do not fit the pattern of the rest of your data can distort aggregate measures like mean or standard deviation.

QA Process:
Describe your QA process and include the SQL queries used to execute it.

Cheking for Missing Data: Using the COUNT(*) and the WHERE function, we can get a count of NULL values in that specific column

```sql
SELECT COUNT(*)
FROM products
WHERE orderedquantity IS NULL
```

Checking for Dublicate Entries: Using the GROUP BY and HAVING aggregations, we can find if the primary key has dublicate entries.

```sql
SELECT productsku, COUNT(*)
FROM products
GROUP BY productsku
HAVING COUNT(*) > 1;
```

Check for Data Tyoes: Just by looking at the headers, you can see below them what type of data it is (ex. VARCHAR, INT, or NUMERICAL).

```SQL
SELECT *
FROM products
```

Verify Foreign Key Relations: Using the JOIN functions to confirm relations with the foreign key.

```SQL
select *
from products 
left join sales_report using (productsku)
```






