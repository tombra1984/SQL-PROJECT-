What issues will you address by cleaning the data?
Unit price evaluation in table
Unifying the decimal place across the dataset 
changed unwanted data
removed unwanted columns 



Queries:
Below, provide the SQL queries you used to clean your data.
SELECT *, unit_price / '1000000' as d_unit_price
from analytics;

SELECT *, productprice / '1000000' as p_productprice
FROM a_all_sessions;

SELECT * , ROUND(ratio, 1) as ratio
FROM sales_report

  
CREATE TABLE n_all_session AS
SELECT DISTINCT * from all_sessions
DROP all_session
ALTER TABLE n_all_sessions RENAME to all_sessions

ALTER TABLE a_all_sessions
DROP COLUMN productrefundamount, 
DROP COLUMN productrevenue,
DROP COLUMN itemquantity,
DROP COLUMN itemrevenue
DROP COLUMN transactionrevenue;