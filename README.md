# SQL Data Analysis Project – Sales Dataset

## 📌 Project Overview

This project showcases my ability to work with **large datasets (2000+ rows, 20 columns)** using **PostgreSQL**.
It highlights expertise in **data modeling, cleaning, querying, and generating actionable business insights**.

The dataset represents **sales transactions** with details such as orders, customers, products, regions, shipping, and returns.

---

## 🛠️ Tools & Technologies

* **Database:** PostgreSQL
* **Language:** SQL
* **Dataset Size:** 2000+ rows, 20 columns
* **Output:** Queries, insights, and an exported CSV

---

## 🔍 Project Workflow

1. **Data Modeling**

   * Created a relational table structure for the sales dataset.
   * Defined data types for each field (numeric, varchar, date).

2. **Data Exploration**

   * Verified table population with row counts.
   * Previewed sample rows for validation.

3. **Data Cleaning**

   * Checked for duplicates.
   * Standardized categorical values (regions, product categories).
   * Handled missing values logically.

4. **SQL Analysis & Insights**

   * Total sales per category.
   * Average profit across regions.
   * Revenue breakdown by product category.
   * Top 5 customers by lifetime value.
   * Return analysis and percentages.
   * Monthly sales trends.

5. **Export**

   * Final cleaned dataset exported as **CSV** for reporting and sharing.

---

## 📈 Core SQL Queries

```sql
-- Create the sales_data table
CREATE TABLE sales_data (
    order_id INT,
    customer_id INT,
    product_id INT,
    product_name VARCHAR(50),
    category VARCHAR(50),
    quantity INT,
    price NUMERIC(10,2),
    discount INT,
    order_date DATE,
    ship_date DATE,
    region VARCHAR(50),
    country VARCHAR(50),
    payment_method VARCHAR(50),
    shipping_cost NUMERIC(10,2),
    profit NUMERIC(10,2),
    sales_channel VARCHAR(50),
    return_status VARCHAR(50),
    customer_age INT,
    customer_gender VARCHAR(10)
);

-- Verify dataset load
SELECT COUNT(*) FROM sales_data;

-- Preview sample rows
SELECT * FROM sales_data LIMIT 10;

-- Total Sales per Category
SELECT category, SUM(quantity * price) AS total_sales
FROM sales_data
GROUP BY category
ORDER BY total_sales DESC;

-- Average Profit by Region
SELECT region, ROUND(AVG(profit), 2) AS avg_profit
FROM sales_data
GROUP BY region;

-- Revenue by Product Category
SELECT category, ROUND(SUM(quantity * price), 2) AS total_revenue
FROM sales_data
GROUP BY category
ORDER BY total_revenue DESC;

-- Top 5 Customers by Lifetime Value
SELECT customer_id, ROUND(SUM(quantity * price), 2) AS lifetime_value
FROM sales_data
GROUP BY customer_id
ORDER BY lifetime_value DESC
LIMIT 5;

-- Returns Analysis
SELECT return_status, COUNT(*) AS total_orders,
       ROUND(100.0 * COUNT(*) / SUM(COUNT(*)) OVER(), 2) AS percentage
FROM sales_data
GROUP BY return_status;

-- Monthly Sales Trend
SELECT TO_CHAR(order_date, 'YYYY-MM') AS month,
       ROUND(SUM(quantity * price), 2) AS monthly_sales
FROM sales_data
GROUP BY month
ORDER BY month;
```

---

## 📂 Repository Structure

```
├── data/
│   └── sales_data.csv        # Cleaned dataset exported from PostgreSQL
├── queries/
│   └── analysis_queries.sql  # SQL queries used for analysis
└── README.md                 # Project documentation
```

---

## 🎯 Key Skills Demonstrated

* SQL Table Creation & Schema Design
* Data Cleaning & Preparation
* Aggregations, Grouping & Window Functions
* Business Analysis (Revenue, Profit, Returns, Customer Value)
* Data Export & Documentation

---

## 📬 Contact

For collaborations or opportunities in **Data Analysis** or **Data Entry**, feel free to reach out:

**Ehimenmen Akhabue-Hilltop**
📧 [ehihilltop73@gmail.com](mailto:ehihilltop73@gmail.com)
🌍 LinkedIn: www.linkedin.com/in/akhabue-hilltop-ehimenmen-a56a9a35a

