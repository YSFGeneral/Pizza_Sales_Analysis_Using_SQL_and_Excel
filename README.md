![](pizza3.jpeg)
# Pizza_Sales_Analysis_Using_SQL_and_Excel

## Project Overview
The Pizza Sales Analysis project aims to analyze and visualize the sales data of a pizza business. The analysis helps identify key performance indicators (KPIs), sales trends, and top-performing products. The project leverages SQL for data extraction and Excel for data cleaning, processing, and visualization. The final output is a comprehensive dashboard that provides actionable insights for business decision-making.

### Tools and Software Used
-	Microsoft Office/ Excel – 2019
-	MS SQL Server 19
-	Microsoft SQL Server Management Studio – 19.2

### Key Performance Indicators (KPIs)
  **Total Revenue**
o	SQL Query:
sql
Copy code
SELECT SUM(total_price) AS Total_Revenue
FROM pizza_sales;

...

	**Average Order Value**
o	SQL Query:
sql
Copy code
SELECT SUM(total_price) / COUNT(DISTINCT order_id) AS Avg_Order_Value
FROM pizza_sales;

...

	**Total Pizzas Sold**
o	SQL Query:
sql
Copy code
SELECT SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales;

...

	**Total Orders**
o	SQL Query:
sql
Copy code
SELECT COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales;

...

	**Average Pizzas Per Order**
o	SQL Query:
sql
Copy code
SELECT SUM(quantity) / COUNT(DISTINCT order_id) AS Avg_Pizzas_Per_Order
FROM pizza_sales;

...

### Charts and Visualizations Requirements
	**Daily Trend for Total Orders**
o	SQL Query:
sql
Copy code
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS Total_Order
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);

	**Hourly Trend**
o	SQL Query:
sql
Copy code
SELECT DATEPART(HOUR, order_time) AS order_hour, COUNT(DISTINCT order_id) AS Total_Order
FROM pizza_sales
GROUP BY DATEPART(HOUR, order_time)
ORDER BY DATEPART(HOUR, order_time);

	**% of Sales by Pizza Category**
o	SQL Query:
sql
Copy code
SELECT pizza_category, 
       CAST(SUM(total_price) AS DECIMAL(10, 2)) AS Total_Sales, 
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10, 2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;

	**% of Sales by Pizza Size**
o	SQL Query:
sql
Copy code
SELECT pizza_size, 
       CAST(SUM(total_price) AS DECIMAL(10, 2)) AS Total_Sales, 
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10, 2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY PCT DESC;

	**Total Pizzas Sold by Pizza Category**
o	SQL Query:
sql
Copy code
SELECT pizza_category, SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales
GROUP BY pizza_category;

	**Top 5 Best Sellers by Total Pizzas Sold**
o	SQL Query:
sql
Copy code
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizzas_Sold DESC;

	**Bottom 5 Worst Sellers by Total Pizzas Sold**
o	SQL Query:
sql
Copy code
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizzas_Sold ASC;

### Data Cleaning and Visualization in Excel
After performing the SQL queries to extract and calculate the necessary data, the information was imported into Excel for further data cleaning, processing, and visualization.

## Dashboard
![](Pizza_sales_dashboard.png)

## Dashboard Insights
### Key Metrics
-	**Total Revenue:** $817,860
-	**Average Order Value:** $38.31
-	**Total Pizzas Sold:** 49,574
-	**Total Orders:** 21,350
-	**Average Pizzas Per Order:** 2.32
### Busy Days and Times
-	**Days:** Orders are highest on weekends, especially Friday and Saturday.
-	**Times:** Peak order times are from 12-1 PM and after 5-8 PM.
### Sales by Category and Size
-	**Category:** Classic category contributes to the highest sales.
	**Size:** Large size pizzas contribute significantly to total sales.
### Best and Worst Sellers
-	**Best Sellers:** Classic Deluxe and Chicken Pizza are the top sellers.
-	**Worst Sellers:** Brie Carre is the least sold.

## Conclusion
The Pizza Sales Analysis project effectively visualizes the sales data, providing clear insights into trends, top-selling products, and peak sales times. These insights can help in making strategic business decisions, such as optimizing inventory, improving marketing strategies, and enhancing customer satisfaction.
