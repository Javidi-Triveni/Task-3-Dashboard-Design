# DAX Measures for Sales Dashboard

1. Total Sales
```dax
Total Sales = SUM('sales_financial'[Sales])
```
- Returns the total sales amount.



2. Total Profit
```dax
Total Profit = SUM('sales_financial'[Profit])
```
- Returns the total profit amount.

---

3. Total Quantity
```dax
Total Quantity = SUM('sales_financial'[Quantity])
```
- Returns the total quantity sold.


4. Profit Margin %
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
```
- Calculates percentage margin from profit/sales.  
- Format this as **Percentage** in Power BI.



5. Sales YoY % (Year-over-Year Growth)
```dax
Sales YoY % =
VAR CurrentSales = [Total Sales]
VAR LastYearSales =
    CALCULATE(
        [Total Sales],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN DIVIDE(CurrentSales - LastYearSales, LastYearSales, 0)
```
- Compares current year sales with previous year.  
- Needs a proper **Date table** with relationship.



6. Sales MoM % (Month-over-Month Growth)
```dax
Sales MoM % =
VAR PrevMonthSales =
    CALCULATE(
        [Total Sales],
        PREVIOUSMONTH('Date'[Date])
    )
RETURN DIVIDE([Total Sales] - PrevMonthSales, PrevMonthSales, 0)
```
- Shows month-to-month sales growth.


7. Cumulative Sales
```dax
Cumulative Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        ALLSELECTED('Date'),
        'Date'[Date] <= MAX('Date'[Date])
    )
)
```
- Running total of sales over time.


8. Product Rank (by Sales)
```dax
Product Rank =
RANKX(
    ALL('sales_financial'[Product]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
```