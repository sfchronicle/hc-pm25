# Analyzing Air Quality Monitor Data
This repo pulls together EPA regulatory air quality monitor data and PurpleAir community air quality monitor data.

All of the code necessary to pull and analyze both data sources is located in the `code` directory in this repo. Scripts are numbered and should be run in order. All files have ample code comments and documentation.

## Data
There are certain source datasets required to run each code file that are not present in the `data/source` directory due to github size limits. Documentation on where to find those files is present in the code files requiring them.

There are several data files created by the code in this repo. Most can be found in the `data/analyzed` directory. Geographic data files can be found in the `GIS` directory.

- `data/analyzed/houmetro-epa-pm25-site-summary.csv`: for each EPA regulatory monitor, this file will list the average daily PM2.5 readings for each year between 2018 and 2024. 3-year rolling averages have also been calculated, according to [EPA regulatory standards](https://www.epa.gov/particle-pollution-designations/particle-pollution-designations-memorandum-and-data-2024-revised). A full data dictionary for this file [can be found here](https://docs.google.com/spreadsheets/d/1b2akNcSm2Mcybt4Sa-3f-L3hgryyWPKYsplwGQeVz3s/edit?gid=691253185#gid=691253185) on the "definitions" tab. 
- `data/analyzed/houmetro-purpleair-pm25-site-summary.csv`: for each PurpleAir community monitor, this file will list the average daily PM2.5 readings for each year between 2018 and 2024. Annual averages are not calculated for years in which the monitor produced fewer than 182 days of readings. 3-year rolling averages have also been calculated, according to [EPA regulatory standards](https://www.epa.gov/particle-pollution-designations/particle-pollution-designations-memorandum-and-data-2024-revised). A full data dictionary for this file [can be found here](https://docs.google.com/spreadsheets/d/1b2akNcSm2Mcybt4Sa-3f-L3hgryyWPKYsplwGQeVz3s/edit?gid=691253185#gid=691253185) on the "definitions" tab. 
    - **NOTE:** the data in these files have been "calibrated".
- `data/analyzed/houmetro-epa-purpleair-pm25-site-summary.csv`: a concatenation of EPA and PurpleAir monitors.
- `data/analyzed/purpleair/sensor-data/`: all files in this directory related to monitor-specific PuprpleAir data scrapes performed in `03_get-historical-purple-air.ipynb`. 
    - **NOTE:** both indoor and outdoor monitor data have been pulled. For most analyses, you will want to exclude indoor monitors. Indoor monitors are identified by the `location_type` field in the sensor info files located in `GIS/purpleair/`. You can also get a read out of indoor monitor sensor IDs by executing the first code block in `04_analyze-purpleair-pm25.ipynb`.
    - **DISCLAIMER:** The raw sensor files have NOT been [calibrated](https://community.purpleair.com/t/calibration-of-purpleair-monitors/482/3). PurpleAir monitor PM2.5 data have been known to overestimate the presence of PM2.5 in ourdoor monitors. Lance Wallace, an industry expert, has developed a calibration method to bring PurpleAir readings closer to what EPA regulatory monitors detect.
- `data/analyzed/houmetro-pa-2022-2024-pm25.csv`: a concatenation of the files in `purpleair/sensor-data/`. 
    - **NOTE:** both indoor and outdoor monitor data are present in this file. For most analyses, you will want to exclude indoor monitors. Indoor monitors are identified by the `location_type` field in the sensor info files located in `GIS/purpleair/`. You can also get a read out of indoor monitor sensor IDs by executing the first code block in `04_analyze-purpleair-pm25.ipynb`.
    - **DISCLAIMER:** The data in this file have NOT been [calibrated](https://community.purpleair.com/t/calibration-of-purpleair-monitors/482/3). PurpleAir monitor PM2.5 data have been known to overestimate the presence of PM2.5 in ourdoor monitors. Lance Wallace, an industry expert, has developed a calibration method to bring PurpleAir readings closer to what EPA regulatory monitors detect.
- `GIS/`: most of the files in this directory are supporting files that can be understood by reading the scripts in `code`. Please reach out to Alexandra Kanik with any questions.


