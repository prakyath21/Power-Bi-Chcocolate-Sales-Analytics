### PowerBi Chocolates Sales Analytics Dashboard
--- 
Description:
This dashboard provides a comprehensive overview of the sales performance, profitability, and shipment metrics for Awesome Chocolates. It offers insights into various aspects of the business, including product-wise sales, profit margins, shipment analysis, and regional performance.

### Key Features:

Sales and Profit: Displays total sales, boxes sold, total costs, total profit, and profit percentage.
Monthly Performance: Shows month-over-month (MoM) percentage changes for sales, boxes, costs, profit, and total shipments.
Product Breakdown: Provides detailed information on sales, profit, profit percentage, and LBS% for each product.
Shipment Analysis: Includes shipment analysis by start of month, region-wise shipments, and a shipment distribution chart.
Visualizations: Employs various charts and graphs to effectively represent data, such as line charts, bar charts, and pie charts.
---
### Objectives:
1.Get the Total Sales of the Chocolates.
2.Get the Total Boxes of the Chocolates.
3.Get the Total Shipments.
4.Total Cost.
5.Total Profit.
6.Calculate the Profit %.
7.LBS Count
8.LBS%
9.MoM Change Analysis
10.YoY Change Analysis
---
### Dataset Description:
---
For Chocolate Data Analysis,we use 3 Datasets-Shipment Data,Calender Table,Dimension Data.

### Shipment Details-No.of rows=6121,No.Of Columns=6

1.Sales Person-Name of Sales Person
2.Geography-Location
3.Product-Indiacates the Chocolate Products
4.Date
5.Sales
6.Boxes

### Dimension Dataset Containes the details of the product,category and cost per box.
---

### Preparing Data For Analysis.
---
'''dax
Total Sales = SUM(shipments[Sales])
