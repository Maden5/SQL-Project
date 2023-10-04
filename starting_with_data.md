Question 1:  What are the top selling products internationally?

SQL Queries:

```SQL
SELECT sk.productsku, al.v2productname, sk.total_ordered
FROM sales_by_sku sk JOIN all_sessions2 al USING (productsku)
GROUP BY sk.productsku, al.v2productname, sk.total_ordered
ORDER BY sk.total_ordered DESC;
```

Answer: 
The top selling products are the Ballpoint, Google stainless bottle, Leatherette Journal, Google Spiral Journal, and Foam Can.
While viewing the whole column, I noticed two things. The top selling product which is the Google Pen, and also the top selling brands, Google and NEST.



Question 2: How much stock is left for the most in demand products?

SQL Queries:
```SQL
SELECT sk.productsku, al.v2productname, sk.total_ordered, sr.stocklevel
FROM sales_by_sku sk JOIN all_sessions2 al USING (productsku)
JOIN sales_report sr USING (productsku)
GROUP BY sk.productsku, al.v2productname, sk.total_ordered, sr.stocklevel
ORDER BY sk.total_ordered DESC;
```

Answer:
While looking at the stock levels, all the top selling products were sufficiently stock.


Question 3: How much visitors that purchased  a product were referred to the site?

SQL Queries:

```SQL
SELECT fullvisitorid, channelgrouping, totaltransactionrevenue
FROM all_sessions2
WHERE totaltransactionrevenue IS NOT NULL
AND channelgrouping LIKE 'Referral%'
GROUP BY fullvisitorid, channelgrouping, totaltransactionrevenue
ORDER BY totaltransactionrevenue DESC;
```

```SQL
SELECT COUNT(channelgrouping), SUM(totaltransactionrevenue)
FROM all_sessions2
WHERE channelgrouping LIKE '%Referral%'
```

Answer:
The first query gave us the total amount each visitor purchased when referred to a product while the second query gives us the total count of referrals which is 2580, and the total amount made from referrals, $6010.


Conclusion:

Certain cities and countries are driving significant transaction revenues on the site. We see unique purchasing habits and product preferences based on region, with specific top-sellers emerging for different areas. By leveraging these insights, we can tailor the marketing and inventory strategies, optimizing revenue and growth for each region
