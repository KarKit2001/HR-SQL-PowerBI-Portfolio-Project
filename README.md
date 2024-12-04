# Human Resources Data Analysis Project
![Capture](https://github.com/user-attachments/assets/6020ea34-f873-4d4b-836d-c945d7ff1bd8)

![Capture_1](https://github.com/user-attachments/assets/58341b73-1a07-4b7e-9e65-ea41953e77b5)

## 📖 Project Overview
This project involves analyzing a Human Resources (HR) dataset to gain insights into employee demographics, turnover rates, tenure, and other key metrics. The data cleaning and analysis were conducted using MySQL, and the findings were visualized in Power BI for better understanding and presentation.

## 1. 🎯 Objective
The primary objective of this project is to clean and analyze the HR dataset to answer key business questions, such as:

- Gender and race breakdown of employees
- Age distribution and tenure of employees
- Employee turnover rates by department
- Geographical distribution of employees
- Changes in employee count over time

## 2. 📊 Dataset Walkthrough  
The dataset was sourced from [Her Data Project](https://herdataproject.gumroad.com/l/hr-dataset), a data analyst YouTuber.  

### Dataset Columns:  
- `id`: Employee ID  
- `first_name`, `last_name`: Employee names  
- `birthdate`: Date of birth  
- `gender`: Gender  
- `race`: Ethnicity  
- `department`: Department of employment  
- `jobtitle`: Job title  
- `location`: Work location  
- `hire_date`: Employment start date  
- `termdate`: Employment end date (if applicable)  
- `location_city`, `location_state`: City and state of the location  

## 3. 🧹 Cleaning the Data
Data cleaning was performed using SQL with the following steps:  
##### 1. Corrected inconsistent date formats for `birthdate`, `hire_date`, and `termdate` columns.  
##### 2. Converted term dates to a valid format and addressed invalid term dates.  
##### 3. Added an `age` column using `birthdate` to calculate the employees’ ages.  
##### 4. Excluded records with negative ages or term dates in the future.  
##### 5. Ensured consistency and validity across key columns.  

Key SQL transformations included:  
```sql
UPDATE hr
SET birthdate = CASE
	WHEN birthdate LIKE '%/%' THEN date_format(str_to_date(birthdate, '%m/%d/%Y'), '%Y-%m-%d')
    ELSE NULL
END;

ALTER TABLE hr
MODIFY COLUMN birthdate DATE;

UPDATE hr
SET age = timestampdiff(YEAR, birthdate, CURDATE());
```

## 4.🔍 Data Analysis
Key business questions addressed include:  
#### 1. **Gender Breakdown:** Gender distribution of employees currently employed.  
#### 2. **Race/Ethnicity Breakdown:** Ethnic distribution of active employees.  
#### 3. **Age Distribution:** Youngest, oldest employees, and distribution across age groups.  
#### 4. **Location Distribution:** Number of employees working in headquarters vs. remote locations.  
#### 5. **Average Employment Length:** Average tenure of terminated employees.  
#### 6. **Departmental Turnover:** Highest turnover rates by department.  
#### 7. **Employee Growth Over Time:** Yearly hiring and termination trends.  

## 5. 📈 Visualization in Power BI  
The cleaned dataset was imported into Power BI to create interactive visualizations, including:  
- Gender distribution  
- Changes in employee numbers (2000-2020)  
- Average length of employment for terminated employees  
- Employee count by state  
- Race distribution  
- Headquarters vs. remote distribution  
- Age distribution by gender  
- Age group distribution  
- Gender distribution by department

## 6. 📋 Summary of Findings  
- **Gender Distribution:** There are more male employees than female.  
- **Employee Growth:** The net change in employees has increased over the years.  
- **Average Tenure:** Terminated employees had an average tenure of 8 years.  
- **State Distribution:** Ohio has the highest number of employees.  
- **Race/Ethnicity:** White employees dominate, while Native Hawaiian and American Indian are the least represented.  
- **Work Location:** Most employees work at the headquarters compared to remote locations.  
- **Age Groups:** Employees are predominantly aged 35-44, followed by 25-34 and 45-54. The smallest group is 55-64.  
- **Turnover by Department:** The Auditing and Legal departments have the highest turnover rates, while Marketing has the least.  
- **Gender by Department:** Gender distribution across departments is fairly balanced, though males are slightly more prevalent.  

## 7. 🙏 Acknowledgment  
Special thanks to **Her Data Project**, a data analyst YouTuber, for providing the dataset and inspiration for this analysis.  

---  

Feel free to explore the code and visualizations further for insights or to expand upon this analysis!  
