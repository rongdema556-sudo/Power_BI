# Power_BI
```
-- Base measure: Total Sales Amount
Total Sales = 
SUMX ( 
    Sales, 
    Sales[Quantity] * Sales[UnitPrice] 
)

-- Prior Year Sales using Time Intelligence
Sales Prior Year = 
CALCULATE (
    [Total Sales],
    SAMEPERIODLASTYEAR ( 'Date'[Date] )
)

-- Year-over-Year Growth % with safe division
YoY Sales Growth % = 
VAR CurrentSales = [Total Sales]
VAR PriorSales = [Sales Prior Year]
VAR SalesDifference = CurrentSales - PriorSales
RETURN
    DIVIDE ( 
        SalesDifference, 
        PriorSales, 
        0 
    )
```
