# Baltic Electricity markets data set

## General information

Data Set Characteristics: Time-Series, Multivariate
Attribute characteristics: Real value
Associated tasks: Regression, Classification
Number of instances: 10608
Number of attributes: 60
Missing values: xx
Area: Business
Data from 01.01.2021 - 18.03.2022
Timezone - CET/CEST +0200/+0300

## Data Set summary:

Consolidated Electricity markets dataset for Baltics markets. Data is from Entso-E, Baltic Transparency, Nordpool and Elering. Even though this data is publicly available, such combined datasets are not publicly available. Help draw inferences between ties between different markets (Physical power markets (Day-Ahead, Intraday), Balancing markets)

## Attribute infromation

1) Production, generation

Timestamp: All markets trade in 1h slots  
Scheduled Generation EE/LV/LT: TSO aggregated Day-Ahead generation  
(Different primary fuel generated electricity, except Wind and Solar)

Wind_actual EE/LV/LT: TSO measured production  
Wind_forecast EE/LV/LT: Day-ahead (before 18:00 previous day) published forecast  
Solar_actual EE/LV/LT: TSO measured production  
Solar_forecast EE/LV/LT: Day-ahead (before 18:00 previous day) published forecast  
Forecasted Load: Published (TSO) 2h BEFORE Day-ahead auction gate closure. Total predicted consumption.  
Actual_Load: Published (TSO) 1h after given hour.  Actual total Load (including losses without stored energy) = Net Generation – Exports + Imports – Absorbed Energy  

2) Physical market (Nordpool)  

NPS EE/LV/LT: NordPool Spot. Day-Ahead auction prices of electricity (EUR/MWh)  
EE Intraday Weighted avg: Intraday weighted average price. NordPool.  


3) Balancing market (Baltic TSO's)

Imbalance Volume EE/LV/LT/Baltic: Aggregated Difference between all BRP schedules and actual measurements. Baltic imbalance volume is the sum of all. (MWh)

Balancing Energy price EE/LV/LT/Baltic: Highest activated bid price (mFRR)  

Normal activations total EE/LV/LT/Baltics: Total mFRR activation. Negative values are DOWN regulation and positive UP.  

---

Direction of imbalance (past settlement): Direction of balancing state (derived from imbalance volume). "-1" if Surplus in system. "1" if deficit in system  

Direction of real-time balancing: Direction based on real-time market price spread.  "1" if Balancing price higher (UP regulation dominates), "-1" if Nordpool price higher  

4) Time information  

Hour  
Weekday - 1-6  
Is_weekend - 0-weekday, 1-weekend (Binary variable)  
Is_peak - 0-not peak, 1- 16-19 and 6-8 (Binary variable)  
month - 1-12 nominal variable  
Season - 1-4. 1-Winter, 2-Spring, 3-Summer, 4-Autumn  




