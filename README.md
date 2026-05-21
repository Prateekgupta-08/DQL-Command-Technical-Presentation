# 📊 DQL SELECT Command — Real-Time Use Cases

> A beginner-friendly presentation on SQL's most-used command, with real-world examples from companies like **Amazon**, **Netflix**, and food delivery apps.

---

## 📁 Repository Contents

```
├── Prateek_SQL_DQL_Select_Command.pptx   # Main presentation file
└── README.md                              # This file
```

---

## 🎯 About This Presentation

This is a **2-minute team knowledge share** slide deck that explains the **DQL SELECT command** in SQL — what it is, how it works, and how top companies use it every day to read and analyze data.

**Format:** PowerPoint (.pptx)  
**Audience:** Beginners / Team knowledge sharing  
**Duration:** ~2 minutes talk time  

---

## 📋 Slide-by-Slide Overview

### Slide 1 — Title
*DQL SELECT Command & Real-Time Use Cases*  
Introduction to the session as a quick team knowledge share.

---

### Slide 2 — What is DQL?
- **DQL** stands for **Data Query Language**
- It is the part of SQL used **only to READ data** — never inserts, updates, or deletes
- There is only **one DQL command**: `SELECT`
- Analogy: Think of a database as a huge Excel sheet — `SELECT` is your search and filter button

---

### Slide 3 — Basic Syntax

```sql
SELECT  column1, column2
FROM    table_name
WHERE   condition           -- filtering
ORDER BY column ASC|DESC   -- sorting
```

| Clause | Purpose |
|--------|---------|
| `SELECT` | Choose which columns to retrieve |
| `FROM` | Specify which table to look in |
| `WHERE` | Filter rows matching a condition |
| `ORDER BY` | Sort results (ASC = low→high, DESC = reverse) |

---

### Slide 4 — SELECT with JOIN

Real query — get customer name and their order details:

```sql
SELECT  c.name, c.city, o.order_id, o.amount, o.status
FROM    customers c
JOIN    orders o  ON  c.customer_id = o.customer_id
WHERE   o.status = 'Delivered'  AND  c.city = 'Mumbai';
```

| Join Type | Description |
|-----------|-------------|
| `INNER JOIN` | Only rows that match in **both** tables |
| `LEFT JOIN` | All rows from left table + matching rows from right (nulls if no match) |
| `RIGHT JOIN` | All rows from right table + matching rows from left (nulls if no match) |

---

### Slide 5 — Real Example: Food Delivery App

**Scenario:** Manager asks — *"Show me all orders above ₹300 placed in Bengaluru today, sorted by amount."*

```sql
SELECT  order_id, customer_name, restaurant, amount, status
FROM    orders
WHERE   city = 'Bengaluru'  AND  amount > 300  AND  order_date = CURDATE()
ORDER BY amount DESC;
```

**Sample Output:**

| order_id | customer_name | restaurant | amount | status |
|----------|---------------|------------|--------|--------|
| 5021 | Priya Sharma | Meghana Foods | ₹820 | Delivered |
| 5035 | Rahul Nair | CTR Malleswaram | ₹560 | Delivered |
| 5048 | Ananya Reddy | Truffles | ₹430 | Out for delivery |
| 5062 | Vikram Joshi | Vidyarthi Bhavan | ₹320 | Delivered |

---

### Slide 6 — Amazon: E-Commerce Queries

**Top Selling Products:**
```sql
SELECT product_name, SUM(quantity_sold) AS total_sold
FROM orders
WHERE order_date >= '2024-01-01'
GROUP BY product_name
ORDER BY total_sold DESC
LIMIT 10;
```

**Customers with Large Orders:**
```sql
SELECT customer_id, name, email, total_amount
FROM customers
WHERE total_amount > 5000
  AND country = 'India'
ORDER BY total_amount DESC;
```

> 💡 **Use case:** Amazon uses these queries to power product recommendations and customer dashboards.

---

### Slide 7 — Netflix: Streaming Analytics

**Most Watched Content by Region:**
```sql
SELECT content_title, region, COUNT(*) AS views
FROM streaming_logs
WHERE streamed_at BETWEEN '2024-01-01' AND '2024-12-31'
GROUP BY content_title, region
ORDER BY views DESC
LIMIT 20;
```

**User Watch History:**
```sql
SELECT u.username, c.title, s.watch_duration, s.completed
FROM users u
JOIN sessions s ON u.user_id = s.user_id
JOIN content c ON s.content_id = c.content_id
WHERE u.subscription = 'Premium'
ORDER BY s.streamed_at DESC;
```

> 💡 **Use case:** Netflix queries streaming data to fuel its recommendation engine and analyze content performance.

---

### Slide 8 — Thank You

---

## 🧠 Key Takeaways

- `SELECT` is the **only DQL command** and the most-used command in SQL
- It **never modifies data** — safe to run anytime
- Combine with `WHERE`, `ORDER BY`, `GROUP BY`, `JOIN` for powerful queries
- Used daily by companies like **Amazon, Netflix, Uber, Spotify** to drive decisions

---

## 🚀 How to View the Presentation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   ```

2. **Open the file:**
   - Download `Prateek_SQL_DQL_Select_Command.pptx`
   - Open with **Microsoft PowerPoint**, **Google Slides** (upload), or **LibreOffice Impress**

---

## 👤 Author

**Prateek**  
SQL Knowledge Share Session  

---

## 📄 License

This presentation is shared for educational purposes. Feel free to use, share, or build upon it with attribution.
