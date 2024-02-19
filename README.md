#  DATA ANALYSIS WITH SQL AND EXCEL

### Overview

The goal of this data analysis project is to offer insights into the sales performance of products across various product categories within a company. Through analyzing different aspects of the product data, we aim to pinpoint trends, provide data-driven recommendations, and enhance our understanding of the company's performance.

### Data source

Product sales Data: The primary dataset used for this analysis is the AdventureWorks containing csv file

### Tools

- SQL Server 2022
- Microsoft SQL Server Management Studio
- Excel

  ### Creating Database

  The database **PROJECTSA** was created.
  ```
  CREATE DATABASE PROJECTSA
  ```
  ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/80ec47fa-2860-4f27-8487-56e587649897)

  ### Data Importation

The dataset used for the data analysis was imorted using the following methods:
1. Right click of **PROJECTSA** and select **Task**
2. From task select **Import Flat File**

  ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/31ccd8ff-cd7b-405c-a100-2fe1472d7bd9)<p>

3. select next from the **Import Flat File Wizard**
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/7a765af6-a8ad-4e6f-979a-a28d211ee1f4)<p>
4. Left click on **Browse** to import file from you documents
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/bc06b03e-722b-4d69-8eaa-1d12f07a8c0c)<p>
5. Select the datasets and click on **Open** to load data and select **Next** <p>
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/adf31b61-e046-4c52-9102-9dd2f8f753c0)<p>
 The datasets from **AdventureWorks** has now been imported successfully
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/5897bc56-8fcc-4804-9e7b-4b2726eaaefa)<p>

  ### Exploratory Data Analysis

 Exploratory Data Analysis (EDA) entailed delving into the product sales data to address essential inquiries, such as:
  - Total Sales for each product name
  - Total tax amount for each product color
  - Total freight for each product name
  - The sum of proportion of the sum of total product cost for each product name

   ### Data Analysis
At this juncture we are going to write queries to asnwer the about questions.
 1. Querry to bring out the total sales for each Product name
   ```
      SELECT
     ProductName,
	SUM(SalesAmount) AS Total_Sales
FROM AdventureWorks_Products AS P 
INNER JOIN AdventureWork_Sales AS S
ON P.ProductKey=S.ProductKey
GROUP BY ProductName 
ORDER BY Total_Sales DESC;
 ```
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/54673020-c6d5-427e-8420-ecbb13b42bd6)<p>
For this querry a view was created to further expolre in excel and also to visualize the data.
```
CREATE VIEW TotalSalesProduct AS
SELECT
     ProductName,
	SUM(SalesAmount) AS Total_Sales
FROM AdventureWorks_Products AS P 
INNER JOIN AdventureWork_Sales AS S
ON P.ProductKey=S.ProductKey
GROUP BY ProductName 
```
In excel on a blank workbook, go to **Data**, then to **Get Data** and select **From Database** then click  **From SQL Server Database**.

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/7d770b52-b812-4272-bb34-5f2ad4a43e8f)

2.  Total tax amount for each product color
 ```
SELECT
     ProductColor,
	SUM(TaxAmt) AS Total_Tax
FROM AdventureWorks_Products AS P 
INNER JOIN AdventureWork_Sales AS S
ON P.ProductKey=S.ProductKey
GROUP BY ProductColor
ORDER BY Total_Tax DESC;
```
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/c4ea40f5-cd25-45b3-9785-827bd0fb158a)<p>
3. Total freight for each product name
```
SELECT
     ProductName,
	SUM(Freight) AS Total_Freight
FROM AdventureWorks_Products AS p  
INNER JOIN AdventureWork_Sales AS S     
ON P.ProductKey=S.ProductKey
GROUP BY ProductName
ORDER BY Total_Freight   DESC 
```
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/5c956631-a398-4a0f-abd1-36536a0bff1d)<p>
4. The sum of proportion of the sum of total product cost for each product name

```
SELECT
     ProductName,
	SUM(TotalProductCost) AS Sum_of_proportion
FROM AdventureWorks_Products AS p  
INNER JOIN AdventureWork_Sales AS S     
ON P.ProductKey=S.ProductKey
GROUP BY ProductName
ORDER BY Sum_of_proportion   DESC
```
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/b9653497-b99a-4347-a662-3e11b37a3ff7)



   
 

  
  
 
