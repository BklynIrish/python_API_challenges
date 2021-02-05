# Python API- What's the Weather Like?

## Background

Whether financial, political, or social -- data's true power lies in its ability to answer questions definitively. So let's take what I've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What's the weather like as we approach the equator?"

Now, I know what you may be thinking: _"Duh. It gets hotter..."_

But, if pressed, how would I **prove** it?

![Equator](Images/equatorsign.png)


## Part I - WeatherPy

In this example, I'll be creating a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To accomplish this, I'll be utilizing a [simple Python library](https://pypi.python.org/pypi/citipy), the [OpenWeatherMap API](https://openweathermap.org/api), and a little common sense to create a representative model of weather across world cities.

My first requirement is to create a series of scatter plots to showcase the following relationships:

* Temperature (F) vs. Latitude
* Humidity (%) vs. Latitude
* Cloudiness (%) vs. Latitude
* Wind Speed (mph) vs. Latitude

After each plot add a sentence or too explaining what the code is and analyzing.

My second requirement is to run linear regression on each relationship, only this time separating them into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude):

* Northern Hemisphere - Temperature (F) vs. Latitude
* Southern Hemisphere - Temperature (F) vs. Latitude
* Northern Hemisphere - Humidity (%) vs. Latitude
* Southern Hemisphere - Humidity (%) vs. Latitude
* Northern Hemisphere - Cloudiness (%) vs. Latitude
* Southern Hemisphere - Cloudiness (%) vs. Latitude
* Northern Hemisphere - Wind Speed (mph) vs. Latitude
* Southern Hemisphere - Wind Speed (mph) vs. Latitude

After each pair of plots explain what the linear regression is modeling such as any relationships I notice and any other analyses I may have.

**Optional** I will be creating multiple linear regression plots. To optimize my code, I will attempt to write a function that creates the linear regression plots.

My final notebook must:

* Randomly select **at least** 500 unique (non-repeat) cities based on latitude and longitude.
* Perform a weather check on each of the cities using a series of successive API calls.
* Include a print log of each city as it's being processed with the city number and city name.
* Save a CSV of all retrieved data and a PNG image for each scatter plot.

### Part II - VacationPy

Now let's use our skills in working with weather data to plan future vacations. Use jupyter-gmaps and the Google Places API as part of this project.

* **Note:** If having trouble displaying the maps I will try running `jupyter nbextension enable --py gmaps` in my environment and retry.

* Create a heat map that displays the humidity for every city from the part I.

  ![heatmap](Images/heatmap.png)

* Narrow down the DataFrame to find the ideal weather condition. For example:

  * A max temperature lower than 80 degrees but higher than 70.

  * Wind speed less than 10 mph.

  * Zero cloudiness.

  * Drop any rows that don't contain all three conditions. One wants to be sure the weather is ideal.

  * **Note:** I will feel free to adjust to any specifications but to be sure I limit the number of rows returned by my API requests to a reasonable number.

* Using Google Places API to find the first hotel for each city located within 5000 meters of my selected coordinates.

* Plot the hotels on top of the humidity heatmap with each pin containing the **Hotel Name**, **City**, and **Country**.

  ![hotel map](Images/hotel_map.png)

As final considerations:

* Create a new GitHub repository for this project called `API-Challenge` (note the kebab-case). **Do not add to an existing repo**
* I will complete my analysis using a Jupyter notebook.
* I WILL use the Matplotlib or Pandas plotting libraries.
* For Part I, I will include a written description of three observable trends based on the data-I don't believe my analyses were added to this repo.
* I intend to use proper labeling of my plots, including aspects like: Plot Titles (with date of analysis) and Axes Labels.
* For max intensity in the heat map, I'll set it to the highest humidity found in the data set.

## Hints and Considerations

* Spend the requisite time necessary to study the OpenWeatherMap API. Based on m iynitial study, I should be able to answer basic questions about the API: Where do I request the API key? Which Weather API in particular will I need? What URL endpoints does it expect? What JSON structure does it respond with? Before I write a line of code, I should be aiming to have a crystal clear understanding of my intended outcome.

* HINT: Create simple test cases outside my main script to confirm that I am using it correctly. Too often, when introduced to a new library, students get bogged down by the most minor of errors -- spending hours investigating their entire code -- when, in fact, a simple and focused test would have shown their basic utilization of the library was wrong from the start. Don't let this be you!

* Part of the expectation in this project is that one will use critical thinking skills to understand how and why it's recommended to use the tools used. What is Citipy for? Why would I use it in conjunction with the OpenWeatherMap API? How would I do so?

* In building my script, pay attention to the cities I am using in my query pool. Am I getting coverage of the full gamut of latitudes and longitudes? Or am I simply choosing 500 cities concentrated in one region of the world? Even if I was a geographic genius, simply rattling 500 cities based on human selection would create a biased dataset. Be thinking of how one should counter this. (Hint: Consider the full range of latitudes).

* Once I have computed the linear regression for one chart, the process will be similar for all others. As a bonus, try to create a function that will create these charts based on different parameters.

* Remember that each coordinate will trigger a separate call to the Google API. If I create my own criteria to plan my vacation, I will try to reduce the results in my DataFrame to 10 or fewer cities.

