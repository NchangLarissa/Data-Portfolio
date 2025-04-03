# Data-Portfolio
This repository contains a collection of some of my projects using tools like SQL, Power bi,project management, business analysis, Python. Each problem focuses on solving a real life problem through data cleaning, analysis and visualisation. The goal is to demonstrate my skills in transforming raw data into actionable insights.
Survey for Data Science Jobs-Dashboard


## A. The Powerbi Dashboard for Survey

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



 ## B. The Internship Report Project
In one of my most engaging and challenging projects, I worked on the digitalization of a company’s outdated system, transforming manual processes into an efficient, automated workflow. The company had long relied on Excel spreadsheets to track open requests, deadlines, and linked files, but this system was cumbersome, prone to errors, and lacked real-time visibility. To modernize it, I migrated the entire tracking system from Excel to Microsoft Lists, which provided a more structured and dynamic database while allowing employees to easily view and link files stored in SharePoint. This transition eliminated the inefficiencies of searching through spreadsheets and improved overall data accessibility.
A key part of the digital transformation involved integrating Power BI into SharePoint to provide employees with real-time insights into their outstanding tasks. I designed a dashboard that automatically refreshed and sent out reminders to employees, alerting them about their open requests. To make it even more effective, I implemented color grading, where requests nearing their deadline turned red, creating an immediate visual cue for urgency. This made it easier for employees to prioritize tasks without sifting through large amounts of data manually.
To ensure a seamless workflow, I automated the reminder process using Power Automate, which scheduled and triggered automatic notifications based on deadlines. Employees received timely reminders without the need for manual follow-ups, reducing the risk of missed deadlines and improving efficiency across teams. I also set up Confluence pages to interlink the work of different employees, ensuring that all relevant documents, updates, and progress tracking were connected in a single digital workspace. This integration allowed employees to quickly navigate between linked files and collaborate more effectively, reducing confusion and streamlining project tracking.
One of the most rewarding aspects of this project was watching a slow, manual, and fragmented system transform into an automated, user-friendly, and efficient process. What once required manual updates, scattered emails, and endless spreadsheet tracking was now centralized, automated, and visually clear. Employees no longer had to worry about missing deadlines, misplacing files, or struggling to find relevant information. This project was not only technically challenging but also incredibly fulfilling, as it significantly improved the company’s workflow, enhanced accountability, and saved countless hours of manual effort.


