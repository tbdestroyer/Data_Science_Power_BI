# Data_Science_Power_BI
Project Description

The project aims to use Microsoft Power BI application for data analytics for vehicle crashes in Maryland. It has data analytics reports and visualizations with statistics. It also uses categorical correlation and machine learning and regression model on some of the dataset variables with Python scripts integrated into Power BI. Reports are published into Power BI service and created as dashboards.
Datasets:
I used two datasets from data.gov.
First dataset contains the Maryland statewide vehicle crashes from 2015 to 2022 which has over 800 thousand entries. This is the main dataset used for accident data analysis.
Publisher opendata.maryland.gov. (2022, November 18). Maryland Statewide Vehicle Crashes. Catalog. Retrieved November 19, 2022, from https://catalog.data.gov/dataset/maryland-statewide-vehicle-crashes
Second dataset has the vehicle registrations for Maryland counties  from 2010 to 2022. Registrations in this dataset are used with the vehicle crash data for normalizing the data and generating other statistics.
I used a subset of the data from 2018 to 2022 to make it more manageable and common timeframe for both datasets. Transformed vehicle crash data has 506 thousand entries from 2018 to 2022.
Publisher opendata.maryland.gov. (2022, October 21). MVA vehicle registration by County from 2010 to 2022. Catalog. Retrieved November 19, 2022, from https://catalog.data.gov/dataset/mva-vehicle-registration-by-county-fy-2010-to-fy-2020
Cleaning and transforming data:

I used mainly Python scripts in Jupiter Notebook to clean and transform the datasets. Some of the data are saved from a DataFrame to a CSV file and then imported as CVS files into Power BI.
Some of the data are imported into Power BI running a Python script directly in Power BI and imported from a DataFrame.
For the vehicle crash data, I  removed 19 columns from the crash data (out of 55) as they were redundant or not used and mostly not populated. I also dropped years except from 2018 to 2022.
I transformed the second data set (registrations) to a more useful structure with the years, counties, and registrations in three columns and added a fourth column for the number of accidents in each year extracted from the crash data table. I used DAX formula in Power BI to add another column to the registrations table for the ratio of accidents to registrations by county. I modified some of the county names (extra spaces etc.) to match the columns/variables between the two datasets.



Data Analysis

Following reports and visualizations are created using different graph types as appropriate. Some of the findings are summarized below.
•	Accidents by County
•	Accidents by year
•	accidents by county and year
•	accidents by county in different light conditions
•	accidents by time of the day
•	accidents by time in 15 min bins
•	accidents by weather type
•	accidents by surface conditions
•	accidents by report type
•	registrations by county
•	accident to registration ratio by county and year
•	Q&A visual with newly defined questions

accidents by year shows that accidents were decreased close 10 thousand in 2020compared to the previous two years. This is most likely due to Covid-19 pandemic and people staying home and working remotely thus reduced driving.
accidents by county by year shows that most accidents were in Baltimore County and a noticeable reduction was seen in 2020.
accidents by county in different light conditions shows that most accidents occur during daylight followed by “Dark lights on” and “Dark no lights”. Seems like people drive at dark forgetting to turn their lights on.
accidents by time shows that highest number of accidents are between 3PM and 6 PM during the day.
accidents by weather type shows that highest number of accidents are in clear days followed by rainy day. We don’t have the number of rainy days, but it still is a high number of accidents in rainy days. This also correlates to the surface condition graph where most accidents are in road surface is dry followed by the wet road surfaces.

Accidents by type shows that number of fatal crashes were highest even the number of accidents were the least in 2020 (middle of Covid-19 pandemic). We don’t have the speed of a crash, but it could be people were speeding in less traffic. This is something that can be analyzed further.

Registrations by county shows that Montgomery County had the most registered cars.

Accidents to vehicle crash graph shows that the proportion is highest for Baltimore City. It means that Baltimore City had the highest number of accidents per registered vehicle. Montgomery County was 12th in this ratio even if it had the highest registered number of vehicles.
Q&A (Natural Language Processing)
Power BI provides a Q&A capability where automatic queries and answers with visualizations are generated. Q&A can also be trained and added your own questions and answers. I demonstrated this under the “Q&A” tab where several Q&A tabs are created related to the dataset.
“Most accidents to registrations by county” tab is a good example that shows the car registrations and accident to registrations ratio where it shows that Montgomery County has less accidents compared to other counties even it has the highest number of cars registered.

Correlation Analysis

Correlation analysis was done for the two categorical variables for the following list to each other using the Cramer’s V correlation.
•	Damage/harm type
•	Type of accident
•	Light condition
•	Road divided or not
•	Surface condition
•	Report type
•	Weather condition
Python stats package is used to generate the correlation and a heat map. There is some but not strong correlation between the weather and surface condition (0.26) and very low correlation otherwise between the other categories. (chrisbss, 2019)
“crash_corr_data” table is generated using Python script in the Jupiter Notebook first and then imported into the Power BI using the Python Script method.
A python visual is added to Power BI and then a python script generates the analysis and the visualization. It is best to test your code in a separate Python script like Jupiter notebook before putting into Power BI. Power BI File->Options and settings->Python Scripting needs to be set for the Python directories and enabled.

Regression Analysis

Regression analysis was performed for Prince George’s County vehicle crashes from 2015 to 2020 data and then a liner regression is done using the ordinary least squares model from the statsmodels package. This code follows almost the same machine learning example from the class exercise (TomReidNZ , 2022) but applies the OLS for regression between the number of crashes and year for PG County.
“pg_county_accidents” table is imported into Power BI and then Python script implements the regression and plots the regression visualization using a Python visual in Power BI. R2 is 0.987 showing a good linear correlation.
Prediction for the year can be changed using the Power BI filter for the predicted year. Python statsmodels package needs to be installed for this analysis (pip install statsmodels).

Publishing to Power BI Service

Once the reports are completed, they can be published to Power BI Service (Web based application interface) and can be added to dashboards. Related reports can be added to the same dashboard as one-page visualizations. Reports can also be pinned as live to a dashboard where changes to reports are automatically reflected in the dashboard.

References

chrisbss1. (2019, September 25). Cramer's V correlation matrix. Kaggle. Retrieved December 06, 2022, from https://www.kaggle.com/code/chrisbss1/cramer-s-v-correlation-matrix/notebook
TomReidNZ. (2022). Introduction - training. Training | Microsoft Learn. Retrieved December 3, 2022, from https://learn.microsoft.com/en-us/training/modules/introduction-to-machine-learning/1-introduction
AllenDowney. (2014). Allendowney/thinkstats2: Text and supporting code for think stats, 2nd edition. GitHub. Retrieved December 13, 2022, from https://github.com/AllenDowney/ThinkStats2
How to calculate Cramer's V in python? GeeksforGeeks. (2022, February 28). Retrieved December 05, 2022, from https://www.geeksforgeeks.org/how-to-calculate-cramers-v-in-python/
