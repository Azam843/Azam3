# Azam3
Perfect 👍 Here’s a README.md that matches the single SQL file I gave you. You can place both (queries.sql + README.md) in one folder and upload to GitHub.


---

# 📊 SQL Aggregate Functions & Grouping

## 🎯 Objective
Use aggregate functions and grouping to **summarize and analyze data** in SQL.

---

## 🛠 Tools
- DB Browser for SQLite  
- MySQL Workbench  

---

## 🗄 Database Schema
**Database:** `SalesDB`  
**Table:** `Sales`

| Column     | Type          | Description                           |
|------------|--------------|---------------------------------------|
| id         | INT (PK, AI) | Unique identifier for each sale       |
| product    | VARCHAR(50)  | Product name                          |
| category   | VARCHAR(50)  | Product category (Electronics, etc.)  |
| quantity   | INT          | Number of units sold                  |
| price      | DECIMAL(10,2)| Price per unit                        |
| sale_date  | DATE         | Date of sale                          |

---

## 📥 Sample Data
```sql
INSERT INTO Sales (product, category, quantity, price, sale_date) VALUES
('Laptop', 'Electronics', 3, 50000, '2025-09-01'),
('Mouse', 'Electronics', 10, 500, '2025-09-01'),
('Chair', 'Furniture', 5, 2000, '2025-09-02'),
('Table', 'Furniture', 2, 7000, '2025-09-03'),
('Headphones', 'Electronics', 4, 2000, '2025-09-04'),
('Sofa', 'Furniture', 1, 15000, '2025-09-05'),
('Keyboard', 'Electronics', 6, 1000, '2025-09-06'),
('Cupboard', 'Furniture', 3, 12000, '2025-09-07');


---

📌 Queries

1️⃣ Total Sales per Category

SELECT category, SUM(quantity * price) AS total_sales
FROM Sales
GROUP BY category;

2️⃣ Number of Products Sold per Category

SELECT category, COUNT(*) AS total_products
FROM Sales
GROUP BY category;

3️⃣ Average Price of Items per Category

SELECT category, AVG(price) AS avg_price
FROM Sales
GROUP BY category;

4️⃣ Total Quantity Sold per Product (within Category)

SELECT category, product, SUM(quantity) AS total_quantity
FROM Sales
GROUP BY category, product;

5️⃣ Categories with Sales Above 50,000

SELECT category, SUM(quantity * price) AS total_sales
FROM Sales
GROUP BY category
HAVING SUM(quantity * price) > 50000;