## C. THE SQL data cleaning Project world layoffs
Problem Statement
The project aimed to analyze global layoffs in 2019 by cleaning and transforming the dataset using SQL. The dataset contained information on the number of people laid off, employee _id, their salaries, and other relevant details. However, it had inconsistencies, including duplicate entries, missing values, and unnecessary columns.
To ensure accuracy and reliability in the analysis, I implemented a structured data-cleaning process in SQL while maintaining a backup of the original dataset.
Steps Followed
1. Creating a Staging Table for Backup
Before making any changes, I created a staging table to store a copy of the raw dataset. This allowed me to preserve the original data in case I needed to undo any changes
CREATE TABLE layoffs_staging AS  
SELECT * FROM layoffs_raw;
This step ensured that all transformations were performed on the staging table without affecting the raw data.
2. Identifying and Removing Duplicate Entries
Duplicate records can lead to misleading statistics. To find and remove them, I used the ROW_NUMBER() function inside a Common Table Expression (CT
WITH CTE AS (
    SELECT *, 
     ROW_NUMBER() OVER (PARTITION BY company, date, industry, total_laid_off ORDER BY id) AS row_num  
    FROM layoffs_staging
)  
DELETE FROM layoffs_staging WHERE id IN (SELECT id FROM CTE WHERE row_num > 1);
The PARTITION BY clause grouped data based on company, date, industry, and total layoffs.
The ORDER BY id ensured that duplicate records were numbered.
Any row with row_num > 1 was deleted.
3. Removing Empty or Unnecessary Columns
Some columns contained excessive missing values or were irrelevant for the analysis. To identify these columns, I ran;
SELECT column_name  
FROM information_schema.columns  
WHERE table_name = 'layoffs_staging';

After identifying redundant fields, I removed them using:
ALTER TABLE layoffs_staging  
DROP COLUMN redundant_column1,  
DROP COLUMN redundant_column2;
 
Similarly, I deleted rows where key fields were completely empty:
DELETE FROM layoffs_staging  
WHERE company IS NULL AND industry IS NULL AND total_laid_off IS NULL;
      This ensured that only meaningful data remained.
4. Handling Null or Blank Entries
The dataset contained missing values, especially in salary and industry columns. Different strategies were used based on the type of missing data:
A. Filling Missing Salary Data with Industry Averages
Since salaries are numerical values, replacing NULLs with the industry average salary ensured a reasonable estimate:
UPDATE layoffs_staging  
SET salary = (SELECT AVG(salary)
FROM layoffs_staging WHERE salary IS NOT NULL)  
WHERE salary IS NULL;
B. Assigning Industry Based on Company Data
If the industry column was NULL, I filled it with the industry corresponding to the same company from other records:
UPDATE layoffs_staging a  
SET industry = (SELECT industry FROM layoffs_staging b  
                WHERE a.company = b.company AND b.industry IS NOT NULL  
                LIMIT 1)  
WHERE industry IS NULL;
 
C. Standardizing Blank Values
Many fields had inconsistent blank values (e.g., '' instead of NULL). To standardize
UPDATE layoffs_staging  
SET industry = 'Unknown'  
WHERE industry IS NULL OR industry = '';
This prevented confusion when performing aggregations.
5. Standardizing and Categorizing Job Titles
The dataset contained inconsistent job titles, making it challenging to analyze layoff trends by role. Some people manually entered job descriptions instead of selecting a predefined category.
A. Creating Job Title Groups
To clean the data, I grouped similar job titles into standardized categories:
UPDATE layoffs_staging  
SET job_title = CASE  
    WHEN job_title ILIKE '%data scientist%' THEN 'Data Scientist'  
    WHEN job_title ILIKE '%engineer%' THEN 'Engineer'  
    WHEN job_title ILIKE '%analyst%' THEN 'Analyst'  
    ELSE 'Other'
END;
Any job title that did not fit into key categories was labeled as "Other".
To verify the data was properly cleaned, I checked for any remaining issues.
 
SELECT*
FROM Layoffs_staging WHERE industry IS NULL OR salary IS NULL; -- Ensured no extra deletions occurs
 
Once everything was validated, I created the final cleaned dataset
 
CREATE TABLE layoffs_cleaned AS  
SELECT * FROM layoffs_staging;
 
Key Insights from the Cleaned Data
Total Layoffs: The dataset showed thousands of employees laid off across various industries.
Industry Trends: The tech industry had the highest number of layoffs, followed by finance and retail.
Salary Impact: Employees earning higher salaries were disproportionately affected in executive and management roles.
Geographic Layoff Patterns: Layoffs were concentrated in certain regions, with North America and Europe seeing the highest impact.
Job Difficulty Levels: Some industries had more layoffs than others, making job transitions harder for certain professionals.

## D. The Cocktail Mixer
Last year, I worked on a project with two friends, where we set out to analyze the feasibility of manufacturing a cocktail mixer. While they focused on the mechanical design and DFMEA (Design Failure Mode and Effects Analysis), I was responsible for conducting an in-depth competitor analysis, cost of production assessment, business planning, and market research. One of the biggest challenges we faced was identifying both direct and indirect competitors. Direct competitors included companies that already manufactured cocktail mixers, while indirect competition came from traditional bartending tools, manual shakers, and even pre-made cocktail solutions that eliminated the need for a mixer. Understanding the strengths and weaknesses of these competitors was crucial in figuring out how to position our product uniquely and ensure its viability in the market.
Beyond competition, another major consideration was cost efficiency and production feasibility. To make the business profitable, we examined how we could take advantage of economies of scale, especially when it came to sourcing raw materials, optimizing manufacturing processes, and reducing costs per unit as production volume increased. A key discussion revolved around whether it would be more cost-effective to produce all the components in-house or outsource certain parts. Manufacturing everything internally would give us greater control over quality but could significantly increase costs while sourcing components externally could lower expenses but introduce supply chain dependencies. After careful analysis, we found that strategic outsourcing or buying specific parts while assembling the final product ourselves would strike the best balance between cost savings and quality assurance.
Our business plan focused on pricing strategies, branding, and sales channels to ensure the cocktail mixer could attract customers and generate revenue. We analyzed market demand, identifying potential customers such as home bartenders, event organizers, and even restaurants looking for a convenient and efficient way to mix drinks. By determining an optimal price point that covered production costs while remaining competitive, we developed a plan that could make the business profitable and scalable. The project was both challenging and rewarding, as it provided us with insights into the complexities of product development, market-entry, and business strategy. Through thorough research and planning, we demonstrated that the cocktail mixer could be a commercially viable product with the right execution.

