## Project Title: Analysis of Covid-19 in NJ:
* Name of Group: Pandemic Solvers
* Team Members: Dasa Simova, Joshua Pohl, Melissa Diep, Shuchi Khandelwal, Paul Shelffo

## Project Description/Outline:
* Our team wanted to analyze the # of Covid-19 cases in NJ by county, and the correlation that population size, # of hospitalizations, # of vaccinations, and age has had in the number of cases per NJ county.

## Research Questions:
1. What is the correlation between population size and # of cases?
    - Hypothesis: very correlated
2. What is the correlation between # of hospitalizations and # of cases?
    - Hypothesis: very correlated
3. What is the correlation between # of vaccinations and # of cases?
    - Hypothesis: very correlated
4. What is the correlation between age and # of cases?
    - Hypothesis: very correlated

## Data Sources:
1.  https://data.cdc.gov/resource/n8mc-b4w4.json?
    - Use: metrics for # of cases, # of hospitalizations by NJ county and by month 
2.  https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/state/new-jersey
    - Use: shows cumulative # of Covid-19 cases by NJ county
4.  www.census.gov
    - Use: can find the population data here      
5. www.api.covidactnow.org
    - Use: Can get # of vaccinations 


## Cleaning up the Data & Initial Visualizations:
### I. CDC Data (June '21 data):
1. First, we sourced the CDC API which includes the # of cases in NJ by county by month.
2. To make the data size smaller, we filtered for June '21 as our sample for analysis. Per the API documentation provided, the new url became: https://data.cdc.gov/resource/n8mc-b4w4.json?res_state=NJ&case_month=2021-06&$limit=20000. We also dropped fields that were unrelated to the research questions.
3. We created a bar graph to show the # of June '21 cases by county and ordered from most cases to least cases.

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/CDC_num_cases_NJ_June%202021.PNG?raw=true)

4. We created a bar graph to show the # of June '21 hospitalizations by county and ordered from most cases to least hospitalizations.

### II. Population Data:
1. The Census API includes the total population size by county as of 2019, which was the most up to date free data available.
2. In preparation for future merging of the data, we formatted the data so that the necessary fields matched the same taxonomy of the CDC Data (example: County, County_Num).
3. We created a bar graph to show the # of June '21 cases by county and ordered from most cases to least cases.

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/Census_population_size_NJ_June%202021.PNG?raw=true)

### IV. USAfacts

### III. Consolidated Data (CDC + USAfacts + Population data)
1. In preparation for linear regression visualiations, we merged our data sources.
2. Then, we created a panda dataframe visualization in descending order from largest to smallest population size.

### Conclusion
1. Research Q1 - Bar graphs and linear regressions support that there is strong correlation between population size and cases.
   * We can see from the bar graphs and consolidated panda dataframe that the most populated counties generally have the most # of cases
   * Linear regression shows a strong positive correlation between population size and cases
3. Research Q2 - Looks like there is strong correlation between hospitalizations and cases, since the counties with the most # of hospitalizations generally have the most # of cases
