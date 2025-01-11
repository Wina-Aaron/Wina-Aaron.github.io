# Indiana Arrest Analysis

## Objective
This project examines arrest data in Indiana, focusing on demographic distributions, offense types, and geographic patterns. Insights are derived through data cleaning, exploratory analysis, and visualizations.

---

## Tools and Libraries
- Python
- Libraries: `pandas`, `geopandas`, `altair`, `matplotlib`, `seaborn`

---

## Key Steps

### 1. Data Cleaning
- Processed arrest data (`Indiana_arrest.csv`) and population data (`co-est2023-pop-18`).
- Cleaned columns with repetitive or null information.
- Formatted population data for county-level analysis.
- Saved cleaned datasets for further use.

### 2. Exploratory Data Analysis (EDA)
- Explored offense types (`CHARGE_TYPE`) and offender demographics (age, gender, race).
- Identified significant features for further analysis.

### 3. Per Capita Offenses by County
- Merged arrest and population data.
- Calculated offenses per capita for each county.
- Top 5 counties by offenses per capita:
  - **Vanderburgh**: 0.027
  - **White**: 0.024
  - **Posey**: 0.022
  - **Allen**: 0.020
  - **Benton**: 0.020

### 4. Visualizations
#### a. Pyramid Chart: Offenses by Age and Gender
- Showed total offenses by age group for males and females.
#### b. Scatter Plot: Population vs. Offenses
- Visualized offenses per capita across population sizes.
#### c. Map: Offenses per Capita by County
- Choropleth map illustrating county-level offense distribution.
#### d. Pie Chart: Charge Type Distribution
- Percentage breakdown of offense types.
#### e. Line Chart: Age Group Across Charge Types
- Displayed trends in charge types for different age groups.

### 5. Additional Analyses
- **Top Charge Types by Gender**: Bar chart showing charge type distribution by gender.
- **Drug-Related Charges by Age**: Bar chart highlighting age group involvement in specific drug charges.
- **Offense Levels by Age Group**: Bar chart visualizing most common offense levels by age group.

---

## Results and Insights
- Traffic and procedural offenses were the most common across counties.
- Drug-related charges varied significantly by age group, with marijuana being the most frequent.
- Counties with higher population densities showed a wider range of offense types.

---

## Code Highlights
```python
# Offense per capita calculation
merged_pop['Offense_per_capita'] = merged_pop['Total Offenses'] / merged_pop['POPULATION_2023']

# Creating Pyramid Chart
pyramid_age_gen = alt.Chart(filtered_data).mark_bar().encode(
    y=alt.Y('OFFENDER_AGE_GROUP:N', title='Offender Age Group', sort='-x'),
    x=alt.X('Total_offenses:Q', scale=alt.Scale(domain=[-max_val, max_val])),
    color=alt.Color('OFFENDER_SEX:N', title='Gender'),
    tooltip=['OFFENDER_AGE_GROUP', 'OFFENDER_SEX', 'Total_offenses:Q']
).transform_calculate(
    Total_offenses="datum.OFFENDER_SEX === 'MALE' ? -datum.Total_offenses : datum.Total_offenses"
)
```
<img src="Images/pyramid.png?raw=true"/>

---

## Future Work
- Expand analysis to include trends over multiple years.
- Study correlations between demographic factors and offense severity.
- Refine visualizations to include interactive elements for deeper insights.

---
