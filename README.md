# 🍕 Tony's Pizza | SQL Report
Project Overview: As the Head of Commercial Strategy, I conducted a comprehensive analysis of sales data to optimize revenue and operational efficiency for a multi-unit pizza franchise. This project transforms 48,000+ rows of raw transactional data into actionable business insights.



### 📊 Business KPIs Identified
Total Revenue: $817,860.05

Total Orders: 21,350

Avg. Pizzas Per Day: 138 units

Peak Performance: The Thai Chicken Pizza ($43,434 in revenue).



### 🛠️ Technical Stack
Database: SQL (MySQL/Excel)

Core Concepts: Joins, Sub-Queries, Window Functions, Aggregations.

Visualization: Power BI / MS Excel for trend analysis.



### 📈 Key Insights & Strategic Recommendations

Staffing Optimization: Peak orders occur consistently between 12-1 PM and 5-7 PM. I recommend a 15% increase in kitchen staff during these windows.

Menu Engineering: The "Classic" category contributes the highest volume, but "Chicken" pizzas generate higher margins. Strategy: Bundle lower-selling "Veggie" pizzas with high-margin items to clear inventory.

Revenue Concentration: 3 specific pizzas drive nearly 15% of total revenue. Ensure supply chain priority for these ingredients (Thai Chicken, BBQ Chicken, California Chicken).




### Example:
Revenue Contribution by Category

I used subqueries and joins to calculate the percentage contribution of each pizza category to the total bottom line. This allows the business to see which product lines are the real "breadwinners."

[select pizza_types.category, 

round(sum(pizzas.price*order_details.quantity) / 

(select sum(pizzas.price*order_details.quantity) from order_details 

join pizzas on pizzas.pizza_id = order_details.pizza_id) * 100,2)  as total_revenue_percentage

from pizza_types

join pizzas

on pizzas.pizza_type_id= pizza_types.pizza_type_id

join order_details

on order_details.pizza_id = pizzas.pizza_id

group by pizza_types.category;]
