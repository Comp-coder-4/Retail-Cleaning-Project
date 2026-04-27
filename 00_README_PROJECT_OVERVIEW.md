# <ins>Retail-Cleaning-Project</ins>

The dataset looks at transactions across 8 categories of products. It gives details such as whether the purchase was made online or instore, customerID and the amount spent in each transaction.

Categories include Furniture, Electric Household Essentials, Beverages, Computer and electronic accessories

In this project I will use abbreviations for 2 category names. I will use **'EHE' abbreviation for 'Electric Household Essentials'** and **'FUR' for 'Furniture'**.
______________________________________ 
The data source provides 3 tables:
1. A main table with transaction details
2. A smaller table containing Item Code, Price and Product Name for EHE products (I will refer to this as a look up table)
3. A smaller table containing Item Code, Price and Product Name for FUR products (I will refer to this as a look up table)

## Business Objective: Clean retail store sales

The goal was to find quality issues with the dataset and clean it to improve data quality. This is done using 2 look up tables with product information.

Tool Used: Excel

Key Excel techniques/functions used:
- TRIM()
- XLOOKUP()

## File Structure
1. **data_cleaning.xlsx** - contains cleaning table and look up tables. Contains the following tabs:
   * **cleaning_retail_store_sales** - cleaning the main table
   * **EHE** - Electric Household Essentials look up table
   * **Furniture** - Furntiture look up table
   * **cleaned_retail_store_sales** - cleaned main table
2. **Imgs folder** - contains screenshots
3. **retail_store_sales.csv** - raw data


## Workflow
### Step 1. Profile the data with Excel Power Query

I used Excel column statistics and column quality to find the following:

1) Missing values in the following columns:
    * Item Code
    * Price Per Unit
    * Quantity
    * Total Spent
    * Discount
  
2) 12,575 transactions. One row per transaction
3) 25 unique customers
4) Transactions made across 3yrs from 2022-25 (01/01/2022 to 18/01/2025)

View 'Profiling.png' image in the Imgs folder for a sample of null columns as shown by column quality feature
    
### Step 2. Calculate Price per Unit using Total_Spent/Quantity. 

Price per Unit column had missing values.

To fill in missing Price values, I used Total_Spent/Quantity where possible.

However, where Quantity was blank, Total Spent was also blank. In these cases, I could not calculate Price per Unit.

### Step 3. Use Look Up Tables to insert values for Item Code to Main Table

I inserted Item Code into the main table for Furniture. To do this I first filtered the main table by Category = Furniture. Then I used XLOOKUP in the main table to insert values for Item Code from the lookup table, using Price Per Unit as the lookup value. See the screenshot named "XLOOKUP (FUR) (find values for Item Code)" in the Imgs folder.

To avoid trailing and/or leading spaces from causing an error during the XLOOKUP, I trimmed the Item Code and Price columns in the main table and the two look up tables. See screenshots named "TRIM main table.png", "Lookup table (EHE).png" and "Lookup table (FUR).

I repeated the same steps for Electric Household Essentials, this time filtering the main table to only show Category = Electric Household Essentials. I encountered a problem when using XLOOKUP where it would fill the entire column, therefore replacing correct values for Item Code for other categories with incorrect values from Electric Household Essentials Item Code. To solve this, I used "Undo Calculated Column" command (see screenshot named "XLOOKUP (EHE) Undo Flashfill.png").

### Step 4. Use Look Up Tables to insert values for Item Name to Main Table

I followed similar steps to Step 3 to insert values for Item Name from the lookup tables to the main table. I used XLOOKUP to match Item code values from the lookup tables with the Item code values in main table. See screenshot named "XLOOKUP (EHE) Item Name.png" 

### Step 5. Removing old columns and columns used for calculations

I now had a new Item Code and a new Price Per Unit column that had trimmed values and no missing values. 

However, there was still an old Item Code column and an old Price Per Unit column with missing values (for Categories EHE and FUR). **This meant I still had redundant data**.

I had to remove the old columns since they still had missing values. For the old Item Code column, I first inserted the same XLOOKUP function that I used in the new trimmed Item Code column. However, this produced a #REF! error (see "Replacing old Item Code with values from XLOOKUP Item Code"). This was because the new trimmed Item Code column had functions in its cells.

I realised that retrieving just the values in the new column without functions could solve this. To do this, I copied the entire dataset into a new excel sheet and used "Paste Special > Values" pasting option (see screenshot "Special Paste.png"). This gave me a dataset without any functions in the cells. 

I could now remove the old Item Code and Price Per Unit columns as well as the columns I used to check my XLOOKUP calculations (see "Data with old columns.png" - old columns in red, calculation columns in blue). After removing these columns, a clean dataset remained (see "Clean data.png").

## Data Source

Data source: https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning
