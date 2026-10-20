# 🛒 Zepto E-commerce SQL Data Analysis Project

A SQL data analyst portfolio project built on a Zepto product inventory dataset. Zepto is one of India's fastest-growing quick-commerce companies. The project follows a real analyst workflow in PostgreSQL: setting up the table, exploring the data, cleaning it, and answering business questions on pricing, discounts, stock and revenue.


---

## 📌 Project Overview

- ✅ Created an inventory table and loaded raw e-commerce data
- ✅ Explored categories, stock availability, duplicates and missing values
- ✅ Cleaned invalid records and converted prices from paise to rupees
- ✅ Wrote 8 business-focused SQL queries on discounts, pricing, revenue and inventory weight

---

## 📁 Dataset

Source: Kaggle, Zepto product listings: https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv

Each row is one SKU. Product names can repeat because the same product is listed in different pack sizes, weights or discounts.

| Column | Description |
|--------|-------------|
| `sku_id` | Unique ID for each entry (primary key) |
| `category` | Product category |
| `name` | Product name |
| `mrp` | Maximum retail price (converted from paise to ₹) |
| `discountPercent` | Discount on MRP |
| `availableQuantity` | Units in inventory |
| `discountedSellingPrice` | Price after discount (converted to ₹) |
| `weightInGms` | Product weight in grams |
| `outOfStock` | `true` = out of stock, `false` = in stock |
| `quantity` | Units per package |

---

## 🔧 Project Workflow

### 1️⃣ Table creation

```sql
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150),
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

### 2️⃣ Data import
Imported the CSV into the `zepto` table using pgAdmin's import feature.

### 3️⃣ 🔍 Data exploration
- Counted total rows and previewed sample data
- Checked every column for null values
- Listed distinct product categories
- Compared in-stock vs out-of-stock products
- Found product names that appear under multiple SKUs
- Checked for products with a price of zero

### 4️⃣ 🧹 Data cleaning
- Deleted rows with an MRP or selling price of zero
- Converted `mrp` and `discountedSellingPrice` from paise to rupees

### 5️⃣ 📊 Business analysis

| # | Question |
|---|----------|
| Q1 | Top 10 best-value products by discount percentage |
| Q2 | High-MRP products (above ₹300) that are out of stock |
| Q3 | Estimated revenue for each category |
| Q4 | Products with MRP above ₹500 and discount below 10% |
| Q5 | Top 5 categories with the highest average discount |
| Q6 | Price per gram for products of 100g and above, sorted by best value |
| Q7 | Products grouped by weight into Low, Medium and Bulk |
| Q8 | Total inventory weight per category |

---

## 🔑 Key Findings

- [Out-of-stock share, from your stock query: X% of products]
- [Category with the highest estimated revenue (Q3)]
- [Category with the highest average discount (Q5)]
- [Best value-for-money product by price per gram (Q6)]


---

## 🛠️ How to Run

1. Clone the repository
```bash
   git clone https://github.com/Anil-analytics-maker/zepto-inventory-sql-analysis.git
```
2. Create a database in pgAdmin or any PostgreSQL client
3. Run `01_create_table.sql` to create the table
4. Import the dataset CSV into the `zepto` table (save as UTF-8 if you get an encoding error)
5. Run `02_analysis.sql` for exploration, cleaning and analysis

> ⚠️ Run the paise-to-rupees update only once, otherwise prices are divided by 100 again.

---

## 🧰 Tools Used

PostgreSQL 18 • pgAdmin 4 • GitHub

---

## 👨‍💻 About Me

Hi, I'm **Anil**, a B.Tech Civil Engineering student at Delhi Technological University, building a career in data analytics with SQL, Python, Excel and Power BI.

## 🚀 Let's Connect

- 💼 LinkedIn: https://www.linkedin.com/in/anildtu27
- 💻 GitHub: https://github.com/Anil-analytics-maker
- 📧 Email: anil_23bt012@dtu.ac.in

  
