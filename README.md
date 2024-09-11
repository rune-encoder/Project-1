# <br> <p align="center"> *EV Adoption and Infrastructure Trends Across the U.S. and Key States: A Comprehensive Data-Driven Exploration* </p>

<br> <p align="center">
![Python Badge](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff&style=flat-square)
![Anaconda Badge](https://img.shields.io/badge/Anaconda-44A833?logo=anaconda&logoColor=fff&style=flat-square)
![Jupyter Badge](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=fff&style=flat-square)
![pandas Badge](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=fff&style=flat-square)
![Plotly Badge](https://img.shields.io/badge/Plotly-3F4F75?logo=plotly&logoColor=fff&style=flat-square)
![NumPy Badge](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=fff&style=flat-square)
![SciPy Badge](https://img.shields.io/badge/SciPy-8CAAE6?logo=scipy&logoColor=fff&style=flat-square)
</p>


## **Table of Contents**
1. [Project Overview](#project-overview)
2. [Dataset Information](#dataset-information)
3. [Analysis Approach](#analysis-approach)
4. [Visualizations and Findings](#visualizations-and-findings)
5. [Conclusion and Implications](#conclusion-and-implications)
6. [Future Work](#future-work)
7. [Credits](#credits)

---

## **Project Overview**

This project aims to analyze electric vehicle (EV) adoption and infrastructure trends across the United States, with a deep dive into Florida, Texas, and California. By examining EV registrations, adoption rates, growth rates, and the role of factors such as median income and charging stations, the project provides insights into the current and future landscape of EV adoption.

## **Dataset Information**

The data includes the following features for each state and county:
- Year
- State and County Names
- Zip Codes
- Population
- EV Registrations
- Cumulative EV Charging Stations
- Median Income
- EV Adoption Rate
- EV Growth Rate

The dataset was cleaned and transformed for analysis, including handling missing data and exploding zip codes for geospatial analysis.

## **Analysis Approach**

The analysis consists of two main parts:
1. **National Overview (All 50 States):**
   - EV registrations and gasoline registrations over time.
   - Adoption rates of EVs and gasoline vehicles.
   - Comparative growth rates of EVs vs gasoline vehicles.
   - Statistical summaries including mean, median, and standard deviation.
   - Five-year forecast using the Prophet model.

2. **State-Specific Deep Dive (Florida, Texas, California):**
   - EV registrations, adoption rates, and growth rates per county.
   - Correlation analysis between EV adoption, median income, and charging stations.
   - Geospatial visualizations of EV adoption by zip code.

## **Visualizations and Findings**

The following key visualizations were produced:
- **Line plots** for EV and gasoline registrations over time.
- **Bar plots** showing the most recent EV and gasoline adoption rates across states and counties.
- **Growth rate plots** comparing the percentage change in EV and gasoline registrations.
- **Correlation matrices** highlighting the relationships between adoption rates, income, and charging stations.
- **Geospatial maps** visualizing EV adoption by zip code for Florida, Texas, and California.

These visualizations revealed:
- Consistent growth in EV registrations across the U.S., with higher adoption rates in states like California.
- A positive correlation between median income and EV adoption rates.
- Counties with high numbers of charging stations showed higher EV adoption rates.

## **Conclusion and Implications**

The findings suggest that:
- Wealthier counties and those with more charging infrastructure are leading in EV adoption.
- EV adoption is expected to continue growing, with a projected increase in registrations over the next five years.
- Policymakers should focus on expanding charging infrastructure and consider income-based incentives to drive adoption in underserved regions.

## **Future Work**

With more time, further analysis could include:
- **Clustering analysis** to group counties with similar characteristics for targeted policy recommendations.
- **Deeper exploration** of the role of policy interventions and state-specific incentives in driving EV adoption.

## **Credits**

>**Datasets Obtained from...**  

_All 50 states vehicle registrations:_
- https://afdc.energy.gov/vehicle-registration  

_FL, CA, TX state EV vehicle registrations:_ 
- https://www.atlasevhub.com/materials/state-ev-registration-data/  

_Population:_ 
- https://www2.census.gov/programs-surveys/popest/datasets/2010-2019/ 
- https://www2.census.gov/programs-surveys/popest/datasets/2020-2023/ 
- https://www.texas-demographics.com/zip_codes_by_population 
- https://www.california-demographics.com/zip_codes_by_population 
- https://www.florida-demographics.com/zip_codes_by_population 

_Income:_ 
- https://www.data.census.gov

_Charging Stations:_
- JD Powers

**Articles Obtained from...**  

_2017 Oklahoma Increase EV Sales:_
- https://www.okenergytoday.com/2018/10/oklahoma-saw-biggest-nationwide-increase-in-electric-vehicle-sales/

_2017 Oklahoma EV infrastructure:_
- https://www.okenergytoday.com/2023/08/major-study-finds-infrastructure-is-holding-back-ev-growth/

_2020 Orange County growth rate changes:_
- https://www.ocregister.com/2017/11/09/tax-plan-would-hit-gov-browns-special-treatment-of-electric-cars/
- https://www.ocregister.com/2017/04/24/orange-county-electric-vehicle-pioneer-fuels-passion-for-irvine-students/
