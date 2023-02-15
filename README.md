# Road-Condition-Detection

i) PROBLEM DEFINITION

The aim is to detect obstacles on the roads utilizing XYZ axis data from the accelerometer of the units installed in the moving vehicles. 
These detections will be used for the development of a digital twin platform where BMS is planning to monitor the state of bad potholes / speed bumps / etc.  
and provide data solutions in road authorities and municipalities where they can prioritize the fixing of obstacles that are causing dangerous events or accidents in the roads

ii) DATASET

The XYZ dataset contains 10hz measurements of the accelerometer of a single vehicle for one day movement activity in rome.

------------------------------------------------------------------------------------------
| Field             | Type           | Description                  | Unit precision  | Example \
------------------------------------------------------------------------------------------ \
| time              | datetime       | 10hz frequency timestamp     |  datetime       | 2022-09-29T09:54:34.315+0000 \
| acc_x             | float          | x-axis acceleration value    |  milli-g        | 10.4 \
| acc_y             | float          | y-axis acceleration value    |  milli-g        |  9.3 \
| acc_z             | float          | z-axis acceleration value    |  milli-g        |  9.3 \
| speed             | float          | The acceleration speed       |  km/h           |  15.3 \
| road_speed_limit  | integer        | The road speed limit         |  km/h           |  120 \
| heading           | float          | Geo position heading         |  degrees        |  359 \
| latitude          | float          | Geo position latitude        |  degrees        |  45.458943 \
| longitude         | float          | Geo position longitude       |  degrees        |  2.228940 \
| vehicle_make      | string         | The vehicle brand            |  -              |  hyundai \
| vehicle_model     | string         | The vehicle model            |  -              |  accent \
| vehicle_type      | string         | The vehicle type             |  -              |  car \
| road_type         | string         | The type of the road         |  -              |  local_road 

iii) APPROACH

1. First step is to load, clean and to sort data for further analysis.
2. The data will be resampled into 1 second intervals as the granularity provided is too detailed.
3. Generation of features is necessary. Instead of only using absolute values of acceleration, speed and heading angle, we will focus on the percent change of these factors.
4. A clustering model will be built to understand the behaviour of the vehicle and to predict the road condition.
5. After the model is built, each cluster will be analyzed and will be assigned to a condition: Normal, Pothole or Speed Bump.

iv) RESULTS

From the results, it is clear that:
Cluster 0 is when vehicle is traveling at high speed without much change in acceleration and heading. Common roads are important roads and motorways.
Cluster 1 is when a vehicle is traveling at relatively high speed with a change in heading and moderate change in acceleration. Most common road types are secondary and motorway.
Cluster 2 is when a vehicle is traveling through mostly secondary roads and there is a sudden change in speed but not a big change in heading.
Cluster 0 is standard roads, Cluster 1 is potholes, Cluster 2 is speed bump.



