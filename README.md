# 🛒 Grocery Store Management System — SQL Project

## 📌 Project Overview

The **Grocery Store Management System** is a SQL-based database project designed to simulate and analyze the operations of a retail grocery store.

The project uses a **relational database** to manage information about suppliers, products, categories, employees, customers, orders, and order details.

The main objective of this project is to use SQL queries to extract meaningful business insights from transactional data and understand customer behavior, product performance, sales trends, supplier contribution, and employee performance.

---

## 🎯 Project Objectives

- Design and manage a relational grocery store database.
- Understand relationships between different business entities.
- Store and manage customer, product, supplier, employee, and order information.
- Use SQL queries to analyze sales and customer behavior.
- Identify top-performing customers and products.
- Analyze revenue by product, category, and supplier.
- Analyze employee performance.
- Identify sales and order trends.
- Generate meaningful business insights from the data.

---

## 🗂️ Database Schema

The database consists of **7 tables**:

| Table | Description | Rows |
|---|---|---:|
| `supplier` | Stores supplier information | 5 |
| `categories` | Stores product categories | 5 |
| `employees` | Stores employee information | 10 |
| `customers` | Stores customer information | 200 |
| `products` | Stores grocery products | 50 |
| `orders` | Stores customer orders | 300 |
| `order_details` | Stores products and quantities within each order | 600 |

---

## 🔗 Table Relationships

The database follows a relational structure with the following relationships:

- **Supplier → Products**: One supplier can supply many products.
- **Categories → Products**: One category can contain many products.
- **Customers → Orders**: One customer can place many orders.
- **Employees → Orders**: One employee can process many orders.
- **Orders → Order Details**: One order can contain multiple order details.
- **Products → Order Details**: One product can appear in multiple order details.

The `order_details` table connects orders and products and allows analysis of product quantities, prices, and revenue.

---

## 🛠️ Technologies Used

- **MySQL**
- **MySQL Workbench**
- SQL

### SQL Concepts Used

- DDL
- DML
- Primary Keys
- Foreign Keys
- Constraints
- JOINs
- GROUP BY
- HAVING
- Aggregate Functions
- Subqueries
- CASE statements
- ORDER BY
- LIMIT
- Date Functions
- String-to-Date Conversion
- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()
- DISTINCT

---

## 📊 Business Analysis

The project analyzes the grocery store from multiple business perspectives.

### 👥 Customer Analysis

The project answers questions such as:

- How many unique customers placed orders?
- Which customers placed the highest number of orders?
- How much did each customer spend?
- What is the average purchase value per customer?
- Who are the top 5 customers by total purchase amount?

### 🛍️ Product Analysis

The project analyzes:

- Number of products in each category.
- Average product price by category.
- Products with the highest sales volume.
- Products generating the highest revenue.
- Sales performance by category and supplier.

### 📈 Sales & Order Analysis

The project analyzes:

- Total number of orders.
- Average order value.
- Orders by date.
- Monthly order and revenue trends.
- Weekday vs weekend sales patterns.

### 🚚 Supplier Analysis

The project analyzes:

- Total number of suppliers.
- Number of products supplied by each supplier.
- Average product price by supplier.
- Revenue contribution by supplier.

### 👨‍💼 Employee Analysis

The project analyzes:

- Number of employees who processed orders.
- Orders handled by each employee.
- Total sales value processed by employees.
- Average order value handled by each employee.

---

## 🔍 Key SQL Queries

Some of the important SQL analyses performed in the project include:

### Top Customers by Purchase Amount

```sql
SELECT c.cust_name,
       SUM(od.total_price) AS Total_Revenue
FROM customers c
JOIN orders o
    ON c.cust_id = o.cust_id
JOIN order_details od
    ON o.ord_id = od.ord_id
GROUP BY c.cust_id
ORDER BY Total_Revenue DESC
LIMIT 5;
