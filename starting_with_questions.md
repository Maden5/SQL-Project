Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: 

Top Cities:

```SQL
SELECT DISTINCT city, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE city <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY city
ORDER BY SUM(totaltransactionrevenue) DESC
LIMIT 5;
```


```SQL
SELECT DISTINCT country, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE country <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY country
ORDER BY SUM(totaltransactionrevenue) DESC
LIMIT 5;
```



Answer: 
The top cities with the highest transaction revenue are San Francisco, Sunnyvale, Atlanta, Palo Alto, and Tel Aviv-Yafo. The countries with the highest transaction revenue are United States, Israel, Australia, Canada, and Switzerland.




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







