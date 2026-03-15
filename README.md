## Social Security Names

from https://www.ssa.gov/oact/babynames/

Data at `data/names-ss-1910-2022.csv.zip`

## Ames Housing Data 

http://jse.amstat.org/v19n3/decock.pdf

Data at ``./data/ames-housing-dataset.zip``

Weather data for those years at ``../data/asos-ames-2007-2010.txt``

## Stack Overflow 2019 Survey (developer_survey_2019.zip 18M)

https://insights.stackoverflow.com/survey/2019

License: ODbL

## Automobile Fuel Economy 1984-2020 (vehicles.csv.zip)

https://www.fueleconomy.gov/feg/download.shtml

## Presidents

From https://qrc.depaul.edu/Excel_File_Listing_Pages/Excellist.asp

## Pokemon

From https://www.kaggle.com/rounakbanik/pokemon (CC0: Public Domain)

## Alta

1980-2019

https://www.ncdc.noaa.gov/cdo-web/datasets/GHCND/stations/GHCND:USC00420072/detail

 Data at ``../data/snow-alta-1990-2017.csv``

 ## Ecommerce Store Sample Transaction

 ``../data/transaction_data.xlsx``

 Documentation - https://www1.ncdc.noaa.gov/pub/data/cdo/documentation/GHCND_documentation.pdf


 * STATION_NAME (max 50 characters) is the (usually city/airport name). Optional
 output field.
 * STATION - 17 characters) is the station identification code. Please see
 http://www1.ncdc.noaa.gov/pub/data/ghcn/daily/ghcnd-stations.txt
 * NAME - name of the station
 * LATITUDE
 * LONGITUDE
 * ELEVATION - meters
 * DATE - YYYY-MM-DD
 * DAPR - Number of days included in the multiday precipitation total (MDPR)
 * DAPR_ATTRIBUTES
 * DASF - Number of days included in the multiday snowfall total (MDSF)
 * DASF_ATTRIBUTES 
 * MDPR -  Multiday precipitation total (mm or inches as per user preference; use with DAPR and DWPR, if
 available)
 * MDPR_ATTRIBUTES
 * MDSF - Multiday snowfall total (mm or inches as per user preference)
 * MDSF_ATTRIBUTES
 * PRCP - Precipitation (mm or inches as per user preference, inches to hundredths on Daily Form pdf file)
 * PRCP_ATTRIBUTES 
 * SNOW -  Snowfall (mm or inches as per user preference, inches to tenths on Daily Form pdf file)
 * SNOW_ATTRIBUTES
 * SNWD -  Snow depth (mm or inches as per user preference, inches on Daily Form pdf file)
 * SNWD_ATTRIBUTES
 * TMAX - Maximum temperature (Fahrenheit or Celsius as per user preference, Fahrenheit to tenths on
 Daily Form pdf file
 * TMAX_ATTRIBUTES 
 * TMIN - Minimum temperature (Fahrenheit or Celsius as per user preference, Fahrenheit to tenths on
 Daily Form pdf file
 * TMIN_ATTRIBUTES
 * TOBS - Temperature at the time of observation (Fahrenheit or Celsius as per user preference)
 * TOBS_ATTRIBUTES
 * WT01 - Fog, ice fog, or freezing fog (may include heavy fog)
 * WT01_ATTRIBUTES
 * WT03 - Thunder
 * WT03_ATTRIBUTES
 * WT04 - Ice pellets, sleet, snow pellets, or small hail
 * WT04_ATTRIBUTES
 * WT05 -  Hail (may include small hail)
 * WT05_ATTRIBUTES
 * WT06 - Glaze or rime
 * WT06_ATTRIBUTES
 * WT11 -  High or damaging winds
 * WT11_ATTRIBUTES

## El Nino (tao-all2.dat.gz)

https://archive.ics.uci.edu/ml/datasets/El+Nino

 zonal winds (west<0, east>0), meridional winds (south<0, north>0),

```
# Data transformation from previous notebook
# col names in tao-all2.col from website
names = '''obs
year
month
day
date
latitude
longitude
zon.winds
mer.winds
humidity
air temp.
s.s.temp.'''.split('\n')

nino = pd.read_csv('data/tao-all2.dat.gz', sep=' ', names=names, na_values='.', 
                   parse_dates=[[1,2,3]])

def clean_cols(val):
    return val.replace('.', '_').replace(' ', '_')

nino = (nino
  .rename(columns=clean_cols)
  .assign(air_temp_F=lambda df_: df_.air_temp_ * 9/5 + 32,
        zon_winds_mph=lambda df_: df_.zon_winds*2.237,
        mer_winds_mph=lambda df_: df_.mer_winds*2.237)
  .drop(columns='obs')
)
```

## Olympic Medals

athlete_events.csv.zip From Kaggle. Medal stats to 2016

## Nvidia Data

nvda_spy.csv SPY and Nvidia data to 2024 from yfinance

## Alone Data

Gemini assisted generated data from Alone TV series


1. Demographic & Background Data

* **`season`**: (Integer) The installment number of the show (1–12).
* **`location`**: (String) The geographical region (e.g., "Vancouver Island," "Great Slave Lake"). This acts as a proxy for ecosystem type.
* **`contestant`**: (String) The name of the participant.
* **`age`**: (Integer) The age of the participant at the time of drop-off.
* **`sex`**: (Categorical: M/F) Biological sex.
* **`starting_weight_kg`**: (Continuous) The weight of the participant at the final medical check before drop-off.
* **`profession`**: (String) The participant's primary career. Useful for "Professional Bias" analysis (e.g., comparing "Survival Instructor" vs. "Electrician").
* **`hometown`**: (String) Origin city/state. Used to calculate "Home Field Advantage" if the climate matches the show location.
* **`exp_years`**: (Integer) Self-reported years of experience in primitive or survival skills.

2. Skill & Performance Metrics (1–5 Scale)

* **`hunt_skill`**: (Ordinal) 1 = Basic/No experience; 5 = Professional guide/Elite bowyer. Measures the ability to track and kill game.
* **`fish_skill`**: (Ordinal) 1 = Recreational; 5 = Commercial fisherman/Expert angler. Often the strongest predictor of longevity.
* **`shelter_quality`**: (Ordinal) 1 = Minimalist tarp/bivouac; 3 = Insulated lean-to; 5 = Permanent log cabin with stone hearth/fireplace.

3. Survival Events & Physiological Data

* **`food_events`**: (Integer) The count of successful "significant" harvests (e.g., a large fish, a squirrel, or big game). Smaller foraged items like berries are usually excluded.
* **`injury_count`**: (Integer) Total number of minor or major physical injuries recorded.
* **`med_flags`**: (Integer) Number of official "Medical Warnings" issued by the production team during weekly checks.
* **`gill_net`**: (Boolean: Y/N) Whether the participant successfully constructed and deployed a gill net.


4. Environmental Stressors

* **`precip_mm`**: (Continuous) Average monthly rainfall/snowfall for that location. High values correlate with "Psychological" tap-outs due to gear failure and wetness.
* **`daylight_hrs`**: (Continuous) The average hours of sunlight during the final third of the stay.
* **`temp_low_c`**: (Continuous) The average nightly low temperature during the participant's final week.

5. Outcome Variables (Target Data)

* **`tapout_reason`**: (Categorical) The primary reason for leaving. Common values:
* *Winner*: Last person standing.
* *Medical*: Forced removal for BMI, injury, or organ failure.
* *Psychological*: Loneliness, "missing family," or "journey complete."
* *Starvation*: Voluntary tap due to lack of calories.


* **`days_lasted`**: (Integer) The total number of 24-hour periods spent in the wilderness. This is usually your **Dependent Variable** for regression analysis.
