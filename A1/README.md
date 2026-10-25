#HCDE410
Files for HCDE410 - Assignment A1

Adapted from # cdsw-2020 https://wiki.communitydata.science/Seattle_open_data

# A1 - Working with Open Data
**Dataset:** Burke-Gilman Trail counter north of NE 70th St (count of bicycle & pedestrians, hourly, by direction), published by the Seattle Department of Transportation.
**Source:** https://data.seattle.gov/Transportation/.../2z5v-ecg8 (pulled 2026-10-12)
**License/terms of use:** The dataset is listed as being part of the public domain on data.seattle.gov

## Questions I asked
- **Q1** When is the trail busiest, and when is it quietest?
    - I defined busy as the average bikes + pedestrians per hour of the day
- **Q2** Do cyclists and pedestrians use the trail at different times of day?
- **Q3** Commuting or recreation? Is there a weekday commute pattern that is missing on weekends?
- **Q4** Direction and flow. Do people go in opposite direction in morning vs evening?

## How to re-run

Open 'A1.ipynb' and run all cells (needs `requests`, `pandas`, `matplotlib`). The notebook requires an internet connections because it pulls data from the City of Seattle API.