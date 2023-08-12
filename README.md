# python-api-challenge
A python with APIs project to visualize the weather of over 500 cities of varying distances from the equator in order to make travel plans, such as finding hotels. 

## Table of Contents
#### Introduction
#### Requirements & Dependencies
#### Analysis and Results
#### Usage
#### Contributing
#### License


#### Introduction
This project uses two Jupyter Notebook (ipynb) scripts with python and appropriate software components, as well as Application Programming Interface (API) to gather weather data about randomly selected cities around the world, in order to short-list hotels in cities that meet specified weather critieria. The project includes making API calls, creating DataFrames, making scatter plots, computing and analyzing linear regressions, creating interactive maps, and saving visulaizations as outputs in a designated folder. 

- The project includes code features for protecting API keys. 

- The code for the random selection of cities is not seeded, and so responses will vary from one API call to another.


#### Requirements & Dependencies
- Developers are highly encouraged to set up a virtual environment to ensure proper management of dependencies. 

You will need the following software components:

- Python (version 3.10.9)
- Pandas (version 2.0.3)
- Matplotlib (version 3.7.1)
- hvplot.pandas
- requests
- scipy.stats.linregress
- citipy

### Analysis (WeatherPy)
##### Random City Selection
An API request was made OpenWeatherMap to randomly select cities around the world using maximum and minimum longitude values (-180 t0 180) as well as maximum and minimum latitude values (-90 to 90). The code for the request includes a "for" loop that appends to a list, and then the total number of cities in the list is calculated and displayed. 

###### Output
<img src = "/Images/len_city_list_pic.png" width="300"/>

---
##### Retrieve Data for Cities
The data for the cities were retrived and handled with JSON. This was done using functions such as "for", "if", "try", "else", "except" and "pass" to ensure that the retrieval continued in instances such as if an error ocurred, or if no data was found.. A logger was included to print different statuses/actions during the data retrieval. 
Here is a sample of how the logger operates:

###### Output
<img src = "/Images/weather_data_log_pic.png" width="600"/>

---
##### Number Cities in the Retrieved Data and Check for Blanks
It is useful to count the number of cities in the retrieved data as well as check that the data is complete. 

###### Output 
<img src =  "/Images/len_city_data_pic.png" width="200"/>

<img src =  "/Images/check_for_blanks_pic.png" width="400"/>

---
##### City DataFrame 
The city data was exported as a csv file and then read by pandas to create a DataFrame.

###### Output
<img src = "/Images/city_data_df_head_pic.png" width="800"/>

---
##### Scatter Plots
The city DataFrame was used to create four scatter plots to check relationships between city latitude and max temperature, humidity, cloudiness, and wind speed. 

###### City Latitude vs Max Temp Output
<img src = "/Images/lat_temp_pic.png" width="600"/>
<br>
<br>
<br>
<br>
<br>

###### City Latitude vs Humidity Output
<img src = "/Images/lat_humid_pic.png" width="600"/>
<br>
<br>
<br>
<br>
<br>

###### City Latitude vs Cloudiness Output
<img src = "/Images/lat_cloud_pic.png" width="600"/>
<br>
<br>
<br>
<br>
<br>

###### City Latitude vs Wind Speed Output
<img src = "/Images/lat_wind_pic.png" width="600"/>

---
##### Hemisphere DataFrames 
Two DataFrames were created: one for cities located in the Northern Hemisphere with latitiude of zero or greater, and another for cities located in the Southern Hemisphere with latitude less than zero. See prewiews of the DataFrames below:

###### Northern Hemisphere DataFrame Head Output
<img src = "/Images/north_hem_df_head_pic.png" width="800"/>
<br>
<br>
<br>
<br>
<br>

###### Southern Hemisphere Dataframe Head Output
<img src = "/Images/south_hem_df_head_pic.png" width="800"/>

---
##### Linear Regressions
A linear regression function was defined and applied to the four relationships that were previously graphed with scatter plots. The regressions were separated by the Northern and Southern Hemisphere DataFrames. A total of 8 linear regressions were done with the r-values and equations printed out for each regression. 

