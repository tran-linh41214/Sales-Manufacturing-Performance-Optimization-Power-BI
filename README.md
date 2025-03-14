# 📊 Project Title: Sales & Manufacturing Performance Optimization | Power BI  
Author: Linh Tran  
Tools Used: Power BI 

---

## 📑 Table of Contents  
1. [📌 Background & Overview](#-background--overview)  
2. [📂 Dataset Description & Data Structure](#-dataset-description--data-structure)  
3. [🧠 Design Thinking Process](#-design-thinking-process)  
4. [📊 Key Insights & Visualizations](#-key-insights--visualizations)  
5. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)

---

## 📌 Background & Overview  

### Objective:
### 📖 Overview 
Adventure Works, a leading player in the manufacturing and sales industry, requires in-depth analysis of its manufacturing data to make informed business decisions. This dashboard collates extensive manufacture and sales data into an easily interpretable format, helping stakeholders understand key sales dynamics and trends.  

### 👤 Stake Holder  
✔️ Production Manager  
✔️ Project Manager   
✔️ Planning Department    
✔️ Warehouse and Quality Management Department


###  ❓Business Questions:  
✔️ Analyze production reports based on the fiscal year.  
✔️ Manage quantity, quality, time, workforce, and production costs for each product category. 

---

## 📂 Dataset Description & Data Structure  

### 📌 Data Source  
- Source: Google BigQuery  
- Format: .csv  

### 📊 Data Structure & Relationships  

#### 1️⃣ Tables Used:  
📅 **Fact table**                          

-  Production_WorkOrder
-  Production_WorkOrderRouting
  
📅 **Dim table**                          
- Product_Product  
- Production_Location  
- Production_ProductCategory  
- Production_ProductSubcategory
- Production_ScrapReason
- Production_BillofMaterials  


#### 2️⃣ Table Schema & Data Snapshot  
<details>
  <summary>📌 Click để mở nội dung</summary>

  <details>
  <summary>Table 1: Production_WorkOrder</summary>Table 1: Production_WorkOrder

| Column Name | Data Type | Description |  
|-------------|----------|-------------|  
| WorkOrder ID  | INT      | Primary key for WorkOrder records. |  
| ProductID       | INT     | Product identification number. Foreign key to Product.ProductID. |  
| OrderQty    | INT     | Product quantity to build. |  
| StockedQty | INT    | Quantity built and put in inventory. |  
| ScrappedQty | smallint | Quantity that failed inspection. |
| StartDate | datetime | Work order start date. |
| EndDate | datetime | Work order end date. |
| DueDate | datetime | Work order due date. |
| ScrapReasonID | smallint | Reason for inspection failure. |
| ModifiedDate | datetime | Date and time the record was last updated. |

  </details>

  <details>
  <summary>Table 2: Product_Product</summary>Table 1: Production_WorkOrder  

| Column Name    | Data Type | Description |  
|---------------|----------|-------------|  
| ProductID | INT      | Primary key for Product records. |  
| Name     | nvarchar(50)      | Name of the product. |  
| ProductNumber      | ProductNumber      | Unique product identification number. |  
| MakeFlag      | bit     | 0 = Product is purchased, 1 = Product is manufactured in-house. Default 1 |  
| FinishedGoodsFlag | bit | 0 = Product is not a salable item. 1 = Product is salable. Default 1 |
| Color | nvarchar(15) |  Product color.|
| SafetyStockLevel | smallint | Minimum inventory quantity.|
| ReorderPoint | smallint | Inventory level that triggers a purchase order or work order.|
| StandardCost | money | Standard cost of the product. |
| ListPrice | money | Selling price. |
| Size | nvarchar(5) | Product size. |
| SizeUnitMeasureCode | nchar(3) | Unit of measure for Size column. |
| WeightUnitMeasureCode | nchar(3) | Unit of measure for Weight column. |
| Weight | decimal(8, 2) | Product weight. |
| DaysToManufacture | int | Number of days required to manufacture the product. |
| ProductLine | nchar(2) | R = Road, M = Mountain, T = Touring, S = Standard |
| Class | nchar(2) | H = High, M = Medium, L = Low |
| Style | nchar(2) | W = Womens, M = Mens, U = Universal |
| ProductSubcategoryID | INT | Product is a member of this product subcategory. Foreign key to ProductSubCategory.ProductSubCategoryID. |
| ProductModelID | INT | Product is a member of this product model. Foreign key to ProductModel.ProductModelID. |
| SellStartDate | datetime | Date the product was available for sale. |
| SellEndDate | datetime | Date the product was no longer available for sale. |
| DiscontinuedDate | datetime | Date the product was discontinued. |
| rowguid | uniqueidentifier | ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample. |
| ModifiedDate | datetime | Date and time the record was last updated. |

</details>
</details> 


#### 3️⃣ Data Relationships:   

<p align="center">
  <img src="https://github.com/user-attachments/assets/df8c4bf7-e720-4721-be27-abc3d43e3702" alt="Description">
</p>


---

## 🧠 Design Thinking Process  


1️⃣ Empathize 

<p align="center">
  <img src="https://github.com/user-attachments/assets/5dc65da6-2bc2-4464-8170-c6f6cce9ffb4" alt="Description">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/11f02aa1-5e7d-4426-a1b2-bf3e7009877b" alt="Description">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e77ade43-0070-4a08-b2a5-8f0e953d4306" alt="Description">
</p>


### **Key Stakeholder & Problem Summary**  
- **Key Stakeholder:** Production Manager  
- **Problem Summary:** The dashboard helps the Production Manager efficiently monitor production progress, product quality, and inventory management in a clear and visual way.

2️⃣ Define point of view  

<p align="center">
  <img src="https://github.com/user-attachments/assets/38cd7502-6fb3-457c-afbb-7ac3780512d0" alt="Description">
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/16fbfd75-603c-418a-b0a0-651f10124336" alt="Description">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/81b32527-88f1-4a99-91cf-fdc76cd7ccda" alt="Description">
</p>


3️⃣ Ideate  

<p align="center">
  <img src="https://github.com/user-attachments/assets/33e57df4-b86e-472d-a106-2dc4f2bd8ff2" alt="Description">
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/aca18458-bd2b-44c7-a171-564dc88c35cd" alt="Description">
</p>



4️⃣ Prototype and review  

---

## ⚒️ Main Process

Giả định Năm tài chính kết thúc ngày 30/9

<details>
  <summary>📌Tính năm tài chính</summary>
 
DAX Tính năm tài chính
 
```power BI

Calendar = 

--Inputs--
VAR WeekStartsOn = "Sun"
VAR FiscalStartMonth = 10

--NOTE: Calendar week starts from Sunday

--Calculation--
RETURN
    ADDCOLUMNS (
        CALENDARAUTO ( FiscalStartMonth - 1 ),
        "MIndex", MONTH ( [Date] ),
        "FiscalMIndex", MONTH ( EDATE ( [Date], - FiscalStartMonth + 1 ) ),
        "CalMonth", FORMAT ( [Date], "mmm" ),
        "CalQtr", "Q"
            & CEILING ( MONTH ( [Date] ), FiscalStartMonth - 1 ) / ( FiscalStartMonth - 1 ),
        "CalYear", YEAR ( [Date] ),
        "Fiscal Week",
        VAR FiscalFirstDay =
            IF (
                MONTH ( [Date] ) < FiscalStartMonth,
                DATE ( YEAR ( [Date] ) - 1, FiscalStartMonth, 1 ),
                DATE ( YEAR ( [Date] ), FiscalStartMonth, 1 )
            )
        VAR FilteredTableCount =
            COUNTROWS (
                FILTER (
                    SELECTCOLUMNS ( GENERATESERIES ( FiscalFirstDay, [Date] ), "Dates", [Value] ),
                    FORMAT ( [Dates], "ddd" ) = WeekStartsOn
                )
            )
        VAR WeekNos =
            IF (
                FORMAT ( FiscalFirstDay, "ddd" ) <> WeekStartsOn,
                FilteredTableCount + 1,
                FilteredTableCount
            )
        RETURN
            "Week " & WeekNos,
        "Fiscal Qtr", "Q"
            & CEILING ( MONTH ( EDATE ( [Date], - FiscalStartMonth + 1 ) ), 3 ) / 3,
        "Fiscal Year",
        VAR CY =
            RIGHT ( YEAR ( [Date] ), 2 )
        VAR NY =
            RIGHT ( YEAR ( [Date] ) + 1, 2 )
        VAR PY =
            RIGHT ( YEAR ( [Date] ) - 1, 2 )
        VAR FinYear =
            IF ( MONTH ( [Date] ) > ( FiscalStartMonth - 1 ), CY & "-" & NY, PY & "-" & CY )
        RETURN
            FinYear,
        "CalWeekNo", WEEKNUM ( [Date], 2 ),
        "Weekend/Working", IF ( WEEKDAY ( [Date], 2 ) > 5, "Weekend", "Working" ),
        "Day", FORMAT ( [Date], "ddd" ),
        "CustomDate", FORMAT ( [Date], "d/mm" )
    )
```
</details>
</details>

- In each step, show your Code

- Include query/ code execution screenshots or result samples

- Explain its purpose and its findings

Measure Table
```power BI
%OnTimeProduction = 
VAR Num_0 = COUNTROWS(FILTER('Production_WorkOrderRouting', 'Production_WorkOrderRouting'[OnTime] = 0))
VAR Num_1 = COUNTROWS(FILTER('Production_WorkOrderRouting', 'Production_WorkOrderRouting'[OnTime] = 1))
RETURN 
Num_1/(Num_0+Num_1)
```

```powwer BI
%Waste = CALCULATE(SUM( 'Production_WorkOrder'[ScrappedQty])/SUM('Production_WorkOrder'[OrderQty]))
```

```power BI
CumulativeTotalsYTD = TOTALYTD(SUM('Production_WorkOrder'[OrderQty]), 'Calendar'[Date], "09/30")

CycleTime = SUM( 'Production_WorkOrderRouting'[ActualResourceHrs] ) / SUM ( 'Production_WorkOrder'[OrderQty] )

OrderQuantity = SUM('Production_WorkOrder'[OrderQty])

SalesOrderQty = SUM(Sales_SalesOrderDetail[OrderQty])

StandardCostInventory = SUM('Production_WorkOrder'[StockedQty])*SUM('Product_Product'[StandardCost])

WasteCost = SUM('Production_WorkOrder'[ScrappedQty]) * AVERAGE('Product_Product'[StandardCost])
```
Production_Bike Table
```power BI
Production_Bike = FILTER(
SUMMARIZE( 'Production_WorkOrder', Production_ProductSubcategory[Name], " Subcategory Totals ", [OrderQuantity]),
    NOT(ISBLANK('Production_ProductSubcategory'[Name])) && 'Production_ProductSubcategory'[Name] <> ""
)
```

```power BI
%Pareto = DIVIDE([CumulativeSum],[TotalSum])

Cumulative = CALCULATE( SUM('Production_Bike'[ Subcategory Totals ]), FILTER( ALL('Production_Bike'[Rank]), 'Production_Bike'[Rank] <= MAX('Production_Bike'[Rank])))

CumulativeSum = 
CALCULATE( SUM( 'Production_Bike'[ Subcategory Totals ]), FILTER( ALLSELECTED( 'Production_Bike'), 'Production_Bike'[Rank] <= MAX( 'Production_Bike'[Rank])))

Production_Bike = FILTER(
SUMMARIZE( 'Production_WorkOrder', Production_ProductSubcategory[Name], " Subcategory Totals ", [OrderQuantity]),
    NOT(ISBLANK('Production_ProductSubcategory'[Name])) && 'Production_ProductSubcategory'[Name] <> ""
)

Rank = RANKX( ALL('Production_Bike'), 'Production_Bike'[ Subcategory Totals ])

TotalSum = CALCULATE( SUM( 'Production_Bike'[ Subcategory Totals ]), ALLSELECTED( 'Production_Bike'))
```

---

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview  

#### 1️⃣ Dashboard 1: Overview

![image](https://github.com/user-attachments/assets/a0c3dcc9-9b3c-4948-a434-a36c67d5b475)
  

📌 Analysis 1:  
Quá trình sản xuất của công ty giai đoạn 2010 - 2014
- Fiscal YTD - Waste: Tổng số sản phẩm bị lỗi trong năm tài chính: 11K
- Fiscal YTD - Production: Số sản phẩm đã sản xuất: 4508K
=> Tỷ lệ sản phẩm lỗi: 0.2%
- Average Production Lead Time: Khoảng thời gian trung bình từ khi bắt đầu đến khi hoàn thành việc sản xuất: 297.34
- Tỷ lệ sản xuất đúng hạn: 41.6%
- Fiscal YTD - Production Hours: Tổng số giờ lao động của công nhân/ Số giờ hoạt động của máy móc trong sản xuất của năm tài chính: 229K
- Cumulative Monthly Totals YTD: tổng số sản phẩm được sản xuất tích lũy từ đầu năm tài chính đến một thời điểm cụ thể trong năm => giúp so sánh với KPI năm để đánh giá hiệu quả, tiến độ và có điều chỉnh kịp thời cho giai đoạn tiếp theo
  Có thể thấy trên biểu đồ số lượng này tăng qua từng năm nhưng tốc độ tăng đang giảm dần
- Waste Cost: Chi phí bị lãng phí: biến động bất thường qua các năm, cao nhất vào tháng 9 năm 2013, dấu hiệu tích cực là sang năm 2014 đã giảm nhiều, nhưng tháng 4 năm 2014 lại tăng khá cao
- Donut chart: phân bổ chi phí trên các công đoạn lắp ráp => xem tốn nhiều chi phí ở công đoạn nào để có các biện pháp cải thiện phù hợp => phần chiếm nhiều nhất subassembly, final assembly, frame forming

#### 2️⃣ Category Analysis  

![image](https://github.com/user-attachments/assets/f2b184fb-2994-4f4a-a6c0-8d5b7971a707)

📌 Analysis 2:   

- Scatter chart: số lượng sản phẩm đã sản xuất và số lượng sản phẩm đã được bán
  => Derailleurs, wheels: số lượng bán ra thấp nhưng số lượng sản xuất lại cao nhất

![image](https://github.com/user-attachments/assets/d998e7e3-18f0-4b60-978e-933fbb30141d)

 
- Wheels: waste percent - tỷ lệ sản phẩm bị lỗi là 0.3% > mức trung bình (0.2%), Standard cost inventory - chi phí lưu kho cao: 254.52M $, Actual Resource Hours đứng thứ 2, chiếm khoảng 1/3 chi phí lắp ráp (actual cost by location - subassembly)
  => cần tìm ra lỗi trong quá trình sản xuất để giảm waste percent, giảm số lượng sản xuất để phù hợp với số lượng bán ra
- Derailleurs: waste percent = average

![image](https://github.com/user-attachments/assets/7123a6cc-527c-4277-92e3-2ac7885611b8)
 
- Linh kiện tốn nhiều chi phí, nhân công, máy móc nhất: Handlebars. Trong đó công đoạn frame forming và frame welding của bộ phận này là tốn kém nhất
  

#### 3️⃣ Bike Production Analysis  
![image](https://github.com/user-attachments/assets/a43e5661-d6c6-4738-86c8-21484d4ddcce)
  
📌 Analysis 3:  

- Biểu đồ line - column chart: columns: số lượng sản phẩm được sản xuất theo từng subcategory, xếp theo thứ tự giảm dần; line: phần trăm cộng dồn tỷ trọng của từng thành phần
Chart 1: các thành phần sản xuất xe đạp
Chart 2: các loại xe đạp/ các sản phẩm xe đạp hoàn thiện
- Table matrix: scrap reason and waste cost
*(Theo Dashboard 2, cần tìm nguyên nhân gây lỗi khi sản xuất wheels)*

![image](https://github.com/user-attachments/assets/e43826d6-6fdb-4c40-814d-ded3f781d55c)


Wheels - On time production percent cao => kiểm tra lại xem nhà máy có tập trung vào việc sản xuất đúng hạn và bỏ qua chất lượng sản phẩm không
Lý do chiếm tỷ lệ nhiều nhất: Sai màu sắc, họa tiết, kích thước mũi khoan quá lớn

![image](https://github.com/user-attachments/assets/596e81c4-9192-4a69-b0b3-35b2135a98da)

- Drailleurs: % ontime production cao nhất, chi phí không quá nhiều => chỉ cần cân đối lại lượng sản xuất và sales

  ![image](https://github.com/user-attachments/assets/c635f296-20cc-4522-bd3e-cede88af3d99)

- Road Bikes: sales cao nhất => mặt hàng chủ chốt => tiếp tục phát triển và khắc phục các lỗi còn tồn tại

![image](https://github.com/user-attachments/assets/5680fa9d-fc8e-4b4d-bf2b-35acdfceebd2)


- Touring bikes: sales khá thấp, lỗi lớn nhất là sai màu sắc => khảo sát lại tệp khách hàng mua Touring bike xem màu sắc có là yếu tố then chốt trong quyết định mua hàng của họ hay không => nếu đúng, khắc phục để tăng sales
---

## 🔎 Final Conclusion & Recommendations  

### 🔍 **Key Insights:**  

- **Production Efficiency Issues**: Low on-time production rate (41.6%) and long lead time (297.34 hours) indicate inefficiencies in scheduling and execution.  
- **Waste & Cost Concerns**: Fluctuating waste costs with high peaks suggest inconsistent quality control; the most resource-heavy processes are *subassembly, final assembly, and frame forming*.  
- **Overproduction Risks**: *Wheels & Derailleurs* have high production but low sales, leading to excess inventory and high storage costs.  
- **Quality Control Challenges**: Wheels have a defect rate above average (0.3%), mainly due to incorrect colors, patterns, and oversized drill holes.  
- **Product-Specific Findings**: *Road Bikes* are the best-selling category, while *Touring Bikes* have low sales, with color mismatch as a key defect.  

### 📌 **Actionable Recommendations:**  

✔️ **Improve Production Scheduling**: Optimize planning to increase on-time production and reduce lead time.   
✔️ **Enhance Quality Control**: Focus on key defect areas (*color accuracy, pattern consistency, precise drilling*) to lower waste and rework.  
✔️ **Adjust Production to Demand**: Align *Wheels & Derailleurs* output with actual sales to reduce overstock and storage costs.  
✔️ **Cost Optimization**: Reassess *subassembly, final assembly, and frame forming* processes to reduce excessive resource consumption.  
✔️ **Customer-Centric Adjustments**: Conduct surveys on *Touring Bike* color preferences before modifying production to boost sales.
