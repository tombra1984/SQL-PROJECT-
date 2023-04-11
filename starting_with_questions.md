Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
SELECT 
	city, 
	country, 
	SUM(totaltransactionrevenue)/1000000 as TTR 
FROM 
	a_all_sessions
where (
	totaltransactionrevenue is not null)
and
(
	city!= 'not available in demo dataset' and city!='(not set)' )
GROUP BY 
	country,city
ORDER BY
	TTR DESC

Answer: "San Francisco" "UNITED STATES" "1564"




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

SELECT 
a.country, 
a.city, 
AVG(orderedquantity) as average 
FROM 
    a_all_sessions as a
JOIN products as p
ON p.sku=a.productsku
where (
	orderedquantity is not null)
and
(
	city!= 'not available in demo dataset' and city!='(not set)' )
	
GROUP BY city, country, orderedquantity 
ORDER BY average DESC

Answer:
Moscow, Russia, 15170





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

SELECT  v2productcategory as p_types, country, city
FROM all_sessions
where (
	v2productcategory is not null 
		and v2productcategory !='not available in demo dataset' 
			and v2productcategory!='(not set)'
			    and v2productcategory!= '${escCatTitle}'				
)
and
(
	city!= 'not available in demo dataset' and city!='(not set)' )
GROUP BY country, city,v2productcategory
ORDER BY p_types


Answer:
most products ordered are apparel/assessories related




**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
SELECT 
p.name, 
city, 
SUM(total_ordered) AS total_quantity_ordered
FROM a_all_sessions AS a
JOIN products as p
on a.productsku=p.sku
JOIN sales_by_sku as s	 
on s.productsku=p.sku	
	 WHERE (
		 name IS NOT NULL
AND country IS NOT NULL
AND city IS NOT NULL  
AND sku IS NOT NULL
AND total_ordered IS NOT NULL)
	 and
	(name != 'not available in demo dataset' and name!='(not set)'
AND country != 'not available in demo dataset' and country!='(not set)'
AND city != 'not available in demo dataset' and city!='(not set)'  
AND sku!= 'not available in demo dataset' and sku!= '(not set)'
)
	 
GROUP BY city, name
ORDER BY total_quantity_ordered DESC




Answer:" Cam Indoor Security Camera - USA", "Mountain View", 2448





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
SELECT b.city,b.country, a.revenue, a.revenue/1000000 AS city_revenue
From a_all_sessions AS b
JOIN analytics as a
ON b.fullvisitorid=a.fullvisitorid 
where (
	revenue is not null)
and
(
	city!= 'not available in demo dataset' and city!='(not set)')
 
GROUP BY a.revenue, b.city, b.country
order by a.revenue desc


Answer:"Mountain View" generated the most revenue and Zurich generated the least







