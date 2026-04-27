# <ins>Retail-Cleaning-Project</ins>

The dataset looks at transactions across 8 categories of products. It gives details such as whether the purchase was made online or instore, customerID and the amount spent in each transaction.

In this project I will use abbreviations for a few category names. I will use 'EHE' abbreviation for 'Electric Household Essentials' and 'FUR' for 'Furniture'.
______________________________________
The data source provides 3 tables:
1. Main table with transaction details (retail_store_sales tab in Excel file)
2. Item table for Electric Household Essentials with Item details on Item Code, Price and Item Name (EHE tab)
3. Item table for Furniture with Item details on Item Code, Price and Item Name (FUR tab)

## Business Objective: Clean retail store sales

The goal was to find issues with the dataset and then clean it using Excel functions and 2 look up tables with information on some products and their prices.

Tool Used: Excel

Key Excel techniques/functions used:
- TRIM()
- XLOOKUP()

## File Structure
Imgs - Screenshots of work

## Workflow:
### Step 1. Profile the data with Excel Power Query

I used Excel column statistics and column quality to find the following:

1. Missing values in the following columns:
    * Item Code
    * Price Per Unit
    * Quantity
    * Total Spent
    * Discount
  
2. 12,575 transactions. One row per transaction
3. 25 unique customers
4. Transactions made across 3yrs from 2022-25 (01/01/2022 to 18/01/2025)

View 'Profiling.png' image in the Imgs folder for a sample of null columns as shown by column quality feature
    
### Step 2. Calculate Price per Unit using Total_Spent/Quantity. 

To fill in missing Price values, I used Total_Spent/Quantity.
I found that where Quantity is blank, Total Spent is also blank.

### Step 3. Insert values for Item Code from Look Up Tables to Main Table

I inserted Item Code into the main table for Furniture. To do this I used XLOOKUP to insert values for Item Code from the Item table into the main table, using Price Per Unit as the lookup value. Please see the screenshot named "XLOOKUP (FUR) (find values for Item Code)" in the Imgs folder. I repeated the same steps for Electric Household Essential transactions. I encountered a problem when using XLOOKUP where it would fill the entire column, therefore replacing correct values for Item Code for other categories with incorrect values from Electric Household Essentials Item Code. To solve this, I used "Undo Calculated Column" command as shown in the screenshot named "XLOOKUP (EHE) Undo Flashfill.png" in the Imgs folder.
     
## Key Insights


## Note

Data source: https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning
