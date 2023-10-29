# Investigating Car Crashes in Chicago, IL

## Overview
The City of Chicago has tasked Halper Consulting with identifying root factors that contribute to a variety of car crashes. Car Crashes have resulted in approximately 80 fatalities in Chicago 2023 YTD. This Project leverages model intepretability to help investigate contributing factors for three distinct car-crash causes.

## The Data
The City of Chicago has provided a dataset of all car crashes within city limits from 2015 - Present 

The Dataset includes:

774,000+ Car Crashes
1,580,000 + Vehicles involved in these crashes

Features of these datasets our exhaustive and include: 
- Weather Conditions
- Vehicle Information
- Road Conditions
- Maneuever at time of Crash
- Primary Crash Cause
- Secondary Crash Cause
- and More

## The Approach

There are three car crash category causes of interest: 

Those Involving:

Traffic Violations
Environment Factors
Distracted Driving
We build out three models for each car crash type and treat it each as seperate binary classification problem


Random Forest
XGBoost
Stacking Classifier with the previous two models and utilizing logistic regression as final estimator
Leveraging the intepretability of the models we use Feature Importances to tease out the most important contributing factors to each crash type

## Initial Findings

- Timing
- The Most Frequent Times for Car Crashes are in the evening commute hours from approximately 3-6PM
![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/80745c52-30bd-45f0-982f-f511a7c6dda6)


- The Most Frequent Day of The Week for Crashes is Saturday

 ![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/30b39d6f-9974-46e6-8f90-dc16311833be)

- The Most Frequent Month for Crashes is from the Late Spring to Early Fall

 ![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/8ed34b85-e6a0-47a4-97e6-9f01a1ac9da2)
 

- The Most Common Crash Cause is Traffic Violations

![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/6090db12-97cc-46ca-b629-7f76db26eacb)


## Model Results 

#### Car Crash Type #1 Traffic Violations
Ran CV Grid Search to Hyperparameter tune both models
- Random Forest Train Score: 0.6976221672294489
- XGBoost Train Score: 0.6923847124441861
- Stacking Classifier Train Score: 0.7221177139299779

![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/88c7896c-6d86-427e-af08-f6588a412d47)


![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/070e28df-fbdf-4253-92d3-8f156dc67f09)

#### Car Crash Type #2 Environmental Factors
- Random Forest Train Score: 0.8400617144785825
- XGBoost Train Score: 0.8404812378109202
- Stacking Classifier Train Score: 0.8456666486223137

![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/279011cc-0885-4ab5-bd22-56d93100bf04)

![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/51258d6d-70cb-4f60-a2d2-eea3a04d2990)


