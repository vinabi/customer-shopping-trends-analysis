# Data Transformation Steps

This document outlines the data cleaning and transformation steps applied to prepare the dataset for analysis in Power BI.

---

## 1. Initial Data Load
Either from here-> https://docs.google.com/spreadsheets/d/e/2PACX-1vRoYzH5DRko2FEHJunpG79Wb93ZF-UwNX9M1Xge4oweLXM16hwXrhA-y4U4iBN400wejpOOWmMl6Yz7/pubhtml
or above files, load the dataset into powerBI.

---

## 2. Data Cleaning & Preprocessing
### Step 1: Rename Table
- Renamed the table to `Customer_Shopping_Trends` for clarity and consistency.

### Step 2: Column Name Refinement
- Standardized column names to be descriptive and consistent:
  - `Customer ID` → `customer_id`
  - `Age` → `age`
  - `Gender` → `gender`
  - `Item Purchased` → `item_purchased`
  - ... and so on.

### Step 3: Remove Extra Columns
- Removed unnecessary columns that do not contribute to analysis.

### Step 4: Split "Color-Size" Column
- Split the `color-size` column into two separate columns:
  - **Color**: Extracted color names.
  - **Size**: Extracted size descriptions.

### Step 5: Handle Review Ratings
- **Original Issue**: Ratings were stored as text (`YES`/`NO`) or invalid values (`3.1`).
- **Solution**: Converted ratings to numerical:
  - Used a conditional transformation to map valid ratings (`3.1`) into a decimal type.
  - Mapped non-numerical values (`YES`/`NO`) to appropriate numerical representations (`1` for YES, `0` for NO).

### Step 6: Map Purchase Frequency
- Mapped textual purchase frequencies into numerical equivalents:
  - `Weekly` → `7`
  - `Biweekly` → `14`
  - `Monthly` → `30`
  - `Quarterly` → `90`
  - ... and so on.

---

## 3. Data Type Adjustments
- Ensured accurate data types for all columns:
  - `customer_id` → Whole Number
  - `age` → Whole Number
  - `gender` → Text
  - `purchase_amount_usd` → Decimal Number
  - `review_rating` → Decimal Number
  - `subscription_status` → Text
  - `frequency_of_purchases` → Whole Number
  - ... and others accordingly.

---

## 4. Save & Load to Power BI Model
- Applied all transformations and loaded the cleaned dataset into Power BI for visualization.

---

These steps ensure the dataset is clean, structured, and ready for analysis in Power BI.
