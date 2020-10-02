# Prediciting Rain

## Introduction

Currently, there are zero commercially available irrigation systems that predict rain. This creates a lot of wasted water annually from watering right before it rains. In Houston alone, approximately 3.7 billion gallons of water is wasted from watering lawns right before it rains annually.

The aim of this project is to build a model to predict whether it will rain tomorrow. In this project we used a readily available dataset of Austrailian weather to build a proof of concept. This dataset is a conglomeration of scraped data from various weather stations in Austrailia over a period of 10 years.

The final model used would reduce wasted water in Houston by 2.9 billion gallons if every residential irrigation system employed this model. If employed worldwide a lot of water would be conserved.



## Libraries Used

To assist us in our research, we utilized the following libraries:

- Pandas - data cleaning and analysis
- Matplotlib - data visualization
- Seaborn - data visualization
- Numpy - data cleaning and analysis
- Math - data analysis
- Pickle - data transfer and storing
- Folium - vizualizations
- Sklearn - modeling


## Project objectives

The main objectives of this project are as follows:
Data collection and cleaning
Analyzing the data
Identify relevant machine-learning algorithms for the project.
Build classification models.
Validate the models.
Identify the most appropriate model.

## Dataset: "Rain in Austrailia"

We used Kaggle dataset for this project. The data comes from scaped weather from the Austrailia Bureau of Meterology. It contains more 140,000 observations and has 24 columns. This data is from 2007 - 2017.

#### Data Columns

- Sunshine: amount of sunshine
- Evaporation: amount of evaportation
- Cloud3pm: cloud cover at 3pm
- Cloud9am: cloud cover at 9am
- Pressure9am: atmospheric pressure at 9am
- Pressure3pm: atmospheric pressure at 3pm
- WindDir9am: wind direction at 9am
- WindGustDir: most common wind gust direction
- WindGustSpeed: max wind gust speed
- WindDir3pm: wind direction at 3pm
- Humidity3pm: humidity at 3pm
- Temp3pm: temperature at 3pm
- WindSpeed3pm: windspeed at 3pm
- Humidity9am: humidity at 9am
- RainToday: yes/no if it rained today
- Rainfall: amount of rainfall today
- WindSpeed9am: wind speed at 9am
- Temp9am: temperature at 9am
- MinTemp: day's min temperature
- MaxTemp: day's max temperature
- Location: weather station location
- RainTomorrow: yes/no if it rained tomorrow
- RISK_MM: amount of next day rain in mm
- Date: date of observation


## Data Cleaning and Feature Selection

This dataset had a lot of missing values in a few of the columns. In order to reduce the amount of nulls the data was grouped by region (custom feature) and date. From there we took the average value of the continuous columns and the mode of the categorical columns for each group. This data was used to impute. After this process we still had 6 observations with null values, so they were dropped.

Feature selection was perfromed in a myriad of ways depending on the type of model, but the best model was a logisitc regressor with kbest = 100 for feature selection. 

### Based on our model we identified three key features
Cloud cover at 3pm, wind direction, and location

Our EDA and modeling can be viewed in detail in our notebook, but here are some of our visualization that we did:

### Weather Stations

<img width="690" alt="Screen Shot 2020-10-02 at 12 57 17 AM" src="https://user-images.githubusercontent.com/65979022/94931392-b64bef00-0495-11eb-9800-892423e6daaa.png">

The weather stations data was collected from can be seen in the image above. The different colors represent the different regions that were feature engineered.

## Modeling

### Modeling Results

<img width="820" alt="modeling-results" src="https://user-images.githubusercontent.com/65979022/94931462-c82d9200-0495-11eb-8ed7-a0ae1bde8de2.png">

Our best model was a Logistic Regression with a recall score of 0.78. Recall was used because reducing false negatives is most important. We don't want to water if it will rain later that day.

### Most Important Features

![most_important_features](https://user-images.githubusercontent.com/65979022/94931420-bcda6680-0495-11eb-89c0-db0e0cc5108c.png)

This is a look at the top 20 most impactful features in our final model. As mentioned earlier cloud cover at 3pm, wind direction, and location are key features.


### Final Model Confusion Matrix 

![confusion_matrix](https://user-images.githubusercontent.com/65979022/94931733-1b9fe000-0496-11eb-8c0f-4a586e0ed57b.png)

As you can see from the normalized confusion matrix above, the model did a good job at limiting false negatives. However, because of this is struggled to with false positives. Overall, the model preformed well. 


## Conclusion

Based on our analysis, we can recommend including a predictive feature in residential irrigation systems. Our model could reduce ~80% of wasted water from watering before it rains. It would be better to market the product toward conservation/environment focused consumers. The model would only save consumers ~$150 annually. Conequently, I believe the water conservation would be a bigger draw for customers rather than the financial benefits. 

Finally, I recommend approaching city officials to make rain prediction required on all irrigation systems. This would increase the impact of water conservation and benefit cities as whole.


## Future Steps

Some additional steps that we would like to explore are as follows:
- Address precision issue
- Build model for residential use
- Predict farther in the future
- Utilize ‘neighboring’ predictions in a pseudo voting classifier model


https://docs.google.com/presentation/d/1jgoE_f_vWHqZwIAOyOTzPJ_BgS-FQCaEOjs7TIGPGzE/edit?usp=sharing
