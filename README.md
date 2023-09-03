# Final-Project-Statistical-Modelling-with-Python - Heather Lane

## Project/Goals

### My goals for this project were quite straightforward:
#### 1. Complete the project in the timeframe allowed and complete it as thoroughly as possible.
#### 2. Focus more on the tools and techniques employed and understanding how they work and how to generate the appropriate code and less on the actual outcomes for these specific data sets.
#### 3. Attempt to incorporate my area of interest into the project, specifically related to the post-secondary sector in Ontario and data related to colleges and universities.

## Process

### Accessing Data and EDA

#### I started by accessing each data set and spending some time learning about the variables provided through EDA. I didn’t include much of my exploratory work with the use of certain pandas functions in the notebooks since this wasn’t requested. But I did look at data types, and summaries of the data using .shape, .value_counts, .nunique, and .describe. I also looked for missing and duplicate data. I went through this process for the City Bikes data, the Foursquare data, and the Yelp data that I requested from each of the three APIs. Rather that getting bar and restaurant data from both Foursquare and Yelp I decided to request data for Post-secondary institutions (a particular POI for me) from Foursquare and to request ‘bar’ information from Yelp. I put each json file into a dataframe and then decided which columns I wanted and created a new dataframe with just the columns I was interested in having for the project (although I didn’t end up using all the ones I chose).

### Creating and Saving DataFrames for the joining data part of the project

#### I created the bikes dataframe using one approach that involved parsing the json file into a data dictionary and then turning the dictionary into a data frame. This was easy since I was just requesting a complete json file with the data for one city (Toronto). I struggled a bit with the Foursquare and Yelp requests as it required a function that would be able to request data for each bike station location based on latitude and longitude. A mentor assisted me with learning the process to request that data directly into a new dataframe. 

#### I saved the data frame created in the city_bikes notebook and the data frames created in the yelp_foursquare_EDA notebook as .csv files so that I could access then easily for the data joining activity in the joining_data notebook.

### Joining Data

#### I accessed the three csv files and created dataframes for each in the joining_data notebook. I joined the Foursquare dataframe to the bikes dataframe first on the “ll” column (which contained latitude and longitude data). I had created a “ll” column in the bikes data by concatenating two columns as a string knowing that this would be required to join the foursquare data. I then joined the Yelp data to the new dataframe that contained the bikes and foursquare data. In this case I joined the Yelp dataframe on both the latitude and longitude columns. The joining process was very straightforward.

### Creating and commenting on visualizations

#### Although we were required to create and comment on only one visualization, I created 4 different ones. Each of them (histogram, scatterplot and bar charts) provided some interesting insights into the data that I commented on in within the notebook.

### Conversion of the dataframe into a SQLite database

#### I did this last step before moving on to the model_building notebook activity.

### Model building

#### I don’t think that the data that I chose to include in the dataframes was the best for building a regression model but I went though the activity to complete what was requested.  I used the number of venues, average number of venue reviews and average venue rating as the independent variables and the percentage of free rental bikes (as a percentage of number of slots at the station) as the dependant variable. I completed the analysis of the output in the model_building notebook, including comments on confounding variables. 

## Results

#### Below are the results from my  regression model. This same discussion can be found in my model_building notebook.

#### R-squared 
##### R-squared reflects the fit of the model. The R-squared value in this model is 0.167 and the Adjusted R-squared is 0.161 which means that the model is capable of explaining only 16.1% of the patterns in the data.

#### P>|t| (p-value)
##### The output here shows a p-value of 0.012 or less for each of the indpendant variables. The probablity of the relationship between number of venues, average number of venue reviews, and average venue rating for venues near a location and of free rental bikes available being due to chance is 1.2% or lower. This of course is only applicable for the specific date and time that the city bikes data was retrieved and could change based on the day and time of day that the data is observed.

#### Coef
##### The coef for the constant and each of the variables is displayed. The interesting one to me is and coef for mean venue rating. It is -11.4077. It indicates a negative correlation between mean venue rating and percent of free bikes at a bike sation. The bike sations with higher rated venues within 1000 metres of the station appear to have a lower percentage of the bikes at that station available for use. This of course could also be because areas where there are higher rated venues also have more atractions, more tourist traffic and are higher populated areas which would explain higher bike rental use.

#### Confounding Variables
##### There are likely other variables that are really the driver behind both the independant and dependant variables in this case, the most obvious ones being the resident population and volume of tourists regularly visiting specific areas of the city. More residents and more tourists would both likely be positively correlated with number of rental bikes being used and number of venues open for business in each region of the city. These are likely confounding variables and should be taken into account when reviewing this model.

##### It should also be noted that the data on bike use was retrieved from the City Bikes API on a specific date and at a specific time. If the data were observed on a different date or at a different time it could impact the model differently. It would make sense to look at some average data or compare the output for data on different days of the week and different months of the year.

## Challenges 

### There were three big challenges for me when doing this project.

#### 1. Figuring out how to get the data from the APIs, particularly from Foursquare and Yelp was a challenge. Getting the url exactly right and figuring out how to iterate through the latitude and longitude of the bike stations was tricky. The mentor I talked to for some time was really helpful in getting though this part of the activity. A classmate was also very helpful in discovering the format required for the Yelp api-key in the request as this was not readily apparent in reviewing the documentation. I still struggle with making sense of the documentation available for many of the tools we are using in this course but it is getting a bit better the more I do. 

#### 2. I have also found making sense of json files and determining how to parse the data from them especially challenging, especially if it is heavily nested. This is also getting better with each activity but a good part of my time spent on this project was focused on overcoming this challenge.

#### 3. The last challenge for me was finding some obvious ways to use the joined data to build a model. These data sets just didn’t seem to have any variables that logically seemed like possible predictors of other variables but I decided that doing the activity and using the tools we are learning was more important than the results or the predictive capability of the model.

## Future Goals

### The main thing I would have done if I had more time is to seek data that may have more predictive capability. I would like to have additional variables to consider, review and include in the model building activity. Some examples:

#### - monthly bike rental volume over a year
#### - neighbourhood populations
#### - tourist traffic and volume throughout the year
#### - restaurant and bar years of operation
#### - restaurant and bar closures
#### - number of post-secondary student bike rentals

