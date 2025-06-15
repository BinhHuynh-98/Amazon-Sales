# Amazon Sales Data Analysis Project

## Overview
This project analyzes Amazon sales data to provide insights into product performance, pricing strategies, customer behavior, and market trends. The analysis helps both sellers and customers make informed decisions based on comprehensive data analysis.

## Features
- **Data Cleaning and Preparation**
  - Price standardization
  - Rating normalization
  - Missing value treatment
  - Duplicate removal
  - New metric calculations

- **Price Analysis**
  - Price range categorization
  - Discount level analysis
  - Savings calculation
  - Price trend analysis

- **Customer Behavior Analysis**
  - Rating distribution
  - Review volume analysis
  - Customer trust indicators
  - Price sensitivity analysis

- **Product Performance Metrics**
  - Category-wise analysis
  - Price range distribution
  - Discount effectiveness
  - Rating patterns

## Getting Started

### Prerequisites
- Python 3.x
- Required Python packages:
  - pandas
  - numpy
  - jupyter

### DAX Measure Power BI
Total Products = COUNTROWS('Amazon Sales')
Average Rating = AVERAGE('Amazon Sales'[rating])
Average Discount = AVERAGE('Amazon Sales'[discount_percentage])
Total Categories = DISTINCTCOUNT('Amazon Sales'[category])

// Price Metrics
Total Original Price = SUM('Amazon Sales'[actual_price])
Total Discounted Price = SUM('Amazon Sales'[discounted_price])
Total Savings = [Total Original Price] - [Total Discounted Price]
Average Savings = AVERAGE('Amazon Sales'[actual_price] - 'Amazon Sales'[discounted_price])
Average Price = AVERAGE('Amazon Sales'[discounted_price])

// Rating Metrics
Products with High Ratings = CALCULATE(
    COUNT('Amazon Sales'[product_id]),
    'Amazon Sales'[rating] >= 4
)
High Rating Percentage = DIVIDE(
    [Products with High Ratings],
    [Total Products],
    0
)

// Review Metrics
Total Reviews = SUM('Amazon Sales'[rating_count])
Average Reviews per Product = DIVIDE(
    [Total Reviews],
    [Total Products],
    0
)

// Category Analysis
Products per Category = 
ADDCOLUMNS(
    VALUES('Amazon Sales'[category]),
    "Product Count", CALCULATE(COUNT('Amazon Sales'[product_id]))
)

Category Average Rating = 
AVERAGEX(
    VALUES('Amazon Sales'[category]),
    CALCULATE(AVERAGE('Amazon Sales'[rating]))
)

// Price Range Groups
Price Range = 
SWITCH(
    TRUE(),
    'Amazon Sales'[discounted_price] <= 500, "Budget (≤500)",
    'Amazon Sales'[discounted_price] <= 2000, "Mid-Range (501-2000)",
    'Amazon Sales'[discounted_price] <= 5000, "Premium (2001-5000)",
    "Luxury (>₹5000)"
)

// Discount Range Groups
Discount Range = 
SWITCH(
    TRUE(),
    'Amazon Sales'[discount_percentage] <= 10, "Low (≤10%)",
    'Amazon Sales'[discount_percentage] <= 30, "Medium (11-30%)",
    'Amazon Sales'[discount_percentage] <= 50, "High (31-50%)",
    "Very High (>50%)"
)

// Top Products
Top Rated Products = 
TOPN(
    10,
    'Amazon Sales',
    'Amazon Sales'[rating],
    'Amazon Sales'[rating_count]
)

Best Value Products = 
TOPN(
    10,
    'Amazon Sales',
    'Amazon Sales'[discount_percentage]
)

// Calculated Columns
Savings Amount = 'Amazon Sales'[actual_price] - 'Amazon Sales'[discounted_price]
Savings Percentage = DIVIDE(
    'Amazon Sales'[actual_price] - 'Amazon Sales'[discounted_price],
    'Amazon Sales'[actual_price],
    0
)

// KPI Calculations
Rating KPI Status = 
IF(
    [Average Rating] >= 4, 1,
    IF([Average Rating] >= 3, 0, -1)
)

Discount KPI Status = 
IF(
    [Average Discount] >= 25, 1,
    IF([Average Discount] >= 15, 0, -1)
)

// Dynamic Ranking
Product Rank by Rating = 
RANK.EQ(
    'Amazon Sales'[rating],
    'Amazon Sales'[rating],
    DESC
)

Category Rank by Sales = 
RANKX(
    ALL('Amazon Sales'[category]),
    CALCULATE(SUM('Amazon Sales'[discounted_price]))
) 


