# My_DSA_Capstone_Project_KMS_Case_Study

This is the second part of my capstone project, it contains the information about KMS case study.

## Project Topic:  Kultra Mega Stores Inventory Analysis

### Project Overview
This is a data analysis project of Kultra Mega Stores (KMS), headquartered in Lagos, Nigeria which specialises in office supplies and furniture.
Its customer base includes individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria. 
As a Business Intelligence Analyst supporting the Abuja division of KMS the Business Manager has shared an Excel file containing order data from 2009 to 2012.
This data will be analyzed and key insights will be presented along with the findings .

### Data Source
The source of this data is from Kultra Mega Stores (KMS) provided by DSA Incubator hub for educational purpose.

### Tools Used
  - SQL Server Management Studio(SSMS)
  - Github (portfolio building and projuct documentation)

### Data Cleaning and Preparation
During this phase, the following was performed
  1. Reviewing and cleaning of data in MS Excel with no duplicates found after checking, the file was saved to CSV UTF-8 format.
  2. Created a new database (KMS_db) in SQL(SSMS) using queries and proceeded to imported the cleaned data saved to CSV UTF-8 format.

### Exploratory Data Anaysis
This process involves exploring of dataset from Kultra Mega Stores(KMS) to answer some questions in both Case scenarios provided.
1. Which product category had the highest sales?
2. What are the Top 3 and Bottom 3 regions in terms of sales?
3. What were the total sales of appliances in Ontario?
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method?
6. 6. Who are the most valuable customers, and what products or services do they typically purchase?
7. Which small business customer had the highest sale?

### SQL queries and outputs

create database KMS_db
----select * from [dbo].[KMS SQL CASE STUDY(10)]

----Question 1; product caegory with highest sales---

Select Product_Category, sum(sales) AS total_sales
from [dbo].[KMS SQL CASE STUDY (10)]
group by Product_category
order by total_sales desc 

Question 2; top 3 and bottom 3region by sales

---top 3
select top 3 region,
sum(sales) AS  total_sales
from [dbo].[KMS SQL CASE STUDY (10)]
group by region
order by Total_sales desc;

select top 3 region,
sum(sales) AS total_sales
from[dbo].[KMS SQL CASE STUDY (10)]
group by Region
order by Total_sales asc;

Question 3; Total sales of appliances in Ontario

select region, sum(sales) as [total sales]
from [dbo].[KMS SQL CASE STUDY (10)]
where Product_sub_category = 'Appliances'
and region = 'Ontario'
group by Region

----QUESTION 5; WHICH SHIPPING METHOD INCURRED THE MOST SHIPPING COST

SELECT TOP 3 Ship_mode,
sum(Shipping_Cost) as [totalshipping cost]
from [dbo].[KMS SQL CASE STUDY (10)]
group by ship_mode
order by [totalshipping Cost] desc;

--QUESTION 6; who is the most valuable customer, what product or service do they purchase?

 select top 3 
customer_name, Product_Sub_Category, product_name,
sum(sales) as totalsales
from [dbo].[KMS SQL CASE STUDY (10)]
group by customer_name, Product_Sub_Category, Product_Name
order by totalsales desc;

---QUESTION 7; small business owners with the highest sales

select top 1
Customer_Name, Customer_Segment,
sum(sales) as totalsales
from [dbo].[KMS SQL CASE STUDY (10)]
where Customer_Segment = 'small business'
group by customer_name, customer_segment
order by totalsales desc;

--Question 8; corporate customer with most orders in 2009-2012


select top 1
Customer_Name, Customer_Segment, 
COUNT(Order_ID)as totalsales
from [dbo].[KMS SQL CASE STUDY (10)]
where Customer_Segment = 'Corporate'
and Order_Date BETWEEN '2009-01-01' and '2012-12-31'
group by customer_name, customer_segment
order by Totalsales desc;

---Question 9; consumer customer with the highest profit

select top 1
Customer_Name, Customer_Segment,
sum(Profit)as totalprofit
from [dbo].[KMS SQL CASE STUDY (10)]
where Customer_Segment = 'Consumer'
group by Customer_Name, Customer_Segment
ORDER BY Totalprofit DESC;

### Key Insights and Findings
The following findings were concluded upon;
 1. Technology has the highest sales with over 5,984,248.175
 2. Top 3 and bottom 3 regions are:
Top 3
    i. West(3,597,549.269)
    ii. Ontario(3,063,212.476)
    iii. Prarie(2,837,304.605)
Bottom 3
    i. Nunavut(116,376.483)
    ii. Northwest Territories(800,847.331)
    iii. Yukon(975,867.376)
3. Total sales of appliances in Ontario 202,346.839
5. The shipping method with the most cost is Delivery Truck with over 51,971.939
6. The most valuable customers are:
   i. Emily Phan
   ii. Jasper Cacioppo
   iii. Craig Carreira
They all bought (Polycom ViewStation™ ISDN Videoconferencing Unit)
7. The small busineses owner with the highest sales is Dennis Kane with over 75,967.593
8. The corporate customer with the most order in 2009-2012 is Adam Hart with total order of 27
9. The most profitable consumer consumeris Emily Phan with profit of 75,967.593
    
   

