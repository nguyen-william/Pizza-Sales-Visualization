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
1. Daily Trends for Total Orders:
2. Monthly Trend for Total Orders:
3. Percentage of Sales by pizza category
4. Percentage of Sales by Pizza sales
5. Total Pizzas Sold by Pizza Category
6. Top 5 Best Sellers by Revenue, total quantity and total orders
7. Bottom 5 sellers by Revenue Total Quantity and Total Orders
