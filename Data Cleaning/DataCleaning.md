## Data Cleaning and Transformation Steps
### 1. **Standardizing Job Titles**

Many job titles referred to the same role but were labeled differently (e.g., “Junior Data Analyst”). Used conditional logic (IF statements) to standardize these variations into consistent titles (e.g., any title containing “Data Scientist” was standardized to “Data Scientist”).

![IF Statement - Roles ](../docs/jobrolespay.png)

### 2. **Handling Company Size Values**

To analyze which company sizes offer the highest salaries, I filtered out rows in the Size column where the values were -1 or “unknown,” since these represented missing or invalid information. Only 44 rows were removed.

### 3. **Extracting Salary Ranges**

Extracted the minimum and maximum salary values from the **Salary Estimate** column, which originally contained a salary range along with the source label “Glassdoor est.” I extracted the numerical values by isolating all text to the left of the opening bracket. From the cleaned salary range, created two separate columns: **Min Sal** and **Max Sal**.

### 4. **Extracting State Abbreviations**

The Location column contained mixed formats, some values included a city and state, while others (e.g., “Remote,” “United States,” or single states) contained no comma. Splitting by comma initially created nulls.
To resolve this, I created artificial commas for locations that lacked one. I also grouped values such as “Remote” and “United States” into a single category labeled “Other.”

I created a custom column called **Location Correction** using an IF statement to assign a comma to each value. 
        

![State Abbreviations ](../docs/locationcorrection.png)

After correcting all values in this way, I split the **Location Correction** column by the comma delimiter to extract the state abbreviation.

### 5. **Calculating Salaries by Role**

To determine which roles paid the best, I duplicated the query and named it “Sal by Role Type dup.”
I kept only the relevant columns: **Min Sal**, **Max Sal**, and **Role Type**.

Changed Min and Max salary columns to Currency and multiplied values by 1,000 to reflect monetary values.

<img src="../docs/multiply.png" width="70%" />

Used Group By on Role Type and calculated:
- Average Min Salary
- Average Max Salary
- Row Count
- All Rows (for exploration)
<!-- 
 ![Calculating Salaries ](docs/salcalculation.png)
-->

<img src="../docs/salcalculation.png" width="50%" />

✅  The results showed that Data Scientist roles had the highest average salary.

![Calculating Salaries ](../docs/HighestSalaries.png)

### 6. **Calculating Salaries by Company Size**
Repeated Step 5 and used columns: **Min Sal**, **Max Sal**, and **Size**.
Used Group By on Role Type and calculated:
- Average Min Salary
- Average Max Salary
- Row Count
  
<img src="../docs/companysizeandpay.png" width="70%" />

 ✅ The results showed that Companies with 51 to 200 employees have the highest average salary

### 7. Calculating Salary by State

To analyze which states offered the highest salaries, I needed to match the state abbreviations in the dataset with their full state names. The challenge was that the dataset only contained state abbreviations in the State Abbr column, without the corresponding full names.

To fix this:

- I imported a State Mapping Table which containtained a list of state full names and their corresponding two letter abbreviations.

- Prepared the Data for Merging
   - Before merging, I ensured that the values in the State Abbr column were clean and consistent. This included applying Trim to remove unwanted spaces and ensure character length consistency.

- Merged the Queries
  - I performed a Left Join between the main dataset and the state mapping table, matching on the 2-letter state abbreviation. This allowed me to bring in the full state names for accurate grouping and reporting.

<img src="../docs/mergecolumns.png" width="70%" />


- Calculated Average Salaries by State
        - After merging, I grouped the data by State and calculated average Min and Max salary values.

**Results:**

✅ Delaware showed the highest average salary, although this was based on only one record.

✅ North Carolina, with 9 records, had the next highest average salary and provided a more reliable sample size.


<img src="../docs/paybystate.png" width="70%" />
