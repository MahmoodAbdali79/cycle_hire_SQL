# Analytics on cycle_hire

As working with BigQuery and analyzing databases, I find `cycle_hire` from from London Bicycle Hires on BigQuery

> This data contains the number of hires of London's Santander Cycle Hire Scheme from 2011 to present. Data includes start and stop timestamps, station names and ride duration. for more detail see [here](https://console.cloud.google.com/bigquery(cameo:product/greater-london-authority/london-bicycles)?project=my-project-341411)


For understand better the dataset, There are some question that I've answered them with SQL. Here is:

- [x] how many bike trips lasted for 20 minutes or longer?
  ```sql
  SELECT COUNT(*) AS number_of_trips
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE duration >= 1200;
  ```
  > Answer : 7334890 bike trips lasted for 20 minutes or longer
  
- [x] What are the names of the stations that bike_id 1710 started from?
  ```sql
  SELECT DISTINCT start_station_name 
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE bike_id >= 1710;
  ```
  > Answer : Atached to this repo
  
- [x] How many bike_ids have ended at "Moor Street, Soho"?
  ```sql
  SELECT COUNT(DISTINCT bike_id) AS number_of_bikes 
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE end_station_name = 'Moor Street, Soho';
  ```
  > Answer : 13116
  
- [x] What is the station_id for "Canton Street, Poplar"?
  ```sql
  SELECT DISTINCT start_station_id
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE start_station_name = 'Canton Street, Poplar';
  ```
  > Answer : 487
  
- [x] What is the name of the station whose ID is 111?
  ```sql
  SELECT DISTINCT start_station_name
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE start_station_id = 111;
  ```
  > Answer : Park Lane , Hyde Park
  
- [x] How many distinct bike_ids had trip durations greater than 2400 seconds (or 40 minutes)?
  ```sql
  SELECT COUNT( DISTINCT bike_id) AS number_of_bike
  FROM `bigquery-public-data.london_bicycles.cycle_hire`
  WHERE duration > 2400
  ```
  > Answer : 13678 bikes
