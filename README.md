
# Retail Sales SQL Analysis Project

This project showcases simple SQL analyses on a retail transaction dataset.  
It is designed for **data analyst** and **eCommerce manager** hiring managers who want to see clear, beginner‑friendly SQL that still delivers valuable insights.

## Dataset

The Kaggle dataset was split into three normalized tables:

| Table | Columns |
|-------|---------|
| **`products`** | `product_id`, `product_category`, `price_per_unit` |
| **`customers`** | `customer_id`, `gender`, `age` |
| **`transactions`** | `transaction_id`, `date`, `customer_id`, `product_id`, `quantity`, `total_amount` |

CSV files are provided in the `/data` folder.

## Key Business Questions & Queries

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
*Insight*: Reveals top‑earning product lines.

### 2. Total Quantity Sold by Customer
```sql
SELECT 
    customer_id,
    SUM(quantity) AS total_items_bought
FROM transactions
GROUP BY customer_id
ORDER BY total_items_bought DESC;
```
*Insight*: Identifies high‑volume buyers.

### 3. Daily Sales Trend
```sql
SELECT 
    date,
    SUM(total_amount) AS daily_revenue
FROM transactions
GROUP BY date
ORDER BY date;
```
*Insight*: Tracks daily revenue peaks and dips.

### 4. Average Spend by Gender
```sql
SELECT 
    customers.gender,
    AVG(transactions.total_amount) AS avg_spend
FROM customers
JOIN transactions ON customers.customer_id = transactions.customer_id
GROUP BY customers.gender;
```
*Insight*: Supports demographic‑based marketing strategies.

## How to Reproduce

1. Clone the repo:
   ```bash
   git clone <your‑repo‑url>
   ```
2. Import the CSVs in `/data` to your SQL environment (e.g., BigQuery, PostgreSQL).
3. Run the queries in `queries.sql` or copy from this README.

---

Feel free to fork or modify this project for your own portfolio!
