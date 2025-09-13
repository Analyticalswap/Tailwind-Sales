# Tailwind-Sales
🔍 Project Overview

Purpose: Data insights for tailwind.
Focus: Sales analysis using Power BI with data modeling, DAX calculations, and dashboards.


📊 Data Sources

Files Used: Three Excel files.
Additional Tables: Created using DAX:

Calendar Table: Custom date table with year, month, quarter, weekday, etc.
Exchange Data: Used to convert revenue figures to USD.


🧮 Key Calculations
✅ Calculated Tables

Calendar Table: Covers dates from Jan 1, 2020 to Dec 31, 2023.
1. Calender Table
 CalendarTable =  
ADDCOLUMNS(
CALENDAR(DATE(2020, 1, 1), DATE(2023, 12, 31)),
"Year", YEAR([Date]),
"Month Number", MONTH([Date]),
"Month", FORMAT([Date], "MMMM"),
"Quarter", QUARTER([Date]),
"Weekday", WEEKDAY([Date]),
"Day", DAY([Date])
)


Sales in USD: Adds country name, exchange rate, and converts gross/net revenue and tax to USD.
Sales in USD = 
ADDCOLUMNS(
    Sales,
    "Country Name", RELATED(Countries[Country]),
    "Exchange Rate", RELATED('Exchange Data'[ExchangeRate]),
    "Exchange Currency", RELATED('Exchange Data'[Exchange Currency]),
    "Gross Revenue USD", [Gross Revenue] * RELATED('Exchange Data'[ExchangeRate]),
    "Net Revenue USD", [Net Revenue] * RELATED('Exchange Data'[ExchangeRate]),
    "Total Tax USD", [Total Tax] * RELATED('Exchange Data'[ExchangeRate])


📐 Calculated Measures

Quarterly Profit Margin: Uses DATESQTD to filter quarterly data.
Quarterly Profit Margin = 
CALCULATE(
    [Yearly Profit Margin],
    DATESQTD(CalendarTable[Date])
)

Median Sales: Median of gross revenue in USD.
Median Sales = 
MEDIAN('Sales in USD'[Gross Revenue USD])

Yearly Profit Margin: Profit ÷ Net Revenue.
Yearly Profit Margin = DIVIDE(SUM('Sales'[Profit]), SUM('Sales'[Net Revenue]),0)

YTD Profit Margin: Year-to-date profit margin using TOTALYTD.
YTD Profit Margin = 
    TOTALYTD([Yearly Profit Margin], CalendarTable[Date])


🔗 Data Model

Includes relationships between:

Sales
Countries
Exchange Data
Calendar Table
<img width="1742" height="1857" alt="image" src="https://github.com/user-attachments/assets/7a6b1a44-cac6-435f-aa66-5f617bd867ac" />



📈 Dashboards

Revenue trends <img width="1681" height="919" alt="image" src="https://github.com/user-attachments/assets/2b076647-2180-40c5-9452-1e465c93e1e5" />
Profit margins <img width="1666" height="909" alt="image" src="https://github.com/user-attachments/assets/8e987278-d4fd-4585-b8d6-6fae465704d6" />
Country-wise performance <img width="1667" height="937" alt="image" src="https://github.com/user-attachments/assets/d5cfa9d6-0e07-497a-a559-770506fc793f" />

Time-based comparisons (monthly, quarterly, yearly)
