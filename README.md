Retail Customer Behavior & Shopping Trends Analysis 📊
📌 Project Overview
This project provides an end-to-end data analytics solution to understand customer shopping patterns. It follows a professional workflow: cleaning raw data in Python, performing deep-dive analysis in SQL, and creating an interactive dashboard in Power BI to drive business decisions.

The goal is to answer key business questions:

Which customer segments contribute most to revenue?
How do discounts and shipping types affect purchasing behavior?
What are the top-performing products across different categories?

🛠️ Tech Stack
Data Cleaning & Engineering: Python (Pandas)
Database Analysis: Microsoft SQL Server (SSMS)
Data Visualization: Power BI
Documentation: Markdown & GitHub

🚀 Key Contributions (Feature Engineering)
Unlike basic versions of this project, I implemented custom data transformation steps to enhance the analysis:

Standardization: Converted all column names to snake_case and lowercase for database compatibility.
Age Binning: Used pd.qcut in Python to segment customers into 4 equal-sized age groups (Young Adult, Adult, Middle-aged, Senior).
Categorical to Numerical Mapping: Transformed frequency descriptions (e.g., 'Weekly', 'Monthly') into a numeric purchase_frequency_days column to allow mathematical modeling.
Redundancy Removal: Identified and dropped redundant features (e.g., promo_code_used) after verifying 100% correlation with discount_applied.

🔍 SQL Business Insights
I used advanced SQL techniques like CTEs (Common Table Expressions) and Window Functions to extract insights:
Customer Segmentation: Classified buyers as 'New', 'Returning', or 'Loyal' based on purchase history.
Product Ranking: Ranked the top 3 products per category using ROW_NUMBER().
Revenue Impact: Analyzed total spend and average ratings influenced by subscription status and discounts.

SQL
-- Example: Ranking top items per category
WITH item_counts AS (
    SELECT category, item_purchased, COUNT(customer_id) AS total_orders,
    ROW_NUMBER() OVER (PARTITION BY category ORDER BY COUNT(customer_id) DESC) AS item_rank
    FROM cleaned_customers
    GROUP BY category, item_purchased
)
SELECT * FROM item_counts WHERE item_rank <= 3;
📈 Power BI Dashboard
The interactive dashboard provides a 360-degree view of the business:

KPI Cards: Total Customers, Average Spend, and Average Rating.

Revenue Analysis: Breakdowns by Gender, Category, and Age Group.

Subscription Trends: Visualizing the high conversion rate of loyal customers to subscribers.

💡 Findings & Recommendations
Loyalty Pays: 'Loyal' customers (10+ purchases) account for the highest average spend. Action: Implement a tiered rewards program to move 'Returning' customers to 'Loyal' status.
Shipping Impact: Customers using 'Express' shipping spend significantly more than those on 'Standard'. Action: Offer free express shipping for orders above a certain threshold to increase AOV (Average Order Value).
Discount Strategy: Certain items are rarely bought without a discount. Action: Optimize pricing for these items or bundle them with high-margin products.

📜 License & Credits
This project is based on a professional workflow by Amlan Mohanty.
Modifications, advanced SQL queries, and additional Python feature engineering were performed by me.
This project is licensed under the MIT License.

📫 Connect with me
LinkedIn: www.linkedin.com/in/karampinaskyriakos
Email: kyrkarabinas@gmail.com
