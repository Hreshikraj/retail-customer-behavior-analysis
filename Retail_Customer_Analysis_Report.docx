DESCRIBE customer_shopping_clean;

SELECT COUNT(*) AS total_records
FROM customer_shopping_clean;

SELECT *
FROM customer_shopping_clean
LIMIT 10;

SELECT `Purchase Amount (USD)`
FROM customer_shopping_clean;

SELECT COUNT(*) AS total_records
FROM customer_shopping_clean;

SELECT
    COUNT(*) AS total_records,
    SUM(CASE WHEN `Customer ID` IS NULL THEN 1 ELSE 0 END) AS missing_customer_id,
    SUM(CASE WHEN Age IS NULL THEN 1 ELSE 0 END) AS missing_age,
    SUM(CASE WHEN Gender IS NULL THEN 1 ELSE 0 END) AS missing_gender,
    SUM(CASE WHEN Category IS NULL THEN 1 ELSE 0 END) AS missing_category,
    SUM(CASE WHEN `Purchase Amount (USD)` IS NULL THEN 1 ELSE 0 END) AS missing_purchase_amount,
    SUM(CASE WHEN `Review Rating` IS NULL THEN 1 ELSE 0 END) AS missing_rating
FROM customer_shopping_clean;

	SELECT
		`Customer ID`,
		COUNT(*) AS record_count
	FROM customer_shopping_clean
	GROUP BY `Customer ID`
	HAVING COUNT(*) > 1;
    
    
    SELECT
    COUNT(*) AS total_records,
    COUNT(DISTINCT CONCAT_WS('|',
        `Customer ID`, Age, Gender, `Item Purchased`,
        Category, `Purchase Amount (USD)`, Location,
        Size, Color, Season, `Review Rating`,
        `Subscription Status`, `Shipping Type`,
        `Discount Applied`, `Promo Code Used`,
        `Previous Purchases`, `Payment Method`,
        `Frequency of Purchases`
    )) AS unique_records
FROM customer_shopping_clean;

Question: How many male and female customers are in the dataset?
SELECT
    Gender,
    COUNT(*) AS total_customers
FROM customer_shopping_clean
GROUP BY Gender
ORDER BY total_customers DESC;
Business insight
Male customers account for approximately 68% of the dataset, while female customers account for approximately 32%.


Question: Which age group has the highest number of customers?
SELECT
    CASE
        WHEN Age BETWEEN 18 AND 25 THEN '18-25'
        WHEN Age BETWEEN 26 AND 35 THEN '26-35'
        WHEN Age BETWEEN 36 AND 50 THEN '36-50'
        ELSE 'Above 50'
    END AS age_group,
    COUNT(*) AS total_customers
FROM customer_shopping_clean
GROUP BY age_group
ORDER BY total_customers DESC;
Business insights
1. Customers above 50 form the largest segment (approximately 38%).
2. Customers aged 18–25 form the smallest segment (approximately 15%).
3. Customers aged 36 and above account for approximately 66% of the dataset.
Business recommendation: The retailer could investigate products and marketing campaigns that appeal to older customers while exploring opportunities to attract younger shoppers.



Which product category generates the highest revenue?
SELECT
    Category,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    COUNT(*) AS total_orders,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY Category
ORDER BY total_revenue DESC;
Business insights
1. Clothing is the top category, contributing approximately 44.6% of total revenue.
2. Accessories is the second-highest category, contributing approximately 31.9%.
3. Outerwear has the lowest revenue.
4. Average purchase amounts are relatively similar across categories.
Business recommendation: The retailer should protect Clothing's strong sales performance and investigate ways to increase Outerwear sales through promotions or product assortment changes.

Question: Which gender contributes more revenue?
SELECT
    Gender,
    COUNT(*) AS total_customers,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY Gender
ORDER BY total_revenue DESC;
Business insights
1. Male customers contribute approximately 67.4% of total revenue.
2. Female customers contribute approximately 32.6%.
3. Female customers have a slightly higher average purchase amount ($60.25 vs. $59.44).
Important distinction: Male customers generate more total revenue mainly because there are more male customers in the dataset. Female customers spend slightly more per purchase on average.


Question: Which season generates the highest revenue?
SELECT
    Season,
    COUNT(*) AS total_orders,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY Season
ORDER BY total_revenue DESC;
Business insights
1. Fall generates the highest revenue at $59,620.
2. Summer generates the lowest revenue at $55,097.
3. Spring has the highest number of orders, but not the highest revenue.
4. Fall also has the highest average purchase amount.
Interesting observation: More orders don't always mean more revenue. Spring has more orders than Fall, but Fall generates more money because its average purchase amount is higher.


Question: Which individual products generate the highest revenue?
SELECT
    `Item Purchased`,
    COUNT(*) AS total_orders,
    SUM(`Purchase Amount (USD)`) AS total_revenue
FROM customer_shopping_clean
GROUP BY `Item Purchased`
ORDER BY total_revenue DESC
LIMIT 10;
Business insights to save
1. Blouse generates the highest revenue ($10,296).
2. Shirt is second ($10,235).
3. Dress is third ($10,200).
4. The top three products have relatively similar revenue.
5. Jewelry generates more revenue than several clothing products.
Business recommendation: Maintain sufficient stock of the top-performing products and investigate whether similar products can generate additional sales.


Question: Which states contribute the highest revenue?
SELECT
    Location,
    COUNT(*) AS total_customers,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY Location
