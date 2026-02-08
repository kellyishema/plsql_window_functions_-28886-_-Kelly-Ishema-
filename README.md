# plsql_window_functions_-28886-_-Kelly-Ishema-

# Business Context
Company Type: Regional automotive dealership group (Kelly Price Auto Group)
Department: Sales Analytics & Customer Relationship Management
Industry: Automobile Retail / New & Used Vehicle Sales
# Data Challenge.
Kelly Price Auto Group operates multiple dealership locations but is struggling with uneven sales performance across territories and limited understanding of customer buying behaviors. The sales management team cannot accurately identify which vehicle types (sedans, SUVs, trucks, luxury) perform best in specific geographic markets, how often customers return for repeat purchases or service, and which customer demographics represent the highest lifetime value. This knowledge gap results in misaligned inventory distribution across dealerships, generic marketing approaches, and missed opportunities to convert one-time buyers into loyal, repeat customers for vehicle upgrades and trade-ins.
# Expected Outcome.
1.	Geographic Vehicle Performance: Identify the top 5 performing vehicle categories by sales revenue and unit volume across Kelly Price's dealership locations (by city/region), enabling optimized inventory allocation and location-specific promotional strategies.
2.	Customer Purchase Cycle Analysis: Segment customers based on their engagement patterns—first-time buyers, repeat customers (purchased 2+ vehicles), service-only customers, and trade-in customers—to quantify the revenue contribution and average transaction value of each segment.
3.	High-Value Customer Targeting: Define specific customer profiles based on total purchase value, vehicle preference patterns, financing vs. cash purchases, and trade-in frequency to enable targeted direct mail campaigns, personalized vehicle recommendations, VIP sales events, and loyalty program development with a projected 20-25% increase in repeat customer rate and higher trade-in capture.

# Step 2: Success Criteria - Five Measurable Goals
Kelly Price Autos - Window Functions Success Criteria
________________________________________
1. Top 5 Vehicle Models per Region
Window Function: RANK() or ROW_NUMBER()
Measurable Goal:
Identify and rank the top 5 best-selling vehicle models in each of Kelly Price's four sales regions (North, South, East, West) based on total sales revenue generated during the fiscal year.
# Success Metric:
•	Generate a ranked list (positions 1-5) for each region showing which vehicle models generate the highest revenue
•	Enable regional managers to make data-driven inventory purchasing decisions
•	Each region will have exactly 5 ranked vehicles to guide restocking priorities
•	Expected outcome: Optimize inventory allocation to increase regional sales by 12-15%
# Business Impact:
Regional managers can immediately see that Ford F-150 ranks #1 in North and West regions but only #4 in South, allowing them to adjust inventory orders accordingly and reduce overstocking of low-performing models.
________________________________________
2. Running Year-to-Date (YTD) Sales Totals
Window Function: SUM() OVER() with cumulative frame
Measurable Goal:
Calculate cumulative monthly sales revenue for each region throughout the year, providing a running total that shows progress toward annual sales targets at any point in time.
# Success Metric:
•	Produce month-by-month running total reports for all four regions
•	Enable sales managers to compare actual YTD performance against target at any month
•	Identify underperforming regions by month 6 (mid-year checkpoint)
•	Track if regions are on pace to meet their annual quotas (e.g., North region target: $4.2M)
# Business Impact:
By August, management can see that East region's YTD total is $1.8M against a target pace of $2.1M, triggering immediate corrective actions like promotional campaigns or additional sales staff allocation.
________________________________________
3. Month-over-Month Sales Growth Rate
Window Function: LAG() and/or LEAD()
Measurable Goal:
Calculate the percentage change in sales revenue from one month to the previous month for each region and vehicle category, identifying growth trends, seasonal patterns, and performance shifts.
# Success Metric:
•	Generate monthly growth rate percentages for each region (e.g., +15.3% or -8.7%)
•	Identify months with negative growth for immediate investigation
•	Detect seasonal patterns (e.g., December consistently shows +20% growth)
•	Flag regions with 3+ consecutive months of declining growth as "at-risk"
Business Impact:
When South region shows -12% growth in March compared to February, management investigates and discovers a local competitor's promotion, enabling rapid competitive response with targeted discounts.
________________________________________
4. Customer Lifetime Value Quartile Segmentation
Window Function: NTILE(4)
Measurable Goal:
Segment Kelly Price's entire customer base into four equal quartiles based on total lifetime purchase value, classifying customers from highest spenders (Q1 - top 25%) to lowest spenders (Q4 - bottom 25%) for targeted marketing prioritization.
Success Metric:
•	Classify 100% of active customers (15 customers) into four distinct quartiles
•	Q1 (Platinum): Top 25% - approximately 5 customers
•	Q2 (Gold): 26-50% - approximately 5 customers
•	Q3 (Silver): 51-75% - approximately 3 customers
•	Q4 (Bronze): Bottom 25% - approximately 2 customers
•	Enable marketing team to allocate resources: 50% budget to Q1, 30% to Q2, 15% to Q3, 5% to Q4
# Business Impact:
Marketing creates VIP preview events exclusively for Q1 customers (who average $89,000 lifetime value), personalized loyalty programs for Q2-Q3, and re-engagement campaigns for Q4, resulting in projected 20% improvement in customer retention.
________________________________________
5. Three-Month Moving Average for Sales Trend Analysis
Window Function: AVG() OVER() with sliding window frame
# Measurable Goal:
Calculate rolling 3-month average sales revenue for each region and vehicle category to smooth out monthly volatility, identify underlying trends, and eliminate seasonal noise from sales performance analysis.
Success Metric:
•	Generate smoothed trend lines for all regions showing 3-month rolling averages
•	Compare raw monthly sales vs. moving average to distinguish genuine trends from temporary fluctuations
•	Improve demand forecasting accuracy by 25% compared to single-month projections
•	Use trend analysis to set realistic quarterly targets based on smoothed historical performance
# ER diagram 
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/af897739-4e46-48d6-a30a-9d30c6bd4362" />
# JOIN QUERIES

