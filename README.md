# 📊 Project Title: Sales & Manufacturing Performance Optimization | Power BI  

![The_ADVENTURE (1)](https://github.com/user-attachments/assets/ad69027d-923a-4487-8326-527443b7d0db)


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
**Problem Summary:** The dashboard helps the Production Manager efficiently monitor production progress, product quality, and inventory management in a clear and visual way.


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
  <summary>📌 Click for detail</summary>

  <details>
  <summary>Table 1: Production_WorkOrder</summary>

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
  <summary>Table 2: Product_Product</summary>  

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

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview  

#### 1️⃣ Dashboard 1: Manufacturing Overview  

![image](https://github.com/user-attachments/assets/10394fee-3130-44cd-b626-c9fb9ad066c9)  
  

📌 Analysis 1: **Production Overview:**

- The company has produced **4,508K products**, which is a significant volume.  
- However, there is **11K in waste**, indicating inefficiencies in the production process.  
- The **average production lead time is 297.34**, which may suggest bottlenecks in the process.  
- **On-time production rate is only 41.6%**, which is relatively low, suggesting delays and inefficiencies in meeting deadlines.


📌 Analysis 2:  **Cumulative Production Trends:**  
<p align="center">
<img src="https://github.com/user-attachments/assets/18431f3e-f170-47e4-99dd-183866f7c913" alt="Description">
</p>

- There is a **steady increase in production across fiscal years**, indicating business growth.  
- Seasonal trends show fluctuations in demand, which could be optimized for better inventory and resource planning.

📌 Analysis 3: **Cost Distribution**  

<p align="center">
  <img src="https://github.com/user-attachments/assets/326aa5aa-b348-47d4-a6b4-20ccc30812b0" alt="Description">
</p>

- The highest actual cost is in subassembly (31.72%), followed by final assembly (26.07%) and frame welding (25.39%).  
➡️ Optimizing these stages could lead to significant cost savings  

📌 Analysis 4: **Waste Cost & Scrap Rate Analysis:**  
- Waste cost fluctuates, but there has been an increasing trend in recent months, suggesting rising inefficiencies.  
- Top 5 subcategories with the highest scrap rate include Cranksets, Wheels, Headsets, Bottom Brackets, and Touring Frames.   
- These categories should be investigated for quality control issues or design flaws.  

*- Most produced products include Wheels, Derailleurs, Forks, Handlebars, and Cranksets.*  
*- Comparing this to the top waste subcategories, Cranksets and Wheels appear in both lists, indicating potential quality issues.*


#### 2️⃣ PRODUCTION COST ANALYSIS  

![image](https://github.com/user-attachments/assets/c5afcc26-6bb7-4e0a-a13a-516332c90209)

*In dashboard 1: Derailleurs, wheels: Low sales volume but highest production quantity*   
📌 Analysis 1:   **Wheels:**



<p align="center">
  <img src="https://github.com/user-attachments/assets/5dbdea73-fb18-41b7-9b92-47d760b2c287" alt="Description">
</p>

- Waste percent is 0.3%, which is higher than the average (0.2%).  
- Standard cost inventory is high at $254.52M.  
- Actual Resource Hours ranks second, and it accounts for about one-third of assembly costs (Actual Cost by Location - Subassembly).  
- High on-time production percent → Check if the factory is prioritizing meeting deadlines over product quality.  

➡️ Identify defects in the production process to reduce the waste percentage.  
➡️ Optimize production volume to align with sales demand, preventing overproduction and high inventory costs.

📌 Analysis 2: **Derailleurs**


<p align="center">
  <img src="https://github.com/user-attachments/assets/5d808b4f-e6d9-4997-b724-d407076503af" alt="Description">
</p>

- Waste percent = average  
- Top waste issues: Handling damage ($3.5K), stress test failures ($2.4K), temperature issues ($2.8K) → Improve quality control & material handling.  
- Moderate inventory cost ($17.15M), but waste reduction needed → Minimize defects & enhance efficiency.  

📌 Analysis 3: **Handlebars** - The components that consume the most cost and resource hours  
![image](https://github.com/user-attachments/assets/4100bef6-5d38-4a00-845c-7d0fe2761cf7)

- Waste & Defects: Key issues include metal gouging and thermoform errors.  
- Efficiency Concerns: Low on-time production suggests scheduling or process inefficiencies.
  


---

## 🔎 Final Conclusion & Recommendations  

### 🔍 **Key Insights:**  

- **Production Efficiency Issues**: Low on-time production rate (41.6%) and long lead time (297.34 hours) indicate inefficiencies in scheduling and execution.  
- **Waste & Cost Concerns**: Fluctuating waste costs with high peaks suggest inconsistent quality control; the most resource-heavy processes are *subassembly, final assembly, and frame forming*.  
- **Overproduction Risks**: *Wheels & Derailleurs* have high production but low sales, leading to excess inventory and high storage costs.  
- **Quality Control Challenges**: Wheels have a defect rate above average (0.3%), mainly due to incorrect colors, patterns, and oversized drill holes.  


### 📌 **Actionable Recommendations:**  

✔️ **Improve Production Scheduling**: Optimize planning to increase on-time production and reduce lead time.   
✔️ **Enhance Quality Control**: Focus on key defect areas (*color accuracy, pattern consistency, precise drilling*) to lower waste and rework.  
✔️ **Adjust Production to Demand**: Align *Wheels & Derailleurs* output with actual sales to reduce overstock and storage costs.  
✔️ **Cost Optimization**: Reassess *subassembly, final assembly, and frame forming* processes to reduce excessive resource consumption.  

