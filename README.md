# Data Cleaning in Power Query

This project showcases my data cleaning and transformation skills using Power Query. The dataset contains job postings for Data Science related roles and was sourced from Kaggle and saved locally as an Excel file for processing.
## Objective
The goal of this project is to clean, prepare, and structure the data so that meaningful insights can be extracted. In particular, the analysis aims to answer the following key questions:
- **Which job titles or roles offer the highest salaries?**
- **Which states provide the best compensation for data professionals?**
- **What company sizes tend to pay the most?**
---
## Methodology
### **Data Source and Import**

The dataset used in this project contains job postings for Data Science–related roles. It was sourced from Kaggle and imported into Power Query from a locally stored CSV file. The objective was to clean, standardize, and prepare the data so meaningful insights could be drawn during analysis.

---
## Data Cleaning and Transformation Steps
### 1. **Standardizing Job Titles**

Many job titles referred to the same role but were labeled differently (e.g., “Junior Data Analyst”). Used conditional logic (IF statements) to standardize these variations into consistent titles (e.g., any title containing “Data Scientist” was standardized to “Data Scientist”).

![IF Statement - Roles ](docs/ifStatementJobRoles.png)

### 2. **Handling Company Size Values**

To analyze which company sizes offer the highest salaries, I filtered out rows in the Size column where the values were -1 or “unknown,” since these represented missing or invalid information. Only 44 rows were removed.

### 3. **Extracting Salary Ranges**

Extracted the minimum and maximum salary values from the **Salary Estimate** column, which originally contained a salary range along with the source label “Glassdoor est.” I extracted the numerical values by isolating all text to the left of the opening bracket. From the cleaned salary range, created two separate columns: **Min Sal** and **Max Sal**.

### 4. **Extracting State Abbreviations**

The Location column contained mixed formats, some values included a city and state, while others (e.g., “Remote,” “United States,” or single states) contained no comma. Splitting by comma initially created nulls.
To resolve this, I created artificial commas for locations that lacked one. I also grouped values such as “Remote” and “United States” into a single category labeled “Other.”

I created a custom column called **Location Correction** using an IF statement to assign a comma to each value. 
        

![State Abbreviations ](docs/generating-commas.png)

After correcting all values in this way, I split the **Location Correction** column by the comma delimiter to extract the state abbreviation.

### 5. **Calculating Salaries by Role**

To determine which roles paid the best, I duplicated the query and named it “Sal by Role Type dup.”
I kept only the relevant columns: **Min Sal**, **Max Sal**, and **Role Type**.

Changed Min and Max salary columns to Currency and multiplied values by 1,000 to reflect monetary values.

Used Group By on Role Type and calculated:
- Average Min Salary
- Average Max Salary
- Row Count
- All Rows (for exploration)
<!-- 
 ![Calculating Salaries ](docs/salcalculation.png)
-->

<img src="docs/salcalculation.png" width="50%" />

The results showed that Data Scientist roles had the highest average salary.

![Calculating Salaries ](docs/HighestSalaries.png)

### 6. **Calculating Salaries by Company Size**
Repeated Step 5 and used columns: **Min Sal**, **Max Sal**, and **Size**.
Used Group By on Role Type and calculated:
- Average Min Salary
- Average Max Salary
- Row Count
  
<img src="docs/companysizeandpay.png" width="70%" />

 The results showed tht Companies with 51 to 200 employees have the highest average salary

### 7. Calculating Salary By State


## 📂 Repository Structure

```
Data-Cleaning-In-Power-Query/
│
├── datasets/                           # Raw datasets used for the project 
│
│   ├── Uncleaned_DS_jobs.csv           # Raw data from Kaggle in csv format
│   ├── State_mapping.xlsx              # State mapping table with full names of states
│   ├── CleanedData.xlsx                # Excel file of relevant columns that are cleaned and transformed
│
├── docs/                               # Screenshots showing different techniques applied during cleaning cleaning and transformations                       
│
└── README.md                           # Project overview
```
---
