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

An additional log file was written to keep track of the EPA API data ingestion progress

# Data:
  The original data used for this analysis can be downloaded at the [USGS Website](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). This project uses the GeoDatabase version of the data. The data was published along with the following paper:
  
  Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

  The data contains vector polygon depicting fires in the United States of America, along with additional features.

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