###### Latitude vs Max Temp Output (North)
<img src = "/Images/north_lat_temp_reg_pic.png" width="600"/>

###### Latitude vs Max Temp Output (South)
<img src = "/Images/south_lat_temp_reg_pic.png" width="600"/>

###### Latitude vs Humidity Output (North)
<img src = "/Images/north_lat_humid_reg_pic.png" width="600"/>

###### Latitude vs Humidity Output (South)
<img src = "/Images/south_lat_humid_reg_pic.png" width="600"/>



###### Latitude vs Cloudiness Output (North)
<img src = "/Images/north_lat_cloud_reg_pic.png" width="600"/>

###### Latitude vs Cloudiness Output (South)
<img src = "/Images/south_lat_cloud_reg_pic.png" width="600"/>

###### Latitude vs Wind Speed (North)
<img src = "/Images/north_lat_wind_reg_pic.png" width="600"/>

###### Latitude vs Wind Speed Output (South)
<img src = "/Images/south_lat_wind_reg_pic.png" width="600"/>
---

### Analysis (VacaytionPy)
##### Read and Preview the City DataFrame
Pandas was used to read and create the city DataFrame that was exported as a csv file in the WeatherPy script.

###### Output
<img src = "/Images/city_data_df_head_pic.png" width="600"/>

---
##### Dynamic Humidity Map
Hvplot was used to create a dynamic humidity map with the city DataFrame. Each city is represented by a circle, and the sizes the circles correspond to the humidity levels of the cities.
###### Output
<img src = "/Images/humidity_map.png" width="1000"/>

---
##### Filtered City DataFrame
The city DataFrame was filtered with weather criteria, such as preferred ranges for temperature, humidity, cloudiness, wind speed, longitude and latitude.  

###### Output
<img src = "/Images/criteria_city_df.png" width="800"/>

---
##### Hotel DataFrame
The pandas "copy" function was used to create a hotel DataFrame with specific columns. An empty column was also added to store the hotel names after the next step-the Geoapify search.  
###### Output
<img src = "/Images/criteria_city_blnk_hotel.png" width="800"/>

---
##### Geoapify Hotel Search
The hotel search was done through Geopaify and handled with JSON. This was done using functions such as "for", "try", and "except" to ensure that the retrieval would be not interrupted. A logger was included to print different statuses/actions during the data retrieval. 
Here is sample of how the logger operates:

###### Logger Output
<img src = "/Images/hotel_search_logger.png" width="600"/>

---
##### Complete Hotel DataFrame
The code for the Geoapify search for hotels include adding the hotel names to create a completed hotel DataFrame as previewed below:

###### Output
<img src = "/Images/complete_hotel_df.png" width="800"/>

---
##### Filtered Hotel Dynamic Map
The hotel DataFrame was filtered to exclude cities where no hotels were found, and then hvplot was used to create a dynamic map of the hotel options across the cities that met the specified weather criteria. 

###### Output
<img src = "/Images/hotel_map.png" alt="regression_screenshot" width="1000"/>

---
#### Usage
Here's how to use the Jupyter Notebook WeatherPy and VacationPy scripts:

- ##### Create a pyhton script to store and import API keys as aliases. 

- ##### Distribute code appropriately across Jupiter Notebook cells to display the desired output.

- ##### Run the code.
- The scripts will make API calls, organize and analyze data to display the specified elements in-line 

#### Contributing

Contributions to this project are highly encouraged! If you wish to contribute, please follow these guidelines:

- Fork the respective repository for the Pymaceuticals Jupyter Notebook script and clone it locally.
- Create a new branch for your feature or bug fix.
- Commit your changes with descriptive commit messages.
- Push your branch to your forked repository.
- Submit a pull request to the original repository.
- Please ensure that your code adheres to the project's coding style and conventions.


If you encounter any issues or have suggestions for improvements, please open an issue on the GitHub repository.

### License
This project is licensed under the MIT License. Feel free to use, modify, and distribute the code as per the terms of the license. 
