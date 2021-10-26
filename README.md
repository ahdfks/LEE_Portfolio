# Project 2: Cyclistic Bike-Share

## Project Overview: https://www.kaggle.com/mollayo/bikeshare-riding-pattern
An optional case study at the end of Google Data Analytics Professional Program.\
This is an opportunity to analyze historical bicycle trip data in order to identify trends, and it is important to understand how casual riders behave differently from annual membership riders.

This analysis will help executives to make decisions about digital marketing programs and strategies to convert casual riders to members. As a junior data analyst at Cyclistic(fictional entity), I completed this project by going through the **6 phases** of the data analysis process: **ASK, PREPARE, PROCESS, ANALYZE, SHARE** and **ACT**

## Phase 1. ASK

*Clearly identify business task:*
* Current situation: annual members are more profitable than casual riders.
* Business goal: convert casual riders to annual members to maximize the number of memberships.
* Gap: we don’t know what makes people to buy memberships.

*Identify stakeholders:*
* Primary stakeholder: Executive team 
* Secondary stakeholder: Director of marketing, Finance analyst, Marketing analytics team

## Phase 2. PREPARE

*Collect or download data:*
* The given open source data [link](http://divvy-tripdata.s3.amazonaws.com/index.html) by Motivate International Inc, under this [license](https://www.divvybikes.com/data-license-agreement). Due to data privacy issues, personal information has been removed or encrypted.
* Assume to use recent 12 months data (05/2020~04/2021).

*Store data:*
* We stored this large volume of data in Google Cloud Storage, then it will be easy to connect with Big Query for cleaning.

*Identify data format:*
* Long format; combines discrete, continuous, and nominal data.
* Each monthly data is organized with effective naming convention (YYYYMM-tripdata).

## Phase 3. PROCESS

*Choose cleaning tool:*
* Depending on the volume of data, we choose BigQuery as a cleaning tool.

*Ensure data’s integrity:*
* Check length of ID column if there're any inconsistent fields.
* Check distinct values in bike type and customer type columns to see if there’re any spelling errors.
* From datetime column, we extract hour, day of week, and calculate time difference.
* Check the mismatching between distinct station name and its unique ID, also check for the mismatching null count, and double check after fixing up.

*Document the cleaning log:*
* Write down cleaning checklist and relevant cleaning method that I prefer to use.

## Phase 4. ANALYZE

*Code and Resources used:*
* R version: 1.4.1717
* Packages: here, skimr, janitor, tidyverse, lubridate, dplyr, yarrr, zoo, hms, circlize, pivottabler

*Debug the query:* to make sure it is valid, complete, and clean before we begin any analysis
* Vertically combined the loaded data.
* Renamed columns and converted datatypes.
* Swapped the start and end time to fix up 10,506 negative riding durations.
* Separately extracted date, time, month, year, and converted them to appropriate datatypes.

*Exploratory Data Analysis:*
* Accumulated each distinct station's ride count & duration during one year.
* Figured out top 20 itineraries among different stations and created a chord diagram:
![chord](https://user-images.githubusercontent.com/79106560/138889461-d8159215-b067-4801-8134-44053e65d137.png)
* Created a pivot table to compare median ride duration between casual riders and members.
   * Finding: casual customers generally have higher median ride duration than members.
* Created a scatter plot to see the relationship between ride count and duration:
![scatter](https://user-images.githubusercontent.com/79106560/138889861-6522ad27-65b5-4f24-86bc-8c453fc9a31a.png)
   * Finding: docked bike is the most frequently used type by both casual riders and members.

* Created the separate bar charts to see the peak hours in each of 12 months:
![3 monthly peak hour](https://user-images.githubusercontent.com/79106560/138890027-dd5a8cab-e77d-4d69-af9b-41f1a942f082.png)
   * Finding: **peak hour = commuting hour (17:00~18:00)**
   * From **Jul to Oct**, we have a larger number of rides at that peak hour than other months.

* Created separate histograms to see the peak hours in each day of week:
![4 weekly peak hour](https://user-images.githubusercontent.com/79106560/138890264-1555eb81-2cff-4ba1-a5e6-5922c60bf1e0.png)
   * Finding: 
      * peak hour during weekend = whole daytime(10:00 ~ 18:00)** for both casual and members\
      * peak hour during weekdays = off work time(16:00 ~ 19:00)** for members\
      * **casual customers are less likely to ride a bike during weekdays than members.**
   * So in order to convert casual riders to members, we need to figure out **how many "commuter" and "non-commuter" riders who don't have membership yet**. To capture those riders, we also need to know the top stations with high riding frequency among casual riders.

* Created rider types distribution at top 20 stations:
![5 rider type](https://user-images.githubusercontent.com/79106560/138890925-abebd8e2-1641-4d52-b3e0-f3b9896f2691.png)
   * Finding: we can prioritize "Streeter Dr & Grand Ave", "Lake Shore Dr & Monroe St", "Millennium Park", "Michigan Ave & Oak St" these 4 stations with more casual customers than members.
* Also, identified another top 20 stations where we have more casual customers than members, and created a column chart to see casual customers' riding frequency:
![6 casual riders](https://user-images.githubusercontent.com/79106560/138891131-98a37080-644c-490c-bbdd-2af3e01c6208.png)
* Lastly, exported dataframe to csv file to create Dashboard on Tableau

## Phase 5. SHARE

*Create effective data visualization to present the findings above:*
* [Click Here to View the Dashboard on Tableau Public](https://public.tableau.com/app/profile/mong1155/viz/GoogleCapstoneCase-bikeshare/Dashboard)
![dashboard](https://user-images.githubusercontent.com/79106560/138895713-c650b960-567d-49f4-a7af-893e4296910d.png)

## Phase 6. ACT

*Draw conclusion:*
* Because off work time and riding count are correlated so well from my findings, we conclude that it is the commuting usage that leads to people to buy annual membership.

*Provide marketing recommendations:*
* In order to know how many potential casual riders are willing to buy annual memberships, we recommend to create 3 tabs(commuting/leisure/sport) in bikeshare app for them to choose while they're making payments.
* Then we need to focus on top 20 stations for casual riders, but beforehand we should make sure there’re enough available bikes, especially docked bikes, because they are the most frequently used type by both members and casual riders.
* Next, after collecting the relevant data from updated app, we can send annual membership discount code to casual riders who chose commuting usage.
* Lastly, if we successfully converted them to members, then we move to next step by expanding more stations.

*Additional recommendations:*
* Compare to off work time, there’s much lower ride count during the morning commuting time, so we need to collect data about customers’ preferred type of transportation to go to work(metro/bikeshare/car/taxi/tram) and the reasons.
* Next, if the survey shows there are significant bikeshare users, then we need to check if we have enough bikes and bikeshare stations near the residential areas.
* Additionally, since bike is a more flexible transportation than metro, we can identify landmarks where there’re fewer metro stations or parking lots but with significant foot traffic.
* So if we can collect landmark foot traffic data, demographical data, and customers surveys, we can expand findings with more new insights.


# Project 1: Healthcare Market Research 

## Project Overview: https://github.com/ahdfks/project_HC_Asia
* Created a dashboard to understand the healthcare market in mainland China, Hongkong, Taiwan and South Korea
* Data collection: scraped over 1500 companies from LinkedIn using linked helper scraper
* Data cleaning: cleaned raw data and derived a file to prioritize companies covering target therapeutic areas
* EDA: parsed string data of each company's specialities to quantify the value they put on each therapeutic area
* Data visualisation: built a dashboard to understand companies/therapeutic areas distribution by each specific level

## Code and Resources used
**Python version:** 3.8.5\
**Packages:** pandas, numpy, seaborn, matplotlib.pyplot\
**Tableau:** 2020.4

## LinkedIn company profile scraping
Scraped 1500+ companies in pharmaceuticals, biotechnology, and medical device industry in the Greater China Region.\
With each company profile, we got the following:
*	Company ID
*	Company name
*	Industry
*	Type of ownership
*	Founded year
*	Company description: with FDA, CE, EMA and other international certifications
*	HQ country: China, Taiwan, South Korea
*	HQ city level
*	HQ province level
*	Specialities: immuno-oncology, CNS, probiotics, cardiovascular, diabetes, orthopedics etc.
*	Profile url
*	Website
*	Phone
*	Staff counts
*	Follower counts

## Data Cleaning 
After scraping the data, it is necessary to clean it up.\
I made the following changes and created the following variables:
*	Simplified name by removing city and business structure abbr out of company name text
* Transformed founded year into age of company
* Created 18 therapeutic categories and matches list\
o  Oncology\
o  Rare diseases\
o  Dermatology\
o  Cardiology\
o  Gastroenterology\
o  Immunology\
o  Neurology\
o  Orthopedics\
o  Pulmonology\
o  Infectious diseases\
o  Hematology\
o  Rheumatology\
o  Endocrinology\
o  Ophthalmology\
o  Diabetes\
o  ENT\
o  Pain management\
o  Urology
* Made a function to separate multi strings in specialities column and then classify therapeutic areas list(above) from each separated speciality
* Added a therapeutic areas file by keeping companies who covered target therapeutic areas above
* Removed duplicated therapeutic areas in each company
* Added specialities length column to get detailed information
* Made a column for if intl certifications were listed in the company description text\
o  CE\
o  FDA\
o  EMA
* Added description length column for in-depth information
* Replaced NaN with null

## Exploratory Data Analysis 
Created the distributions of cleaned data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables:

![thera](https://user-images.githubusercontent.com/79106560/110397060-6f2fde80-8071-11eb-9c9d-a4d8fa97965d.png)
![type](https://user-images.githubusercontent.com/79106560/110399401-1a429700-8076-11eb-98e0-a7f67d5dfa11.png)

## Data Visualisation 
Because Juypyter Notebook has a limitation on data visualisation, I used Tableau to optimize research results by comparing data by country/city/other specific combined levels. The dashboard is made up of following several sections:

<img width="1440" alt="dashboard" src="https://user-images.githubusercontent.com/79106560/110532992-d014f080-811d-11eb-8c6a-3850a811467b.png">

