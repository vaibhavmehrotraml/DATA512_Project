# Part 1: Common Analysis
The impact of wildland fires is widespread and there is a growing body of work pointing to the negative impacts of smoke on health, tourism, property, and other aspects of society.

This project aims to conduct a minimal analysis of the fires and their historical impact for Prescott City, Arizona. We construct an estimate of the impact of these fires, compare it to the Air Quality Index data for the region, and predict the next 25 years of impact estimates.


# Code Files (present in Notebooks/):
- epa_airquality_vai.ipynb: A subset of the originial epa_airquality fetching notebook. This contains the logic to download AQI data.
- process_aqi_data.ipynb: This notebook is responsible for aggregating AQI data and creating a condensed form to be used for downstream analysis
- Part 1 - Common Analysis.ipynb: The complete analysis, from loading the fire polygons to applying GIS logic and developing an impact estimate can be found here. Each portion of the notebook is verbosely labelled.

# Result Files (present in Results/):
- AQIvsEstimate.png: AQI vs Impact Estimate for Prescott City, AZ 
- acres_burnt.png: Graph showing total acres burned per year from 1963-2020 in a 1250 miles radius from Prescott City, AZ
- histogram_fires.png: Number of fires occurring every 50 mile distance from Prescott City, AZ
- predict_impact.png: Predicted Impact Estimates for 25 years in the futurealong with the 95% confidence interval for Prescott City, AZ
- gaseous_aqi.csv: Data collected from the EPA API for gaseous AQI for the Yavapai County
- particle_aqi.csv: Data collected from the EPA API for particle AQI for the Yavapai County
- yearly_aqi_data.csv: Aggregated AQI data
- impact_vs_asthma_incidence.png: Comparision of smoke estimate and rate of asthma incidence
- impact_vs_premature_death.png: Comparision of smoke estimate and rate of premature deaths
- impact_vs_asthma_deaths.png: Comparision of smoke estimate and rate of asthma deaths    
- impact_vs_fertility.png: Comparision of smoke estimate and fertility rate
- predicted_incidence_rate.png: Predicted rate of asthma incidence taking into account the smoke estimate
- predicted_premature.png: Predicted rate of premature deaths taking into account the smoke estimate
        
# Data:
## [Combined Wildland Fire Datasets (US Geological Survey)](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
  The original data used for this analysis can be downloaded at the [USGS Website](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). This project uses the GeoDatabase version of the data. The data was published along with the following paper:

  The Combined Wildland Fire Datasets, developed by the U.S. Geological Survey, is a comprehensive collection of wildfire data for the United States and certain territories from the 1800s to the present. It integrates data from 40 wildland fire sources, each with varying spatial scales, resolutions, and periods, into a unified dataset. This dataset provides a single set of polygons with a singular fire boundary for each fire, aiming to create a more comprehensive and accurate representation of fire data while reducing duplication. It includes detailed attributes for each fire event. It is intended for a wide range of applications, from environmental research to policy-making, offering a valuable resource for understanding wildfires' spatial and temporal patterns.


  Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

  The data contains vector polygon depicting fires in the United States of America, along with additional features.

## [American Community Survey 1-Year Data (2005-2022): Female Fertility](https://www.census.gov/data/developers/data-sets/acs-1year.html)
The American Community Survey (ACS) is an ongoing survey that provides yearly data, giving communities the current information they need to plan investments and services. The ACS covers various topics about the U.S. population's social, economic, demographic, and housing characteristics. This data is aggregated and publically hosted by the US Census Bureau. US Census Bureau data is available for public use.
Within this dataset of over 600 columns, I focused on three:
S1301_C04_001E: Estimate of Women with births in the past 12 months per 1000 for ages 15 to 50 years
S1301_C04_001M: Margin of Error Women with births in the past 12 months per 1000 for ages 15 to 50 years
YEAR: Year of data collection.

Citation: Bureau, U.C. (2020). American Community Survey 1-Year Data (2005-2019). [online] The United States Census Bureau. Available at: https://www.census.gov/data/developers/data-sets/acs-1year.html.

## [Centers for Disease Control and Prevention Data[4]: Premature Mortality Rate](https://fred.stlouisfed.org/series/CDC20N2U004025)
The crude death rate is the number of deaths reported each calendar year divided by the population multiplied by 100,000. Premature death rate includes all deaths where the deceased is younger than 75 years of age. 75 years of age is the standard consideration of premature death according to the CDC's definition of Years of Potential Life Loss. Although the CDC collects the original dataset, an aggregated version of this dataset, compiled by the Federal Research Bank of St. Louis, will be used for this analysis. CDC data is available for public use.
This dataset is relatively straightforward and contains only two columns:
CDC20N2U004025: Premature mortality rate
DATE: Date of data collection

Citation: Explore  Fertility Census Data. [online] Available at: https://data.census.gov/table/ACSST1Y2022.S1301?t=Fertility 

CDC (2018). Data & Statistics. [online] Centers for Disease Control and Prevention. Available at: https://www.cdc.gov/datastatistics/index.html 

Centers for Disease Control and Prevention, Premature Death Rate for Yavapai County, AZ [CDC20N2U004025], retrieved from FRED, Federal Reserve Bank of St. Louis; https://fred.stlouisfed.org/series/CDC20N2U004025, November 15, 2023.


## [Institute for Health Metrics and Evaluation Global Burden of Disease: Asthma Data](https://vizhub.healthdata.org/gbd-results/)
The Global Burden of Disease (GBD) study provides a comprehensive picture of mortality and disability across countries, time, age, and sex. It quantifies health loss from hundreds of diseases, injuries, and risk factors to improve health systems and eliminate disparities. For the academic scope of this analysis, this data is available free of charge under a non-commercial user agreement.

After subsetting the data for the relevant disease, I used the following data:
Rate of deaths caused due to Asthma.
Rate of Ashtma incidence.
	Which will be derived from the following columns:
measure_name: This indicates the type of data or metric being reported, such as incidence and mortality rate, 
location_name: Refers to the geographical area or region to which the data applies, ranging from global to country-specific levels.
sex_name: Specifies the biological sex (male, female) for which the data is reported, or 'both' if the data encompasses all sexes.
age_name: Denotes the age group or range for which the data is relevant, such as 0-5 years, 15-49 years, or all ages.
cause_name: Identifies the specific health condition, disease, or cause of death being studied or reported on. In my case, this will be ‘Asthma.’
metric_name: Refers to the specific measurement used in the dataset, such as rate, number, or proportion.
year: Indicates the calendar year to which the data corresponds.
val: Represents the primary value or measurement reported for the given parameters.
upper: Gives the upper bound or the higher estimate of the confidence interval for the reported value.
lower: Provides the lower bound or the lower estimate of the confidence interval for the reported value.

Citation: 

Global Burden of Disease Collaborative Network. Global Burden of Disease Study 2019 (GBD 2019) Results. Seattle, United States: Institute for Health Metrics and Evaluation (IHME), 2020. Available from https://vizhub.healthdata.org/gbd-results/ 
Institute for Health Metrics and Evaluation. (2021). IHME free-of-charge non-commercial user agreement. [online] Available at: https://www.healthdata.org/Data-tools-practices/data-practices/ihme-free-charge-non-commercial-user-agreement. 

# Data Description
A description of each column in the final merged dataframe can be found in the README file inside the `Results/` folder
# Dependencies:
- Pandas
- Seaborn
- Matplotlib
- Shapely
- Geopandas


# License:
MIT License

Copyright (c) 2023 Vaibhav Mehrotra

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.