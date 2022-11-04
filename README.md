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
Our topic is energy consumption.

### <a name="WhyEnergyConsumption"></a> Why Energy Consumption?
According to un.org, The world’s population is projected to reach 8 billion on November 15th, 2022.  The latest projections by the United Nations suggest that the global population could grow to around 8.5 billion in 2030, 9.7 billion in 2050, and 10.4 billion in 2100.  As our population increases so do our energy needs.  Those rising energy needs will not only influence our lives but will also affect the lives of our children.  Climate change, energy shortages, and increased energy costs are just scratching the surface of the impact.  To aid in kickstarting the conversation, we would like to build a model predicting the total amount of energy consumption and the rate of energy consumption, for a particular region.  We hope that our model may spark a desire for people to lead a more energy-efficient life.

### <a name="Questions"></a> Questions we hope to answer with Data
* Can we build a model to predict energy consumption for the following year?
* Can we identify any trends in energy consumption?

### <a name="DescriptionOfSourceData"></a> Description of our Source Data

### <a name="Approach"></a> Approach:

## <a name="Database"></a> Database

### <a name="DBSchema"></a> Schema
<img src="Resources/Static/Images/SchemaForSegment1.png">

### <a name="Preprocessing"></a> Preprocessing of Data
* Add season and time of day attributes to the data for additional analysis 

## <a name="Analysis"></a> Analysis & Visualizations

## <a name="MachineLearningModel"></a> Machine Learning Models
We are using a superivised model because we are using labled data. More specfically, our model will be multiple linear regression because we are predicting energy consumption in megawatts using multiple independent variables. Our target variable will be megawatts used per hour. Our features will be tempearture,cloud cover,humidity,precipitation,dew point,season,wind speed,and wind direction. 

## <a name="Technologies"></a> Technologies

We used the below technologies while completing this project:

- Tableau
- React
- Python
- SQL - PostGres DB
- API's

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
