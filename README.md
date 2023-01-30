# Barrier Interaction Behaviour Analysis

MoveApps 

Github repository: https://github.com/nilanjanchatterjee/Barrier_Interaction_Bahaviour_Analysis

## Description
The app identifies and classifies different behaviors of animal encounters with linear features (road, rail tracks, barriers, fences etc.). It requires a user specified buffer distance, minimum and maximum time interval for identification of different behaviors. The app is based on the BaBA package (Xu et al. 2021) https://besjournals.onlinelibrary.wiley.com/doi/10.1111/1365-2664.13806 

## Documentation
Animals do not behave in the usual manner when they encounter linear features and barriers. The app identifies these different behavior classes based on the changes in movement. The identified behaviors can be classified into three broad classes **Usual movement**, **Altered movement** and **Trapped**. **Usual movement** consists of Average movement and Quick cross, **Altered movement** consists of Bounce, Back and Forth and Trace while **Trapped** is signified when the animal movement is restricted within a close vicinity of the feature for a significant time. For more details about the behavior classes please go through the manuscript on BaBA app by Xu et al. 2021 (https://besjournals.onlinelibrary.wiley.com/doi/10.1111/1365-2664.13806).

### Input data
*move/moveStack* in Movebank format
*Linear feature layers* in Shapefile(.shp) format

### Output data
*MoveStack* in Movebank format   
*Road encounter* in .csv format   

### Artefacts
- Encounter_event_data.csv: Details of the identified behaviours
- Encounter_data.csv : Details of the road encounters 
- Event_plot_output.pdf: Document of plot of all identified behaviors 


### Parameters 
buffer: Distance to evaluate the effect of the linear feature/Barrier. Unit: `metres`.    
b_time: Maximum duration, that an encounter event would be considered as a short event *bounce* or *quick cross*. Unit: `hours`   
p_time: Minimum duration, that an encounter event would be considered as a *trapped* condition. Unit: `hours`   
w: The length of time, to include around the encounter event to calculate average movement straightness using a moving window. Locations included are all locations within `w/2` before the first location of the encounter event and `w/2` after the last location of the event.

### Null or error handling
*The app contains road shapefile from the Y2Y region but users can upload their own shapefiles also. Please be careful that the projection of the barrier feature shapefile should be lat-long (epsg 4326). Moreover, the identified behaviours are function of the user specified input (buffer and time), please be careful and use time intervals with respect to the fix-intervals.*

*Example* : **Parameter `b_time`**:  should not be smaller than the fix-intervals. If your data set has very different fix-intervals please create multiple workflows of individuals with similar fix-intervals.