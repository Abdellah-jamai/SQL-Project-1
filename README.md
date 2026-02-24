# Product Analytics Dashboard






https://github.com/user-attachments/assets/1d732789-d4a4-42b0-b361-27ffbe410161




## 🔗 Project Overview

This project involves an end-to-end data analysis of a retail dataset containing 1,000+ records. 
The goal was to transform raw transactional data into an interactive executive dashboard that identifies key revenue drivers and profit margins.

## Request From Management

**Subject:** Request for dashboard development: Product analytics overview
Dear ...,
I hope this message finds you well. I would like to request the development of a high-level product analytics dashboard that provides insights into key product performance metrics.
This dashboard will support strategic decision-making and allow us to track performance trends effectively.

**What we need in the dashboard (page 1)**

**1.Revenue by country:** Top-performing regions with corresponding revenue.

**2.Revenue by Date and Year:** Comparative trends.

**3.Profit and Unit sales Year-over-Year (YoY) Change:** High-level summary of YoY growth.

**4.Revenue breakdown by discount band:** Distribution of revenue across different discount categories.

**5.Detailed table view:** Revenue and profit details by country and year.

Add whatever else you feel is necessary!

## 🛠️ Tech Stack

**SQL Server:** Data extraction, cleaning, and complex transformations (CTEs).

**Power BI:** Data modeling and interactive visualization.

## 🧹 Data Cleaning (SQL)

To ensure data integrity, I implemented a cleaning script that handled the following:

**Currency Formatting:** Removed symbols and converted pricing to numeric types.

**Null Handling:** Removed records with missing product identifiers.

**Join Optimization:** Performed a complex join between Sales and Discount tables using both Discount_Band and Month to prevent data duplication.

SQL
/* Example: Handling the complex Discount Join */
SELECT 
    s.Date,
    p.Product,
    (p.Sale_Price * s.Units_Sold) * (1 - (d.Discount / 100.0)) AS Net_Revenue
FROM product_sales s
JOIN Product_data p ON s.Product = p.[Product ID]
JOIN discount_data d ON TRIM(s.[ Discount Band ]) = TRIM(d.[Discount Band]) 
    AND FORMAT(s.Date, 'MMMM') = d.Month;


