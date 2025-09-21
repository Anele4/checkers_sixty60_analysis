
# 🛒 Checkers Sixty60 E-Commerce Sales Analysis

## 📌 Overview
This end-to-end project analyzes sales performance across the Checkers Sixty60 e-commerce platform. Using SQL, Excel, Power Query, and Power BI, the dashboard uncovers trends in outlet performance, product categories, fat content segmentation, and customer ratings. The goal is to deliver actionable insights for retail strategy and operational optimization.

---

## 🎯 Objective
To transform raw transactional data into a dynamic dashboard that highlights key performance indicators, outlet segmentation, and product-level insights for the Checkers Sixty60 platform.

---

## 🛠️ Tools Used
- **SQL** – Data cleaning, aggregation, and KPI extraction  
- **Excel** – Preprocessing and validation  
- **Power Query** – Data transformation  
- **Power BI** – Dashboard design and visualization  
- **DAX** – KPI calculations and matrix logic  
- **Python** – Exploratory analysis (optional mini projects)

---

## 📊 Key Metrics & Visuals

### 🔹 Top KPIs
- **Total Sales**: R1M  
- **Average Sales**: R142  
- **Number of Items**: 5,938  
- **Average Rating**: 4.0

### 🔹 Fat Content Breakdown (Donut Chart)
- **Low Fat** vs **Regular Fat** segmentation
- Sales distribution by fat content across outlet locations

### 🔹 Item Type Performance (Bar Chart)
- Fresh Milk, Flavored Milk, Yogurt, Butter, etc.
- Sales and quantity breakdown by product category

### 🔹 Outlet Size Distribution (Donut Chart)
- Small, Medium, Large outlet segmentation
- Sales contribution by outlet size

### 🔹 Outlet Location Performance (Bar Chart)
- KZN, WC, GP, EC regions
- Sales trends and regional comparisons

### 🔹 Matrix Card: Outlet Type Metrics
- Total Sales, Avg Sales, No. of Items, Avg Rating, Item Visibility
- Outlet Type comparison across all KPIs

---

## 📸 Screenshots
![Dashboard Overview] <img width="793" height="395" alt="image" src="https://github.com/user-attachments/assets/9ea94e00-10c0-441e-a870-51a58edfb0fb" />
![Fat Content Donut]<img width="301" height="206" alt="image" src="https://github.com/user-attachments/assets/dc3c3c99-654e-436c-9ba7-7bf663cf7a2e" />
![Outlet Matrix Card]<img width="215" height="352" alt="image" src="https://github.com/user-attachments/assets/67c7dbf7-d5ae-4604-b794-861836a5a08f" />


---

## 🧮 SQL Queries Used

### 🔹 Data Cleaning
```sql
UPDATE sixty60_data_final
SET Item_Fat_Content =
  CASE
    WHEN Item_Fat_Content IN ('LF', 'low fat') THEN 'Low Fat'
    WHEN Item_Fat_Content = 'reg' THEN 'Regular'
    ELSE Item_Fat_Content
  END;
```

### 🔹 KPI Calculations
```sql
SELECT CAST(SUM(Total_Sales) / 1000000.0 AS DECIMAL(10,2)) AS Total_Sales_Million FROM sixty60_data_final;
SELECT CAST(AVG(Total_Sales) AS DECIMAL(10,1)) AS Avg_Sales FROM sixty60_data_final;
SELECT COUNT(*) AS No_of_Orders FROM sixty60_data_final;
SELECT CAST(AVG(Rating) AS DECIMAL(10,0)) AS Avg_Rating FROM sixty60_data_final;
```

### 🔹 Fat Content by Outlet Location
```sql
SELECT Outlet_Location_Type,
  CAST(SUM(CASE WHEN Item_Fat_Content = 'Low Fat' THEN Total_Sales ELSE 0 END) AS DECIMAL(10,2)) AS Low_Fat,
  CAST(SUM(CASE WHEN Item_Fat_Content = 'Regular' THEN Total_Sales ELSE 0 END) AS DECIMAL(10,2)) AS Regular
FROM sixty60_data_final
GROUP BY Outlet_Location_Type
ORDER BY Outlet_Location_Type;
```

### 🔹 Sales by Outlet Size
```sql
SELECT Outlet_Size,
  CAST(SUM(Total_Sales) AS DECIMAL(10,2)) AS Total_Sales,
  CAST((SUM(Total_Sales) * 100.0 / SUM(SUM(Total_Sales)) OVER()) AS DECIMAL(10,2)) AS Sales_Percentage
FROM sixty60_data_final
GROUP BY Outlet_Size
ORDER BY Total_Sales DESC;
```

### 🔹 All Metrics by Outlet Type
```sql
SELECT Outlet_Type,
  CAST(SUM(Total_Sales) AS DECIMAL(10,2)) AS Total_Sales,
  CAST(AVG(Total_Sales) AS DECIMAL(10,0)) AS Avg_Sales,
  COUNT(*) AS No_Of_Items,
  CAST(AVG(Rating) AS DECIMAL(10,2)) AS Avg_Rating,
  CAST(AVG(Item_Visibility) AS DECIMAL(10,2)) AS Item_Visibility
FROM sixty60_data
GROUP BY Outlet_Type
ORDER BY Total_Sales DESC;
```

---

## 🧠 Insights & Takeaways
- **Low Fat products** dominate in Tier 1 locations, while Regular Fat is more evenly distributed.
- **Fresh Milk** is the top-selling item type, followed by Flavored Milk and Yogurt.
- **Medium-sized outlets** contribute the highest percentage of total sales.
- **KZN region** leads in sales volume, followed by WC and GP.
- **Outlet Type 1** shows the highest average rating and item visibility.

---

## ✨ Lessons Learned
- How to standardize categorical data using SQL CASE statements
- Designing matrix cards and conditional formatting in Power BI
- Using DAX to calculate dynamic KPIs and segment metrics
- Building storytelling visuals that guide strategic decisions

---

## 👤 About Me

I’m Anele, a BSc Applied Food & Tech graduate who pivoted into data analytics to solve real-world problems with precision and creativity. After completing a data analyst/scientist course, I delivered two end-to-end client projects using SQL, Excel, Power Query, and Power BI—transforming raw data into actionable dashboards. I’ve also built Python mini-projects for data cleaning and visualization.

My passion lies in making insights beautiful and impactful. I blend technical logic with design aesthetics to create dashboards that not only inform but inspire action. I’m currently open to freelance roles and independent contracts where I can help businesses turn data into clarity.

---

## 🔗 Connect With Me

- **LinkedIn**: [Anele Promise Ndlovu](https://www.linkedin.com/in/anele-promise-ndlovu-6a8586277)  
- **GitHub**: [Anele4](https://github.com/Anele4)
```
