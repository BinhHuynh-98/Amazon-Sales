# Amazon Sales Data Analysis Project

## Overview
This project analyzes Amazon sales data to provide insights into product performance, pricing strategies, customer behavior, and market trends. The analysis helps both sellers and customers make informed decisions based on comprehensive data analysis.

## Project Structure
```
Amazon Sales/
├── amazon.csv                 # Raw Amazon sales dataset
├── amazon_cleaned.csv         # Cleaned dataset ready for analysis
├── Amazon_Data_Cleaning_Basic.ipynb  # Jupyter notebook for data cleaning
├── Amazon_Sales_Insights_Report.md   # Comprehensive analysis report
└── README.md                  # This file
```

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

### Installation
1. Clone the repository:
```bash
git clone [repository-url]
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

### Usage
1. Data Cleaning:
   - Open `Amazon_Data_Cleaning_Basic.ipynb` in Jupyter Notebook
   - Run the cells to clean the dataset
   - The cleaned data will be saved as `amazon_cleaned.csv`

2. Analysis:
   - Review the insights in `Amazon_Sales_Insights_Report.md`
   - Use the cleaned dataset for further analysis

## Key Insights

### For Sellers
- Optimal pricing strategies
- Discount effectiveness
- Category performance
- Product improvement opportunities

### For Customers
- Best times to purchase
- Price range recommendations
- Category-specific insights
- Value for money indicators

## Data Dictionary

### Main Columns
- `product_name`: Name of the product
- `discounted_price`: Current selling price
- `actual_price`: Original price
- `discount_percentage`: Discount offered
- `rating`: Product rating (1-5)
- `rating_count`: Number of ratings
- `category`: Product category
- `subcategory`: Product subcategory

### Calculated Columns
- `savings_amount`: Difference between actual and discounted price
- `savings_percentage`: Percentage of savings
- `price_range`: Categorized price range
- `discount_range`: Categorized discount level

## Future Enhancements
1. Time-series analysis of price trends
2. Seasonal discount patterns
3. Category-specific customer behavior
4. Competitive analysis within price ranges
5. Impact of ratings on sales performance

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- Amazon for providing the dataset
- Contributors and maintainers of the project

## Contact
For any questions or suggestions, please open an issue in the repository.

---
*Note: This project is for educational and analytical purposes only. All data used is publicly available and anonymized.* 