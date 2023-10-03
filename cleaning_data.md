What issues will you address by cleaning the data?

1. Date Column: The dates came back as 'YYYY-MM-DD' in the SQL column, which saved me time on changing the format, but the rows are not according to the date. The dates are all over the place, you have January next to July.

2. Empty Columns: While observin the columns, some came back blank. These columns don't add value and can be removed for clarity and to optomized storage. I noticed 4 empty columns in the all_sesions file and also 1 empty column in the analytics file.

3. Unit Cost/Price/Revenue Adjustment: The data stored is stored as 1/100 000 of a cent, so dviding the price by 1 000 000 or multiplying it by 0.000001 would get you the dollar amount. This issue was specifically on columns totaltransactionrevenue, productprice, productrevenue, and transactionrevenue in the all_sessions table. For the analytics table, only unit_price and revenue came up.

4. Time Format: The time format in all_sessions was in seconds, this column should be in a regular SQL format such as 'HH24:MI:SS'.




Queries:
Below, provide the SQL queries you used to clean your data.


