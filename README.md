# covid19-project
## Project Title: Analysis of Covid-19 in NJ
* Name of Group: Pandemic Solvers
* Team Members: Dasa Simova, Joshua Pohl, Melissa Diep, Shuchi Khandelwal, Paul Shelffo


## Project Description/Outline:
* Our group is looking to analyze the number of Covid-19 cases in NJ by county, and the correlation that population size, location, and vaccinations has had in the number of cases per NJ county.

## Research Questions:
1. What is the correlation between population size and # of cases?
    - Hypothesis: very correlated
2. What is the correlation between # of hospitalizations and # of cases?
    - Hypothesis: very correlated
3. What is the correlation between # of vaccinations and # of cases?
    - Hypothesis: very correlated
4. What is the correlation between age and # of cases?
    - Hypothesis: very correlated

## Data sources:
1. https://data.cdc.gov/resource/n8mc-b4w4.json?
    - Use: metrics for # of cases, # of hospitalizations 
2. www.census.gov
    - Use: can find the population data here      
3. www.api.covidactnow.org
    - Use: Can get # of vaccinations 


## Cleaning up the Data & Initial Visualizations:
### A. CDC Data:
1. First, we sourced the CDC API which includes the number of Covid-19 cases in NJ by county by month.
2. To make the data size smaller, we filtered for June 2021 as our sample for analysis. Per the API documentation provided, the new url became: https://data.cdc.gov/resource/n8mc-b4w4.json?res_state=NJ&case_month=2021-06&$limit=20000. We also dropped fields that were unrelated to the research questions.
4. We created a bar graph to show the number of Covid-19 cases by county and ordered from most cases to least cases

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/CDC_num_cases_NJ_June%202021.PNG?raw=true)

## Visualization will include:
* We will show linear regression (3-4 total) line graphs to show correlation for each of our research questions
* Bar chart to show highest to least number of cases by county
* Pie chart to show % of total vaccinations by county
* etc.
  
