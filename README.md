# 🛫 Airline Database Analysis using SQL (January 2025)

This project focuses on analyzing a real-time airline database to extract operational and performance metrics. The goal was to write complex SQL queries using JOINs, CASE statements, and window functions to support data-driven decisions.

---

## 📌 Project Overview

- **Client/Scenario:** Real-time airline operations and booking dataset
- **Goal:** Enable insights into flight performance, customer booking behavior, and operational efficiency
- **Technology:** SQL (MySQL/PostgreSQL/SQL Server)

---

## 🎯 Problem Statement

Airline management required analytical insights from their operations database to track:

- On-time vs delayed flights
- Average delay by airline and route
- Frequent flyers and revenue contribution
- Aircraft utilization
- Booking patterns by season, class, and customer type

---

## 🔍 Project Tasks

### ✅ Task Summary

| Task | Description |
|------|-------------|
| 1 | Extract on-time vs delayed flight counts per airline |
| 2 | Identify top 5 routes by passenger traffic |
| 3 | Use window functions to find the rank of airlines by average delay |
| 4 | Use CASE statements to categorize flights as "On-Time", "Moderately Delayed", or "Severely Delayed" |
| 5 | Join flight and passenger tables to calculate average revenue per flight |
| 6 | Use subqueries to extract passengers who flew more than 3 times in a month |
| 7 | Aggregate total seats vs booked seats by aircraft type |

---

## 🔧 Tools & Technologies

- **SQL (PostgreSQL / MySQL)**
- **DBMS / Cloud SQL / SQL Workbench**
- **ER Diagram & Schema Documentation (Optional)**

---

## 💡 Key SQL Techniques Used

- `INNER JOIN`, `LEFT JOIN`, `SELF JOIN`
- `CASE` statements for classification
- `RANK()`, `ROW_NUMBER()`, `DENSE_RANK()` using `OVER()` clause
- Subqueries and CTEs (Common Table Expressions)
- Aggregation functions (`COUNT`, `SUM`, `AVG`, `GROUP BY`)

---

## 📊 Sample Queries

```sql
-- Example: Rank airlines by average arrival delay
SELECT airline, 
       AVG(arrival_delay) AS avg_delay,
       RANK() OVER (ORDER BY AVG(arrival_delay) DESC) AS delay_rank
FROM flights
GROUP BY airline;

-- Example: Classify flights using CASE
SELECT flight_id,
       departure_delay,
       CASE 
         WHEN departure_delay <= 10 THEN 'On-Time'
         WHEN departure_delay <= 30 THEN 'Moderately Delayed'
         ELSE 'Severely Delayed'
       END AS delay_category
FROM flights;
