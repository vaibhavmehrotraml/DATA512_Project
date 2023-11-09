# Part 1: Common Analysis
This project aims to conduct a minimal analysis of the fires and their historical impact for Prescott City, Arizona. We construct an estimate of the impact of these fires, compare it to the Air Quality Index data for the region, and predict the next 25 years of impact estimates.


# Code Files:
- epa_airquality_vai.ipynb: A subset of the originial epa_airquality fetching notebook. This contains the logic to download AQI data.
- process_aqi_data.ipynb: This notebook is responsible for aggregating AQI data and creating a condensed form to be used for downstream analysis
- Part 1 - Common Analysis.ipynb: The complete analysis, from loading the fire polygons to applying GIS logic and developing an impact estimate can be found here. Each portion of the notebook is verbosely labelled.

# Result Files:
- AQIvsEstimate.png: AQI vs Impact Estimate for Prescott City, AZ 
- acres_burnt.png: Graph showing total acres burned per year from 1963-2020 in a 1250 miles radius from Prescott City, AZ
- histogram_fires.png: Number of fires occurring every 50 mile distance from Prescott City, AZ
- gaseous_aqi.csv: Data collected from the EPA API for gaseous AQI for the Yavapai County
- particle_aqi.csv: Data collected from the EPA API for particle AQI for the Yavapai County
- yearly_aqi_data.csv: Aggregated AQI data

# Data:
  The original data used for this analysis can be downloaded at the [USGS Website](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)