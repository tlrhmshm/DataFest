# ASA DataFest 2017

## Introduction
We were given a dataset (n = 11 million) of customer search information from 2015 on a website (that can't be disclosed until after May) for booking hotels. Main variables in the dataset were the user's unique ID, day of search, city from where the search was performed, desired checkin/checkout day, the number of clicks in the user's session, and whether or not they booked a hotel. From this we were to come up with an analysis, in two days, that could provide useful insight to the company at hand.

## Overview
Our question was: can we use weather to predict increases in usage of the website or demand in booking hotels? The idea being that inclement weather could a) increase desire to travel to a destination with different weather, and b) promote internet activity due to less outdoor activity. If (a) is found to be true, the website could price discriminate by ordering their hotel listings in such a way that puts slightly more pricey hotels towards the top. By "nudging" users into checking out hotels that are at higher prices, they could capitalize on this increase in demand. Then, if (b) is found to be true, the website could alter their advertisement bidding to be slightly more aggressive in areas that have poor weather forecasts for the day. By targeted marketing during advantageous times, the website could gain more traffic and stand to profit.

The research presented here is preliminary by nature - but based on the results, and the scalability of the methods used, an investment into further research (purchasing an API to gather historical and current weather data) to investigate this question would come at minimal cost (less than $2,000) and may reveal profitable patterns. 

## Methodology (summary)
We used weather because of how difficult it is to predict. Looking at within months, it is very unlikely to be correlated with confounding factors, and through this it provides what can be thought of as many small natural experiments. It's also observable and easily accessed. Although we were only able to examine a small amount of weather data due to having to download data for each city manually, with the purchase of an API key this process would be streamlined and weather data for every city could be easily collected, making future research very doable.

We examined data at two levels: at the individual observation level to look at the probability of booking to a specific location during differing weather conditions, and the city-day level to look at the overall relationship between weather and website activity. Downloading weather data from the NOAA for 11 cities that had some of the most user activity, the daily weather summaries were joined on using the date. From this we created the "WTI Index" that correspondeds to how poor the weather was, higher being poorer weather, and was constructed using  a weighted sum of several components. These components included how bad the weather compared to the previous 7 days' weather, how much precipitation there was, the temperature, and the type of weather, i.e. if it was hailing, snowing, thunderstorms, etc. 

## Results
The first exploratory analysis looked simply at at how bookings changed with temperature. The graph of this is showed below, and you can see that within all cities there are more bookings when the heating-cooling-difference increases, meaning that the temperature gets colder.

![Bookings & Temperature](https://cloud.githubusercontent.com/assets/25534898/25184988/0408761c-24ea-11e7-8475-cf49088040d3.png)

This shouldn't be taken at face value, as there could be many confounding variables that make the relationship between the temperature and number of bookings less than causal. To isolate the effects between temperature and bookings, we tested the relationship using a logistic regression framework. Using a step-wise logistic regression, we looked at if temperature is still a significant predictor of bookings after controlling for city fixed effects, season fixed effects, and user search characteristics. We find that it *is* significant at the 99% level, and that for every increase in one degree farenheit it increases the probability of booking by ~0.03%. 

![Bookings & Temp Regression](https://cloud.githubusercontent.com/assets/25534898/25184987/04086046-24ea-11e7-801e-5dcc3f7328de.png)

This relationship is further visualized in the figure below. Categorizing weather for days as poor (1) and good (0) using the WTI index we created, the distribution of number of clicks within each city is examined for the Fall of 2015. We see again that, the majority of the time, clicks increase during periods of poor weather, indicating that website usage increases on days with relatively bad weather.

![Clicks & Weather, City Level](https://cloud.githubusercontent.com/assets/25534898/25184990/044a0e24-24ea-11e7-98e8-cc827e1b9dd6.png)

## Conclusion
While the results gathered aren't robust enough to outright recommend strategic pricing in periods of inclement weather and to use weather forecasts to alter advertisement pricing algorithms, I believe that the results are strong enough to be a call to invest in additional research to run this analysis using the full set of user data and weather data. The main takeaway is that there there does appear to be a significant relationship between weather and user activity, and there are trends within cities in how they react to poor weather - we see increases in activity and bookings in most, and decreases in others. When running this analysis on the full scale, we may be able to segment the consumer market and categorize cities by how they react to weather. This would help even better identify areas and situations in which could be capitalized by user search "nudges" and strategic advertising.
