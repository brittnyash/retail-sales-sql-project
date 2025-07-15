
# Retail SQL Analysis – Portfolio Project

## 🧠 Objective

This project showcases SQL skills in an eCommerce setting using a Kaggle dataset. The data was normalized into three relational tables and queried using clean, single-join SQL syntax to uncover revenue patterns, top customers, and product performance. The goal is to demonstrate strong fundamentals in business-oriented data analysis.

---

## 🗃️ Dataset Structure

| Table         | Description                                       |
|---------------|---------------------------------------------------|
| `customers`   | Customer profile including ID, gender, and age    |
| `products`    | Unique combinations of product category and price |
| `transactions`| Each sale: date, customer, product, quantity, and total amount |

---

## 🔍 Business Questions Answered

| # | Question                                      | SQL Concepts Used            |
|---|-----------------------------------------------|-------------------------------|
| 1 | Which product categories generate the most revenue? | JOIN, GROUP BY, ORDER BY  |
| 2 | Who are the most active buyers?               | GROUP BY, SUM                 |
| 3 | How does revenue vary by day?                 | GROUP BY, DATE                |
| 4 | What’s the average spend by gender?           | JOIN, GROUP BY, AVG           |
| 5 | Which customers are repeat buyers?            | GROUP BY, HAVING, COUNT(DISTINCT) |
| 6 | Which products generate the most revenue?     | GROUP BY, ORDER BY            |

---

## 🧾 SQL Queries

### 1. Total Revenue by Product Category
```sql
SELECT 
    product_category,
    SUM(total_amount) AS total_revenue
FROM products
JOIN transactions ON products.product_id = transactions.product_id
GROUP BY product_category
ORDER BY total_revenue DESC;
```

### 2. Total Quantity Sold by Customer
```sql
SELECT 
    customer_id,
    SUM(quantity) AS total_items_bought
FROM transactions
GROUP BY customer_id
ORDER BY total_items_bought DESC;
```

### 3. Daily Sales Trend
```sql
SELECT 
    date,
    SUM(total_amount) AS daily_revenue
FROM transactions
GROUP BY date
ORDER BY date;
```

### 4. Average Spend by Gender
```sql
SELECT 
    customers.gender,
    AVG(transactions.total_amount) AS avg_spend
FROM customers
JOIN transactions ON customers.customer_id = transactions.customer_id
GROUP BY customers.gender;
```

### 5. Repeat Customers (Multiple Purchase Days)
```sql
SELECT 
    customer_id,
    COUNT(DISTINCT date) AS purchase_days
FROM transactions
GROUP BY customer_id
HAVING purchase_days > 1;
```

### 6. Top Products by Revenue
```sql
SELECT 
    product_id,
    SUM(total_amount) AS revenue
FROM transactions
GROUP BY product_id
ORDER BY revenue DESC;
```

---

## 📈 Visualizations

### 📊 Total Revenue by Product Category
![Revenue by Category](revenue_by_category.png)

### 📈 Daily Revenue Trend
![Daily Revenue Trend](daily_revenue_trend.png)

### 👤 Top 10 Customers by Quantity Purchased
![Top Customers](top_customers_quantity.png)

### 🟣 Revenue Share by Gender
![Revenue by Gender](revenue_by_gender.png)

---

## 💡 Why This Project Stands Out

- Real-world structure (customers, products, transactions)  
- Queries are readable and realistic for interviews  
- Easy to expand with RFM analysis, promotions, or marketing attribution  

---

## 📁 Downloadable Assets

- 📄 [`README.md`](./README_with_charts.md)  
- 📄 [`retail_sql_queries.sql`](./retail_sql_queries.sql)  
- 📄 [`retail_sql_project_walkthrough.pdf`](./retail_sql_project_walkthrough.pdf)  
- 📊 [`retail_products.csv`](./retail_products.csv)  
- 👤 [`retail_customers.csv`](./retail_customers.csv)  
- 🧾 [`retail_transactions.csv`](./retail_transactions.csv)  

---

> Feel free to fork this project and adapt it to your own use case!
