# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
1. Understanding how to upload CVS files onto SQL
2. Find out the risk factors on the files
3. How to clean the data
4. Analyze the e-commerce dataset, focusing on understanding patterns related to products ordered by visitors based on their geographic locations
5. Determine if there are any trends or patterns 

## Process
1. Upload CVS files to pgadmin
2. Have the QA listing of all the risk factors
3. Clean the data, remove empty columns and change unit price and revenue into dollars
4. Evaluated the provided dataset, and managed to receive the trends between countries and cities


## Results
The data gave us an insight on the top selling products and categories for each region and countries. Using this date we can find the trends within each region and utilize it for future prediction of sales. We can also ditstinct purchasing behaviors emerged across regions, whether they were referred or not. Ultimately, the data provided a clear picture of the revenue contributions of different region, highlighting their importance to the business. 

## Challenges 
1. File corruption, when I tried to upload my last file (all_sessions), I kept on receiving error. A mentor suggested to delete the file and redownload it due to a corrupted file. His suggestion was correct, once I reupload it using the same query, SQL accepted the file.
2. When I made my duplicate tables, I kept on receiving an error message after I removed some columns. SQL was not letting me view the table. I figured I might have to restart pgadmin to see my results, once it was rerunned, I was able to view my tables. 
3. Finding out if there any duplicate records and empty columns. 


## Future Goals
1. Inspect more columns and rows while data cleaning
2. Investigate seasonal trends or time base patterns in purchasing
3. Use more advanced queries to predict future purchasing trends based on location

