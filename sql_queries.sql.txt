
-- ==================================================
-- Coffee Shop Business Intelligence Analysis
-- ==================================================


--Total Transactions

SELECT count(*)
FROM `coffee shop sales`;

-- Data Information

DESCRIBE `coffee shop sales`;

-- Store Locations

SELECT distinct store_location
FROM `coffee shop sales`;


-- ==================================================
-- Store Performance Analysis
-- ==================================================

-- Question:
-- How many transactions were recorded at each store location?

SELECT 
	store_location,
    count(*) as total_transactions
FROM `coffee shop sales`
GROUP BY store_location;


-- ==================================================
-- Store Revenue Analysis
-- ==================================================

-- Question:
-- Which store generated the highest revenue?

SELECT
    store_location,
    ROUND(SUM(transaction_qty * unit_price), 2) AS revenue
FROM `coffee shop sales`
GROUP BY store_location;

