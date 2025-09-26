# Retail 2023 Spend Prediction 🛍️

## About  
This project addresses a **customer-level spend prediction problem** using retail invoice data.  
The task is to forecast **the total amount each customer will spend in 2023**, given historical purchases from 2021–2022 and partial 2023 records.  
The evaluation metric is the **R² score**.  

---

## Data Processing Workflow  

### 1. Preprocessing  
- Removed canceled invoices (those with `Invoice` IDs starting with `C`).  
- Converted mixed date formats (`InvoiceDate`) into a unified Gregorian calendar.  
- Handled missing values (`Customer ID`, `Description`, `UnitPrice`, etc.).  
- Calculated **transaction value** for each row as:  
  **Transaction Value = Quantity × UnitPrice**

### 2. Feature Engineering  
- Aggregated data at the **customer level**.  
- Built yearly features (2021, 2022) such as:  
  - total spend  
  - average basket size  
  - number of transactions  
- Constructed the **target variable** as the sum of spending for each customer in 2023.  

### 3. Modeling  
- Baseline models: Linear Regression, Random Forest.  
- Main model: **linear Regression** tuned for regression.  
- Used cross-validation to avoid overfiting.  

### 4. Prediction  
- Generated predictions for each **Customer ID** in the test set.  
- Saved results to a CSV file named **`submission.csv`** with the format:  

| Customer ID | Prediction |
|-------------|------------|
| 0           | 2100.2334  |
| 1           | 909.2300   |
| 2           | 230.1202   |
| 3           | 12222.0000 |

