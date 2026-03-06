# retail-sales-analytics-powerbi
Power BI dashboard analyzing retail sales, customer insights, and product performance using DAX and interactive visualizations.
Retail Sales Analytics Dashboard (Power BI)
This project analyzes retail sales data to generate insights into revenue performance, customer behavior, product trends, and transaction patterns using Power BI and DAX.
The dashboard includes interactive filters, drill-down capabilities, and role-based access control.

![dashboard](https://github.com/user-attachments/assets/532b2dba-4f6f-41d0-997c-5ebca587fa15)

_____<img width="1240" height="658" alt="dashboard page (2)" src="https://github.com/user-attachments/assets/fba97391-fa25-4fdc-9776-a50ba3850d7b" />
___________________________________
Project Objectives
The dashboard answers key business questions such as:
•	What is the total revenue generated?
•	How many transactions occurred?
•	Which product categories perform best?
•	What are the customer demographics?
•	How do revenue and transactions trend over time?
 
 

Cleaning begins
•	Removed duplicate values
•	Checked for error or emply values through column distribution
•	Checked and standardized formatting
•	Created dimension tables (customer and product)
•	Removed dimension columns from fact table (which are already present in 
Create Data Model (Star Schema) 	 

1. Key Performance Indicators (KPIs)
Total Revenue
Revenue is calculated using quantity sold multiplied by the unit price.
Total Revenue =
SUMX(
    Sales,
    Sales[Quantity] * Sales[Price per Unit]
)

Total Transactions
Total Transactions = COUNTROWS(Sales)

Average Revenue per Transaction
Avg Revenue per Transaction =DIVIDE(    [Total Revenue],   [Total Transactions])

Total Quantity Sold
Total Quantity Sold = SUM(Sales[Quantity])

Revenue by Product Category
Visual used:
•	Bar Chart
•	Axis → Product Category
•	Values → Total Revenue
This shows which product categories generate the most revenue.

Revenue Distribution by Gender
Visual used:
•	Pie Chart
•	Legend → Customer Gender
•	Values → Total Revenue
This highlights differences in purchasing behavior between male and female customers.

Average Transaction Value by Category
Avg Transaction Value =DIVIDE(  [Total Revenue],    DISTINCTCOUNT(Sales[TransactionID]))
Visual used:
•	Column Chart
•	Axis → Product Category
•	Values → Average Transaction Value
This helps identify categories with the highest-value transactions.
Average Customer Age
Average Customer Age =AVERAGE(dimcustomers[Age])
This provides insight into the demographic profile of customers.

2. Charts & Visualizations
Sales Overview
Revenue Trend Over Time
Visual used:
•	Line Chart
•	Axis → Date
•	Values → Total Revenue
This visualizes how revenue changes across daily, weekly, and monthly periods.

Revenue by Product Category
Visual used:
•	Bar Chart
•	Axis → Product Category
•	Values → Total Revenue
This highlights top-performing product categories.

Customer Insights
Revenue by Gender
Visual used:
•	Pie Chart
•	Legend → Gender
•	Values → Total Revenue

Customer Age Distribution
Customer ages were grouped using bins of size 10.
Example groups:
•	Teens & Kids (<20)
•	Young Adults (20–30)
•	Adults (30–50)
•	Seniors (50+)
Visual used:
•	Column Chart
•	Axis → Age Groups
•	Values → Customer Count

Product Performance
Sales by Category and Month
Visual used:
•	Stacked Column Chart
Fields:
•	Axis → Date[Month]
•	Legend → Product Category
•	Values → Total Revenue
This shows how each category performs over time.

Top 10 Customers
Visual used:
•	Bar Chart
Fields:
•	Axis → Customer Name
•	Values → Total Revenue
A Top N filter was applied to display the top 10 customers by revenue.

Transaction Trends
Revenue vs Transactions by Month
Visual used:
•	Clustered Column Chart
Fields:
•	Axis → Month
•	Values → Total Revenue
•	Values → Total Transactions
This allows comparison between sales volume and transaction frequency.

Correlation Between Quantity Sold and Revenue
Visual used:
•	Scatter Plot
Fields:
•	X-axis → Quantity
•	Y-axis → Total Revenue
This helps analyze whether higher quantities lead to higher revenue.

3. Navigation & Filtering
Interactive navigation was implemented using Power BI slicers.
Filter by Date Range
•	Slicer type → Between
•	Field → Date
Users can dynamically filter data across a custom time range.

Filter by Customer
•	Slicer type → Dropdown
•	Field → Customer ID
Allows viewing transactions for specific customers.

Filter by Product Category
•	Slicer field → Product Category
Users can view data for a single category or multiple categories.
4. Drill-Down Functionality
Drill-down hierarchies allow users to explore data at different levels of detail.
Example hierarchy:
Year → Month → Day
Users can drill from yearly trends down to daily transactions directly within visuals.
This enables deeper analysis such as:
•	Viewing sales trends for a specific category
•	Analyzing customer purchase patterns
•	Investigating transactions for a particular date

5. Row-Level Security (RLS)
Row-Level Security was implemented to restrict data access based on user roles.
Sales Manager Role
Role name:
sales_manager
Rule applied:
Sales[Region] = "North"
This ensures the Sales Manager only sees data for the North region.

Product Manager Role
Role name:
product_manager
Rule applied:
Products[Category] = "Electronics"
This ensures the Product Manager only sees sales related to the Electronics category.

Technologies Used
•	Power BI
•	DAX (Data Analysis Expressions)
•	Power Query
•	Data Modeling
•	Row-Level Security (RLS)

Key Insights
The dashboard enables stakeholders to:
•	Monitor revenue performance over time
•	Identify top-performing product categories
•	Analyze customer demographics and behavior
•	Track transaction patterns and correlations
•	Implement secure role-based data access

