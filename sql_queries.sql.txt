
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


-- ==================================================
-- Product Category Revenue Analysis
-- ==================================================

-- Question:
-- Which product category generated the highest revenue?

SELECT
    product_category,
    ROUND(
        SUM(transaction_qty * unit_price),
        2
    ) AS revenue
FROM `coffee shop sales`
GROUP BY product_category
ORDER BY revenue DESC;


-- ==================================================
-- Top Products by Revenue
-- ==================================================

-- Question:
-- Which products generated the highest revenue?

SELECT
    product_type,
    ROUND(
        SUM(transaction_qty * unit_price),
        2
    ) AS revenue
FROM `coffee shop sales`
GROUP BY product_type
ORDER BY revenue DESC
LIMIT 10;


-- ==================================================
-- Underperforming Products by Revenue
-- ==================================================

-- Question:
-- Which products generated the lowest revenue?

SELECT
    product_type,
    ROUND(
        SUM(transaction_qty * unit_price),
        2
    ) AS revenue
FROM `coffee shop sales`
GROUP BY product_type
ORDER BY revenue ASC


-- ==================================================
-- Peak Business Hours Analysis
-- ==================================================

-- Question:
-- When are the busiest business hours?

SELECT
    HOUR(transaction_time) AS business_hour,
    COUNT(*) AS total_transactions
FROM `coffee shop sales`
GROUP BY HOUR(transaction_time)
ORDER BY HOUR(transaction_time);


-- ==================================================
-- Store Preference Analysis
-- ==================================================

-- Question:
-- Do customer preferences vary by store location?

SELECT
    store_location,
    product_type,
    ROUND(
        SUM(transaction_qty * unit_price),
        2
    ) AS revenue
FROM `coffee shop sales`
GROUP BY
    store_location,
    product_type
ORDER BY revenue DESC;



