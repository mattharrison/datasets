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
