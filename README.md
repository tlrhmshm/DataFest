# ASA DataFest 2017

## Introduction
We were given a dataset (n = 11 million) of customer search data on a website (that can't be disclosed until after May) for booking hotels. Main variables in the dataset were a user's unique ID, day of search, city from where the search was performed, desired checkin/checkout day, the number of clicks in the user's session, and whether or not they booked a hotel. From this we were to come up with an analysis, in two days, that could provide useful insight to the company at hand.

## Summary
Our question was: can we use weather to predict increases in usage or demand of the website? The idea being that inclement weather could a) increase desire to travel to a destination with different weather, or b) promote internet activity due to less outdoor activity. If (a) is found to be true, the website could price discriminate by ordering their hotel listings in such a way that puts slightly more pricey hotels towards the top. By "nudging" users into checking out hotels that are at higher prices, they could capitalize on this increase in demand. If (b) is found to be true, then the website could alter their advertisement bidding to be slightly higher in areas that have poor weather forecasts for the day. By marketing during advantageous times, the website could gain more traffic.

The research presented here is preliminary by nature - but based on the results, and the scalability of the methods used, an investment into further research to investigate this question would come at minimal cost and may reveal profitable patterns. 

## Methodology


![Clicks & Weather](https://cloud.githubusercontent.com/assets/25534898/25184990/044a0e24-24ea-11e7-98e8-cc827e1b9dd6.png)
![Bookings & Temperature](https://cloud.githubusercontent.com/assets/25534898/25184988/0408761c-24ea-11e7-8475-cf49088040d3.png)
![Bookings & WTI Regression](https://cloud.githubusercontent.com/assets/25534898/25184989/043153f2-24ea-11e7-8c1f-f9a742f168a5.png)
![Bookings & Temp Regression](https://cloud.githubusercontent.com/assets/25534898/25184987/04086046-24ea-11e7-801e-5dcc3f7328de.png)
