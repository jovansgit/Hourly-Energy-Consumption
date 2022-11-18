# Hourly-Energy-Consumption
<img src="Resources/Static/Images/energy.jpg" align="center" height="300" width="1200">


## Table of Contents
- [Project Overview](#ProjectOverview)
  * [What is our Topic?](#WhatTopic)
  * [Why Energy Consumption?](#WhyEnergyConsumption)
  * [What questions are we hoping to answer?](#Questions)
  * [Description of Source Data](#DescriptionOfSourceData)
  * [Approach?](#Approach)
- [Database](#Database)
  * [Schema](#DBSchema)
  * [Preprocessing of Data](#Preprocessing)
- [Analysis & Visualizations](#Analysis)
- [Machine Learning Models](#MachineLearningModel)
- [Technologies](#Technologies)
- [Communication Protocols](#CommunicationProtocols)
- [Resources](#Resources)

## <a name="ProjectOverview"></a> Project Overview

### <a name="WhatTopic"></a> What is our Topic? 
The topic we will analyze is energy consumption.

### <a name="WhyEnergyConsumption"></a> Why Energy Consumption?
According to un.org, The world’s population is projected to reach 8 billion on November 15th, 2022.  The latest projections by the United Nations suggest that the global population could grow to around 8.5 billion in 2030, 9.7 billion in 2050, and 10.4 billion in 2100.  As our population increases so do our energy needs.  Those rising energy needs will not only influence our lives but will also affect the lives of our children.  Climate change, energy shortages, and increased energy costs are just scratching the surface of the impact.  To aid in kickstarting the conversation, we would like to build a model predicting the total amount of energy consumption and the rate of energy consumption, for a particular region.  We hope that our model may spark a desire for people to lead a more energy-efficient life.

### <a name="Questions"></a> Questions we hope to answer with Data
* Can we build a model to predict energy consumption for the following week?
* Can we identify any trends in energy consumption?

### <a name="DescriptionOfSourceData"></a> Description of our Source Data
We are using a data set from Kaggle which contains Date Time and Mega Watts of energy consumed to seed our database.  This data set spans from 2004-2018.  The original source for the energy consumption data is from the EIA.gov open data API, which has more recent readings of the data. For data after 2018, we are using the EIA.gov API.  We will also use population and regional temperature data gathered from Visual Crossings and Open Weather API's.

### <a name="Approach"></a> Approach:
We're going to pull the data in a CSV format into a database table. Later we will append the API sourced additional consumption readings.

## <a name="Database"></a> Database

### <a name="DBSchema"></a> Schema
<img src="Resources/Static/Images/Updated_Schema_Seg_2.png">

### <a name="Preprocessing"></a> Preprocessing of Data for EDA & Machine Learning Model
* The original datatime column was used to create several other date columns to depict daily and weekly trends. 
* There were 4 repeated datetimes with 2 different energy comsumption rates. As a result we replaced the energy consumption value of duplicated datetimes with the mean energy consumption. 
* In the dataset, we found 11 missing values in the COMED_MW columns. To fill these missing values we use mean interpolation.
* Seasonality was tested using the seasonal decomposition function. We used the multiplcative method because our amplitude changes across days. 

## <a name="Analysis"></a> Analysis & Visualizations
  1. The base time series plot below demonstrates the seasonality of the data over multiple years, however the years themselves are obscured by the density of the data
    <img src="https://github.com/jovansgit/Hourly-Energy-Consumption/blob/main/New%20folder/time_series_plot.png">
  When looking at one week of the data, the plot has clear daily seasonality, with a repeated pattern of hourly consumption rates occurring each day. We also observe an upward trend within this week of data, but this trend is likely a part of the annual seasonality we saw previously.
    <img src="https://github.com/jovansgit/Hourly-Energy-Consumption/blob/main/New%20folder/time_series_week_plot.png">
  2.  After breaking the Datetime Index into their own dimensions in terms of the hour of day, day of the week, month of year, and year of our dataset range. We can see that energy consumption is slightly higher Monday thru Friday than it is Saturday and Sunday, which is to be expected since many businesses do not operate on weekends in the U.S. Energy consumption typically peaks around July and August, and there are several more outliers within the months preceding and following the peak period than are observed during the cooler months (November thru April). Hourly energy consumption is at its lowest around 5 AM. After this time, usage increases at a higher rate until noon when the rate of change slows, building up to 7 PM when consumption declines back to the morning low. The mean energy consumption rates and interquartile ranges are fairly consistent from year to year, although a slight downward trend is observable.
    <img src="https://github.com/jovansgit/Hourly-Energy-Consumption/blob/main/New%20folder/boxplots.png">
  3.  The subplots help us identify the unique fluctuations of energy consumption rate by year. For example, post 2013 there is not the same heavy usage, causing lower peak summer energy usage.
    <img src="https://github.com/jovansgit/Hourly-Energy-Consumption/blob/main/New%20folder/seasonal_subplots.png">
  4.  One of the aspects of looking at time series data is seasonality. Since the amplitude of the daily data isn't consistent, we used 
  the multiplicative process for determining seasonality (Trend * Seasonality * Residuals) and as a result the top chart has consistent amplitude and demonstrates re-occuring seasonal cycles.
    <img src="https://github.com/jovansgit/Hourly-Energy-Consumption/blob/main/New%20folder/multiplicative_decomp.png">

## <a name="MachineLearningModel"></a> Machine Learning Models
  We have chosen a deep learning model,the LSTM (Long-Short Term Memory) network. We have chosen LSTM because it is able to detect both long and short term seasonal patterns. This was a good choice for our data beccause we are dealing with hourly energy consumption over the span of several years, so there will be several lengths  of seasonal trends.LSTM can triage the impact of different events, an example of this in on our data could be days with extreme weather. Some drawbacks of using LSTM is that it takes longer to train and require more memeory due to having more paremeters.
 
 Our data was broken into a 85% for our training set and 15% for our testing set. Our traning set includes dates from December 31st 2011 1:00am to July 17th 2:00pm and our training set includes dates from July 17th 3:00pm to January 2nd 2018 1:00pm.  We created our model with 50 nuerons in the LSTM layer, 10 epochs, and 3 lags. As we continue to determine how to calculate accuracy we will see if we need to adjust any parameters or the dates in our training set. 
 
## <a name="Technologies"></a> Technologies

We used the below technologies while completing this project:

- Tableau
- Python
- SQL - PostGres DB
- API's
- Colaboratory - Google

## <a name="CommunicationProtocols"></a> Communication Protocols

**Slack** – A messaging tool we used to coordinate meetings, send links and data <br>
**Microsoft Teams/Zoom** – We held meetings using Microsoft Teams and Zoom platforms <br>
**GitHub** – We utilized GitHub for Version management and collaboration. <br>

## <a name="Resources"></a> Resources

[1] **Data Files:** <br>
- [Kaggle DataFiles](Resources/DataFiles) <br>

[2] **API's:** <br>
- [The U.S. Energy Information Administration API](https://www.eia.gov/opendata/)
- [Open Weather API](https://openweathermap.org/api) <br>
- [Visual Crossing Weather API](https://www.visualcrossing.com/weather-api) <br>
- [US Census Population Data](https://www.census.gov/data/developers/data-sets/popest-popproj/popest.html) <br>

