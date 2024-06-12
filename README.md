# Atlas Labs HR Analytics: Power BI Project

![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/scott-graham-5fNmWej4tAA-unsplash.jpg)

## Overview
The core goal of this case study is to build a report using fictitious datasets from a tech company called Atlas Labs. The Atlas Labs HR team wants to monitor key metrics related to employees. Their secondary goal is to understand what factors impact employee attrition.

## Background
This project uses fictitious data from Atlas Labs, a leading tech company. The motivation behind this project is to demonstrate the power of data analytics in the HR domain, helping organizations make data-driven decisions. The analysis focuses on understanding workforce dynamics and identifying key factors that influence employee satisfaction and attrition.

## Project Objectives
- Analyze HR metrics to understand workforce dynamics and trends.
- Identify factors influencing employee attrition and retention.
- Provide actionable recommendations to improve HR strategies and organizational performance.

## Dashboard Link
The report contains 4 interactive pages:

![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/Overview%20Page.png)
![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/Demographics%20Page.png)
![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/Performance%20Tracker%20Page.png)
![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/Attrition%20Page.png)

Access the Power BI dashboard [here](https://app.powerbi.com/view?r=eyJrIjoiOWVmNTM0ZDQtOTYxOS00NGNhLWE4YWItOTlkNGMyNGMxMzQzIiwidCI6IjQ5MWM2ZTNhLTA3MjItNDhmMi1iMDFhLWFhMzliODc0MGYxNiJ9).

## Project Components

### Data Processing
#### Requirements Gathering, Data Connections, and Data Transformation
For this case study, we use the Kimball modeling approach to model our data. The fact table stores the information about employee yearly reviews. We also work with multiple dimension tables to provide more context to the data we are analyzing. The final data model follows a snowflake schema.

#### Data Loading
1. **Open an empty PowerBI file and load and prepare the dataset:** 
    - Import all the CSV files and load them into PowerBI.
    - Ensure that the data is clean. Refer to [this article]([link-to-article](https://dev.to/datawired22/data-analysis-flow-in-5-steps-using-powerbi-jm1)) for the expectations of clean data.
    - Add either "Fact" or "Dim" at the beginning of each table name, depending on the type of table it is.

#### Data Cleaning
1. **Cleanse the data to remove duplicates, handle missing values, and ensure data integrity.**
2. **Structure and format the data for analysis:**
    - Rename datasets and verify data types.
    - Ensure proper formatting of text, numbers, or dates.

### Data Preparation
1. **Building the Data Model: Date Dimension and Relating Tables:**
    - Create a dedicated date table for accurate date and time reporting. Here is the DAX code for the calculated Date Table:
    ```DAX
    DimDate = 
    ADDCOLUMNS (
        CALENDAR (DATE(2000, 1, 1), DATE(2050, 12, 31)),
        "Year", YEAR([Date]),
        "Month", MONTH([Date]),
        "Day", DAY([Date]),
        "Quarter", QUARTER([Date]),
        "MonthName", FORMAT([Date], "MMMM"),
        "DayName", FORMAT([Date], "DDDD")
    )
    ```

2. **Connecting Tables:**
    - Connect the `DimDate` table to `FactPerformanceRating` and the `DimEmployee` table. Note that the last relationship will be inactive due to PowerBI's limitations on multiple active relationships between the same tables.
    - Connect the `DimEducationLevel` table to the `DimEmployee` table.
    - Connect `FactPerformanceRating` table columns (`EnvironmentSatisfaction`, `JobSatisfaction`, `RelationshipSatisfaction`, and `WorkLifeBalance`) to the `DimSatisfactionLevel` table, using `EnvironmentSatisfaction` as the active connection.
    - Connect `FactPerformanceRating` table columns (`SelfRating`, `ManagerRating`) to `DimRatingLevel` using the `SelfRating` column as the active connection.

### Data Analysis
1. **Exploratory Data Analysis (EDA):** Explore HR metrics and identify patterns, trends, and outliers.
2. **Attrition Analysis:** Analyze factors contributing to employee attrition, including demographics, job satisfaction, and performance ratings.
3. **Performance Metrics:** Create custom measures to quantify employee performance, satisfaction, and engagement.
### Data Modeling
- **Performance Ratings Fact Table:** Central to our analysis, containing yearly employee reviews with 11 columns and multiple rows per employee.
- **Dimension Tables:** Five dimension tables—Employee, Education Level, Rating Level, Satisfied Level, and Date—provide contextual information, enriching our exploration.
- **Calculated Table:** Dim — Date table links the Fact — Performance Rating table and Dim — Employee table, with secondary inactive relationships to adhere to Power BI's limitations.

You can find the data model below: ![](https://github.com/yanny-alt/Atlas-Labs-HR-Analytics-Power-BI-Project/blob/main/Images/Atlas%20Labs%20HR%20Data%20Model.png)

### Key Columns
- **Performance Ratings Fact Table:** PerformanceID, EmployeeID, ReviewDate, EnvironmentSatisfaction, JobSatisfaction, RelationshipSatisfaction, WorkLifeBalance, SelfRating, ManagerRating, TrainingOpportunitiesWithinYear, TrainingOpportunitiesTaken.
- **Dimension Tables:** EmployeeID, FirstName, LastName, Gender, Age, BusinessTravel, Department, DistanceFromHome, State, Ethnicity, Education, EducationField, JobRole, MaritalStatus, Salary, StockOptionLevel, Overtime, HireDate, Attrition, YearsAtCompany, YearsInMostRecentRole, YearsSinceLastPromotion, YearsWithCurrManager, SatisfactionID, SatisfactionLevel, RatingID, RatingLevel, EducationID, EducationLevel.

### Insights and Recommendations
1. **Insights from Dashboard:** 
- Atlas Labs has employed over 1,470 people.
- Currently, Atlas Labs employs over 1,200 people.
- The largest department by far is Technology.
- The attrition rate for employees leaving the organization is 16%.
- The majority of employees are between 20-29 years old.
- Currently, Atlas Labs employs 2.7% more women than men.
- Employees who identify as non-binary make up 8.5% of total employees.
- White employees have the highest average salary, while those from 'Mixed or multiple ethnic groups' have one of the lowest average salaries.

2. **Recommendations:**
   - Address high attrition in sales roles and among frequent travelers.
   - Review travel requirements and gather employee feedback to mitigate travel-related attrition.
   - Implement strategies to improve job satisfaction and work-life balance.
   - Enhance support and career development for diverse employee groups.

## Conclusion
This HR Analytics Project using Power BI offers valuable insights into workforce dynamics and employee retention strategies. By leveraging data-driven insights, organizations can optimize HR processes, enhance employee satisfaction, and drive organizational success.

## Data Cleaning and Preparation Process
- **Data Loading:** Load and prepare the dataset, renaming datasets and verifying data types.
- **Formatting:** Ensure proper formatting of text, numbers, or dates.

## Data Transformation Process
- **Calculated Columns and Measures:** Create calculated columns and measures for detailed analysis.
- **Relationships:** Establish relationships between tables to create a cohesive data model.

## Measures Created
- **TotalEmployees:** 
  ```DAX
  TotalEmployees = DISTINCTCOUNT('Dim - Employee'[EmployeeID])

- **InactiveEmployees:**
  ```DAX
   InactiveEmployees = CALCULATE([TotalEmployees], 'Dim - Employee'[Attrition] = "Yes")

 - **% Attrition Rate:**
   ```DAX
   % Attrition Rate = DIVIDE([InactiveEmployees],[TotalEmployees])
   
- **TotalEmployeesDate:**
  ```DAX
  TotalEmployeesDate = CALCULATE([TotalEmployees], USERELATIONSHIP('Dim - Employee'[HireDate], DimDate[Date]))

  - **JobSatisfaction:**
  ```DAX
   JobSatisfaction = MAX('Fact - PerformanceRating'[JobSatisfaction])
  
- **EnvironmentSatisfaction:**
  ```DAX
  EnvironmentSatisfaction = CALCULATE(MAX('Fact - PerformanceRating'[EnvironmentSatisfaction]), USERELATIONSHIP('Fact - PerformanceRating'[EnvironmentSatisfaction],'Dim - SatisfiedLevel'[SatisfactionID]))

- **RelationshipSatisfaction:**
  ```DAX
  RelationshipSatisfaction = CALCULATE(MAX('Fact - PerformanceRating'[RelationshipSatisfaction]), USERELATIONSHIP('Fact - PerformanceRating'[RelationshipSatisfaction],'Dim - SatisfiedLevel'[SatisfactionID]))

- **WorkLifeBalance:**
  ```DAX
  WorkLifeBalance = CALCULATE(MAX('Fact - PerformanceRating'[WorkLifeBalance]), USERELATIONSHIP('Fact - PerformanceRating'[WorkLifeBalance],'Dim - SatisfiedLevel'[SatisfactionID]))

- **SelfRating:**
  ```DAX
  SelfRating = CALCULATE(MAX('Fact - PerformanceRating'[SelfRating]), USERELATIONSHIP('Fact - PerformanceRating'[SelfRating],'Dim - RatingLevel'[RatingID]))

- **ManagerRating:**
  ```DAX
  ManagerRating = CALCULATE(MAX('Fact - PerformanceRating'[ManagerRating]), USERELATIONSHIP('Fact - PerformanceRating'[ManagerRating],'Dim - RatingLevel'[RatingID]))



