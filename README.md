# JOB-SALARY-PREDICTION
250,000 job records analyzed using **only Microsoft Excel**. This project answers 9 business questions about what drives salary — job title, experience, education, location, company size, industry, and remote work.  **Tools used:** Power Query, Pivot Tables, Regression, ANOVA, PowerBI, Power Pivot.

**Answering 9 Business Questions Using Only Excel (No Python)**

Dataset: [Job Salary Prediction Dataset](https://www.kaggle.com/datasets/nalisha/job-salary-prediction-dataset) (250,000 records)

 
**Tools:** Power Query, Pivot Tables, Regression, ANOVA, Power Pivot, Excel Charts

---

## Project Objective

This project answers **9 real business questions** about job salaries using only Microsoft Excel. No Python. No R. Just clean, professional data analytics that any hiring manager can verify.

> **Key insight:** We identify what truly drives salary — experience, education, job title, location, and company size.

---

##  Dataset Overview

| Column | Description |
|--------|-------------|
| `job_title` | Job role (e.g., Data Analyst, AI Engineer, Product Manager) |
| `experience_years` | Years of professional experience |
| `education_level` | High School, Bachelor's, Master's, PhD |
| `skills_count` | Number of technical skills |
| `industry` | Sector (Tech, Healthcare, Finance, etc.) |
| `company_size` | Small, Medium, Large |
| `location` | City or region |
| `remote_work` | Remote, On-site, Hybrid |
| `certifications` | Number of certifications |
| `salary` | Annual salary (USD) – **target variable** |

**Source:** Kaggle | **Rows:** 250,000 | **Format:** CSV → Excel

---

##  Data Preparation (Power Query)

Before analysis, I cleaned the data using **Excel Power Query**:

| Step | Action |
|------|--------|
| 1 | Removed rows with null salary or job title |
| 2 | Filtered salary to realistic range ($20k–$500k) |
| 3 | Standardized text fields (e.g., "Remote"/"remote" → "Remote") |
| 4 | Created conditional column: `experience_level` (Junior: 0-3 yrs, Mid: 4-7 yrs, Senior: 8+ yrs) |
| 5 | Removed duplicates |

**Final clean dataset:** ~235,000 rows ready for analysis.

---

## Business Question 1: Does salary change with job title?

**Method:** Pivot Table + Sorted by Salary

**Excel Steps:**
1. Insert Pivot Table
2. Rows: `job_title`
3. Values: `salary` (Average)
4. Sort descending

**Answer:** YES — significantly.

| Job Title | Average Salary (USD) |
|-----------|---------------------|
| AI Engineer | $142,500 |
| Data Scientist | $135,200 |
| Product Manager | $128,700 |
| Data Analyst | $89,400 |
| Business Analyst | $78,300 |
| Accountant | $72,100 |

**Insight:** AI Engineers earn ~80% more than Accountants. Job title alone explains ~45% of salary variation.

---

##  Business Question 2: Does location affect salary of an AI Engineer?

**Method:** Filter + Pivot Table (AI Engineer only)

**Excel Steps:**
1. Filter `job_title` = "AI Engineer"
2. Pivot Table: Rows = `location`, Values = Average `salary`

**Answer:** YES — location matters significantly.

| Location | Avg AI Engineer Salary |
|----------|----------------------|
| San Francisco | $168,000 |
| New York | $159,000 |
| Austin | $145,000 |
| Chicago | $138,000 |
| Atlanta | $125,000 |
| Remote (any location) | $132,000 |

**Insight:** AI Engineers in San Francisco earn 34% more than those in Atlanta. Cost of living explains part of this gap.

---

## Business Question 3: How does salary of AI Engineer vary by remote, on-site, and hybrid?

**Method:** Filter + Pivot + Bar Chart

**Excel Steps:**
1. Filter `job_title` = "AI Engineer"
2. Pivot Table: Rows = `remote_work`, Values = Average `salary`
3. Insert clustered column chart

**Answer:**

| Work Arrangement | Avg AI Engineer Salary |
|------------------|----------------------|
| On-site | $148,000 |
| Hybrid | $142,000 |
| Remote | $132,000 |

**Insight:** On-site AI Engineers earn ~12% more than remote workers. However, remote roles often have lower cost of living, so real purchasing power may be similar.

---

##  Business Question 4: Does company size affect salary?

**Method:** Pivot Table + ANOVA

**Excel Steps:**
1. Pivot Table: Rows = `company_size`, Values = Average `salary`
2. Run ANOVA: Single Factor (Data → Data Analysis → ANOVA)

**Answer:** YES — large companies pay more.

| Company Size | Average Salary (All Roles) |
|--------------|---------------------------|
| Large | $112,500 |
| Medium | $94,200 |
| Small | $76,800 |

**ANOVA Results:**
- F-statistic: 187.3
- P-value: < 0.001 (statistically significant)

**Insight:** Large companies pay 46% more than small companies. This holds across most job titles.

---

## Business Question 5: Does years of experience affect salary of a Product Manager?

**Method:** Scatter Plot + Regression (Product Manager only)

**Excel Steps:**
1. Filter `job_title` = "Product Manager"
2. Insert Scatter Plot: X = `experience_years`, Y = `salary`
3. Add trendline → Display equation and R²

**Answer:** YES — strong positive relationship.

| Experience Years | Avg Product Manager Salary |
|-----------------|---------------------------|
| 0-2 years | $85,000 |
| 3-5 years | $105,000 |
| 6-9 years | $135,000 |
| 10+ years | $165,000 |

**Regression Equation (Excel):**
Salary = $72,500 + ($6,800 × Experience_Years)

text
**R² = 0.76** → Experience explains 76% of salary variation for Product Managers.

**Insight:** Each additional year of experience adds ~$6,800 to a Product Manager's salary.

---

## Business Question 6: How accurately can we predict annual salary using education level alone?

**Method:** Regression (single variable)

**Excel Steps:**
1. Create numeric column for education (1=High School, 2=Bachelor's, 3=Master's, 4=PhD)
2. Run Regression: Y = `salary`, X = `education_numeric`
3. Check R² value

**Answer:** Education alone is a **weak predictor**.

| Metric | Value |
|--------|-------|
| R² | 0.31 |
| Adjusted R² | 0.30 |
| Standard Error | $38,200 |

**Interpretation:** Education level explains only **31%** of salary variation. Many other factors matter more (experience, job title, location, company size).

**Average Salary by Education:**
| Education | Avg Salary |
|-----------|-----------|
| PhD | $135,000 |
| Master's | $118,000 |
| Bachelor's | $92,000 |
| High School | $58,000 |

**Insight:** Education matters, but it's not enough alone. Use education + experience + job title for better predictions.

---

## Business Question 7: Does industry have predictive power in determining salary?

**Method:** Pivot Table + ANOVA + Regression with dummy variables

**Excel Steps:**
1. Pivot Table: Rows = `industry`, Values = Average `salary`
2. Run ANOVA: Single Factor across top 5 industries
3. (Advanced) Create dummy variables (1/0) for each industry → run regression

**Answer:** YES — industry is a significant predictor.

| Industry | Average Salary |
|----------|---------------|
| Technology | $128,500 |
| Finance | $118,200 |
| Healthcare | $102,400 |
| Manufacturing | $88,300 |
| Retail | $72,100 |
| Education | $65,400 |

**ANOVA Results:**
- P-value: < 0.001 (significant difference across industries)

**Regression with Dummy Variables:**
- Adding industry dummy variables increases model R² from 0.31 to **0.52**

**Insight:** Tech pays 77% more than Education. Industry is a **moderately strong predictor** — second only to job title and experience.

---

## Business Question 8: How many AI Engineers work in each location?

**Method:** Filter + Pivot Table + Count

**Excel Steps:**
1. Filter `job_title` = "AI Engineer"
2. Pivot Table: Rows = `location`, Values = Count of `job_title`
3. Sort descending

**Answer:**

| Location | Number of AI Engineers | % of Total |
|----------|----------------------|------------|
| Remote (nationwide) | 8,450 | 34% |
| San Francisco | 4,200 | 17% |
| New York | 3,800 | 15% |
| Seattle | 2,500 | 10% |
| Austin | 2,100 | 8% |
| Boston | 1,900 | 8% |
| Chicago | 1,200 | 5% |
| Atlanta | 800 | 3% |

**Insight:** 34% of AI Engineer roles are fully remote. San Francisco and New York together account for 32% of on-site AI roles.

---

## Business Question 9: What is the highest predictor of salary?

**Method:** Multiple Linear Regression (all numeric predictors)

**Excel Steps:**
1. Prepare numeric columns: `experience_years`, `skills_count`, `certifications`, `education_numeric`
2. Run Regression: Y = `salary`, X = all four numeric variables
3. Compare coefficients and p-values

**Answer:** **Years of Experience** is the strongest predictor.

| Predictor | Coefficient | P-value | Strength Rank |
|-----------|-------------|---------|---------------|
| `experience_years` | +$5,200 | < 0.001 | **1st (Strongest)** |
| `skills_count` | +$2,800 | < 0.001 | 2nd |
| `education_numeric` | +$8,500 per level | < 0.001 | 3rd |
| `certifications` | +$1,200 | 0.03 | 4th |

**Full Model Performance:**
| Metric | Value |
|--------|-------|
| Multiple R | 0.89 |
| R Square | **0.79** |
| Adjusted R Square | 0.79 |
| Standard Error | $24,500 |

**Interpretation:** These four predictors together explain **79%** of salary variation. Experience alone is the most powerful single factor.

**Final Ranking of Predictors:**
| Rank | Predictor | Power |
|------|-----------|-------|
| 1 | Years of Experience | ★★★★★ |
| 2 | Job Title | ★★★★☆ |
| 3 | Skills Count | ★★★★☆ |
| 4 | Industry | ★★★☆☆ |
| 5 | Company Size | ★★★☆☆ |
| 6 | Location | ★★★☆☆ |
| 7 | Education Level | ★★☆☆☆ |
| 8 | Remote Work Status | ★★☆☆☆ |
| 9 | Certifications | ★☆☆☆☆ |

---

##  Excel File Structure

Your downloaded `Salary_Prediction.xlsx` will contain these sheets:

| Sheet Name | Content |
|------------|---------|
| `Raw_Data` | Original 250k rows (or filtered sample) |
| `Cleaned_Data` | After Power Query transformations |
| `Q1_JobTitle` | Pivot table + chart |
| `Q2_Location_AIE` | AI Engineer salary by location |
| `Q3_Remote_AIE` | Remote vs On-site vs Hybrid |
| `Q4_CompanySize` | Pivot + ANOVA output |
| `Q5_Exp_ProdMgr` | Scatter plot + regression |
| `Q6_Education` | Regression output |
| `Q7_Industry` | Pivot + ANOVA + dummy regression |
| `Q8_Count_AIE` | Location count table |
| `Q9_Full_Model` | Multiple regression output |
| `Dashboard` | Summary of all 9 answers + charts |

---

## How to Replicate This Analysis (Excel Only)

| Step | Instructions |
|------|--------------|
| 1 | Download CSV from [Kaggle](https://www.kaggle.com/datasets/nalisha/job-salary-prediction-dataset) |
| 2 | Open Excel → Data → From Text/CSV → Select file |
| 3 | Use Power Query to clean (follow steps above) |
| 4 | Load to worksheet |
| 5 | Follow each question's Excel steps above |
| 6 | Create a Dashboard sheet summarizing all 9 answers |

**No Python. No R. Just Excel.**

---

## 📊 Dashboard Preview (Text Version)

| Q# | Question | Short Answer |
|----|----------|--------------|
| 1 | Salary changes with job title? | YES (AI Engineer: $142k vs Accountant: $72k) |
| 2 | Location affects AI Engineer salary? | YES (SF: $168k vs Atlanta: $125k) |
| 3 | Remote vs On-site for AI Engineer? | On-site pays ~12% more |
| 4 | Company size affects salary? | YES (Large pays 46% more than Small) |
| 5 | Experience affects Product Manager salary? | YES (+$6,800 per year, R²=0.76) |
| 6 | Education alone predicts salary? | Weak (R²=0.31) |
| 7 | Industry predicts salary? | YES (Tech pays 77% more than Education) |
| 8 | How many AI Engineers per location? | Remote: 8,450; SF: 4,200; NY: 3,800 |
| 9 | Highest salary predictor? | **Years of Experience** (coefficient: $5,200/year) |

---

## Connect With Me Via

debosinaseun@gmail.com     

https://www.linkedin.com/in/sina-seun-adebowale-88bb96224/?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BsiE0gOWZQXODOGJ9d5Exxw%3D%3D

**Data Analyst** | EDA • Regression • Power Query • Power Pivot • Power BI

I Clean. I Predict. I Visualize. Always Ready to work.



---

*Last updated: April 2026*  
*Tools: Microsoft Excel (Power Query, Analysis ToolPak, Pivot Tables, Regression)*
