# LITA_CAPSTONE_PROJECT2
A documentation of my project assessment for LITA by The Incubator Hub
## Project Title: Customer Segmentation for a Subscription Service

## Project Overview:
This project involves analyzing customer data for a subscription service to identify 
segments and trends. The goal is to understand customer behavior, track subscription types,identify key trends in cancellations and renewals and present a dashboards that visualizes the insight.
### Tools used:
- Microsoft Excel
   - For data cleaning
   - For data exploration
   - For data analysis
- Structured Query language(SQL) for Quering data.
- Power BI for data visualization.

## Exploratory Data Analysis: 
Data Cleaning and Exploration: The dataset given contained duplicated records. To gain insight and avoid overstating the outcome,I embarked on removing duplicate and prepare the data for exploration.

## Data Exploration: Excel and SQL
In Excel: I carried out exploration by using pivot table to summarize
- Revenue by region
- Revenue by Subscription type
- Subscription type distribution
- Customer Count by region
- Revenue by region abd subscription type

![Screenshot (45)](https://github.com/user-attachments/assets/b3ba612e-b876-4424-af55-e84461d1607b)

I used excel for to calculate
- Most popular subscription type
- Average subscription duration

![Screenshot (46)](https://github.com/user-attachments/assets/99ec2ea3-223a-4172-86c3-d09d271b2da0)




In SQL: I wrote the queries to extract insight  from the following questions
- Total Number of Customer By Region
```
select Region,
 count(CustomerID) as TotalCustomerbyRegion
  from [dbo].[LITA Capstone Customer]
    Group by Region
```

- Most Popular Subscription Type
```
select SubscriptionType,
  count(CustomerName) as MostPopularSubscritionType
   from [dbo].[LITA Capstone Customer]
     Group by SubscriptionType
       Order by SubscriptionType asc
```

 - Total Revenue by Subscription Type
 ```
select SubscriptionType,
 sum(Revenue) as TotalRevenue
   from [dbo].[LITA Capstone Customer]
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
select SubscriptionType,
 count(CustomerID) as ActiveSubscription
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
 from  [dbo].[LITA Capstone Customer]
```
- Customer with subscription loonger than 12 months
```
select CustomerID, CustomerName,Region, SubscriptionType,SubscriptionStart,SubscriptionEnd,Canceled
   from  [dbo].[LITA Capstone Customer]
     where datediff(month, SubscriptionStart, SubscriptionEnd) > 12
```

### Visualization and Reporting with PowerBI:


I developed an ineractive dashboard using PowerBI to visualizee the sales performance of the Subscription Service. The dashboard provides key insights into

- Total revenue 
- Total number of customer 
- Average revenue per customer
- Average subscription duration
- Subscription type by revenue
- Subscription type by region
- Active and cancelled subscribers

  
It allows users to filter data by product and region.


![Screenshot (40)](https://github.com/user-attachments/assets/7281097c-3930-4c71-8a12-769ec37193b3)


### Inference and Conclusion:

#### Revenue by Region
Inference : his shows how much revenue each region contributed to the overall revenue of the Subscription Service. 

Conclusion:The pivot table show that the 'East' region contributed the highest revenue than other regions to the overall total revenue. This suggest higher customer demand or better market penetration in the region.

Recommendation: It is required that the Subscription Service Company carry out expansion strategy and focus on marketing in the high-revenue region in order to maximize returns. For underperforming region, the company should consider targeted campaign to increase sales.

#### Revenue by Subscription Type 
Inference: The pivot table and pie chart provide insight into which subscription type is the most popular and brings highest return.

Conclusion: The 'Basic' subscription type contribute more revenue than 'Standard' and 'Premium' subscription type. This shoes price sensitivity among customer.

Recommendations: For the 'Standard' and 'Premuim' subscription type, the subscription service should adjust pricing or add more benefits to encourage upgrade. This is to maintain customer satisfaction and loyalty.

#### Customer Count by Region 
Inference: This helps to understand where the most customer are located.

Conclusion: The 'East' region has the highest customer count followed by the 'South' with a margin of 42 count. This indicate high demand in the 'East' thsn other regions.

Recommendation: The region with low customer count 'West' and 'North' should be evaluated and the Subscription Service Company should consider marketing campaign to increase awareness.

#### Average revenue per Customer 
Inference: This indicate the average amount each customer contribute to the total revenue.

Conclusion: The 'South' and 'West' region have a higher average revenue which suggest that customers opted for high value and morr expensive subscription type, while the 'East' and 'North' have a low average revenue.

Recommendation: To increase average revenue, the Subscription Service Company should consider offering value-added services or encourage upgrade.




