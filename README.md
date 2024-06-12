# Pizza-Sales-Visualization
This project aims to analyze pizza sales data using SQL for data querying and Power BI for data visualization. The goal is to provide insights into sales performance, customer preferences, and trends over time.

Pizza Sales Analysis
Table of Contents

    Introduction
    Project Structure
    Dataset
    Installation
    Usage
    SQL Queries
    Power BI Dashboard
    Contributing
    License
    Acknowledgements
    Contact

Introduction

This project aims to analyze pizza sales data using SQL for data querying and Power BI for data visualization. The goal is to provide insights into sales performance, customer preferences, and trends over time.
Project Structure

    data/: Contains the pizza sales dataset (CSV, Excel, or other formats).
    sql/: Contains SQL scripts for data extraction and transformation.
    powerbi/: Contains the Power BI dashboard file (.pbix).
    docs/: Contains documentation and additional resources.

Dataset

The dataset includes information about pizza sales, such as:

    Order ID
    Pizza type
    Quantity
    Price
    Order date
    Customer details

Installation
Prerequisites

Ensure you have the following installed:

    SQL Server
    Power BI Desktop
    Git (optional, for cloning the repository)

Steps

    Clone the Repository (optional)

    sh

    git clone https://github.com/your_username/pizza_sales_analysis.git
    cd pizza_sales_analysis

    Set Up the Database
        Import the dataset into your SQL database.
        Run the SQL scripts provided in the sql/ directory to create tables and insert data.

    Open Power BI Dashboard
        Open the Power BI Desktop application.
        Load the Power BI dashboard file (pizza_sales_dashboard.pbix) from the powerbi/ directory.

Usage
Running SQL Queries

    Use the SQL scripts in the sql/ directory to perform various analyses on the pizza sales data.
    Example SQL queries:

    sql

    -- Total sales by pizza type
    SELECT pizza_type, SUM(quantity * price) AS total_sales
    FROM pizza_sales
    GROUP BY pizza_type;

    -- Monthly sales trend
    SELECT DATE_TRUNC('month', order_date) AS month, SUM(quantity * price) AS total_sales
    FROM pizza_sales
    GROUP BY month
    ORDER BY month;

Using the Power BI Dashboard

    Open the Power BI dashboard file (pizza_sales_dashboard.pbix).
    Refresh the data to load the latest sales data from your SQL database.
    Explore various visualizations and reports to gain insights into pizza sales.

SQL Queries

Provide detailed descriptions of the SQL queries used for different analyses. Include the purpose of each query and example results.
Power BI Dashboard
Overview

    Sales Overview: Total sales, average sales per order, etc.
    Sales by Pizza Type: Distribution of sales across different pizza types.
    Time Series Analysis: Monthly/weekly sales trends.
    Customer Analysis: Insights into customer preferences and behavior.

Visualizations

Describe the key visualizations included in the dashboard and what insights they provide.
Contributing

Contributions are welcome! To contribute:

    Fork the Project
    Create your Feature Branch (git checkout -b feature/YourFeature)
    Commit your Changes (git commit -m 'Add some feature')
    Push to the Branch (git push origin feature/YourFeature)
    Open a Pull Request


Problem Statement
We would like to visualize various aspects of our pizza sales data to gain insight and understand key trends. We have indentified the following requirement for creating charts:



 A. KPI(Key Performance Indicator)
 1. Total Revenue
     ```sql
    SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

![pizza sales total revenue](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/4e5fa02c-8a39-4881-b0b4-9313ad2f470f)

 2. Average Order Value
    ```sql
    SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
![Average Order Value](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/0eff76b3-8a5e-49b4-94a3-0b737166a398)

 3. Total Pizza Sold
     ```sql
    SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales

![Total Pizzas Sold](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/8d22b13e-c409-4c1e-9d87-4a0d40ec188b)

 4. Total Orders
    ```sql
    SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales

![Total Orders](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/fd6d26c4-3765-4762-8f44-2faff730b4c8)

 5. Pizzas Per Order
     ```sql
    SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
    CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
    AS Avg_Pizzas_per_order
    FROM pizza_sales

![Average Pizzas Per Order](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/7b226440-0328-4be5-bd37-2f3ecb2b90d8)


B. Daily Trends for Total Orders
   ```sql
    SELECT * FROM pizza_sales

    SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
    FROM pizza_sales
    GROUP BY DATENAME(DW, order_date)
```
![Daily Trends for Total Orders](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/56539569-4dd5-44c0-8670-cb660c2871c8)



C. Monthly Trends for Orders
```sql
    select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
    from pizza_sales
    GROUP BY DATENAME(MONTH, order_date)Output
```
![Monthly Trend for Orders](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/bee2c3d5-066e-41ee-b8f0-b46d56619f74)



D. % of Sales by Pizza Category
```sql
    SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
    CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
    FROM pizza_sales
    GROUP BY pizza_category
```
![% of Sales by Pizza Category](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/e4652bbe-a198-4444-ae33-1183239b99d9)



E. % of Sales by Pizza Size
```sql
    SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
    CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
    FROM pizza_sales
    GROUP BY pizza_size
    ORDER BY pizza_size
```
![% of Sales by Pizza Size](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/8af03940-579a-4bcf-b52c-14fe8dd440c2)



F. Total Pizzas Sold by Pizza Category
```sql
    SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
    FROM pizza_sales
    WHERE MONTH(order_date) = 2
    GROUP BY pizza_category
    ORDER BY Total_Quantity_Sold DESC
```
![Total Pizzas Sold by Pizza Category](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/3e945859-49cf-43eb-a30f-c9c272789026)



G. Top 5 Pizzas by Revenue
```sql
    SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Revenue DESC
```
![Top 5 Pizzas by Revenue](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/19c1b138-99ed-4a2c-a766-17c8cd2d1baf)



H. Bottom 5 Pizzas by Revenue
```sql
    SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Revenue ASC
```
![Bottom 5 Pizzas by Revenue](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/350f26bf-3819-4ab6-85ca-e1e99a52a388)



I. Top 5 Pizzas by Quantity
```sql
    SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Pizza_Sold DESC
```
![Top 5 Pizzas by Quantity](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/913f80f9-ba8e-4d49-af3d-a4e15acd68b7)



J. Bottom 5 Pizzas by Quantity
```sql
    SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Pizza_Sold ASC
```
![Bottom 5 Pizzas by Quantity](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/ae50546d-c5e4-42da-9380-ebe37b399e10)



K. Top 5 Pizzas by Total Orders
```sql
    SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders DESC
```
![Top 5 Pizzas by Total Orders](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/01ebe542-1e12-481a-a441-d8a9885bd26e)



L. Bottom 5 Pizzas by Total Orders
```sql
    SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders ASC
```
![Bottom 5 Pizzas by Total Orders](https://github.com/nguyen-william/Pizza-Sales-Visualization/assets/77467480/abd06af5-0d40-431f-aa01-5f8da0ead4cf)