#### Car Crash Type #3 Distracted Driving 
- Random Forest Train Score: 0.8401293732932101
- XGBoost Train Score: 0.8409955218357096
- Stacking Classifier Train Score: 0.8422562659015861

 ![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/107069ba-66b7-48d2-95b3-d9c21dda5b92)

 ![image](https://github.com/JackHalper/Phase-4-Project/assets/137962760/1a89b4a8-a92d-43ff-ba8e-a120c46dd9cd)

# Feature Importances

## Car Crash Type #1 Traffic Violations

### XGBoost
- ROAD_DEFECT_RUT, HOLES: 0.13282505
- ROADWAY_SURFACE_COND_ICE: 0.05840006
- MANEUVER_PASSING/OVERTAKING: 0.03762629
- MANEUVER_SKIDDING/CONTROL LOSS: 0.0326024
- MANEUVER_CHANGING LANES: 0.030215977
- WEATHER_CONDITION_CLEAR: 0.027446792
- MANEUVER_OTHER: 0.02605336
- MANEUVER_U-TURN: 0.023584208
- ROAD_DEFECT_OTHER: 0.02240528
- VEHICLE_TYPE_UNKNOWN/NA: 0.021395873
  
 ### - Random Forest
 - ROAD_DEFECT_RUT, HOLES: 0.05645262324059971
 - CRASH_HOUR: 0.05555619387826054
 - WEATHER_CONDITION_CLEAR: 0.054109648605325376
 - MANEUVER_PASSING/OVERTAKING: 0.05321098109402222
 - WEATHER_CONDITION_SNOW: 0.04986857608792069
 - ROADWAY_SURFACE_COND_SNOW OR SLUSH: 0.04866723068492083
 - ROADWAY_SURFACE_COND_ICE: 0.03832337226654902
 - VEHICLE_TYPE_UNKNOWN/NA: 0.03285615569803651
 - MANEUVER_STRAIGHT AHEAD': 0.0312895027236073
 - MANEUVER_SKIDDING/CONTROL LOSS: 0.031096388965273402

### Key Takeaways:

- Road Defects, including Ruts and Potholes, is the top feature for both models indicating that it is an important predictor of traffic-violation related crashes. Road defects may increase the risks of - violating traffic laws (speeding etc.)
- Another common top predictor is Icy/or Snow/Slushy Surface; This again may penalize speeding/otherwise violating traffic laws driver's in that mistakes are amplified
- Another common predictor is executing an overtaking maneuver

## Recommendations

- Fix and maintain roads to eliminate dangerous defects
- increase/enhance enforcement of penalties on days with snowy/icy road conditions and have law enforcement focus on illegal/violating overtaking maneuevers to disincentivize these and hopefully minimize crashes associated with traffic violations

## Car Crash Type #2 Environmental Factors

### XGBoost
- WEATHER_CONDITION_CLEAR: 0.136448742551223
- WEATHER_CONDITION_SNOW: 0.12638171982848465
- ROADWAY_SURFACE_COND_SNOW OR SLUSH: 0.1073100102163434
- ROAD_DEFECT_RUT, HOLES: 0.10538344599489798
- ROADWAY_SURFACE_COND_ICE: 0.07478381855189199
- WEATHER_CONDITION_RAIN: 0.04295527146602885
- ROADWAY_SURFACE_COND_WET: 0.042676797262312834
- CRASH_MONTH: 0.031638746219184076
- ROAD_DEFECT_NO DEFECTS: 0.029894871234032946
- ROAD_DEFECT_OTHER: 0.02513702881114677
  
 ### - Random Forest
 - WEATHER_CONDITION_CLEAR: 0.4920067
 - WEATHER_CONDITION_SNOW: 0.102035984
 - ROAD_DEFECT_RUT, HOLES: 0.08848574
 - ROADWAY_SURFACE_COND_ICE: 0.03640183
 - ROADWAY_SURFACE_COND_UNKNOWN: 0.028032944
 - ROAD_DEFECT_OTHER: 0.021701712
 - WEATHER_CONDITION_CLOUDY/OVERCAST: 0.013265923
 - ROADWAY_SURFACE_COND_SNOW OR SLUSH: 0.013091118
 - ROADWAY_SURFACE_COND_WET: 0.008959251
 - ROAD_DEFECT_UNKNOWN': 0.0074572377
### Key Takeaways/Recommendations
- Weather Condition Clear is the top predictor of this crash, which is perplexing given this is the environmental factors crash cause
- Environmental Factors include the following more granular crash types:
   - Weather
   - Vision Obscured
   - Road Engineering/Surface/Marking Defects
   - Road Construction
   - Evasive Action Due to Animal
   - Object
   - Non-Motorist
   - Animal
 - Unsuprisingly, Road Defects and Weather related factors comprise the top 10 of both feature importance arrays
 - Weather can't be controlled so likely fixing road defects is the only actionable takeaway from this category

   ## Car Crash Type #3 Distracted Driving

### XGBoost
- WEATHER_CONDITION_CLEAR: 0.08245022
- ROADWAY_SURFACE_COND_SNOW OR SLUSH: 0.049165007
- ROAD_DEFECT_RUT, HOLES: 0.038293786
- LIGHTING_CONDITION_DARKNESS, LIGHTED ROAD': 0.02742191
- ROADWAY_SURFACE_COND_ICE: 0.026420686
- MANEUVER_STRAIGHT AHEAD: 0.024488121
- MANEUVER_PASSING/OVERTAKING: 0.023601545
- MANEUVER_SLOW/STOP IN TRAFFIC: 0.021619132
- VEHICLE_TYPE_UNKNOWN/NA: 0.020935193
- MANEUVER_CHANGING LANES: 0.02038911
  
 ### - Random Forest
 - WEATHER_CONDITION_CLEAR': 0.15399593769831993
 - WEATHER_CONDITION_SNOW: 0.10793584668692917
 - ROAD_DEFECT_RUT, HOLES: 0.09323719809401416
 - ROADWAY_SURFACE_COND_SNOW OR SLUSH: 0.09048174146416985
 - ROADWAY_SURFACE_COND_ICE: 0.06989832895770214
 - ROADWAY_SURFACE_COND_WET: 0.04918333659082352
 - WEATHER_CONDITION_RAIN': 0.03914730614911011
 - ROAD_DEFECT_NO DEFECTS': 0.03193895623891997
 - CRASH_MONTH: 0.030939976851954668
 - ROAD_DEFECT_OTHER: 0.02425734237940196
### Key Takeaways/Recommendations
- Once Again Weather/Surface Conditions and Road Defects dominate the feature importance; Clear Weather shows up again; this may be due to the fact that Driver's are more comfortable taking risks in a safe-seeming environment; in other words, clear dry conditions may lull drivers into complacency
- Road Defects and Weather Conditions/Surface Conditions once again dominate the top 10 in terms of feature importance suggesting these factors may play a role in all types of crashes and increase the risk of crash from all causes