ORDER BY total_revenue DESC
LIMIT 10;
Business insights 
1. Montana has the highest revenue among the 10 locations ($5,717).
2. California ranks second ($5,605).
3. Illinois ranks third ($5,537).
4. West Virginia has the lowest revenue among these top 10 locations ($5,045).
5. West Virginia has the highest average purchase amount ($63.86), despite having the lowest total revenue in this group.
Business recommendation: Investigate customer acquisition and marketing opportunities in high-revenue states, while examining why some states have higher average purchases but lower overall revenue.



Question: Which payment methods are most commonly used by customers?
SELECT
    `Payment Method`,
    COUNT(*) AS total_transactions,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY `Payment Method`
ORDER BY total_transactions DESC;
Business insights 
1. PayPal is the most frequently used payment method, with 673 transactions.
2. Bank Transfer is the least frequently used, with 606 transactions.
3. PayPal generates the highest total revenue ($39,849).
4. Debit Card has the highest average purchase amount ($60.85).
5. Revenue is relatively evenly distributed across payment methods.
Business recommendation: Continue supporting multiple payment methods. Investigate whether offering incentives for less-used payment methods could improve adoption.



Question: Do subscribed customers generate more revenue than non-subscribed customers?
SELECT
    `Subscription Status`,
    COUNT(*) AS total_customers,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY `Subscription Status`
ORDER BY total_revenue DESC;
Business insights
1. Non-subscribed customers represent approximately 73.3% of the dataset.
2. Subscribed customers represent approximately 26.7%.
3. Non-subscribed customers generate more total revenue because they are a much larger group.
4. Average purchase amounts are almost identical between the two groups.
Business recommendation: The retailer could investigate why subscription adoption is relatively low and test benefits such as exclusive discounts or free shipping.



Question: Do customers who use discounts spend more or less than customers who don't?
SELECT
    `Discount Applied`,
    COUNT(*) AS total_customers,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY `Discount Applied`
ORDER BY total_customers DESC;
Business insights 
1. Approximately 57.5% of customers did not use discounts.
2. Approximately 42.5% used discounts.
3. Customers without discounts had a higher average purchase amount ($60.13 vs. $59.12).
4. Non-discount purchases generated more total revenue.
Business recommendation: The retailer should evaluate whether discounts are actually increasing sales volume enough to justify the reduction in selling price.




Question: Which shipping method is most popular, and which generates the highest revenue?
SELECT
    `Shipping Type`,
    COUNT(*) AS total_orders,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY `Shipping Type`
ORDER BY total_orders DESC;
Business insights
1. Free Shipping is the most popular method, with 667 records.
2. Free Shipping also generates the highest recorded revenue, at $40,264.
3. 2-Day Shipping has the highest average purchase, at $60.59, despite having the fewest records.
4. Standard Shipping has the lowest average purchase, at $58.41.
Business recommendation
The business could investigate whether Free Shipping encourages more purchases. It could also examine whether customers using 2-Day Shipping tend to spend more. However, this dataset alone cannot prove that shipping choice causes higher spending.




Question: Which purchase frequency category is most common?
SELECT
    `Frequency of Purchases`,
    COUNT(*) AS total_records,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY `Frequency of Purchases`
ORDER BY total_records DESC;
Business insights
1. Every 3 Months is the most common reported purchase frequency, with 577 records.
2. Weekly is the least common, with 535 records.
3. Bi-Weekly has the highest average purchase amount ($60.75).
4. The average purchase amounts are quite close across all frequency groups, ranging from $58.80 to $60.75.
Business recommendation
The business could investigate whether customers who purchase less frequently respond to targeted reminders or seasonal campaigns. It could also explore what drives the slightly higher average purchase among Bi-Weekly customers.




Question: How many customers fall into low-, medium-, and high-spending groups?
SELECT
    CASE
        WHEN `Purchase Amount (USD)` <= 40 THEN 'Low Spending'
        WHEN `Purchase Amount (USD)` <= 80 THEN 'Medium Spending'
        ELSE 'High Spending'
    END AS spending_segment,
    COUNT(*) AS total_records,
    SUM(`Purchase Amount (USD)`) AS total_revenue,
    ROUND(AVG(`Purchase Amount (USD)`), 2) AS average_purchase
FROM customer_shopping_clean
GROUP BY spending_segment
ORDER BY total_revenue DESC;
Business insights
1. Medium Spending is the largest segment, representing approximately 47.7% of all records.
2. High Spending represents approximately 25.0% of records but contributes around 38.0% of recorded revenue.
3. Low Spending represents approximately 27.3% of records and contributes around 13.7% of recorded revenue.
4. High-spending records have an average purchase amount of $90.54, compared with $29.97 for low-spending records.
Business recommendation
- Maintain engagement with medium-spending customers because they form the largest segment.
- Explore loyalty rewards or relevant product recommendations for high-spending customers.
- Test targeted offers to encourage low-spending customers to consider additional or higher-value purchases.




Question: What are the 10 largest purchases in this dataset, and which products and categories are associated with them?
SELECT
    `Customer ID`,
    `Item Purchased`,
    Category,
    `Purchase Amount (USD)`,
    Location,
    Gender
FROM customer_shopping_clean
ORDER BY `Purchase Amount (USD)` DESC
LIMIT 10;
Business insights
1. All 10 records have the same purchase amount: $100.
2. Clothing appears most often, with 5 of the 10 records.
3. Footwear appears twice, while Outerwear and Accessories appear once each.
4. The purchases come from different locations, so no single location dominates this top 10.
Important observation: Because all 10 amounts are exactly $100, this query does not identify one uniquely highest-value purchase. It identifies records tied at the maximum purchase amount.





