# Overview

Welcome to My Analysis of the Data Job Market in ***Spain***

This project focuses on data analysis roles in Spain, created from a desire to effectively navigate and understand the job market. It explores top-paying and in-demand skills to identify optimal opportunities for data analysts.

The data is sourced from Luke [Barousse's Python Course](https://www.youtube.com/watch?v=wUSDVGivd-8), which provided a foundation for my analysis, including detailed information on job titles, salaries, locations, and essential skills. Using Python scripts, I address key questions about in-demand skills, salary trends, and the intersection of demand and compensation in data analytics.

# The Questions

Here are the primary questions I aimed to answer in this project:

What are the most in-demand skills for the top three most popular roles?

How are in-demand skills trending for data analysts?

How well do jobs & skills pay for data analysts?

What are the optimal skills for data analysts to learn? (High demand & high-paying skills)

# Tools I Used

For my deep dive into the data analyst job market, I harnessed the power of several key tools:

  - **Pandas Library**: For data manipulation & analysis.
  - **Matplotlib**: To visualize data trends & insights.
  - **Seaborn Library**: For creating advanced & detailed visualizations.
- **Jupyter Notebooks**: To run Python scripts & document notes alongside the analysis.
- **Visual Studio Code**: My preferred IDE for executing Python scripts.
- **Git & GitHub**: For version control & sharing my code & analysis for collaboration. 

# Data Preparation & Cleanup

Preparing the data was an essential step to ensure accuracy & usability for analysis. The process included:

    1. Importing necessary libraries & loading the dataset.

    2. Conducting initial cleaning tasks, such as handling missing or inconsistent entries.

    3. Ensuring the data was structured & ready for analysis by aligning it with the project’s objectives.

This meticulous preparation laid the groundwork for generating reliable insights & actionable findings about the data analyst job market in Spain.

# The Analysis

## 1. What are the most in demand skills for the top 3 most popular data roles?

To find the most in demand skils for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, & got the top 5 skills for the top 3 roles.
This query highlights the most popular job titles & their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](3_Project/2_Skill_Demand.ipynb)

### Visualization Data

```python


fig, ax = plt.subplots (len (job_titles), 1)


for i, job_title in enumerate (job_titles):
    df_plot = df_skills_perc [df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot (data = df_plot, x = 'skill_percent', y = 'job_skills', ax = ax [i], hue = 'skill_count', palette = 'tab10')

plt.show ()

```

### Results

![Visualization of Top Skills for Data Nerds](3_Project/Images/Skills%20Likelihood%20for%20Positions%20in%20Spain.png)

### Key Insights on in Demand Skills for Data Roles in Spain

#### 1. Python: 
##### A highly versatile & in-demand skill, prominently featured in 68% of job postings for Data Scientists & Data Engineers.
#### 2. SQL: 
##### The most sought-after skill for Data Analysts & Data Engineers, appearing in over half of job postings for both roles.
#### 3. Technical Skills for Data Engineers: 
##### Data Engineers are expected to have advanced proficiency in tools such as AWS, Azure, & Spark, setting them apart from Data Analysts & to a lesser extent, Data Scientists.

## Visualize Data

```python
from matplotlib.ticker import PercentFormatter
df_plot = df_DA_Spain_percent.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')

ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter())

```
![Trending Top 5 Data Analysis Skills in Spain](3_Project/Images/Trending%20Top%20Skills%20for%20Data%20Analaysts%20in%20Spain.png)

***Bar graph visualizing the trending top skills for data analysts in Spain in 2023***

### Insights:
- SQL remains the most consistently in demand skill throughout the year, although it shows a gradual fluctuation in demand.
- Both Python & Tableau show a relatively stable demand throughout the year with some flunctuations but they remain essential skills for data analysts.
- Excel & Power BI while both less in demand compared to mostly SQL shows both upward & downward trend throught the year. 

## 2. How are in-demand skills trending for Data Analysis in Spain?

## Visualize Data

```python
from matplotlib.ticker import PercentFormatter
df_plot = df_DA_Spain_percent.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')

ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter())

```
![Trending Top 5 Data Analysis Skills in Spain](3_Project/Images/Trending%20Top%20Skills%20for%20Data%20Analaysts%20in%20Spain.png)

***Bar graph visualizing the trending top skills for data analysts in Spain in 2023***

### Insights:
- SQL remains the most consistently in demand skill throughout the year, although it shows a gradual fluctuation in demand.
- Both Python & Tableau show a relatively stable demand throughout the year with some flunctuations but they remain essential skills for data analysts.
- Excel & Power BI while both less in demand compared to mostly SQL shows both upward & downward trend throught the year.


## 3. How well do jobs & skills pay for Data Analysts?

### Salary Analysis for Data Nerds

```python
sns.boxplot(data=df_Spain_top10.dropna(subset=['job_title_short']), x='salary_year_avg', y='job_title_short', order=job_order)
ticks_x = plt.FuncFormatter(lambda y, pos: f'€{int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.tight_layout()
plt.show()

```
### Results

![Salary Distribution of Data Jobs in Spain](3_Project/Images/Salary%20Distribution.png)

### Insights

