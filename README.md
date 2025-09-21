


# ☕ Coffee Shop Sales Analysis

## 📌 Overview
This end-to-end project analyzes coffee shop sales data to uncover trends in customer behavior, product performance, and outlet engagement. Built using SQL, Excel, Power Query, and Power BI, the dashboard delivers actionable insights for retail decision-makers.

---

## 🎯 Objective
To transform raw transactional data into a dynamic, interactive dashboard that highlights sales performance, product category trends, and outlet-level metrics.

---

## 🛠️ Tools Used
- **SQL** – Data extraction, cleaning, and aggregation  
- **Excel** – Preprocessing and validation  
- **Power Query** – Data transformation  
- **Power BI** – Dashboard design and visualization  
- **Python** – Exploratory analysis and charting (mini projects)

---

## 📊 Key Metrics & Visuals

### 🔹 Top KPIs
- **Total Sales**: `$76.15K` (↓ 6.8% vs LM)
- **Total Orders**: `16,359` (↓ 5.5% vs LM)
- **Total Quantity Sold**: `23,550` (↓ 5.3% vs LM)

### 🔹 Product Category Breakdown
| Category   | Sales     | Quantity |
|------------|-----------|----------|
| Coffee     | $33.41K   | 9.91K    |
| Breakfast  | $14.56K   | 3.91K    |
| Sandwich   | $10.15K   | 2.73K    |
| Tea        | $6.23K    | 2.13K    |
| Pastry     | $5.32K    | 2.01K    |
| Other      | $6.48K    | 2.84K    |

### 🔹 Store Performance
- **Store A**: $27.25K (↓ 7.2% vs LM)  
- **Store B**: $24.18K (↓ 4.8% vs LM)  
- **Store C**: $24.72K (↓ 8.1% vs LM)

### 📸 Screenshots
![Dashboard Overview]<img width="665" height="421" alt="image" src="https://github.com/user-attachments/assets/00440afa-bc1c-4b93-94f8-37cd281b1568" />
![Donut Chart Breakdown]<img width="239" height="184" alt="image" src="https://github.com/user-attachments/assets/9d47b83f-7490-47d0-a450-bd6e835c5c25" /> 
![Donut Chart Breakdown]<img width="237" height="179" alt="image" src="https://github.com/user-attachments/assets/c487a365-7a80-427e-a9d0-8dc1d522865b" />


---

## 🧮 SQL Queries Used

### 🔹 Data Cleaning
```sql
UPDATE blinkit_data
SET Item_Fat_Content =
  CASE
    WHEN Item_Fat_Content IN ('LF', 'low fat') THEN 'Low Fat'
    WHEN Item_Fat_Content = 'reg' THEN 'Regular'
    ELSE Item_Fat_Content
  END;
```

### 🔹 KPIs
```sql
SELECT CAST(SUM(Total_Sales) / 1000000.0 AS DECIMAL(10,2)) AS Total_Sales_Million FROM blinkit_data;
SELECT CAST(AVG(Total_Sales) AS INT) AS Avg_Sales FROM blinkit_data;
SELECT COUNT(*) AS No_of_Orders FROM blinkit_data;
SELECT CAST(AVG(Rating) AS DECIMAL(10,1)) AS Avg_Rating FROM blinkit_data;
```

### 🔹 Pivoted Sales by Fat Content
```sql
SELECT Outlet_Location_Type,
  ISNULL([Low Fat], 0) AS Low_Fat,
  ISNULL([Regular], 0) AS Regular
FROM (
  SELECT Outlet_Location_Type, Item_Fat_Content,
         CAST(SUM(Total_Sales) AS DECIMAL(10,2)) AS Total_Sales
  FROM blinkit_data
  GROUP BY Outlet_Location_Type, Item_Fat_Content
) AS SourceTable
PIVOT (
  SUM(Total_Sales)
  FOR Item_Fat_Content IN ([Low Fat], [Regular])
) AS PivotTable
ORDER BY Outlet_Location_Type;
```

---

## 🧠 Insights & Takeaways
- **Coffee** is the top-selling category, contributing over 40% of total revenue.
- **Weekday sales** outperform weekends by nearly 3x.
- **Store A** leads in revenue but shows the sharpest decline vs last month.
- **Low Fat vs Regular** segmentation reveals outlet-specific preferences.

---

## ✨ Lessons Learned
- How to clean and standardize categorical data using SQL
- Designing intuitive dashboards with conditional formatting and custom icons
- Using Power Query to streamline transformations
- Building storytelling visuals that guide business decisions

---
## 👤 About Me

I’m Anele, a BSc Applied Food & Tech graduate who pivoted into data analytics to solve real-world problems with precision and creativity. After completing a data analyst/scientist course, I delivered two end-to-end client projects using SQL, Excel, Power Query, and Power BI—transforming raw data into actionable dashboards. I’ve also built Python mini-projects for data cleaning and visualization.

My passion lies in making insights beautiful and impactful. I blend technical logic with design aesthetics to create dashboards that not only inform but inspire action. I’m currently open to freelance roles and independent contracts where I can help businesses turn data into clarity.

## 🔗 Connect With Me

- **LinkedIn**: [Anele Promise Ndlovu](https://www.linkedin.com/in/anele-promise-ndlovu-6a8586277)  
- **GitHub**: [Anele4](https://github.com/Anele4)
