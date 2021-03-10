# Hawaii Climate Analysis

![Image](http://www.hawaiipictureoftheday.com/wp-content/uploads/2014/01/1490595_604961066218954_1448251652_o-1024x683.jpg)

## Background

The objective of this project is to conduct a climate analysis of Hawaii in order to determine when is the best time to visit.  Data explorations can be done by connecting to the SQLite database provided.  Then, Python and SQL Alchemy can be used to perform the the climate analysis.

## Requirements

1) Line Graph - Plot the Precipitation vs Dates for 1 Year
2) Summary Table - Total number of Observations for each Station
3) Histogram - Frequency Hawaii's Temperature Range from the Most Active Station
4) Climate Flask Application -  Create api routes to return JSON data for the following:
    * Precipitation from the previous year
    * Stations from the datasets
    * Temperature of Observations (TOBS) from the previous year
    * Temperature Statistics for Start Date with the minimum temperature, the average temperature, and the max temperature for a given start date of your choice from the               database.
    * Temperature Statistics for Start Date and End Date with the minimum temperature, the average temperature, and the max temperature for a given start date and end date of         your choice from the database.
5) Hypothesis Testing of Climate Analysis
6) Bar Graph showing the average, minimum, and maximum temperature for chosen vacation dates
7) Calculating the total precipitation for all available stations for chosen vacation dates
8) Stacked line graph of the daily normals from chosen vacation dates


## Datasets

* [Hawaii SQLite Database](https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/Resources/hawaii.sqlite)
* [Hawaii Climate Measurements CSV](https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/Resources/hawaii_measurements.csv)
* [Hawaii Station Names CSV](https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/Resources/hawaii_stations.csv)


## Methods

<details>
   <summary><b>Dependencies and Database Connections</b></summary>
   
* Import Dependencies
* Connect to SQLite Database
* Retrieve all the table names in the database
* Create classes for each table
</details>

<details>
   <summary><b>Line Graph - Plot the Precipitation vs Dates for 1 Year</b></summary>
   
* Retrieve the most recent date from the measurement database
* Convert information to datetime format to retrieve all the dates from 1 year ago
* Perform SQL query to filter for all the dates and precipitation in the past year
* Create Dataframe to store all the information
* Using the information from the dataframe, create a line graph using Matplotlib
</details>

<details>
   <summary><b>Summary Table - Total number of Observations for each Station</b></summary>
   
* Perform SQL query that displays the station id, station name, and number of observations for each station
* Obtain count of all the stations available
* Sort by descending order to determine the most active station
* Calculate the minimum, maximum, and average temperature for the most active station
</details>

<details>
   <summary><b>Histogram - Frequency Hawaii's Temperature Range from the Most Active Station</b></summary>
   
* Perform SQL query that displays the date and temperature for the most active station for the past year
* Create Dataframe to store all the information
* Using the information from the dataframe, create a histogram using Matplotlib
</details>

<details>
   <summary><b>Climate Flask Application</b></summary>
   
* Using flask, connect to the database in SQLite.
* Create different routes to display climate and station information in JSON format
* Perform queries to retreive information 
   * **Home page (/)**<br> - background information and links to all api routes.
   * **Precipitation (/api/v1.0/precipitation)** <br> - Return a JSON list of all precipitation information of the past year.
   * **Stations (/api/v1.0/stations)**<br/> - Return a JSON list of stations from the dataset.
   * **TOBS (/api/v1.0/tobs)** <br/> - Return a JSON list of temperature observations (TOBS) for the previous year.
   * **Temperature Statistics for Start Date (/api/v1.0/startdate)**<br/> - Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a  given start date of your choice to the last day on the database.
   * **Temperature Statistics for Start Date and End Date (/api/v1.0/startdate/enddate)**<br/> - Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start date and last date of your choice. 
   * **Note:**  Dates should be entered in the format YYYY-MM-DD.<br/>
      * Example 1 (/api/v1.0/2017-05-01)
      * Example 2 (/api/v1.0/2017-05-01/2017-05-08)
</details>

<details>
   <summary><b>Hypothesis Testing of Climate Analysis</b></summary>
   
* Perform SQL queries to retrieve average climate information for June
* Repeat the same process for December
* Perform t-test to determine if there are any significant differences in the June and December temperatures
</details>

<details>
   <summary><b>Bar Graph showing the average, minimum, and maximum temperature for chosen vacation dates</b></summary>

* Create a function that returns the minimum, average, and maximum temperature by entering the start and end dates for your vacation.
* Create another function where it returns the annual average for the previous year data at the same time.
* Create list to plot the data on a bar graph with an error bar.
   * The bar graph is the average temperage.
   * The error bar is the difference between the maximum and minimum temperature.
</details>

<details>
   <summary><b>Total precipitation for all available stations for chosen vacation dates</b></summary>

* Create a query to select the station id, station name, latitude, longitude, station elevation and sum of the precipitation for each station.
* Create a dataframe to see information.
</details>

<details>
   <summary><b>Stacked line graph of the daily normals from chosen vacation dates</b></summary>
   
* Create a function that calculates the minimum, average, and maximum for all historic data matching a specific day
* Format the vacation dates to month and day
* Create a list that stores these dates
* Create an empty list to store minimum, average and maximum temperature
* Use the date list to loop through the function to retrieve the temperature results.  Then append them to the empty temperature list.
* Create pandas dataframe to plot stacked line graph.
* Plot line graph with the dataframe information
</details>

