# Alooma SE Challenge Response

## 1.	Introduction
This document addresses the Alooma SE challenge.  It provides the steps performed and the results yielded as an outcome of the exercise.

Link to Alooma SE Challenge doc:  https://github.com/Dkusner/Challenge1/blob/master/request/Alooma%20-%20Solutions%20Engineer%20Assessment.md

## 2.	Software Versions and Tools
This assignment was built using the following OS and SW tools:
* Python 3.6.3 64bits
* MySQL 6.3.10 64bits
*	IOS – High Sierra 10.13.4
*	Data from Hubspot  -“Engagements Overview”

Link to Engagements Overview:  https://developers.hubspot.com/docs/methods/engagements/engagements-overview

## 3.	Extracting Data:

### 3.1	Pulling Data from Hubspot. 
The python script 'getEngagements.py' extracts the engagement data using Hubspot's Engagement API and converts the response to csv output.  The csv output is required for import to MySQL.
The libraries imported in python are:
* urllib
* urllib.request
* json
* csv
* time
* os	

Link to getEngagements.py:  https://github.com/Dkusner/Challenge1/blob/master/source/getEngagements.py

### 3.2	Python Algorithm to Retrieve Data

* 'getEngagements.py' retrieves the engagement data from the Hubspot Engagements API.
* Response from API call is translated into Json format so that analysis can be conducted.
* The python script extracts the relevant fields and outputs a CSV file for use to import into MySQL.
* To run the python code, run command: runfile('~getEngagements.py') from python console.
* Output: Once the command is executed, a csv file "getEngagements_output.csv"  is created in the home directory.

Link to getEngagements_output.csv:  https://github.com/Dkusner/Challenge1/blob/master/output/getEngagements_output.csv

## 4.	Importing and Reading the Data in MySQL

*	The Data Import Wizard in MySQL Workbench was used to import the data from 'getEngatements_output.csv'.  All defaults were used during the import.
* The import wizard produced the following schema for the 'engagements' table:
  * id (int)
  * portalId (int)
  * createdAt (text)
  * type (text)
* Indexes were created on the following fields in order to ensure optimal performance during the specified SQL query:
  * createdAt
  * type
* The SQL file 'typeDailyCount.sql' queries the engagements per day and groups them by type.
* THe output from the SQL query shows the count of each type per day.

Link to SQL query typeDailyCount.sql:  https://github.com/Dkusner/Challenge1/blob/master/source/typeDailyCount.sql

Link to output from SQL query:  https://github.com/Dkusner/Challenge1/blob/master/output/type_daily_count.csv

## 5.	(Bonus) 14-Day Moving Average on Daily Counts Per Engagement Type

* The SQL file 'Eng14DayAvg.sql' queries the engagements per day and groups them by type - the performs a join from the source table using the avg() sql function to generate a 14 day average based on the date difference.
* The output from the SQL query shows the average for that engagement type for the prior 14 days.

Link to SQL query Eng14DayAvg.sql:  https://github.com/Dkusner/Challenge1/blob/master/source/Eng14DayAvg.sql

Link to csv output from SQL query:  https://github.com/Dkusner/Challenge1/blob/master/output/eng_avg14day.csv
