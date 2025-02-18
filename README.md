# Adventure-Works-Sales-Dashboard

## Project Overview 
The Adventure Works Sales Dashboard is an interactive, multi-page dashboard designed to provide comprehensive insights into the company’s sales performance. Built using Power BI, the dashboard spans seven pages, each offering a unique perspective on key sales metrics, customer insights, product performance, and market trends. The dashboard aims to support data-driven decision-making by delivering actionable insights to stakeholders.

## Project Objectives:
### Analyze Overall Sales Performance:
-Track key performance indicators (KPIs) such as total revenue, profit, order count, and return rate.

-Identify monthly trends in revenue, orders, and returns for better forecasting.

### Understand Customer Behavior:
-Analyze customer segmentation based on total revenue, order volume, and annual income.

-Explore customer performance through detailed statistics and year-based comparisons.

### Evaluate Product Performance:

The product page of the Adventure Works dashboard includes the following product metrics for selection: return quantity, return rate, total orders, total revenue, profit,

Profit and price adjustment, total order and revenue target, total order and profit target, and total order and order target.

### Geographical Insights:

-Utilize a map visualization to assess sales distribution across Europe, North America, and the Pacific.

### Visualize order trends by category to uncover demand patterns.

### Key Influencer Identification:

### Interactive Insights via Q&A:

Enable dynamic exploration of data through a Q&A interface.
Allow users to query the dashboard using natural language for quick insights.

## Data Source

Dataset has been provided by Crisp Academy ,here is the dataset for adventure work [Click Here](https://github.com/Zaki1203/Adventure-Works-Sales-Dashboard/blob/main/AdventureWorks%2BRaw%2BData.zip)

## Tools

I've utlized microsoft powerbi for data cleaning using power query and creating interactive dashboard

## Data Preparation

First, unzip the folder and open Power BI. Select the folder containing the sales data and load it into Power BI by choosing the appropriate folder column. Click on 'Combine and Load' to import the data. Subsequently, load the remaining tables one by one. Once the data is loaded, perform a data type inspection for each column, Do basic data cleaning removing duplicates,unnessary columns and add new measure columns

## Data Modelling 

Once our data is Prepared we will do Data modelling 

![image](https://github.com/user-attachments/assets/7fa439e3-10d9-4839-916c-debd3e54f20a)


## Dax
Anuualincome_Grade = IF('Customer Lookup'[AnnualIncome] >= {150000},"Very High",IF('Customer Lookup'[AnnualIncome]>={100000},"High",IF('Customer Lookup'[AnnualIncome]>={50000},"Average",IF('Customer Lookup'[AnnualIncome]<={50000},"Low"))))

Eduacation_Category = SWITCH('Customer Lookup'[EducationLevel],
"High School","High School",
"Partial high School","High school",
"Bachelors","Undergrad",
"Partial College","Undergrad",
"Graduate Degree","Graduate"
)

top = IF([srannk]<=Parameter[Parameter Value],[Total Revenue])

Customer Metrics Selection = {
    ("Total Customer", NAMEOF('Calendar Lookup'[Total Customer]), 0),
    ("Total Revenue Per Customer", NAMEOF('Calendar Lookup'[Total Revenue Per Customer]), 1)
}

Price Adjustment Value = SELECTEDVALUE('Price Adjustment'[Price Adjustment])

Product Metric Selection 2 = {
    ("Profit", NAMEOF('Sales Data'[Profit]), 0),
    ("Returned Qt", NAMEOF('Returns Data'[Returned Qt]), 1),
    ("Returned_Rate", NAMEOF('Sales Data'[Returned_Rate]), 2),
    ("Total Orders", NAMEOF('Calendar Lookup'[Total Orders]), 3),
    ("Total Revenue", NAMEOF('Sales Data'[Total Revenue]), 4)
}

Returned Qt = COUNT('Returns Data'[ReturnQuantity])

Adjusted Profit = [Adjusted Revenue]-SUMX('Sales Data',RELATED('Product Lookup'[ProductCost]))

Adjusted Revenue = SUMX('Sales Data',[Adjusted Price]*'Sales Data'[OrderQuantity])

Profit = [Total Revenue]-[Total Cost]

Retail_Price = RELATED('Product Lookup'[ProductPrice])

Returned_Rate = DIVIDE([Returned Qt],[sales qt],"No sales")

sales qt = SUM('Sales Data'[OrderQuantity])

Total Cost = SUMX('Sales Data',RELATED('Product Lookup'[ProductCost])*'Sales Data'[OrderQuantity])

Total Revenue = SUMX('Sales Data',RELATED('Product Lookup'[ProductPrice])*'Sales Data'[OrderQuantity])

## Dashboard Overview 

![image](https://github.com/user-attachments/assets/9f5f079f-7b24-4653-ba69-c098938c1d22)

![image](https://github.com/user-attachments/assets/c03bd610-7b19-4f69-a01c-4b2753f00e5b)

![image](https://github.com/user-attachments/assets/b8f9005a-6155-4728-b27d-8453e1fb28e1)

![image](https://github.com/user-attachments/assets/bc91349b-360f-43ed-a5cc-b192ba5bb0fe)

![image](https://github.com/user-attachments/assets/e348fdfb-c1ba-41d4-b2de-f6380575ace8)

![image](https://github.com/user-attachments/assets/e9a4cd57-ab2c-4167-ad11-3706beb76e6f)

![image](https://github.com/user-attachments/assets/27b6d799-3ee2-402f-8e08-ac704ddd51ee)


## Key Insights


-Total Revenue is 24.91M ,10.5M Profit, 25.16K Orders, 2.1% Return Rate
-There was peaking trend in high revenue in jan 2022
-monthly revenue 1.83M, Monthly orders 2146 ,Monthly Returns 166
-Most of the catergory sold are from accessories
-water bottle -30oz has the highest total orders
-fender set mountain has the highest total revenue 
-Sport 100 helmet,Red has highest return rate of 3.3%
-17.4k total customers,1.43k total revenue per customer
-most orders are ordered by professional
-mr.maurice shan is top customer by revenue with 12.41k
-us has the highest number of orders







