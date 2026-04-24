# <ins>Retail-Cleaning-Project</ins>

The dataset looks at transactions across 8 categories of products. It gives details such as whether the purchase was made online or instore, customerID and the amount spent in each transaction.

In this project I will use abbreviations for a few category names. I will use 'EHE' abbreviation for 'Electric Household Essentials' and 'FUR' for 'Furniture'.
______________________________________
The data source provides 3 tables:
    * Main table with transaction details (retail_store_sales tab in Excel file)
    * Item table for Electric Household Essentials with Item details on Item Code, Price and Item Name (EHE tab)
    * Item table for Furniture with Item details on Item Code, Price and Item Name (FUR tab)

## Business Objective: Clean retail store sales

The goal was to find issues with the dataset and then clean it using Excel functions and 2 look up tables with information on some products and their prices.

Key Excel techniques/functions used:
- TRIM()
- XLOOKUP()

## Workflow:
1. Find missing values. I found missing values in the following columns:
    * Item Code
    * Price Per Unit
    * Quantity
    * Total Spent
    * Discount   
3. Calculate Price per Unit using Total_Spent/Quantity. I found that where Quantity is blank, Total Spent is also blank.
4. Deduce Item Code from Price

     
Tool used: Excel

## Key Insights


## File Structure

## Note

Data source: https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning
