# ***Pizza_Sales_SQL***

Project Overview
**Project Title**: Pizza Sales Analysis
**Level**: Beginner
**Database**:pizza_sales_SQL

This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. This project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.

Objectives
**Set up a pizza sales database**: Create and populate a retail sales database with the provided sales data.
**Data Cleaning**: Identify and remove any records with missing or null values.
**Exploratory Data Analysis (EDA)**: Perform basic exploratory data analysis to understand the dataset.
**Business Analysis**: Use SQL to answer specific business questions and derive insights from the sales data.

##Project Structure

##1. Database Setup
**Database Creation**: The project starts by creating a database named pizza_sales_SQL.
**Table Creation**: A table named pizza_sales is created to store the sales data. The table structure includes columns for pizza_id,	order_id,	pizza_name_id,	quantity,	order_date,	order_time,	unit_price,	total_price,	pizza_size,	pizza_category,	pizza_ingredients,	Aq.
<img width="1747" height="25" alt="image" src="https://github.com/user-attachments/assets/35963253-7bd7-4586-b0cb-fa4558d1aaff" />



A. KPI’s
1. Total Revenue:
SELECT 
   SUM(total_price) AS Total_Revenue 
FROM pizza_sales;
 
2. Average Order Value
SELECT 
   (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value 
FROM pizza_sales;
 
3. Total Pizzas Sold
SELECT 
    SUM(quantity) AS Total_pizza_sold
 FROM pizza_sales;
 
4. Total Orders
SELECT
   COUNT(DISTINCT order_id) AS Total_Orders 
FROM pizza_sales;
 
5. Average Pizzas Per Order
SELECT 
   CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
   CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
      AS Avg_Pizzas_per_order
FROM pizza_sales;
 

B. Daily Trend for Total Orders
SELECT 
    DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id)
      AS total_orders 
FROM pizza_sales;
    GROUP BY DATENAME(DW, order_date)
Output:
 

C. Monthly Trend for Orders
select 
     DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id)      as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date);


Output
 

D. % of Sales by Pizza Category
SELECT 
  pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
  CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
Output
 

E. % of Sales by Pizza Size

SELECT 
   pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
   CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales)
 AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size;
Output
 

F. Total Pizzas Sold by Pizza Category
SELECT
   pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC;
Output
 

G. Top 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
 
H. Bottom 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
 

I. Top 5 Pizzas by Quantity

SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
Output
 

J. Bottom 5 Pizzas by Quantity
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
Output
 

K. Top 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
 

L. Borrom 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
 
NOTE
If you want to apply the pizza_category or pizza_size filters to the above queries you can use WHERE clause. Follow some of below examples
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC

**PROBLEM STATEMENT**

KPI'S REQUIREMENT

We need to analyze key indicators for our pizza sales data to gain insights into our business performance. Specifically, we want to calculate the following metrics:

1. Total Revenue: The sum of the total price of all pizza orders.

2. Average Order Value: The average amount spent per order, calculated by dividing the total revenue by the total number of orders.

3. Total Pizzas Sold: The sum of the quantities of all pizzas sold.

4. Total Orders: The total number of orders placed.

5. Average Pizzas Per Order: The average number of pizzas sold per order, calculated by dividing the total number of pizzas sold by the total number of orders.


**CHARTS REQUIREMENT**

4.Percentage of Sales by Pizza Size:

Generate a pie chart that represents the percentage of sales attributed to different pizza sizes. This chart will help us understand customer preferences for pizza sizes and their impact on sales.

5.Total Pizzas Sold by Pizza Category:

Create a funnel chart that presents the total number of pizzas sold for each pizza category. This chart will allow us to compare the sales performance of different pizza categories.

6.Top 5 Best Sellers by Revenue, Total Quantity and Total Orders

Create a bar chart highlighting the top 5 best-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will help us identify the most popular pizza options.

7. Bottom 5 Best Sellers by Revenue, Total Quantity and Total Orders

Create a bar chart showcasing the bottom 5 worst-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will enable us to identify underperforming or less popular pizza options.