## Scripts

* [Climate Analysis Notebook](https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/climate_starter.ipynb)
* [Climate Flask Application](https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/app.py)

## Results

### Precipitation Analysis

* The average precipiation for the year is around 1.75 inches of rain.  
* The maximum precipitation is 6.7 inches around early September. The graphs show that there are more rainfalls around this period of time than the rest of the year. 
* Another time that rains a lot is during spring in the month of April.
* Average precipitaiton tends to be lower in June and October.
<p float="left">
  <img src="https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/Output%20Files/Annual%20Precipitation.png" width="700">
  <img src="https://github.com/cecileung1208/Hawaii-Climate-Analysis/blob/master/Output%20Files/Precipitation%20Stats.png" width="100"> 
</p>


### **Station Analysis**

To ensure that my analysis is accurate, weather information have been gathered from various stations.  

A query have been designed to determine the total number of stations and the most active station with the highest number of observations. 

| Station ID    | Station Name | Total Counts |
| ------------- | ------------- | ------------- |
|USC00519281 | WAIHEE 837.5, HI US | 2772|
|USC00519397 | WAIKIKI 717.2, HI US | 2724|
|USC00513117 | KANEOHE 838.1, HI US | 2709|
|USC00519523 | WAIMANALO EXPERIMENTAL FARM, HI US | 2669|
|USC00516128 | MANOA LYON ARBO 785.2, HI US | 2612|
|USC00514830 | KUALOA RANCH HEADQUARTERS 886.9, HI US | 2202|
|USC00511918 | HONOLULU OBSERVATORY 702.2, HI US | 1979|
|USC00517948 | PEARL CITY, HI US | 1372|
|USC00518838 | UPPER WAHIAWA 874.3, HI US | 511|


Then, a histogram has been created to show the frequency of the range of temperature in Hawaii form the most active station.

![Image](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/Output%20Files/Annual%20Temperature.png)


## **2. - Climate App**

Upon the completion of my initial analysis, a [Flask API file](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/app.py) have been designed for the queries I have developed.  The file can be run on Visual Studio Code.

The Flask API have the following routes:


* **Home page (/)**

* **Precipitation (/api/v1.0/precipitation)**<br/> - Return a JSON list of all precipitation information of the past year.
    
* **Stations (/api/v1.0/stations)**<br/> - Return a JSON list of stations from the dataset.
  
* **TOBS (/api/v1.0/tobs)** <br/> - Return a JSON list of temperature observations (TOBS) for the previous year.
  
* **Temperature Statistics for Start Date (/api/v1.0/startdate)**<br/> - Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start date of your choice to the last day on the database.
  
* **Temperature Statistics for Start Date and End Date (/api/v1.0/startdate/enddate)**<br/> - Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start date and last date of your choice. 
  
  **Note:**  Dates should be entered in the format YYYY-MM-DD.<br/>
         Example 1 (/api/v1.0/2017-05-01)<br/>
         Example 2 (/api/v1.0/2017-05-01/2017-05-08)<br/>
         
  
## **3. - Other Useful Analysis**

I have conducted additonal analysis to make the most out of my trip in the [Climate Starter Notebook](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/climate_starter.ipynb).

### **Temperature Analysis I**

Analysis have been conducted by determining the averages of June an December for all stations across all available years in the dataset. 

A T-Test has been conducted to determine to test the difference of the mean with the following hypothesis.

Null Hypothesis: Mean Difference = 0<br/>
Alternative Hypothesis: Mean Difference > 0<br/>

P-value = 0.00036573

Since the p-value is almost 0.0004 , there is a difference in the mean temperatures in June and December.  Paired t-tests are considered more powerful than unpaired t-tests because using the same samples eliminiate variation between the samples that could be caused by anything other than what’s being tested.

Details of the average figures are in the [Climate Starter Notebook](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/climate_starter.ipynb)

### **Temperature Analysis II**

My manager have approved my vacation days!  I am off to Hawaii from August 2 to August 10 and will be having lots of fun in the sun!!

The calc_temps function have been created to calculate the min, avg, and max temperatures for my trip.  The below graph shows the range of temperature during August 2 to August 10.

![Image](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/Output%20Files/Trip%20Average%20Temperature.png)

### **Daily Rainfall Analysis**

Calculating the the total rainfall per weather station using the previous year's matching dates for my trip.



|Station ID| Station Name | Latitude | Longitude | Elevation | Total Rainfall|
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
|USC00516128|	MANOA LYON ARBO 785.2, HI US|	21.33310|	-157.80250|	152.4|	0.92|
|USC00514830|	KUALOA RANCH HEADQUARTERS 886.9, HI US|	21.52130|	-157.83740|	7.0|	0.20|
|USC00519281|	WAIHEE 837.5, HI US|	21.45167|	-157.84889|	32.9|	0.06|
|USC00519397|	WAIKIKI 717.2, HI US|	21.27160|	-157.81680|	3.0|	0.02|
|USC00519523|	WAIMANALO EXPERIMENTAL FARM, HI US|	21.33556|	-157.71139|	19.5|	0.00|

### **Daily Normals**

The daily_normal function was used to calculate the averages for the min, avg, and max temperatures for my trip.  This date string will be in the format %m-%d that will use all historic TOBS that match that date string.

![Image](https://github.com/cecileung1208/SQLAlchemy-Surfs-Up/blob/master/Output%20Files/Daily%20Normals.png)

