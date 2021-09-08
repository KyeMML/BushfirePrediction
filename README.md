# BushfirePrediction
Predicting the occurence of naturally occuring South-Australian Wildfires


## Data Description
The dataset is the combination of ERA5 temporal statistics and NASA fire detection confidence labels.  
ERA5 dataset: https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-pressure-levels?tab=form  
NASA dataset: https://firms.modaps.eosdis.nasa.gov/download/

## ERA5 Dataset
The ERA5 dataset contains the following temporal variables:

## Divergence
Fraction of cloud cover
Geopotential
Ozone mass mixing ratio
Potential vorticity
Relative humidity
Specific cloud ice water content
Specific cloud liquid water content
Specific humidity
Specific rain water content
Specific snow water content
Temperature
U component of wind
V component of wind
Vertical velocity
Vorticity (relative)
As well as the following location variables:
latitude
longtitude
time
The latitude and longtitude was removed from the dataset to transform the data into a two dimensional dataframe. Time was translated into a date format in datetime type.
Temporal variables were averaged across latitude and longtitude, grouped by date. This is only possible because the latitude and longtitude area covered is very small, covering only Kangaroo island.

## NASA Dataset
The NASA dataset contains the following temporal variables:

brightness (VIIRS I-4 channel brightness temperature of the fire pixel measured in Kelvin)
scan (The algorithm produces approximately 375 m pixels at nadir. Scan and track reflect actual pixel size.)
track (The algorithm produces approximately 375 m pixels at nadir. Scan and track reflect actual pixel size.)
satellite (N= Suomi National Polar-orbiting Partnership (Suomi NPP))
instrument
confidence (l = low confidence, n = nominal, h = high)
version ("1.0NRT" - Collection 1 NRT processing, "1.0" - Collection 1 Standard processing.)
bright_t31 (Channel brightness temperature of the fire pixel measured in Kelvin.)
frp (Fire Radiative Power)
daynight
type (Inferred hot spot type:0 = presumed vegetation fire, 1 = active volcano, 2 = other static land source, 3 = offshore detection (includes detections over water)) As well as the following location variables:
latitude (Center of nominal 375 m fire pixel)
longitude (Center of nominal 375 m fire pixel)
acq_date (Acquisition Date)
acq_time (Acquisition Time)
The only variables utilised in the NASA dataset was the confidence and acquisition date.
I should note that the NASA data only reports when the satellite can see the specified location as it orbits. This results in 'dark' spots, where dates are missing without reported confidence levels of fires.

## Combined Dataset
The combined data of ERA5 temporal statistics and NASA confidence labels culminates into a dataframe spanning from the first of january 2017 to the first of january 2021.
The NASA data contributing with 28 cases of 'h' (high confidence) vegetation fires. The combined dataset contains 1461 rows and 18 columns. The confidence labels replaced with binary representations, with nominal and low replaced with 0 and occuring 1433 times, while high confidence replaced with 1 and occuring 28 times.

