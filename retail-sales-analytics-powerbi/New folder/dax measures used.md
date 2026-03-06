1\. Total Revenue



Calculates total revenue by multiplying quantity sold with price per unit for each transaction.



Total Revenue =

SUMX(

&nbsp;   Sales,

&nbsp;   Sales\[Quantity] \* Sales\[Price per Unit]

)

2\. Total Transactions



Counts the total number of transactions recorded.



Total Transactions =

COUNTROWS(Sales)

3\. Average Revenue per Transaction



Calculates the average value of each transaction.



Avg Revenue per Transaction =

DIVIDE(

&nbsp;   \[Total Revenue],

&nbsp;   \[Total Transactions]

)

4\. Total Quantity Sold



Calculates the total number of products sold.



Total Quantity Sold =

SUM(Sales\[Quantity])

5\. Average Transaction Value



Used to compare transaction value across product categories.



Avg Transaction Value =

DIVIDE(

&nbsp;   \[Total Revenue],

&nbsp;   DISTINCTCOUNT(Sales\[TransactionID])

)

6\. Average Customer Age



Calculates the average age of customers.



Average Customer Age =

AVERAGE(dimcustomers\[Age])