- There is a significant variations in salaries across different job titles with Senior Data Scientist & Machine Learning Engineer positions tending to have the highest salary potential with up to €225K, indicating the high value placed on advanced data skills & experience in the industry.

- Business Analysts & Software Engineers show the lowest median salaries of all data jobs but with the widest range of salaries demonstrating solid consistency with virtually non-existant outliers.
- Data Scientists on the other hand, not only have the 3rd lowest median salary but also have the smallest differences in typical salaries with a few outliers on the higher end of the salary spectrum, denoting that exceptional skills or circumstances may lead to higher pay in the roles.

### Highest Paid & Most in Demand Skills for Data Analysts

### Visualize Data

```python

fig, ax = plt.subplots (2, 1)
sns.barplot(data = df_Spain_top_pay, x = 'median', y = df_Spain_top_pay.index, ax = ax [0], hue = 'median', palette="vlag")
sns.barplot(data = df_Spain_DA_skills, x = 'median', y = df_Spain_DA_skills.index, ax = ax [1], hue = 'median', palette = 'mako')
plt.show()

```

### Results
in-demand skills for data analysts in Spain:

![The Highest Paid & Most In-Demand Data Analyst Skills in Spain](3_Project/Images/highest%20paid%20skills.png)
*Two seperate bar graphs visualizing the highest paid skills & most in-demand skills for data analysts in Spain.*

- The top graph shows specialized technical skills like: `npm`, `looker`, `sap`, `angular` as well as Python libraries like `numpy`, `scikit-learn` `matplotlib` all having a seemingly similar salaries with `smartsheet` leading the pack up & reaching a high salary of €160k.

- The bottom graph highlights foundational skils like `looker`, `python` including `jupyter`,  `tableau`, `airflow`, & `sql` are in high demand with high salary with Python leading the pack when including Pandas library & jupyter notebooks.

There's a clear distinction between the skills that are highest paid & those that are most in-demand. Data Analysts aiming to maximize their career potential should consider developping a diverse skill set that includes both high-paying specialized skills & widely in-demand foundational skills.

## 4. What is the most optimal skill to learn for Data Analysts?

#### Visualize Data

```python
import matplotlib.pyplot as plt
from adjustText import adjust_text

plt.scatter (df_Spain_skills_high_demand
['skill_percent'], df_Spain_skills_high_demand 
['median_salary'])
plt.show()
```

### Results

![Most Optimal Skills for Data Analysts in Spain](3_Project/Images/Optimal%20Skills.png)
*A scatter plot visualizing the most optimal skills (high paying & high demand) for data analysts in Spain*

### Insights:

- The scatter plot shows that most of the `libraries`, `analyst_tools` & `programming` knowledge (coloured green, orange & blue respectively) tend to cluster at higher salary levels compared to other categories, indicating that said skills may offer greater salary benefits within the broader data analysis field.

- Although both `Python` & `SQL`  have a lower median salary compared to other skills, they both share the highest percentage of all job postings amongst all other skills. 

- `Cloud` skills share the lowest percentage amongst the other skills as well as having a lower median salary compared to other skills.

# What I Learned

Through this project, I gained valuable insights into the data analyst job market while enhancing my technical expertise in Python. Here are the main takeaways:

   - **Advanced Python Usage**:
    Leveraged libraries like Pandas for data manipulation & Seaborn & Matplotlib for visualization, enabling efficient execution of complex analysis tasks.
   - **Data Cleaning Importance**:  Recognized the critical role of data cleaning & preparation in ensuring accurate & reliable insights.
   - **Strategic Skill Analysis**: Explored the importance of aligning personal skills with market demand, understanding how skill demand, salaries, & job availability influence career planning in tech.

   # Insights

   This project revealed key insights about the data analytics job market in Spain:

   - **Skill Demand & Salary Correlation**: A strong correlation exists between the demand for specific skills and corresponding salaries. Proficient use of tools like ***Python*** & ***SQL*** is often rewarded with a higher compensation.
   - **Market Trends**: The dynamic nature of skill demand underscores the need for continuous learning to stay competitive in the data analytics field.

   - **Economic Value of Skills**: Identifying in-demand and well-compensated skills can help data analysts prioritize learning efforts for optimal career growth.

# Challendges I Faced

The project posed several challenges that offered valuable learning opportunities:

   - **Data Inconsistencies**: Addressing missing or inconsistent entries required meticulous attention to detail and robust cleaning techniques to maintain data integrity.

   - **Complex Data Visualization**: Crafting clear and impactful visualizations of intricate datasets was challenging but critical for conveying insights effectively.
   - **Balancing Breadth & Depth**: Striking a balance between detailed analysis and broader coverage required thoughtful prioritization to ensure comprehensive yet focused results.

   # Conclusion 

 This project offered valuable insights into the data analyst job market, revealing critical skills & trends shaping the field. I learned that skills like Python & SQL are both in high demand & lucrative, underscoring the importance of continuously updating my expertise.

By tackling challenges like data inconsistencies & designing effective visualizations, I gained a deeper appreciation for the complexities of data analysis. This exploration reinforced the value of adaptability & continuous learning, providing a solid foundation for future endeavors in the dynamic field of data analytics.