# INNER JOIN

This join returns only records that exist in both tables.

In dealership terms:
You only see leads that actually became sales.
If a lead never resulted in a sale, it is excluded.
# LEFT JOIN

This join returns all records from the first table, plus matching records from the second table.

In dealership terms:
You see every lead, whether or not it turned into a sale.
Leads without sales still appear, but sales information is empty.
# RIGHT JOIN

This join returns all records from the second table, plus matching records from the first.

In dealership terms:
You see every sale, even if the original CRM lead is missing.
# FULL OUTER JOIN

This join returns all records from both tables, matching where possible.

In dealership terms:
You can identify:

Leads with no sales.

Sales with no leads.
# CROSS JOIN

This join combines every row from one table with every row from another.

In dealership terms:
Every dealership is matched with every sales target or incentive plan.
# SELF JOIN

This join matches a table to itself.

In dealership terms:
You compare customer records against other customer records to find:

Repeat buyers

Multiple purchases by the same person.

# Key Insights
1. Vehicle Performance Varies Strongly by Region

SUVs and higher-priced vehicles (e.g., BMW X5, Ford F-150) consistently rank among the top-selling models in their regions, indicating regional preferences and stronger margins from premium inventory.

2. Sales Momentum Builds Over Time, Not Evenly

Running monthly sales totals show a steady upward trend, with noticeable jumps in later months. This indicates cumulative momentum driven by repeat customers and improved conversion rates, rather than one-off spikes.

3. Month-over-Month Growth Is Inconsistent Across Regions

Some regions experience positive month-over-month growth while others show declines, highlighting uneven regional performance.

# Integrity Statement
I affirm that this submission is my original work and complies fully with academic integrity requirements. 
No unauthorized assistance or materials were used.

# References.
Academic & Textbook Resources

Elmasri, R., & Navathe, S. B. (2016). Fundamentals of Database Systems (7th ed.). Pearson Education.
— Authoritative source on ER diagrams, relational modeling, primary keys, and foreign keys.

Silberschatz, A., Korth, H. F., & Sudarshan, S. (2020). Database System Concepts (7th ed.). McGraw-Hill Education.
— Covers SQL querying, relational integrity, and analytical database concepts.

Kimball, R., & Ross, M. (2013). The Data Warehouse Toolkit (3rd ed.). Wiley.
— Business-focused resource on fact tables, dimensions, and analytics-ready schema design.

Official Documentation

PostgreSQL Global Development Group. (2024). PostgreSQL Documentation – Window Functions.
— Official documentation for RANK(), SUM() OVER(), LAG(), NTILE(), and AVG() OVER().

Oracle Corporation. (2023). Oracle SQL Language Reference – Analytic Functions.
— Official reference for ANSI-compliant SQL analytic/window functions.

Microsoft Learn. (2024). SQL Server Documentation – OVER Clause.
— Official Microsoft resource explaining running totals, moving averages, and ranking.

ISO/IEC. (2016). ISO/IEC 9075: SQL — Database Language Standard.
— International standard defining SQL syntax and behavior.

Tutorials & Learning Resources

W3Schools. (2024). SQL Tutorial: SQL Window Functions.
— Beginner-friendly tutorial explaining window functions with examples.

Mode Analytics. (2023). SQL Window Functions Tutorial.
— Practical, analytics-oriented guide to ranking, running totals, and time-based analysis.

DataCamp. (2024). SQL Window Functions Course.
— Hands-on tutorial resource for analytical SQL queries.

Business & Industry Resources

IBM. (2023). Introduction to Relational Databases and SQL.
— Business-focused overview of relational databases and analytical querying.

Amazon Web Services (AWS). (2024). Best Practices for Designing Relational Databases.
— Industry guidance on schema design and analytics performance.

# screenshots proving personal work.

<img width="1306" height="634" alt="personal work screenshot1" src="https://github.com/user-attachments/assets/ad1d6463-1ae7-4348-b42e-2210e5f9b7b9" />

<img width="1098" height="641" alt="personal work screenshot2" src="https://github.com/user-attachments/assets/c0575508-3274-491f-8d6c-6916068765a6" />
