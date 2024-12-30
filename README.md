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
