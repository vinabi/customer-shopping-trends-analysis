# DAX Formulas Reference  

This document outlines the DAX formulas used in the Power BI dashboard for advanced calculations and insights.  

---

## 1. Age Categories  
### Purpose:  
Categorize customers into predefined age groups for demographic analysis.  
```dax
Age Category = 
SWITCH(
    TRUE(),
    ShoppingTrends[Age] < 18, "Under 18",
    ShoppingTrends[Age] >= 18 && ShoppingTrends[Age] <= 25, "18-25",
    ShoppingTrends[Age] >= 26 && ShoppingTrends[Age] <= 35, "26-35",
    ShoppingTrends[Age] >= 36 && ShoppingTrends[Age] <= 50, "36-50",
    "50+"
)
```

## 2. Total Purchase Amount by Customer
### Purpose:
Calculate the total amount spent by each customer.
```dax
Total Purchase Amount = 
SUM(ShoppingTrends[purchase_amount_usd])

```

## 3. Customer Loyalty Score
### Purpose:
Measure customer loyalty based on the number of previous purchases.
```dax
Loyalty Score = 
SUM(ShoppingTrends[previous_purchases])
```

## 4. High-Value Purchasers Flag
### Purpose:
Identify customers who are high-value purchasers based on a threshold.
```dax
High Value Purchaser = 
IF(
    ShoppingTrends[Total Purchase Amount] > 1000, 
    "Yes", 
    "No"
)
```

## 5. Gender-Based Purchase Frequency
### Purpose:
Calculate the total purchase frequency grouped by gender.
```dax
Gender Purchase Frequency = 
CALCULATE(
    SUM(ShoppingTrends[frequency_of_purchases]), 
    ALLEXCEPT(ShoppingTrends, ShoppingTrends[gender])
)
```
## 6. Top 5 Countries by Purchase Amount
### Purpose:
Retrieve the top 5 countries by total purchase amount for geographical analysis.
```dax
Top 5 Countries = 
TOPN(
    5, 
    SUMMARIZE(
        Customer_Shopping_Trends, 
        Customer_Shopping_Trends[location], 
        "Total Purchase Amount", 
        SUM(Customer_Shopping_Trends[purchase_amount_usd])
    ), 
    [Total Purchase Amount], 
    DESC
)
```

## 7. Shipping Type Popularity
### Purpose:
Count the popularity of each shipping type in the dataset.
```dax
Shipping Popularity = 
COUNTROWS(ShoppingTrends)
```

## 8. Seasonal Trends
### Purpose:
Analyze the purchase trends across different seasons.
```dax
Seasonal Trends = 
CALCULATE(
    SUM(Customer_Shopping_Trends[purchase_amount_usd]), 
    ALLEXCEPT(Customer_Shopping_Trends, Customer_Shopping_Trends[season])
)
```

## 9. Key Performance Indicators (KPIs)
### Total Sales
```dax
Total Sales = 
SUM(ShoppingTrends[purchase_amount_usd])
```

### Average Purchase Amount
```dax
Average Purchase Amount = 
AVERAGE(ShoppingTrends[purchase_amountusd])
```

### Average Review Rating
```dax
Copy code
Average Review Rating = 
AVERAGE(ShoppingTrends[review_rating])
```

These DAX formulas were essential in deriving insights and visualizations for the Power BI dashboard.


### Let me know if you need further adjustments or additional formulas! 😊
