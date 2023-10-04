What issues will you address by cleaning the data?

1. Date Column: The dates came back as 'YYYY-MM-DD' in the SQL column, which saved me time on changing the format, but the rows are not according to the date.

2. Empty Columns: While observin the columns, some came back blank. These columns don't add value and can be removed for clarity and to optomized storage. I noticed 4 empty columns in the all_sesions file and also 1 empty column in the analytics file.

3. Unit Cost/Price/Revenue Adjustment: The data stored is stored as 1/100 000 of a cent, so dviding the price by 1 000 000 or multiplying it by 0.000001 would get you the dollar amount. This issue was specifically on columns totaltransactionrevenue, productprice, productrevenue, and transactionrevenue in the all_sessions table. For the analytics table, only unit_price and revenue came up.

4. Time Format: The time format in all_sessions was in seconds, this column should be in a regular SQL format such as 'HH24:MI:SS'.

5. Duplicate Entries: Test each primary keys for dublicate entries.

6. Missing Data: Missing data would cause mathematical problems on important table such as products.

Queries:
Below, provide the SQL queries you used to clean your data.


1. Data Column: When creating table, have the date column database as DATE

```SQL
CREATE TABLE all_sessions
    DATE DATE
```

2. Empty Columns:

```SQL
SELECT productrevenue
FROM all_sessions
WHERE productrevenue IS NOT NULL;
```

This helped me find any values in an empty column.
If the column was found to be completely empty, the column was then removed in a duplicate table.

```SQL
ALTER TABLE all_sessions2 DROP COLUMN productrevenue
```

3. Unit Cost/Price/Revenue Adjustment:

```SQL
UPDATE analytics2
SET unit_price = unit_price / 1000000;
```

4. Time Format in the Duplicate Table:

```SQL
UPDATE all_sessions2
SET time = TO_CHAR(TO_TIMESTAMP(time::integer), 'HH24:MI:SS');
```

5. Dublicate Entries: 

```SQL
SELECT productSKU, COUNT(*) 
FROM products 
GROUP BY productSKU 
HAVING COUNT(*) > 1;
```

6. Missing Data:

```SQL
SELECT * 
FROM sales_by_sku 
WHERE productSKU IS NULL OR total_ordered IS NULL;
```
