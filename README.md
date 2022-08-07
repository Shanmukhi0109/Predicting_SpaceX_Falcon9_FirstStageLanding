SpaceX advertises the launch of Falcon9 rocket with a cost of 62 million dollars. As SpaceX reuses the first stage there is much of saving. Hence predicting the landing of the first stage is important to determine the cost of launch so that other companies can use the information to bid against SpaceX for rocket launch.

	1. First Data is collected using API's:
	•   Here we define a series of helper functions that will help us to use the API to extract information using identification numbers because after extracting data using the SpaceX API we see lot of data are API's.
	•  We will again use the API's to get information about the launches using the ID's. Finally the data will be stored in the lists present in every helper function. 
	• Then the lists and other columns required are converted into dictionary which again converted into pandas dataframe.
	• All the fields with only Falcon 9 launches are retrieved and basic data wrangling is done by imputing Payload mass column null values with mean.
	
	2. Data collection with Web Scrapping:
	• Historical launch records  of Falcon 9  are retrieved from a web page titled "List of Falcon 9 and Falcon Heavy launches https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches using Beautiful soup object.
	• All the tables are retrieved from the web page and to print actual records we took table no 3 and iterated over the <th> element to see the column names.
	• Some helper functions are already provided to process web scrapped HTML table.
	• A dictionary is created from all the column names as keys and all required parsing is done to fill all column values to their respective columns and later converted the dictionary into an dataframe.
	
	Final Dataset Columns:
	['Flight No.', 'Launch site', 'Payload', 'Payload mass', 'Orbit', 'Customer', 'Launch outcome', 'Version Booster', 'Booster landing', 'Date', 'Time']
	
	3. Exploratory data analysis(EDA):
	• Null values percentages and data types of each column are checked.
	• Calculated the number of launches on each site.
	• Calculated the number and occurrence of each orbit.
	• Calculated the number and occurrence of mission outcomes per orbit type.
	• Created a landing outcome column label based on outcome column.
	
	4. EDA with SQL:
	• Dataset is loaded in IBM Db2  console and loaded the sql connection and  established a connection to the database.
	• Following queries were executed as part of exploration:
		○ Display the names of the unique launch sites in the space mission.
		○ Display 5 launch sites where launch sites begin with the string 'CCA'.
		○ Display the total payload mass carried by boosters launched by 'NASA (CRS)'.
		○ Display average payload mass carried by the booster version F9 v1.1.
		○ List the date when the first successful landing outcome in ground pad was achieved.
		○ List the name of the boosters which have success in drone ship and have payload mass greater than 4000 but less than 6000.
		○ List the total number of successful and failure mission outcomes.
		○ List the names of the booster_versions which have carried the maximum payload mass.
		○ List the failed Landing_outcomes in drone ship , their booster versions and launch site names for in year 2015.
		○ Rank the count of landing outcomes between the date 2010-06-04  and 2017-03-20 in descending order.
		
	5. EDA with Data Visualization:
	• In order to understand the affect on variables on launch outcome following visualizations have been plotted:
		○ Scatter plots between Flight Number and Payload Mass, Flight Number and Launch Site, Payload Mass and Launch Site , Flight Number and Orbit type, Payload Mass and Orbit
		○ Bar plot for the success rate of each orbit.
		○ Line chart for launch success yearly trend.
		○ By visualizing we have found the important variables that affect the launch and Feature Engineering is done by selecting few features for further analysis. 
		○ One hot Encoding is done to all categorical variables to create dummy variables and make a dataframe resulting all feature columns and their encoded ones
		○  As such dataframe contains only numbers all the numeric columns are cast to float64.
		
	6. Launch Sites Locations Analysis with Folium:
	• All the launch sites are added on to the map by their coordinates using folium.map.marker and folium.circle 
	• All the success/failed outcomes are marked on map using Marker clusters because there could be many markers with same coordinates.
	• Mouse position is used to obtain coordinates of location when hovered. Then all the nearby proximities locations are taken and distance from the launch sites are calculated. 
	• Later using folium.marker to add marker at the  nearby proximity and Polyline is used to draw line from proximity to launch site.
	
	7.  Dashboard using Plotly Dash:
	• A pie chart depicting the total success launches by site
	• Scatter plot of Payload mass and Class with hue of Booster version Category and scaler for Payload range.
	
	8. Machine Learning Prediction:
	• Explanatory variables are standardized and transformed and response variable is changed into numpy array.
	• Train and test splits are done with 20% test size.
	• Logistic Regression, SVM, Decision tree Classifiers, KNN are used and Hyper parameter tuning is done using GridSearchCV  object and fitted it to find the best parameter.
	• Accuracy of test data is calculated.
	• Yhat is predicted and respective confusion matrix are plotted.
	
	All the models have nearly an accuracy of 83.3%
	
	
	
	
		
		
		
		
		
	
![image](https://user-images.githubusercontent.com/110771738/183310957-2254efe1-0563-4836-9772-cd9597cba931.png)

  
