🛒 Walmart Inventory Optimization Dashboard (Power BI)
📌 Project Overview

Designed and developed a Power BI dashboard to analyze multi-store sales, holding costs, safety stock levels, and macroeconomic indicators using a structured star schema model.

The solution enables store-level performance analysis and inventory efficiency monitoring.

🏗 Data Modeling

Implemented a star schema architecture:

Fact Table

Weekly Sales

Holding Cost

Safety Stock

Inventory Cost

Dimension Tables

Dim_Store

Dim_Date

Department

Relationships

One-to-many (Dimension → Fact)

Single-direction filtering

Optimized model to avoid circular dependencies

📐 DAX Measures
Total Sales =
SUM(sales_final[Weekly_Sales])

Total Holding Cost =
SUM(sales_final[Holding_Cost])

Inventory to Sales % =
DIVIDE([Total Holding Cost], [Total Sales])

Avg Weekly Sales =
AVERAGE(sales_final[Weekly_Sales])

Lowest Performing Store =
VAR StoreTable =
    ADDCOLUMNS(
        VALUES(Dim_Store[Store]),
        "StoreSales", [Total Sales]
    )
VAR BottomStore =
    TOPN(1, StoreTable, [StoreSales], ASC)
RETURN
    MAXX(BottomStore, Dim_Store[Store])
📊 Dashboard Components

KPI Cards (Dynamic Measures)

Time-Series Trend Analysis (Sales vs Holding Cost)

Store-Level Performance Comparison (Bar Charts)

Scatter Plot (Safety Stock vs Weekly Sales)

CPI vs Sales Trend Analysis

Interactive Slicers (Date, Store, Department)

⚙️ Technical Highlights

Dynamic ranking logic using TOPN

Context-aware measures with CALCULATE and ADDCOLUMNS

Efficient filter context handling

Clean visual hierarchy and executive layout

Optimized performance with proper relationship modeling

🧠 Analytical Capabilities

Store efficiency identification

Cost-to-revenue ratio monitoring

Safety stock demand alignment evaluation

Time-based performance comparison

Inflation impact assessment

🚀 Business Outcome

The solution enables proactive inventory management by identifying misaligned stock allocation and store-level inefficiencies, supporting data-driven cost optimization and performance monitoring.
