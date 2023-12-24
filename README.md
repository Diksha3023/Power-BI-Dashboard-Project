 **Introduction**<br>
Welcome to the Sales Dashboard project! This dashboard provides a comprehensive overview of sales data, enabling users to analyze and make informed business decisions.<br>
**Features**<br>
* Interactive charts and graphs<br>
* Real-time sales data updates<br>
* User-friendly interface<br>
**Data Analysis using Power BI**<br>
  1. **Data cleaning**:<br>
  * Remove rows containing null values in the markets table.<br>
  * Cleaning negative values from the sales amount column of transactions table.<br>
  * converting the USD currency of some of the rows into INR.<br>
  * removing the duplicate INR and USD currencies.<br>
  2. **Different DAX functions used to create different measures**<br>
  * To create measure for total revenue:<br>
  Revenue = SUM('sales transactions'[norm_sales_amount])<br>
  * To create measure for total sales quantity:<br>
  Sales Qty = SUM('sales transactions'[sales_qty])<br>
  * To create measure for Top Customer:<br>
    Top Customer = SELECTCOLUMNS(CALCULATETABLE('sales customers',FILTER('sales customers','sales customers'[customer_code]== SELECTCOLUMNS(TOPN(1,SUMMARIZE('sales transactions','sales transactions'[customer_code],"Amount",SUM('sales transactions'[norm_sales_amount])),[Amount],DESC),"top",[customer_code]))),"Name",[custmer_name])<br>
  * To create measure for Top Product:<br>
    Top Product = SELECTCOLUMNS(TOPN(1,SUMMARIZE('sales transactions','sales transactions'[product_code],"Amount",SUM('sales transactions'[norm_sales_amount])),[Amount],DESC),"top",[product_code])<br>
  
  
  
  
  

