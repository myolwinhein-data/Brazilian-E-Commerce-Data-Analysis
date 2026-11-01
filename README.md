# Brazilian-E-Commerce-Data-Analysis
Brazilian E-Commerce Data Analysis using SQL and Power BI. This project explores sales performance, customer behavior, product trends, payment methods, and delivery performance to generate meaningful business insights and support data-driven decision-making.

## Dataset Used
- https://www.kaggle.com/olistbr/brazilian-ecommerce/home/?utm_source=chatgpt.com

## Questions ( KPIs )
### 1. Customer Analysis
- Where customers come from (state, city) — geographic distribution
- New vs returning customer ratio by month
- Customer Lifetime Value (CLV) — top customers by total spend
- Cohort analysis: retention rate by acquisition month

### 2. Product & Category Insights
- Top 20 products by quantity sold and by revenue
- Categories with the lowest average review score — quality warning
- Relationship between product price and review score
- Freight value analysis by product weight and dimensions

### 3. Operations & Delivery
- Average delivery time 
- Percentage of late deliveries 
- Correlation between delivery time and review score
- Seller performance: top sellers by revenue and on-time delivery rate

### 4. Payment Behaviors
- Distribution of payment methods 
- AOV by payment method
- Share of orders using installments and average number of installments
- Payment method with the highest cancellation rate

## Project Process
I used a clear, step-by-step process to download, clean, and organize the Olist E-commerce data before creating my dashboards.
### Step 1: Data Extraction & Inspection: 
- Downloaded 9 Olist CSV files from Kaggle and thoroughly inspected the schema to assess its potential for sales and customer analytics.

### Step 2: Database Setup:
- Built a dedicated MySQL database with 9 empty staging tables and imported the raw CSV datasets into the environment.

### Step 3: Data Quality Audit:
- Ran SQL queries across all tables to identify data quality issues, specifically auditing for NULL values, duplicate primary keys (customer_id, product_id), and improper data formats.

### Step 4: Dimension Table Creation & Cleaning:
- Constructed cleaned dimension tables directly using SQL:
##### Text Normalization: 
- Standardized city/state fields in dim_geo, dim_customer, and dim_seller using TRIM(), LOWER(), and UPPER().
##### Translation & Null Handling: 
- Mapped Portuguese category names to English in dim_product using a LEFT JOIN, replacing missing text with 'Unknown' and missing numbers with 0 via COALESCE().
##### Date Formatting: 
- Converted raw timestamp strings into true date types in dim_date using STR_TO_DATE(), extracting year, month, and quarter attributes.

### Step 5: Fact Table Assembly & Filtering: 
- Built the central fact_sales table by connecting primary keys from dimension tables using relational JOINs. Applied a WHERE clause to isolate delivered orders with non-null delivery dates, ensuring 100% accurate logistics and performance metrics.

## Key Insights
### 1.Sales Performance Analysis
- Growth: Revenue and total customers are up YoY, but declining orders and lower AOV show customers are buying cheaper products.
- Top Categories: Health_beauty leads with $1.4M in revenue, followed closely by watches_gifts and bed_bath_table.

### 2.Customer Deep-Dive Analysis
- Location & Trend: Most customers live in SP. Acquisition peaked in Nov 2017 (Black Friday) but has since stagnated.
- Retention Alert: 99% of customers buy only once—retention drops below 1% after Month 1.

### 3.Product & Category Insights
- Top Volume: Health_beauty and bed_bath_table have the most orders.
- Quality Warning: Security_and_services has the lowest ratings, requiring immediate seller investigation.

### 4.Operations & Delivery Performance
- Speed: Deliveries are fast (5–10 days average), but fast shipping does not always guarantee 5-star reviews.
- Top Sellers: Top-revenue sellers maintain a 90%+ on-time delivery rate.

### 5.Payment Behavior Analysis
- High-Spenders: Credit Card users generate the highest Average Order Value.
- Popularity: Followed by Boleto, Debit Cards, and Vouchers.

## Recommendations
### 1.Solve the YoY Sales and Order Growth 
- Total revenue is growing, but total orders are going down. We should make customers to buy more items together in one order. We can give them discount like 2 buy get 1.

### 2.Fixing the Retention Rate
- The Cohort Heatmap shows that most of customers buy only one time and do not return in month 1. We should give them discount coupons for their next purchase immediately after they buy. This will make them return to our shop.

### 3.Focus Marketing Budget on SP State and Top 3 Categories
- Most of our customers live in SP state, and categories like health_beauty, watches_gift and bed_bath_table make the most money. We should spend more advertisement budget to target people in SP state with these top products.

### 4.Target Marketing in RJ, MG, and RS States
- After SP state, most of our customers live in RJ, MG, and RS states. We should create special promotions or discounts for these states to get more sales from them.

### 5.Review  in "Security and Services"
- The security_and_services category has very bad review ratings from customers. We should check these sellers and stop their shops if they do not improve their quality.

### 6.Checking Product Quality
- Some orders are delivered very fast (5 to 10 days) but still get very low rating from customers. This may be that  the delivery is fast, but the product quality is bad. We should survey these customers to ask about product quality.

## Final Conclusion
- During this project, I encountered several key challenges and valuable learning opportunities. Technically, importing large CSVs via the SQL Import Wizard caused missing data, requiring database adjustments to achieve complete loads. Complex SQL queries for cohort retention and anomaly detection, along with advanced Power BI DAX calculations, presented steep learning curves that required additional technical guidance. Model-wise, incorporating four supplementary tables revealed missing business metrics—such as customer demographics and product costs—which, if present, would have enabled full Net Profit and demographic analyses. Ultimately, navigating these real-world data hurdles provided deep, practical insights into end-to-end data processing and analytics.

## Appendix
### Power BI Dashboard
- Created three dashboards ( Executive Overview Dashboard, Customer Deep Dive Analysis Dashboard and Products, Review & Operation Analysis ).
##### Executive Overview Dashboard
- <img width="1907" height="936" alt="Screenshot 2026-11-01 220512" src="https://github.com/user-attachments/assets/6931ebca-05f8-4b92-9edd-1f7584dde2c2" />


##### Customer Deep Dive Dashboard
- <img width="1907" height="966" alt="Screenshot 2026-11-01 220552" src="https://github.com/user-attachments/assets/86733770-e588-4292-9cc1-b083bc6bd2ec" />


##### Products, Review & Operation Dashboard
- <img width="1907" height="967" alt="Screenshot 2026-11-01 220624" src="https://github.com/user-attachments/assets/035b84bd-0e1e-483c-976d-63dbbb519e8a" />


### SQL query
- I wrote and documented 10 high-quality MySQL queries. I will describe two key MySQL queries that are used on Power BI dashboard.
##### Cohort Retention 
- <img width="1907" height="977" alt="image" src="https://github.com/user-attachments/assets/61fb1708-9799-4496-88e9-25aa52cac3b3" />


##### New vs Returning Customers
- <img width="1907" height="988" alt="Screenshot 2026-11-01 222155" src="https://github.com/user-attachments/assets/f160f3e9-3af2-4d1a-864d-4ee75f362fc1" />

