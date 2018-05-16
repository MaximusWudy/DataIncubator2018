### Read Material for Data Incubator Interview
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

$$
\begin{aligned}
logit(E[y_{ij}|\mu_i]) = \beta_0 &+ u_i + \beta_1*Speed_{ij} + \beta_{2}*1\{Time_{ij} = Morning\} + \beta_{3}*1\{Time_{ij} = Afternoon\} \\
&+ \beta_{4}*1\{Time_{ij} = Night\} + \beta_{5}*1\{Time_{ij} = Midnight\} + \beta_6*Rainfall_{ij}\\
& + \beta_7*Snowdepth_{ij} + \beta_{8}*1\{Weather\ Type_{ij}=Fog\}+ \beta_{9}*1\{Weather\ Type_{ij}=Thunder\} \\
&+ \beta_{10}*1\{Weather\ Type_{ij}=Smoke\}+ \beta_{11}*1\{Weather\ Type_{ij}=Ice Pellet\}\\
& + \beta_{12}*1\{Roadwork_{ij}=True\} + \beta_{13}*1\{311Service_{ij}=True\}
\end{aligned}
$$

$$
i:\ street,\ \ j:\ accident\ at\ street\ i,\ u_i\sim N(0, \sigma^2)
$$

$$
\begin{aligned}
y_{ij} &= 1,\ if\ accident\ j\ caused\ by\ nondriver\ factors\ happens\ at\ street\ i\\
y_{ij} &= 0,\ otherwise
\end{aligned}
$$
