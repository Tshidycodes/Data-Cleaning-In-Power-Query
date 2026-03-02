# Data Cleaning & Exploratory Data Analysis in Power Query

This project showcases my ability to clean and transform raw data using Power Query. I thereafter carried out an Exploratory Data Analysis (EDA) to help understand the data, identify patterns and ensure that the data is clean and ready for use. 

---

## Objective
- The primary objective of this project is to clean and transform the dataset to ensure it is ready for analysis.
- To validate the effectiveness of the cleaning process, exploratory analysis was performed to demonstrate that the transformed data could successfully answer questions such as:
- **Which job titles or roles offer the highest salaries?**
- **Which states provide the best compensation for data professionals?**
- **What company sizes tend to pay the most?**

---

## DataSet

The dataset used in this project contains job postings for Data Science–related roles. It was sourced from Kaggle and imported into Power Query from a locally stored CSV file.

---

## Project Workflow
1. Data Collection
2. Data Cleaning & Transformation
3. Exploratory Data Analysis
4. Insights and conclusions
   
---
## Key Insights
 - **Which job titles or roles offer the highest salaries?**
   ✅  The results showed that Data Scientist roles had the highest average salary.

   <img src="docs/salcalculation.png" width="50%" />
   
- **Which states provide the best compensation for data professionals?**
✅ Delaware showed the highest average salary, although this was based on only one record.

✅ North Carolina, with 9 records, had the next highest average salary and provided a more reliable sample size.
<img src="docs/paybystate.png" width="70%" />
  
- **What company sizes tend to pay the most?**
   ✅ The results showed that Companies with 51 to 200 employees have the highest average salary
  <img src="docs/companysizeandpay.png" width="70%" />
---

## Conclusion 
This project successfully demonstrated my ability to clean, transform, and prepare real world job posting data using Power Query. Through standardizing text fields, parsing salary ranges, correcting location data, merging lookup tables, and performing grouped aggregations, the dataset was transformed and fully ready for analysis.

---

## Project Structure

**Data-Cleaning-In-Power-Query/**

├── 📁 [**Data Cleaning**](Data%20Cleaning/) 

│└── 📝 [**DataCleaning.md**](Data%20Cleaning/DataCleaning.md) — Detailed cleaning steps, transformations, and EDA.

├── 📁 [**datasets**](datasets/) — Raw and processed datasets used in this project. 

│    ├── 📄 [**Uncleaned_DS_jobs.csv**](datasets/Uncleaned_DS_jobs.csv) — Original Kaggle dataset. 

│    ├── 📄 [**State_mapping.xlsx**] (datasets/State_mapping.xlsx) — Reference table for state names. 

│    └── 📊 [**CleanedData.xlsx**](datasets/CleanedData.xlsx) — Final cleaned and transformed output.

├── 📁 [**docs**](docs/)— Screenshots of Power Query techniques and transformations.

└── 📄 README.md — Project overview and documentation.


