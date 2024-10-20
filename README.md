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
1.Created a Measure for Total Sales.
``` dax
Total Sales = SUM(shipments[Sales])
```
2.Created a measure for Total Cost.
``` dax
Total Costs = SUM(shipments[Costs])
```
3.Created a measure for Total Profit.
``` dax
Total Profit = [Total Sales]-[Total Costs]
```
4.Created a measure for Profit %.
``` dax
Total profit % = DIVIDE([Total Profit],[Total Sales])
```
5.Created a measure for Total Shipments.
``` dax
Total Shipments = COUNTROWS(shipments)
```
6.Created a measure for Total Boxes.
``` dax
Total Boxes = SUM(shipments[Boxes])
```
7.Created a meaure for LBS Counts.
``` dax
LBS Count = CALCULATE([Total Shipments],shipments[Boxes]<50)
```
8.Created a measure for LBS %.
``` dax
LBS % = DIVIDE([LBS Count],[Total Shipments])
```
9.Created a measure for Latest Date.
``` dax
Latest Date = LASTDATE('calendar'[Start of Month])
```
10.Created a measure for total sales latest Month.
``` dax
Total Sales Latest Month = 
var ld=[Latest Date]
RETURN
CALCULATE([Total Sales],'calendar'[Start of Month]=ld)
```
11.Created a measure for total profit latest Month.
``` dax
Total Profit Latest Month = 
var ld=[Latest Date]
RETURN
CALCULATE([Total Profit],'calendar'[Start of Month]=ld)
```
12.Created a measure for MoM Profit %
``` dax
MoM Profit% = 
var this_month=[Total Profit]
var prev_month=CALCULATE([Total Profit],PREVIOUSDAY('calendar'[Date]))
RETURN
DIVIDE(this_month-prev_month,prev_month)
```
13.Created a measure for total sales previos month.
``` dax
Total Sales (prev month) = CALCULATE([Total Sales],PREVIOUSMONTH('calendar'[Date]))
```
14.Created a measure for Total Boxes latest month.
``` dax
Total Boxes Latest Month = 
var ld=[Latest Date]
RETURN
CALCULATE([Total Boxes],'calendar'[Start of Month]=ld)
```
15.Created a measure for Latest MoM Cost Change%.
``` dax
Latest MoM Cost Change % = 
var ld=[Latest Date]
var this_month_cost=[Total Cost Latest Month]
var prev_month_cost=CALCULATE([Total Costs],'calendar'[Start of Month]=EDATE(ld,-1))
RETURN
DIVIDE(this_month_cost-prev_month_cost,prev_month_cost)
```
16.Created a measure for latest shipments %.
``` dax
MoM Shipments change % = 
var this_month=[Total Shipments]
var prev_month=CALCULATE([Total Shipments],PREVIOUSDAY('calendar'[Date]))
RETURN
DIVIDE(this_month-prev_month,prev_month)
```
17.Created a measure for latest mom sales change%.
``` dax
Latest MoM Sales Change% = 
var ld=[Latest Date]
var this_month_sales=[Total Sales Latest Month]
var prev_month_sales=CALCULATE([Total Sales],'calendar'[Start of Month]=EDATE(ld,-1))
RETURN
DIVIDE(this_month_sales-prev_month_sales,prev_month_sales)
```
18.Created a measure for latest mom boxes change %.
``` dax
Latest Mom Boxes Change % = 
var ld=[Latest Date]
var this_month_sales=[Total Boxes Latest Month]
var prev_month_sales=CALCULATE([Total Boxes],'calendar'[Start of Month]=EDATE(ld,-1))
RETURN
DIVIDE(this_month_sales-prev_month_sales,prev_month_sales)
```
### Visualizations.
1.Used a name card visual for all the KPI which consists of Total Sales,Total Boxes,Total Costs,Total Profit,Total Shipments.
![kpi](https://github.com/user-attachments/assets/7d26da13-b400-45ac-8fa2-5764e21b0d35)
---
2.Created a line chart which indicates all the insights for the kpi.
![Sales by start of month](https://github.com/user-attachments/assets/8e153067-d1ae-41be-8c9a-0606ecff1a91)
---
3.Created a Gauge Chart For the profit indicator.
![image](https://github.com/user-attachments/assets/cae27d5d-f63e-4fd1-a972-cf874321638c)
---
4.Created a stacked Column chart for shipment analysis.
![Shipment Analysis](https://github.com/user-attachments/assets/c304d26d-28c1-4674-a465-d067201fa509)
---
5.Created a Table Visual which indicated all the sales person details and their contributions.
![Sales details](https://github.com/user-attachments/assets/ed184e53-72ba-4186-8c8d-0316bbc23618)
---
6.Created a Table chart which indicated all the Product details.
![Product Details](https://github.com/user-attachments/assets/cc317190-8689-4aae-ba6d-cdd09ce79b9c)
---
### Final Dashboard
![Sales Analytics SS](https://github.com/user-attachments/assets/d537fc8e-97b3-4283-be14-0a5018378346)










