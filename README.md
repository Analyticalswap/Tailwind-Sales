# Tailwind-Sales
🔍 Project Overview

Purpose: Data insights for tailwind.
Focus: Sales analysis using Power BI with data modeling, DAX calculations, and dashboards.


📊 Data Sources

Files Used: Three Excel files from course resources.
Additional Tables: Created using DAX:

Calendar Table: Custom date table with year, month, quarter, weekday, etc.
Exchange Data: Used to convert revenue figures to USD.


🧮 Key Calculations
✅ Calculated Tables

Calendar Table: Covers dates from Jan 1, 2020 to Dec 31, 2023.
Sales in USD: Adds country name, exchange rate, and converts gross/net revenue and tax to USD.

📐 Calculated Measures

Quarterly Profit Margin: Uses DATESQTD to filter quarterly data.
Median Sales: Median of gross revenue in USD.
Yearly Profit Margin: Profit ÷ Net Revenue.
YTD Profit Margin: Year-to-date profit margin using TOTALYTD.


🔗 Data Model

Includes relationships between:

Sales
Countries
Exchange Data
Calendar Table


📈 Dashboards

Revenue trends
Profit margins
Country-wise performance
Time-based comparisons (monthly, quarterly, yearly)
