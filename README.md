**Data Storage Solutions for Data Analytics: Sales Analysis**

    ( This repository contains the complete project for the Data Storage Solutions for Data Analytics module. 
      The project undertakes the end-to-end development of a comprehensive business intelligence solution for a grocery sales environment.
      It transforms raw transactional data into actionable intelligence through a robust data warehouse, multi-platform reports, 
      and a comparative analysis of relational and graph database technologies. )


**Project Vision and Goals**

**Vision:** To architect and deploy a complete business intelligence ecosystem that transforms raw operational data into strategic assets.

**Goals:** The key objectives of this project were to:

1. Design a Star Schema Data Warehouse: Model and implement a scalable dimensional model to integrate disparate data sources into a unified repository.

2. Develop an Automated ETL Pipeline: Implement reliable data integration using SQL Server Integration Services (SSIS) for cleansing, transforming, and loading data into the warehouse.

3. Deliver Multi-Platform Reports: Create four operational reports in SSRS for detailed analysis and an interactive Tableau dashboard for exploratory insights.

4. Conduct a Comparative Database Analysis: Implement a parallel data model in Neo4j and compare query performance between SQL and Cypher (CQL)
   to evaluate the strengths of each database technology.

**Business Solution and Architecture:**

This solution was designed to provide critical insights for key stakeholders, including 
Sales Managers monitoring team performance and Marketing Analysts assessing promotional ROI. The architecture follows a standard data warehousing lifecycle.

**1. Data Source**
The project uses the "Grocery Sales Dataset" from Kaggle, a synthetic dataset designed to emulate real-world transactional data.
It is comprised of interconnected CSV files representing sales, products, customers, and employees.


**2. Data Warehouse Design (Star Schema)**
A classic star schema was designed to serve as the single source of truth. This model, centered around a 
FactSales table linked to DimProduct, DimCustomer, DimEmployee, and DimDate dimensions,
was chosen for its simplicity and high-performance querying capabilities, which are critical for analytical tools.


**3. ETL Process (SSIS)**

An automated ETL pipeline was developed using SQL Server Integration Services (SSIS) to extract data from the source CSV files, 
perform transformations, and load it into the data warehouse.

**Dimension Tables:** The DimProduct, DimCustomer, and DimEmployee tables were populated first to ensure referential integrity.
This involved joining multiple source files (e.g., products with categories) using Merge Join transformations and creating full name attributes 
using Derived Column transformations.

**Fact Table:** The FactSales table was populated by looking up the integer-based surrogate keys from the dimension tables
and calculating new measures like GrossSalesAmount and DiscountPercentage on the fly.


**Results:** Reports and Visualizations
The project delivered insights through two distinct platforms: SSRS for static operational reports and Tableau for dynamic, exploratory analysis.


**SSRS Reports:**
Four operational reports were built using SQL Server Reporting Services (SSRS). A key insight from these reports is the 
Top 10 Most Sold Products in the U.S., providing clear, actionable data for inventory and marketing management.

**Interactive Tableau Dashboard:**
An interactive dashboard was developed in Tableau to provide a high-level overview of sales performance for management.

**Dashboard Link:** https://public.tableau.com/app/profile/bimal.bimal/viz/CA1_Sales_USA/Dashboard1?publish=yes

**The dashboard includes four key components:**
1. Executive KPI Scorecards: At-a-glance metrics for Total Sales, Quantity Sold, and Total Transactions.
2. Discount Strategy Effectiveness: A combination chart analyzing the financial impact of discounts by correlating sales volume with average order value.
3. Geographic Sales Map: A bubble map visualizing sales hotspots across U.S. cities, using size for sales volume and color for average order value.
4. Employee Performance Leaderboard: A bar chart that ranks employees by sales and compares their performance against a dynamic, user-defined sales target.

**Comparative Analysis: SQL vs. NoSQL (Neo4j)**

A comparative analysis was performed to evaluate the performance of a traditional relational database (SQL Server) against a modern graph database (Neo4j).
Using the classic Northwind database, seven queries were executed in both SQL and Cypher (CQL).

Key Finding: While both databases were efficient for simple queries, the Neo4j graph database significantly outperformed SQL on complex, multi-hop join queries.
For example, finding "Suppliers for a Customer's Products" or "Customers who bought shared products" was computationally expensive and slow in SQL 
but highly efficient and intuitive to write in Cypher.  This demonstrates the power of graph databases for analyzing highly connected data.

**Challenges and Key Learnings**

Several data quality and performance challenges were addressed during the ETL process:
1. Handling Missing Values: The SalesDate column contained NULL values, which had to be isolated using a conditional split to prevent data loss
and ensure only valid transactions populated the fact table.
2. Data Type Alignment: Careful configuration of data conversion transformations in SSIS was required to manage mismatches between flat-file source types and SQL Server destination types,
preventing data truncation errors.
3.Performance Scaling for SSRS: The source sales.csv file (6.6 million rows) was too large for performant report generation in SSRS.
A pragmatic data scaling strategy was implemented by creating a smaller, representative subset of 5,000 rows specifically for SSRS development.

**How to Navigate This Repository**

1. /Dataset: Contains the source CSV files used for the project.

2. /ETL_SSIS: Includes the Microsoft SQL Server Integration Services (SSIS) project files for the ETL pipeline.

3. /Neo4j & SQL: Contains the CQL and SQL scripts used for the comparative database analysis.

4. /Reports: Contains Technical Report, Individual Contribution Report, CQL v/s SQL Report and the four operational reports created using SSRS.

5. /TableauWorksheet: The Tableau workbook file and screenshot of the dashboard for the interactive dashboard.

6. /Presentation: The presentation slides summarizing the project.

**Team Members**
1. Bimal C Biju - 20059265 
2. Sri Sandeep Sakthivel - 20065749 
3. Harsha Choudhary - 20044005 
