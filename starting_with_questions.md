Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: 

**Top Cities:**

```SQL
SELECT DISTINCT city, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE city <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY city
ORDER BY SUM(totaltransactionrevenue) DESC
LIMIT 5;
```

**Top Countries:**

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

**Cities:**

```SQL
SELECT city, AVG(productQuantity)
FROM all_sessions
WHERE productQuantity IS NOT NULL
 AND city <> 'not available in demo dataset'
GROUP BY city
ORDER BY AVG(productQuantity) DESC
LIMIT 5;
```

**Countries**

```SQL
SELECT country, AVG(productQuantity)
FROM all_sessions
WHERE productQuantity IS NOT NULL
 AND country <> 'not available in demo dataset'
GROUP BY country
ORDER BY AVG(productQuantity) DESC
LIMIT 5;
```



Answer:
The top 5 cities are Madrid, Salem, Atlanta, Houston, and New York.
The top 5 countries are Spain, United States, Colombia, Finland, and France.





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

**Cities**

```SQL
SELECT city, v2productcategory, totaltransactionrevenue
FROM all_sessions2
WHERE city <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY city, v2productcategory, totaltransactionrevenue
ORDER BY totaltransactionrevenue DESC;
```

**Countries**

```SQL
SELECT country, v2productcategory, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE country <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY country, v2productcategory, totaltransactionrevenue
ORDER BY SUM(totaltransactionrevenue) DESC
```


Answer:
Cities: Yes, there is a pattern, focusing on western United States, visitors usually purchase the Home/Nest products while around the Atlanta region, visitors purchase bags. Tel Aviv-Yafo usualllying purchases the Home/Nest while Sunnyvale purchases Housewares.

Countries: Yes, there is a pattern within the countries,  United States focused on a wide range of catelogs, such as Home/Nest, Bags, Electronics, Home/Office, and houswares. Isreali and Australian customers usually order Home/Nest products while Canada focussed on Apparel.





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

**Cities**

```SQL
SELECT city, v2productname, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE city <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY city, v2productname, totaltransactionrevenue
ORDER BY SUM(totaltransactionrevenue) DESC
LIMIT 5;
```

**Countries**

```SQL
SELECT Country, v2productname, SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE country <> 'not available in demo dataset'
    AND totaltransactionrevenue IS NOT NULL
GROUP BY country, v2productname, totaltransactionrevenue
ORDER BY SUM(totaltransactionrevenue) DESC
```

Answer: Yes, while United States is focussed on reusable shopping bags, Isreal and Australia perfer Nest products.

Cities: 

Atlanta: Reusable Shopping Bag =   742
Sunnyvale: SPF-15 Slim & Slender Lip Balm  =  649
Tel Aviv-Yafo: Nest® Protect Smoke + CO Black Wired Alarm-USA =   602
Los Angeles: Nest® Cam Outdoor Security Camera - USA  =  363
Sydney: Nest® Cam Indoor Security Camera - USA  =  358

Countries: The top selling products for each country is:

United State: Reusable Shopping Bag  =  1015
Israel: Nest® Protect Smoke + CO Black Wired Alarm-USA  =  602
Australia: Nest® Cam Indoor Security Camera - USA  =  358
Canada: Google Men's 3/4 Sleeve Raglan Henley Grey  =  82
Switzerland: YouTube Men's 3/4 Sleeve Henley  = 16





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

**Cities**

```SQL
SELECT al.city, SUM(a.revenue)
FROM all_sessions2 al JOIN analytics2 a USING (fullvisitorid)
WHERE al.city <> 'not available in demo dataset'
    AND revenue IS NOT NULL
GROUP BY al.city
ORDER BY SUM(a.revenue) DESC;
```

**Countries**

```SQL
SELECT al.country, SUM(a.revenue)
FROM all_sessions2 al JOIN analytics2 a USING (fullvisitorid)
WHERE al.country <> 'not available in demo dataset'
    AND revenue IS NOT NULL
GROUP BY al.country
ORDER BY SUM(a.revenue) DESC;
```


Answer:
Cities:

Mountain View  =  10549.4899960000000000
San Bruno  =  4230.9900000000000000
New York  =  3485.7899920000000000
Sunnyvale  =  3039.2599920000000000
Chicago  =  1383.6300000000000000
Charlotte  =  1161.3899930000000000
Kirkland  =  1103.5200000000000000
San Francisco  =  987.4499980000000000
Los Angeles  =  942.9999990000000000
Jersey City  =  933.8500000000000000

Countries:

United States  =  115229.2799000000000000
Canada  =  487.6700000000000000
Germany  =  69.9800000000000000
Japan  =  30.8800000000000000
Switzerland  =  16.9900000000000000






