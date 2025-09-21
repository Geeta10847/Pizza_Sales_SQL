# Pizza_Sales_SQL

## Project Overview

**Project Title:** Pizza Sales Analysis  
**Level:** Beginner  
**Database:** pizza_sales_SQL

This project demonstrates SQL skills and techniques commonly used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing data cleaning, exploratory data analysis, and answering business questions with SQL.

## Objectives

- **Set up a pizza sales database:** Create and populate a retail sales database with the provided sales data.
- **Data Cleaning:** Identify and remove records with missing or null values.
- **Exploratory Data Analysis (EDA):** Perform basic EDA to understand the dataset.
- **Business Analysis:** Use SQL to answer business questions and derive insights from sales data.

## Project Structure

### 1. Database Setup

- **Database Creation:** Create a database named `pizza_sales_SQL`.
- **Table Creation:** A table named `pizza_sales` is used to store sales data. Columns include:  
  `pizza_id, order_id, pizza_name_id, quantity, order_date, order_time, unit_price, total_price, pizza_size, pizza_category, pizza_name`.

### 2. KPI Queries

**A. Total Revenue**
```sql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```

**B. Average Order Value**
```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
```

**C. Total Pizzas Sold**
```sql
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
```

**D. Total Orders**
```sql
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;
```

**E. Average Pizzas Per Order**
```sql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order FROM pizza_sales;
```

### 3. Trend Analysis

**Daily Trend for Total Orders**
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);
```

**Monthly Trend for Orders**
```sql
SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, order_date);
```

### 4. Sales Distribution

**% of Sales by Pizza Category**
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
```

**% of Sales by Pizza Size**
```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size;
```

### 5. Best/Worst Sellers

**Top 5 Pizzas by Revenue**
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC;
```

**Bottom 5 Pizzas by Revenue**
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC;
```

**Top 5 Pizzas by Quantity**
```sql
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC;
```

**Bottom 5 Pizzas by Quantity**
```sql
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC;
```

**Top 5 Pizzas by Total Orders**
```sql
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC;
```

**Bottom 5 Pizzas by Total Orders**
```sql
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC;
```

> **Tip:** Use WHERE clause to filter by pizza_category or pizza_size, e.g.:
```sql
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC;
```

## Problem Statement

Analyze key business indicators for the pizza sales data:

1. Total Revenue
2. Average Order Value
3. Total Pizzas Sold
4. Total Orders
5. Average Pizzas Per Order

## Charts Requirement

- **Percentage of Sales by Pizza Size:** Pie chart
- **Total Pizzas Sold by Pizza Category:** Funnel chart
- **Top 5 Best Sellers by Revenue, Quantity, Orders:** Bar chart
- **Bottom 5 Best Sellers by Revenue, Quantity, Orders:** Bar chart

## Files

- [`PIZZA_SALES_SQL_QUERIES_pro2.pdf`](PIZZA_SALES_SQL_QUERIES_pro2.pdf): Contains detailed SQL queries.
- [`pizza_sales_excel_file.xlsx`](pizza_sales_excel_file.xlsx): Raw sales data in Excel format.

---

Feel free to explore the queries and customize them for deeper analysis!# ***Pizza_Sales_SQL***


