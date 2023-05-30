
# Problem Statement

Earth is getting hotter day by day and these extreme weather events cause humongous damage to agriculture, energy and transportation with events like hurricanes, floods, heatwaves, heavy rainfall. Accurate long term predictions are useful to help people prepare and take action and adapt to these weather conditions.

## Task

Forcast sub-seasonal temperatures (temperatures over two-week period) with in United States

## Goals

Data Preprocessing

Feature engineering

Modeling

Build predictive models - I plan to start with base model: Linear regression and then move to Boosting techniques as required

## Dataset

The dataset is created in collaboration with climate change AI and everything was put together by WiDS 2023 Datathon team. 

## Data Description

The dataset consists of ~400k rows and 246 columnns like temperature, precipitation, humidity, start_date, location, and many other values generated from meterology labs. The columnn names are code like names and difficult to understand by labels. So need to look for documentation when required.

### Data Preprocessing

1. Missing Values: Ideally in many machine learning probems we either impute with mean or we delete the row if the percentage of missing values is significantly less. But in time series problem we cannot impute with mean nor we delete instead we use ffill() which just uses the last observed value.
   * Cannot impute with mean because: there will be a huge difference between current value and mean value. 
   * if it is snowing today, it is likely to snow tomorrow (logic for not imputing with mean)
3. Time ranges: the train dataset is from 2014 to 2016 and test dataset is for 2022. This is called Data-Drift which we will be tackling going further.
4. Different Unique Locations in train and test data: Noticed locations varying in train and test sets. 

  #### Insights
  1. There are 514 unique locations for given date
  2. There are difference in existing locations in train and test data
  3. For consecutive location groups (269,268)in train and test dataframes, found a precision error (in 16th digit after decimal) between         latitude and longitude points causing the difference in locations ultimately

    train_df location group 269
    lat and lon 0.5454545454545454 0.3666666666666666
  
    test_df location group 268
    lat and lon 0.5454545454545454 0.3666666666666665
  
  4. Round off the value to 14th digit to overcome this error and verify the values are same in train and test sets

4. Since this a time series problem it is better to change startdate to datetime

 
 









