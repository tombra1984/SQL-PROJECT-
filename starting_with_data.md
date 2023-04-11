Question 1: 

SQL Queries:
DELETE FROM all_sessions
	WHERE fullvisitorid 
		IN (
			SELECT fullvisitorid 
			FROM all_sessions 
			GROUP BY fullvisitorid 
			HAVING COUNT (*) >1)


Question 2: 

SQL Queries:
SELECT COUNT (
    fullvisitorid) 
FROM
all_sessions
Answer:

13421

Question 3: 

SQL Queries:
SELECT COUNT (visitid) 
FROM 
 a_all_sessions
Answer:
13421


Question 4: 

SQL Queries:
select name as productname, fullvisitorid as visitor
from products as v2p
join a_all_sessions as p
on p.productsku=v2p.sku
order by v2productname desc
Answer:

" Leatherette Notebook Combo"
"SPF-15 Slim & Slender Lip Balm"
" Infant Short Sleeve Tee Green"
"Badge Holder"
" Metallic Notebook Set"
"Spiral Notebook and Pen Set"
"22 oz Android Bottle"
"Red Shine 15 oz Mug"

Question 5: 

SQL Queries:


select 
round(sum(transactions)*100.0/sum(pageviews),1) as percent
from all_sessions
where transactions >0
Answer:7%
