![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/Covid_image2.png?raw=true)

## Project Title: Analysis of Covid-19 in NJ
* Name of Group: Pandemic Solvers
* Team Members: Dasa Simova, Joshua Pohl, Melissa Diep, Shuchi Khandelwal, Paul Shelffo

## Project Description/Outline
* Our team wanted to analyze the # of Covid-19 cases in NJ by county, and the correlation that population size, # of hospitalizations, # of vaccinations, and age has had in the # of cases per NJ county.

## Research Questions
1. What is the correlation between population size and # of cases?
    - Hypothesis: very correlated
2. What is the correlation between # of hospitalizations and # of cases?
    - Hypothesis: very correlated
3. What is the correlation between # of vaccinations and # of cases?
    - Hypothesis: very correlated
4. What is the correlation between age and # of cases?
    - Hypothesis: very correlated

## Data Sources
1.  https://data.cdc.gov/resource/n8mc-b4w4.json?
    - Use: metrics for # of cases, # of hospitalizations by NJ county and by month 
2.  https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/state/new-jersey
    - Use: shows cumulative # of Covid-19 cases by NJ county
4.  www.census.gov
    - Use: population data for NJ by county      
5. www.api.covidactnow.org
    - Use: metrics for vaccinations 


## Cleaning up the Data
### I. CDC Data (June '21 data)
1. First, we sourced the CDC API which includes the # of cases and hospitalizations in NJ by county by month.
2. To make the data size smaller, we filtered for June '21 as our sample for analysis. Per the API documentation provided, the new url became: https://data.cdc.gov/resource/n8mc-b4w4.json?res_state=NJ&case_month=2021-06&$limit=20000. We also dropped fields that were unrelated to the population and hospitalizations research questions.


### II. USAfacts Data (7-15-21)
1. We wanted to further prove any hypothesis made with population vs June 21 cases by comparing population to the total cumulative cases by NJ county. 
2. We found the total cumulative cases for all states as of 7-15-21 in CSV format from USAfacts.
3. We cleaned the data by filtering for just NJ cases, and dropped all fields except for the County name, County_Num, and cases as of 7-15-21. Most of the other columns represented # of cases as of a different date.

### III. Population Data (2019)
1. We sourced Census API which includes the total population size by county as of 2019. This was the most up to date free data available.
2. In preparation for future merging of the data, we formatted the data so that the necessary fields matched the same taxonomy of the CDC Data (example: County, County_Num).


### IV. Vaccination Data
1. We used population data for the counties in NJ from the most up to date dataset from 2019. 
2. Data about vaccination was found at  www.api.covidactnow.org in csv format, in time series for each county. The full dataset consists of 11319 entries, for 21 counties, for 2020 and 2021 per day. After we collected the data, we dropped the data not related to the vaccination and the number of cases and also the rows which didn't provided data in the selected fields (NaN values). Final dataset has 2892 entries(rows). Further analyses was performed with data about actual vaccination initiated, actual vaccination completed, actual new cases and data pertaining to the identification of the county, and the day when the data were collected. 
3.  The term vaccination completed refers to the number of individuals who have received a single dose from a one-dose vaccine course,  or their second dose from a two-dose vaccine course; vaccination initiated refers to the number of individuals who have received only one dose from a two-dose vaccine course.
4. The created stacked bar graph showceses the  percentage of population vaccinated -  vaccination initiated over vaccination completed, with markers used to point the actual total cases in % of population by county,NJ.

![Image](Images/Vaccination_counties_NJ_Jun2021.png) 

5. Then the time series data were used to showcase vaccination by date and  actual new cases by date by county in NJ. For the county with population vaccinated at the highest rate (Morris County) and at the lowest rate (Cumberland County) bar graph was selected to provide outlook at the vaccination data vs actual new cases data.

![Image](Images/Vaccinaction_Morris.png)

![Image](Images/Vaccinaction_Cumberland.png)


## Consolidated Data / Visualizations
1. In preparation for outputting visualizations to show if there is correlation, we merged our data sources (CDC + USAfacts + Population data).
2. Then, we created a panda dataframe visualization in descending order from largest to smallest population size.

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/Consolidated_df.PNG?raw=true)

3. We outputted linear regression and bar graph visualizations to show correlation between:

  ##### I. Population (2019) vs Cases (June 2021)

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/LinRegression_population_vs_num_June21_cases.PNG?raw=true)

   ##### II. Population (2019) vs Cumulative Cases (as of 7-15-21)


![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/Census_population_total_cases_USAfacts.PNG?raw=true)

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/LinRegression_population_vs_total%20YTD%20cases.PNG?raw=true)   
   
   ##### III. Hospitalizations vs Cases (June 2021)

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/CDC_hosp_and_num_cases_NJ_June%202021.png?raw=true)

![alt text](https://github.com/melissadiep94/covid19-project/blob/main/Images/LinRegression_hosp_vs_num_June21_cases.PNG?raw=true)


   #####  IV. Vaccination vs Actual New Cases by County - Morris & Cumberland (Jun2021)
    

![Image](Images/Linear_regr_Vaccinaction_Morris.png)

![Image](Images/Linear_regr_Vaccinaction_Cumberland.png)


## Conclusion
1. Research Q1 - Bar graphs and linear regressions support that there is strong correlation between population size and cases.
   * We can see from the bar graphs and consolidated panda dataframe that the most populated counties generally have the most # of cases
   * Linear regression shows a strong positive correlation between population size and cases
2. Research Q2 - Bar graphs and linear regressions support that there is a moderate correlation between hospitalizations and cases
   *  We can see from the bar graph and consolidated panda dataframe that counties with the fewest # of cases have the lowest # of hospitalizations (i.e. Salem), however it is a bit unexpected that Passaic has the most # of hospitalizations at 40, since 4 other counties had more # of cases. Other factors must have contributed to Passaic's high # of hospitalizations.
   *  Also, the linear regression shows a moderate correlation with an r-squared of 0.62. Passaic can also be seen as an outlier in this visualization, as this point is the most out of alignment with the line plot. 
