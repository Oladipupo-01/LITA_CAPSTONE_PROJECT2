# LITA_CAPSTONE_PROJECT2
A documentation of my project assessment for LITA by The Incubator Hub
## Project Title: Customer Segmentation for a Subscription Service

## Project Overview:
This project involves analyzing customer data for a subscription service to identify 
segments and trends. The goal is to understand customer behavior, track subscription types,identify key trends in cancellations and renewals and present a dashboards that visualizes the insight 
### Tools used:
- Microsoft Excel
  1 For data cleaning
  2 For data exploration
  3 For data analysis
- Structured Query language(SQL) FOR quering data.
- Power BI for data visualization.

## Exploratory Data Analysis: 
Data Cleaning and Exploration: The data given has

## Data Exploration: Excel and SQL
In Excel: I carried out exploration by using pivot table to summarize
-
-
-

![Screenshot (45)](https://github.com/user-attachments/assets/b3ba612e-b876-4424-af55-e84461d1607b)

I used excel for to calculate
-
-

![Screenshot (46)](https://github.com/user-attachments/assets/99ec2ea3-223a-4172-86c3-d09d271b2da0)




In SQL: I wrote the queries to extract insight  from the following questions
- Total Number of Customer By Region
```
select Region,
count(CustomerID) as TotalCustomerbyRegion from [dbo].[LITA Capstone Customer]
 Group by Region
```

- Most Popular Subscription Type
```
select SubscriptionType, count(CustomerName) as MostPopularSubscritionType from [dbo].[LITA Capstone Customer]
 Group by SubscriptionType
 Order by SubscriptionType asc
```

 - Total Revenue by Subscription Type
 ```
select SubscriptionType,
 sum(Revenue) as TotalRevenue from [dbo].[LITA Capstone Customer]
group by SubscriptionType
order by SubscriptionType asc
```

- Top 3 Region By Subscription Cancellation
```
select top 3 Region,
count(CustomerID) as Top3CancellationbyRegion
from [dbo].[LITA Capstone Customer]
where Canceled = '1'
group by Region
order by Top3CancellationbyRegion desc
```

- Active and Cancelled Subscription
```
select SubscriptionType, count(CustomerID) as ActiveSubscription
from [dbo].[LITA Capstone Customer]
where Canceled = '0'
group by SubscriptionType

select SubscriptionType, count(CustomerID) as CancelledSubscription
from [dbo].[LITA Capstone Customer]
where Canceled = '1'
group by SubscriptionType
```

- CUSTOMER WHO CANCELLED WITHIN 6 MONTH
```
select CustomerID, CustomerName,Region, SubscriptionType,SubscriptionStart,SubscriptionEnd,Canceled
from  [dbo].[LITA Capstone Customer]
where Canceled = '0'
and DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
```

- Average subscription duratioon
```  
select avg(datediff(day, SubscriptionStart, SubscriptionEnd)) as AverageSubscription
from [dbo].[LITA Capstone Customer]
```
- Customer with subscription loonger than 12 months
```
select CustomerID, CustomerName,Region, SubscriptionType,SubscriptionStart,SubscriptionEnd,Canceled
from  [dbo].[LITA Capstone Customer]
where datediff(month, SubscriptionStart, SubscriptionEnd) > 12
```

### Visualization and Reporting with PowerBI
I developed an ineractive dashboard using PowerBI to visualizee the sales performance of the Subscription Service. The dashboard provides key insights into 
-
-
-
It allows users to filter data by product and region.


![Screenshot (40)](https://github.com/user-attachments/assets/7281097c-3930-4c71-8a12-769ec37193b3)




