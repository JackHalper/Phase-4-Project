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





