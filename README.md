# 💡 Cisco Stock SQL Case Study

## 🌟 Overview
This SQL project analyzes historical stock data for Cisco Systems Inc. (CSCO) to extract insights on performance, volatility, and trading activity. It was built using a SQLite database, real-world financial data, and SQL queries.

---

## 📊 Dataset
- **File:** `CSCO.csv`
- **Columns:**
  - `Date`
  - `Open`, `High`, `Low`, `Close`, `Adjusted Close`
  - `Volume`
- **Frequency:** Daily stock prices

---

## 🛠 Tools Used
- **DB Browser for SQLite** – for database setup and SQL queries
- **VS Code** – documentation and version control
- **Git & GitHub** – project hosting
- **Excel / Google Sheets** – optional for visualizations

---

## 🧹 Data Preparation
- Imported `CSCO.csv` into SQLite as the `stock_data` table
- Removed rows with `NULL` in the `Close` column
- Verified formatting and data integrity

---

## 🔍 SQL Analysis & Insights

### 📈 1. Daily Return %
```sql
SELECT 
    Date,
    Close,
    LAG(Close) OVER (ORDER BY Date) AS Prev_Close,
    ROUND(((Close - LAG(Close) OVER (ORDER BY Date)) / LAG(Close) OVER (ORDER BY Date)) * 100, 2) AS Daily_Return_Pct
FROM stock_data;
Exported as: daily_returns.csv
