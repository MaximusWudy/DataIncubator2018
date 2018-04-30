### Data Incubator Capstone Project Proposal
#### Author: Ancheng (Maximus) Deng 201804

Traffic is among the biggest causes of injuries or deaths in today’s mega cities. With Google map, people are feeling more convenient travelling but not more secured, for that there hasn’t been one product that can alert people about potential traffic accidents on streets they are driving through. During my capstone project, I am about to establish an early warning system called TES (Traffic Early-warning System) that can predict on the probability of accidents based on traffic speed, weather condition, roadwork and unsolved 311 service report on streets in Brooklyn, New York City. This system can further be embedded into navigators like Google Maps to make safer trip planning.

During this challenge I finished with data wrangling and exploratory analysis on Brooklyn motor vehicle collision hot spots map, which can reflect the change or continuing of collision hot spots from Mar 2017 to Jan 2018. I also created a tree map indicating top contributor within each selected factor group (such as severe weather condition, Cause of Collision and Vehicle Type). 

#### Plot Explanation: 
(1)Dynamic gif showing the growing of traffic collision hot spots in Brooklyn from 201703 to 201801. Atlantic Avenue and Flatbush Avenue are top 2 street names where most of the traffic collisions happen.
(2)Tree map indicating the top contributors within each factor that could be significant in the TES model. Note that the area proportion of the factors is not as meaningful as the area proportion of the contributors within factors. Note that during the time range of interest, there are more collisions happened in even weekday (Tue, Thu, Sat) plus Friday; Driver Inattention/Distraction is definitely the top cause of collision; when the collision happens within the open and closed time of a 311 traffic service request, then the request (as factor Complaint in the plot) will also be counted as a contributor towards the collision; Fog/heavy fog and haze/smoke are two severe weather types relative to thunder and damaging wind.

#### TES Prediction Model Description:
Generalized Mixed Effect model will be my first choice to obtain probabilities of a upcoming collision. The model takes into account the street levels variability (different streets should have different ‘intercepts’ which can be simplified using a random variable from a certain distribution assumption) and generally has a better performance than logistic regression model. I would also consider ensemble models such as XGBoost to enhance the performance of my model.

#### Data Sources: 
(1)NYPD Motor Vehicle Collisions (201703-201801); 
(2)Historical Weather Near Brooklyn (2015-2018); 
(3)311_Service_Requests_from_2010_to_Present; 
(4)Street_Closures_due_to_construction_activities_by_Block (2017-Present) 
(5)511NY Traffic Information
(6)Real-Time Traffic Speed Data
