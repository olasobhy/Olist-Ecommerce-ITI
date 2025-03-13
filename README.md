# Olist-Ecommerce-ITI 

## Overview
Welcome! This project focuses on the **design and implementation of a database and data warehouse** for Olist, a Brazilian e-commerce platform. It aims to provide a structured approach for managing transactional data, supporting efficient query processing, and enabling advanced business intelligence solutions.

The dataset used in this project is a **Brazilian e-commerce public dataset** of orders made at Olist Store. It contains information on **100,000 orders** from **2016 to 2018** across multiple marketplaces in Brazil.

## Project Goals
- **Design and implement a relational database** (OLTP) to store and manage transactions efficiently.
- **Implement stored procedures, triggers, and views** to ensure data consistency and optimize performance.
- **Develop a data warehouse** (OLAP) for business intelligence and analytics.
- **Perform ETL processes** (Extract, Transform, Load) to clean, integrate, and prepare data for analysis.
- **Develop an SSAS Tabular Model** for multi-dimensional analysis and advanced reporting.
- **Create dashboards and reports using SSRS, Power BI, Excel, and Tableau** for data visualization and decision-making.

## Project Structure

## Database Design
### Entity-Relationship Diagram (ERD)
![ERD](https://github.com/dinaibrahim6/Olist-Ecommerce-ITI/blob/main/Database/ERD_and_Mapping/ERD.PNG)

### Mapping ERD to Relational Model
![Relational Model](https://github.com/dinaibrahim6/Olist-Ecommerce-ITI/blob/main/Database/ERD_and_Mapping/Olist%20E-commerce%20Mapping%20Schema.png)

### Database Diagram
![Database Diagram](https://github.com/dinaibrahim6/Olist-Ecommerce-ITI/blob/main/Database/ERD_and_Mapping/DB_Diagram.PNG)

## Database Programming

### Views
#### Sales and Product Performance Views
- `vw_sales_by_category`: Aggregates total sales by product category.
- `vw_product_performance`: Tracks sales, total orders, and units sold for each product.
- `vw_seller_performance`: Summarizes total revenue and item count per seller.
- `vw_top_selling_products`: Lists the top 10 best-selling products by revenue.

#### Time-Based Sales Summaries
- `vw_monthly_sales`: Summarizes total sales and order count per month.
- `Yearly_Sales_Summary`: Provides a yearly breakdown of orders, revenue, and average order value for delivered orders.

#### Customer and Order Insights
- `vw_customer_purchase`: Tracks customer purchases, including total spending and order details.
- `vw_high_value_customer`: Identifies customers who have spent over a defined threshold.
- `vw_pending_orders`: Lists orders that are still in processing or created status.

#### Delivery and Payment Analytics
- `vw_avg_delivery_days`: Calculates the average delivery time per seller.
- `vw_payment_summary`: Summarizes payment methods and total payment values.

#### Seller Performance Insights
- `vw_Top_sellers`: Lists the top 10 sellers by total revenue and items sold.

### Stored Procedures
- **GenerateSales**: Generates a sales report within a specified date range.

- **CustomerDemographics**: Provides demographic insights based on customer location and login type.

- **Product Performance**: Analyzes the sales performance of a specific product.
  
- **Seller Performance**: Evaluates a seller's performance based on orders, revenue, and units sold.
  
- **Customer Satisfaction**: Provides insights into customer satisfaction based on review scores.
  
- **Payment Methods**: Summarizes the usage of different payment methods within a given timeframe.
  
- **Customer Category**: Categorizes customers based on their login type within a given timeframe.
  
- **Monthly Sales**: Generates a sales report for a specific year, broken down by month.
  
- **Top-Selling Products**: Retrieves the top N selling products based on sales volume.
  
- **Insert Order with Data Validation**: Ensures customer existence before inserting an order.

### Triggers
- **Prevent Orders with Zero Value** (`prevent_order_zero_value`)
   - Ensures orders have a positive total value; rolls back transactions if value is zero or negative.

- **Prevent Custom Payment Values ≤ 10% of Order Value** (`prevent_wrong_payment`)
   - Ensures that a custom payment value is at least 10% of the total order value.

- **Enforce Review Creation After Order Completion** (`Review_After_Delivery`)
   - Ensures that reviews can only be created for completed orders.

- **Track Late Deliveries** (`log_late_deliveries`)
   - Logs late deliveries in `Late_Delivery_Log` if the actual delivery date exceeds the estimated delivery date.

- **Prevent Order Deletion** (`prevent_order_deletion`)
   - Prevents deletion of records from the Orders table.

- **Prevent Over-Payment** (`Prevent_Over_Payment`)
   - Ensures total payments for an order do not exceed the total order price.
