### Reading Material for Data Incubator Interview
#### Author: Ancheng (Maximus) Deng 201805

Traffic is among the biggest causes of injuries or deaths in today’s mega cities. With Google map, people are feeling more convenient travelling but not more secured, for that there hasn’t been one product that can alert people about potential traffic accidents on streets they are driving through. During my capstone project, I am about to establish an early warning system called TES (Traffic Early-warning System) that can predict on the probability of accidents based on traffic speed, weather condition, roadwork and unsolved 311 service report on streets in Brooklyn, New York City. This system can further be embedded into navigators like Google Maps to make safer trip planning.

#### Original Data Source:

(1)NYPD Motor Vehicle Collisions (201703-201801); 

(2)Historical Weather Near Brooklyn (2015-2018); 

(3)311_Service_Requests_from_2010_to_Present; 

(4)Street_Closures_due_to_construction_activities_by_Block (2017-Present) 

#### Plot Explanation: 

(1)Dynamic gif showing the growing of traffic collision hot spots in Brooklyn from 201703 to 201801. Atlantic Avenue and Flatbush Avenue are top 2 street names where most of the traffic collisions happen.

![alt text](https://github.com/MaximusWudy/DataIncubator2018/blob/master/Brooklyn_cumulative_ggmap_v3.gif "Brooklyn Cumulative Collision Density")


(2)Tree map indicating the top contributors within each factor that could be significant in the TES model. Note that the area proportion of the factors is not as meaningful as the area proportion of the contributors within factors. 

![alt text](https://github.com/MaximusWudy/DataIncubator2018/blob/master/Tree_map_v2_1078_790.png "Treemap")

Note that during the time range of interest, there are more collisions happened in even weekday (Tue, Thu, Sat) plus Friday; Driver Inattention/Distraction is definitely the top cause of collision; when the collision happens within the open and closed time of a 311 traffic service request, then the request (as factor Complaint in the plot) will also be counted as a contributor towards the collision; Fog/heavy fog and haze/smoke are two severe weather types relative to thunder and damaging wind.

#### Added Data Source:

(5) NYC Real Time Traffic Speed Data Feed (2017-2018)

#### Generalized Linear Mixed Effect Model

Initial Model
![alt text](https://github.com/MaximusWudy/DataIncubator2018/blob/master/GLMM_mod1.png "GLMM Model 1")

Final Model
![alt text](https://github.com/MaximusWudy/DataIncubator2018/blob/master/GLMM_mod2.png "GLMM Model 2")
