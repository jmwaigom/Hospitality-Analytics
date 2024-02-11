# ORUS Luxury Hotels & Resorts 

![Orus8](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/82627eec-8134-4da8-81a4-be44c78e3bb7)

## Performance Analytics - Power BI Project 
### Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Data Source](#data-source)
- [Data Preparation and Processing](#data-preparation-and-processing)
- [Dashboard](#dashboard)
- [Data Analysis and Insights](#data-analysis-and-insights)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
### Project Overview
ORUS is a company that owns and operates seven hotel brands in four states in the United States, namely: Boston, Chicago, Los Angeles and New York City. The General Manager (GM)
of ORUS wants a high level overview of how the brands have been performing across the locations. He wants to know the performance of the brands in terms of revenue, booking volume,
occupancy and customer rating in the months of May, June and July of 2022. He has outsourced the job to your private data consultancy company and you have been assigned with building 
a dashboard and creating a summary report to convey key insights on the overall performance of the company

### Objectives
Display the following on the dashboard
1. KPIs: Revenue generated and realized, total bookings, average occupancy, average customer rating and rate of successful bookings
2. Revenue by hotel and their pro-rata share
3. Average occupancy and customer rating by hotel
4. Proportion of total bookings and revenue that's being generated through each booking platform
5. Pro-rata share of revenue by room class in each hotel

### Data Source
The data used for this analysis was from the following csv files: "fact_aggregated_bookings_us.csv", "fact_bookings_us.csv", "dim_rooms_us.csv", "dim_hotels_us.csv", and "dim_date_us.csv".  

### Data Preparation and Processing
The files were loaded into Power Query for some cleaning and transformation. A few transformations that were carried out included: merging queries, changing data types, removing duplicates, adding custom columns, filtering rows and extracting months from dates.

The data was then loaded into the model view of power BI whereby relationships were formed across tables.

![modelview](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/f4da727a-1b75-43cf-a8cd-6053106fb7bd)

Once relationships were formed, visualizations were created in the report view of Power BI to address the objectives of the project. In the process, several DAX formulas were created to enhance analysis. For example: Booking Success Rate was calculated by dividing checked out bookings (which were considered successful bookings) by total bookings. This was acccomplished through the DAX formula below.

```
Booking Success Rate = 
VAR SuccessfulBookings = CALCULATE(COUNT(fact_bookings[Booking_ID]),fact_bookings[Booking Status] = "Checked Out")
VAR TotalBookings = COUNT(fact_bookings[Booking_ID])
RETURN
    DIVIDE(SuccessfulBookings,TotalBookings,0)

```
Several Power BI report pages were created to show visualizations that addressed project objectives. Finally, several visualizations were taken from each report page and used to create a dashboard


### Dashboard
![OrusDasboardEdit2](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/d8f9acfd-cdff-43db-bc79-df72e4551a86)

### Data Analysis and Insights
Overall, ORUS Hotels generated 23.07M and realized 19.65M of revenue from it (about 85%). For the total realized revenue, NYC was the leading city totaling around 7.69M (39.1%) followed by Chicago 4.83M (24.6%), Boston 3.73M (19.0%) and LA 3.39M (17.3%). This seems to correlate to some extent with the number of hotels in each city. All 7 ORUS brands are present in NYC, all but ORUS seasons in Chicago and Boston, and 5 brands in LA (all but ORUS Exotica and ORUS Seasons)

Overall, ORUS Exotica was leading by 18.54%, followed by Orus Palace, 18.08% then ORUS City, 17.03%. The overall performance of ORUS Exotica appears to be heavily driven by its strong performance in NYC where it generated over 2.4M in realized revenue. This is the highest compared to any other hotel in either NYC or any leading hotel in the other 3 cities (ORUS Bay in Boston: 788K, ORUS City in Chicago: 959K, ORUS Palace in LA 1.04M). Strong performance of ORUS Exotica in NYC is significant, because despite being located in only 3 cities (all except LA), it still outperformed ORUS Palace and ORUS City (2nd and 3rd overall performers) which are located in all 4 cities. The strong performance of ORUS Exotica could be attributed to its significantly higher booking volume compared to other hotels in NYC. It totaled a whopping 13K bookings (30.7%) which is more than double of any other hotel in NYC and any top booked hotels in any of the 3 other cities (see table and column chart below)

![Bookings](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/3db74e64-3f95-4390-bf14-7f7500a8210d)

![Edit3](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/7648529d-f0c7-4aff-9ca6-70bb7787d9ed)

ORUS seasons was the least overall revenue contributor (3.93%) because it's located in NYC only compared to the rest of the hotels which are located in at least 3 cities each.

The overall booking success rate was 70.21% meaning that roughly 7 out of 10 bookings are likely for the guests to show up, stay the lenghth of their booking and check-out. This likelihood seems to be relatively even/similar across all hotels and cities. 

The overall average occupancy for all hotels across all cities was slightly over half hotel capacity (58.31%). This is below the national average of 65% for May-July 2022  ORUS Blu had the highest overall occupancy at 63.14% while ORUS seasons had the lowest at 44.51%. Also, there was higher occupancy in LA hotels than the rest of the cities. See table below for breakdown of occupancy by hotel and city

![Screenshot 2024-02-11 004841](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/4311da80-be44-4eee-96d5-84cae817bab4)

Generally, across all hotels and cities, Elite room class led in revenue (~33%), followed by premium (~27%), then Presidential (~22%). Standard generated the least revenue(~18%). Despite Standard being the cheapest option (averaging ~$110 per 2 guests), it wasn't the top booked room class. Elite led in booking volume despite being pricier than Standard (averaging ~$155 per 2 guests). Presidential was the least room class because it was the priciest (averaging ~$312 per 2 guests). However, it generated more revenue than Standard by 4%.

All across cities and hotels, around 41% of the bookings were through an unidentified platform, followed by marketyourtrip (~20%). The least bookings were done through direct offline (~5%).

During the time period (May-Jun), revenues began declining around week 28 (early July) and hit the lowest on week 32 (last week of July). It appears that this may have been caused by irreversible decline in bookings beginning week 28, with the lowest bookings recorded on week 32. From this dataset, it's hard to pinpoint the reason for decline in bookings hence declining in revenue beginning week 28. The only factor that is worth investigating would be customer rating over time. However, as it can be seen below, it doesn't seem like customer ratings were trending down over time hence leading to lower traffic. For that reason, the cause of decline in bookings cannot be clearly established. One plausible assumption could be major news in the press about management, scandal or safety concerns with one or more ORUS hotels in one or several locations.   

![Edit4](https://github.com/jmwaigom/Hospitality-Analytics/assets/155841258/d71ab627-b034-4391-81ad-ccd3acdbb5ed)

### Recommendations
Further study/investigation should be conducted to find out what exactly happened around week 28 or slightly earlier that may have led to decline in booking volume. 

The unidentified booking platform should be identified so that it can be promoted through marketing campaigns. Furthermore, since revenue is heavily driven by booking volume, more effort should be directed towards marketing campaign. ORUS should consider investing in online ads and offering deals to attract more customers.

Generally, ORUS should consider improving customer experience for better rating. That could be upgrading amenities, room service, room quality, safety protocols and general customer care. This will increase customer satisfaction which will enhance the reputation of ORUS, hence attracting more customers.

Further study should be conducted to investigate the primary cause of the gap between generated and realized revenues and figure out ways of reducing that gap so as to maximize net revenue

A survey should be conducted to learn why some customers cancel or don't show up for their reservations. The reasons may be purely personal, but it's worth finding in case the reasons have to do with ORUS to any extent.


### Limitations
Average price per room class was not provided, so an estimate was made by calculating average revenue generated per 2 guests for each room class. This could be a good rough estimate for analysis purposes, but may not be accurate.

### References
- [Statista](https://www.statista.com/statistics/206546/us-hotels-occupancy-rate-by-month)


