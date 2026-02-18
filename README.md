# E-commerce Database (MySQL)

## Overview
This project demonstrates the creation of a simple e-commerce database using MySQL.  
It includes tables for customers, orders, and products, along with sample data and various SQL queries to perform common operations such as joins, aggregations, updates, and schema normalization.

---

## Database Name
`ecommerce`

---

## Tables

### 1. customers
Stores customer details.

| Column   | Type            | Description                          |
|----------|-----------------|--------------------------------------|
| id       | INT (PK, AI)    | Unique identifier for each customer  |
| name     | VARCHAR(100)    | Customer name                        |
| email    | VARCHAR(100)    | Customer email (unique)              |
| address  | VARCHAR(255)    | Customer address                     |

---

### 2. products
Stores product information.

| Column      | Type            | Description                         |
|-------------|-----------------|-------------------------------------|
| id          | INT (PK, AI)    | Unique identifier for each product  |
| name        | VARCHAR(100)    | Product name                        |
| price       | DECIMAL(10,2)   | Product price                       |
| description | TEXT            | Product description                 |
| discount    | DECIMAL(5,2)    | Discount on product (added later)   |

---

### 3. orders
Stores order details placed by customers.

| Column        | Type            | Description                                 |
|---------------|-----------------|---------------------------------------------|
| id            | INT (PK, AI)    | Unique identifier for each order            |
| customer_id   | INT (FK)        | References customers(id)                    |
| order_date    | DATE            | Date when the order was placed              |
| total_amount  | DECIMAL(10,2)   | Total amount of the order                   |

---

## Sample Data
The project includes sample records for:
- Multiple customers
- Several products (Product A, B, C, D)
- Orders with different dates and total amounts

---

## SQL Tasks Covered

### 1. Retrieve customers who placed orders in the last 30 days
Uses JOIN and date filtering with `CURDATE()`.

### 2. Total amount spent by each customer
Uses GROUP BY and SUM aggregation.

### 3. Update product price
Updates the price of Product C to 45.00 using an UPDATE statement.

### 4. Add new column
Adds a `discount` column to the products table using ALTER TABLE.

### 5. Top 3 most expensive products
Orders products by price in descending order and limits results.

### 6. Customers who ordered Product A
(Without normalization) assumes a product reference in orders; otherwise requires normalization.

### 7. Join customers and orders
Retrieves customer names along with their order dates.

### 8. Orders with amount greater than 150
Filters orders based on total_amount.

### 9. Database Normalization
Introduces an `order_items` table to correctly map:
- Orders ↔ Products
- Supports multiple products per order

### 10. Average order total
Calculates the average of all order totals using AVG().

---

## Notes on Normalization
Initially, the database contains only:
- customers
- orders
- products

To properly track which products belong to each order, the database is normalized by adding:
- `order_items` table (order_id, product_id, quantity, price)

This follows best practices for relational database design.

---

## Requirements
- MySQL Server
- MySQL Workbench or any SQL client

---

## How to Run
1. Create the database:
   ```sql
   CREATE DATABASE ecommerce;
   USE ecommerce;
