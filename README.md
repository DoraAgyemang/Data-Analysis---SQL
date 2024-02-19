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
   
5. Left click on **Browse** to import file from you documents
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/bc06b03e-722b-4d69-8eaa-1d12f07a8c0c)<p>
   
6. Select the datasets and click on **Open** to load data and select **Next** <p>

   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/adf31b61-e046-4c52-9102-9dd2f8f753c0)<p>
   
 The datasets from **AdventureWorks** has now been imported successfully
 
   ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/5897bc56-8fcc-4804-9e7b-4b2726eaaefa)<p>

  ### Exploratory Data Analysis

 Exploratory Data Analysis (EDA) entails delving into the product sales data to address essential queries, such as:
  - Total Sales for each product name
  - Total tax amount for each product color
  - Total freight for each product name
  - The sum of proportion of the sum of total product cost for each product name

   ### Data Analysis
At this juncture we will querry the data to asnwer the business questions above.
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
From the above table it can be seen that the total sales for each product was brought out from the AdventureWorks product and AdventureWorks Sales by using inner join to join the tables using what they have in common (ProductKey) since they are two different tables. It was then querried to be grouped by Product Name and Ordered the Total Sales to be in Descending order with Road-150 Red.48 with the highest Total Sales. 

For this querry a view was created to further explore in excel and also to visualisee the data.
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
In creating a view, we populated a stored **SELECT** statement and querried it like a table. This because a view do not accept parameters. Here, we created a view that **executes a SELECT statement**, and returns the names products and their total sales for an end user.

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
The above querry brought out the Total Tax by the Product color with Red having the highest Total Tax.
A view was created just as seen in 1 above
```
CREATE VIEW TotalTaxAmount AS
SELECT
     ProductColor,
     SUM(TaxAmt) AS Total_Tax
FROM AdventureWorks_Products AS P 
INNER JOIN AdventureWork_Sales AS S
ON P.ProductKey=S.ProductKey
GROUP BY ProductColor
```

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
In this querry we brought out the Total freight for ach product name where Road-150 Red.40 has the highest total freight.
View was created for this querry

```
CREATE VIEW TotalFreight AS
SELECT
     ProductName,
     SUM(Freight) AS Total_Freight
FROM AdventureWorks_Products AS p  
INNER JOIN AdventureWork_Sales AS S     
ON P.ProductKey=S.ProductKey
GROUP BY ProductName
```

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
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/b9653497-b99a-4347-a662-3e11b37a3ff7)<p>
Per the querry we brought out the sum of proportion for each product name with Road-150 Red.48 with the highest sum of proportion.
A view was created for this querry
```
CREATE VIEW TotalProductCost AS 
SELECT
     ProductName,
     SUM(TotalProductCost) AS Sum_of_proportion
FROM AdventureWorks_Products AS p  
INNER JOIN AdventureWork_Sales AS S     
ON P.ProductKey=S.ProductKey
GROUP BY ProductName
```

### Importing Data from SQL to Excel For Report

  In excel on a blank workbook, go to **Data**, then to **Get Data** and select **From Database** then click  
   **From SQL Server Database**.
   
![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/7d770b52-b812-4272-bb34-5f2ad4a43e8f)

  A prompt will pop upt for the server name to the inputted. 
 
 ![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/d02859ad-4722-4d1b-a446-d5969692b149)

 Go the SQL server and on object explorer click on connect then select Database engine

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/89ad2ce4-3fe6-49cc-a7aa-32fb662c94a5)

A prompt will appear. You then copy the server name and paste in the excel pop up 

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/c1519def-f97d-4ba5-ac51-db0d01b86112)

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/78b32588-cb8c-46fd-bf30-69ce876625c4)

Click okay. There is then another prompt for you to select your data, after which you click load

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/cc58791e-cb34-48be-8e95-78fa11970638)

### Pivot Tables and Pivot Charts
Pivot Tables and a pivot charts were created for the data in Excel 

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/7d0ac91c-61e2-4372-bea6-3df046f2983b)

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/cf383322-d361-4456-b32c-f077be6d70df)

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/2a56a892-786c-44a2-b4d5-9ec1c1326a87)

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/7c4f5de1-7054-4c3b-b46d-0167aa3c22f5)

Finally a dashboard was created for the the four charts

![image](https://github.com/MYZDEE/Data-Analysis---SQL/assets/128803445/a646d024-2967-4658-adca-fb7afd5896f7)











  
  
 
