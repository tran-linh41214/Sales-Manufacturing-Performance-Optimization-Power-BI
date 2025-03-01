# 📊 Project Title: [Adventure Works Sales]  
Author: [Linh Tran]  
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
Adventure Works, a leading player in the manufacturing and sales industry, requires in-depth analysis of its sales data to make informed business decisions. This dashboard collates extensive sales data into an easily interpretable format, helping stakeholders understand key sales dynamics and trends.  

### 👤 Stake Holder  
✔️ Production Director
✔️ Project Manager 
✔️ Planning Department  
✔️ Warehouse and Quality Management Department


###  ❓Business Questions:  
✔️ Analyze production reports based on the fiscal year.
✔️ Manage quantity, quality, time, workforce, and production costs for each product category. 

### 🎯Project Outcome:  
Summarize key findings and insights/ trends/ themes in a concise, bullet-point 
format.  
Features
Time Series Analysis: Visual representation of sales trends over the three-year period.
Product Performance Tracking: Insights into top-performing and underperforming products.
Customer Demographics Analysis: Breakdown of sales data by customer demographics such as age, location, and purchasing habits.
Sales Territory Mapping: Geographic visualization of sales distribution and territory performance.
Revenue and Profit Analysis: Detailed analysis of revenue streams and profitability.
Interactive Filter: Customizable filters for in-depth analysis of specific time frames, products, regions, and customer segments.
Benefits
Strategic Decision Making: Empowers management with data-driven insights for strategic planning.
Performance Tracking: Enables sales teams to monitor and improve their performance.
Market Understanding: Helps in understanding market trends and customer preferences.
Efficient Reporting: Provides an efficient way to communicate key sales metrics to stakeholders.
 _Example:_

✔️ Sales Trends: The top X% of products generate Y% of revenue.  
✔️ Inventory Optimization: Certain products are frequently out-of-stock, causing revenue loss.  
✔️ Customer Behavior: Returning customers spend Z% more per transaction than new customers.  

---

## 📂 Dataset Description & Data Structure  

### 📌 Data Source  
- Source: Google BigQuery  
- Format: (.csv, .sql, .xlsx, etc.)  

### 📊 Data Structure & Relationships  

#### 1️⃣ Tables Used:  
| **Fact table**                          | **Dim table**                          |
|-----------------------------------------|---------------------------------------|
| Production_WorkOrder                    | Product_Product                        |
| Production_WorkOrderRouting             | Production_Location                    |
|                                         | Production_ProductCategory             |
|                                         | Production_ProductSubcategory          |
|                                         | Production_ScrapReason                 |
|                                         | Production_BillofMaterials             |

![image](https://github.com/user-attachments/assets/df8c4bf7-e720-4721-be27-abc3d43e3702)

#### 2️⃣ Table Schema & Data Snapshot  
<details>
  <summary>📌 Click để mở nội dung</summary>

  Table 1: Production_WorkOrder

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

Table 2: Product_Product  

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



Table 2: Sales Transactions  

👉🏻 Insert a screenshot of table schema 


 _Example:_

| Column Name    | Data Type | Description |  
|---------------|----------|-------------|  
| Transaction_ID | INT      | Unique identifier for each sale |  
| Product_ID     | INT      | Foreign key linking to Products table |  
| Quantity       | INT      | Number of items sold |  
| Sale_Date      | DATE     | Date of transaction |  


📌If the table is too big, only capture a part of it that contains key metrics you used in the projects or put the table in toggle

#### 3️⃣ Data Relationships:  
Describe the connections between tables—e.g., one-to-many, many-to-many.  

👉🏻 Include a screenshot of Data Modeling to visualize relationships.  

---

## 🧠 Design Thinking Process  

Explain the step-by-step approach taken to solve the problem.  

👉🏻 Insert a screenshot of the Design Thinking steps (Screenshot your Excel design thinking tables for better presentation).  

1️⃣ Empathize 

![image](https://github.com/user-attachments/assets/5dc65da6-2bc2-4464-8170-c6f6cce9ffb4)

![image](https://github.com/user-attachments/assets/11f02aa1-5e7d-4426-a1b2-bf3e7009877b)

![image](https://github.com/user-attachments/assets/e77ade43-0070-4a08-b2a5-8f0e953d4306)

### **Key Stakeholder & Problem Summary**  
- **Key Stakeholder:** Production Manager  
- **Problem Summary:** The dashboard helps the Production Manager efficiently monitor production progress, product quality, and inventory management in a clear and visual way.

2️⃣ Define point of view  

![image](https://github.com/user-attachments/assets/38cd7502-6fb3-457c-afbb-7ac3780512d0)

![image](https://github.com/user-attachments/assets/16fbfd75-603c-418a-b0a0-651f10124336)

![image](https://github.com/user-attachments/assets/81b32527-88f1-4a99-91cf-fdc76cd7ccda)


3️⃣ Ideate  

![image](https://github.com/user-attachments/assets/33e57df4-b86e-472d-a106-2dc4f2bd8ff2)

![image](https://github.com/user-attachments/assets/aca18458-bd2b-44c7-a171-564dc88c35cd)


4️⃣ Prototype and review  

---

## ⚒️ Main Process

1️⃣ Data Cleaning & Preprocessing  
2️⃣ Exploratory Data Analysis (EDA)  
3️⃣ SQL/ Python Analysis 

- In each step, show your Code

- Include query/ code execution screenshots or result samples

- Explain its purpose and its findings


4️⃣ Power BI Visualization  (applicable for PBI Projects)

---

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview  

#### 1️⃣ Dashboard 1 Preview  
👉🏻 Insert Power BI dashboard screenshots here  

📌 Analysis 1:  
- Observation: _Describe trends, key metrics, and patterns._  
- Recommendation: _Suggest actions based on insights._  

#### 2️⃣ Dashboard 2 Preview  
👉🏻 Insert Power BI dashboard screenshots here

📌 Analysis 2:   
- Observation: _Describe trends, key metrics, and patterns._  
- Recommendation: _Suggest actions based on insights._  

#### 3️⃣ Dashboard 3 Preview  
👉🏻 Insert Power BI dashboard screenshots here  

📌 Analysis 3:  
- Observation: _Describe trends, key metrics, and patterns._  
- Recommendation: _Suggest actions based on insights._  

---

## 🔎 Final Conclusion & Recommendations  

👉🏻 Based on the insights and findings above, we would recommend the [stakeholder team] to consider the following:  

📌 Key Takeaways:  
✔️ Recommendation 1  
✔️ Recommendation 2  
✔️ Recommendation 3
