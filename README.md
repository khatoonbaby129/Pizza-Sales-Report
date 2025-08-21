Pizza Sales Analysis

KPIs Requirement:
Total Revenue
Total Orders
Avg Pizzas per Order
Avg Order Values
Total Pizza Sold

Chart Requirement:
Daily Trend Analysis
Monthly Trend Analysis
% Sales by Pizza Category
% Sales by Pizza Size
Total Pizza Sold by Pizza Category
Top 5 Best Seller - Revenue,  Quantity , Orders
Bottom 5 Best Seller - Revenue , Quantity , Orders


SQL Query  and DAX
T. Revenue 
sql: - select sum(total_price) as total_revenue from pizza_sales
dax: - total_revenue = sum(pizza_sales[total_price])


avg_order_value
sql: - select sum(total_price) / count(distinct order_id) as avg_order_value from pizza_sales
DAX: - avg_order_value = sum(total_revenue] / [total_orders]

T. pizza_sold
sql: - select sum(quantity) as total_pizza_sold from pizza_sales
DAX: - total_pizza_sold = sum(pizza_sales[quantity])

T.Orders
sql: - select count(distinctount order_id) as total_orders from pizza_sales
DAX: - total_orders = distinctcount(pizza_sales[order_id])

avg_pizzas_per_order
sql: - select sum(quantity) / count(distinct order_id) as avg_pizzas_per_order from pizza_sales
DAX: - [total_pizza_sold] / [total_orders]
 
day_name
select dayname(order_date) as day_name from pizza_sales
select to_char(order_date , 'Day') as day_name from pizza_sales

month_name
select monthname(order_date) as month_name from pizza_sales

pizza_category wise total_sales %
select category , sum(total_price)  * 100 / (select sum(total_price) from pizza_sales) as pct_category from pizza_sales group by category 

ppizza_size wise total_sales %
select pizza_size , sum(total_price) * 100 / (select sum(total_price) from pizza_sales) as pct_size from pizza_sales group by size order by pct_size desc

T. Revenue by Pizza name
select pizza_name ,  sum(total_price) as total revenue from pizza_sales
group by pizza_name ,
order by total_revenue desc

top 5 pizza_name 
select pizza_name , sum(total_price) as total_revenue from pizza_sales group by pizza_name order by total_revenue desc
limit 5

bottom 5 pizza_name
select pizza_name , sum(total_price) as total_revenue from pizza_sales group by pizza_name order by total_revenue asc

top 5 Pizza_orders
select pizza_name , count(distinct orders_id) as total_orders from pizza_sales group by pizza_name order by total_orders desc

bottom 5 pizza_orders
select pizza_name , count(distinct order_id) as total_orders from pizza_sales group by pizza_name order by total_orders asc


Insights:

Days
orders are highest on weekends, Friday/Saturday evening

Months
Max orders: July and January

Category
classic category contributes to maximum sales & total orders

Size
Largest size pizza contributes maximum to sales

Revenue
The Thai Chicken contributes to maximum Revenue

Quantity
The classic deluxe pizza contributes to maximum total orders

Toral Orders
The classic deluxe pizza contributes maximum to total orders

Revenue
The Brie Carre  minimum Revenue

Quantity
The Brie Carre contributes to minimum total orders

Toral Orders
The Brie Carre contributes minimum to total orders
