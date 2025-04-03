# Data-Portfolio
This repository contains a collection of some of my projects using tools like SQL, Power bi,project management, business analysis, Python. Each problem focuses on solving a real life problem through data cleaning, analysis and visualisation. The goal is to demonstrate my skills in transforming raw data into actionable insights.
Survey for Data Science Jobs-Dashboard


For the Powerbi Dashboard, Here are the steps taken to do it


## Problem Statement

The goal of this project was to analyze a dataset from a Data Science Jobs Survey to extract meaningful insights. The dataset included various job-related details such as job titles, salary ranges, programming languages used, and work-life balance ratings.

However, since the survey was anonymous, many participants did not follow instructions correctly. Specifically:

Instead of selecting "Other" when their job title was not listed, they manually entered different job descriptions.
This resulted in inconsistencies and redundant categories.
The dataset required cleaning and transformation before meaningful analysis could be performed.
To address these issues, data cleaning, transformation, and appropriate visualizations were applied using Power BI.

### Steps followed 

 1. Data Cleaning & Transformation
 
-Imported the dataset into Power BI.

-Opened the Power Query Editor to preprocess the data.

-Identified unnecessary columns and removed them to keep only relevant information.

-Handled missing values where necessary.

-Extracted and transformed the salary range:

-The given salary values were in ranges (e.g., $40K-$60K).
Converted these ranges into an average salary by dividing the sum of the two salary values by 2.

-Created a new column to store the calculated average salary.
Grouped and Cleaned Job Titles:
Since respondents entered different variations of job titles instead of selecting "Other," the data became messy.
Created groups in Power Query to consolidate job titles into meaningful categories (e.g., combining all variations of "Data Scientist" into a single category).

-Ensured data types were correctly assigned (e.g., numerical values for salary and categorical values for job titles)

2. Data Loading into Power BI
Loaded the cleaned and transformed data into Power BI for visualization.
Ensured that all applied changes were correctly reflected in the dataset.

3. Visualization & Dashboard Design
Selected the most suitable visuals to present insights:
-Bar Chart to display average salary by job title.

-Pie Chart/Column Chart for favorite programming languages.

-Map Visualization for survey participants’ countries.

-Gauge Charts for happiness with salary and work-life balance ratings.

-Stacked Bar Chart for difficulty in breaking into the data field.

-Slicer Filters to allow users to explore data dynamically (e.g., filtering by country or job title).

-Created card visuals to highlight key metrics:
  
 
<img width="426" alt="Image" src="https://github.com/user-attachments/assets/c89300b8-6cf8-41a3-992e-9964d8069345" />


-Total survey responses: 630

-Average age of survey takers: 29.87 years

--Happiness with salary rating: 4.27/10

-Work-life balance rating: 5.74/10

4. Handling Job Difficulty Levels
The dataset included responses on how difficult respondents found breaking into the data field.

---Used a stacked bar chart to visualize different difficulty levels:
-Easy

-Neither easy nor difficult

-Difficult

-Very difficult

Found that a significant percentage of respondents struggled to enter the field.

5. Dashboard Refinement
Adjusted colors, labels, and formatting for clarity.
Ensured interactivity by linking slicers and filters to relevant charts.
Verified that all calculations and aggregations were correct.
Published the dashboard for sharing and interaction.
Key Insights (from Dashboard)

Average Salary by Job Title – Data Scientists, Data Engineers, and Data Architects had the highest salaries.

Popular Programming Languages – Python was the most preferred language, followed by R and C++.

Survey Respondents by Country – The majority of responses came from the United States, followed by India, Canada, and the UK.

Challenges in Entering the Field – A significant portion of respondents found it difficult or very difficult to break into data science.

Happiness with Salary & Work-Life Balance – Overall, respondents rated their salary satisfaction at 4.27/10 and work-life balance at 5.74/10.

 
       
