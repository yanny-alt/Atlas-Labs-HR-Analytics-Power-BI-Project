# Atlas Labs HR Analytics: Power BI Project

## Overview
The core goal of this case study is to build a report using fictitious datasets from a tech company called Atlas Labs. The Atlas Labs HR team wants to monitor key metrics related to employees. Their secondary goal is to understand what factors impact employee attrition.

## Background
This project uses fictitious data from Atlas Labs, a leading tech company. The motivation behind this project is to demonstrate the power of data analytics in the HR domain, helping organizations make data-driven decisions. The analysis focuses on understanding workforce dynamics and identifying key factors that influence employee satisfaction and attrition.

## Project Objectives
- Analyze HR metrics to understand workforce dynamics and trends.
- Identify factors influencing employee attrition and retention.
- Provide actionable recommendations to improve HR strategies and organizational performance.

## Dashboard Link
Access the Power BI dashboard [here](link-to-dashboard).

## Project Components

### Data Processing
1. **Data Collection:** Obtain raw HR data from various sources.
2. **Data Cleaning:** Cleanse the data to remove duplicates, handle missing values, and ensure data integrity.
3. **Data Preparation:** Structure and format the data for analysis.

### Data Analysis
1. **Exploratory Data Analysis (EDA):** Explore HR metrics and identify patterns, trends, and outliers.
2. **Attrition Analysis:** Analyze factors contributing to employee attrition, including demographics, job satisfaction, and performance ratings.
3. **Performance Metrics:** Create custom measures to quantify employee performance, satisfaction, and engagement.

### Data Modeling
- **Performance Ratings Fact Table:** Central to our analysis, containing yearly employee reviews with 11 columns and multiple rows per employee.
- **Dimension Tables:** Five dimension tables—Employee, Education Level, Rating Level, Satisfied Level, and Date—provide contextual information, enriching our exploration.
- **Calculated Table:** Dim — Date table links the Fact — Performance Rating table and Dim — Employee table, with secondary inactive relationships to adhere to Power BI's limitations.

### Key Columns
- **Performance Ratings Fact Table:** PerformanceID, EmployeeID, ReviewDate, EnvironmentSatisfaction, JobSatisfaction, RelationshipSatisfaction, WorkLifeBalance, SelfRating, ManagerRating, TrainingOpportunitiesWithinYear, TrainingOpportunitiesTaken.
- **Dimension Tables:** EmployeeID, FirstName, LastName, Gender, Age, BusinessTravel, Department, DistanceFromHome, State, Ethnicity, Education, EducationField, JobRole, MaritalStatus, Salary, StockOptionLevel, Overtime, HireDate, Attrition, YearsAtCompany, YearsInMostRecentRole, YearsSinceLastPromotion, YearsWithCurrManager, SatisfactionID, SatisfactionLevel, RatingID, RatingLevel, EducationID, EducationLevel.

### Insights and Recommendations
1. **Insights from Dashboard:** 
   - TotalEmployees: 1470 employees.
   - ActiveEmployees: 1233, InactiveEmployees: 237, with an attrition rate of 16.1%.
   - Hiring trends over time, departments, and job roles insights.
   - Demographics insights including age, gender, marital status, and ethnicity.
   - Performance tracker for individual reviews and ratings.
   - Attrition analysis based on demographics, job roles, travel, overtime, and tenure.

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
