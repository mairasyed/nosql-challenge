# nosql-challenge
 # UK-Food-Hygiene-Ratings-Analysis-using-MongoDB

 The goal is to help the editors of a food magazine, Eat Safe, Love, to evaluate the data and assist their journalists and food critics in deciding where to focus future articles. The project aims to provide insights into the ratings data to identify establishments that meet the magazine's criteria for featuring in their articles.


# UK Food Rating Analysis for Eat Safe, Love Magazine

Hey, let's explore the "uk_food" as NoSQL database with  PyMongo and Pretty Print and  analyze the data using Pandas Python library.

![Alt text](Images/1_monogdb_pandas.jpg)


### 1 Introduction 

This web scraping and analysis consists of three parts.

Part 1: Setup jupyter notebook and database.

Part 2: Update the 'uk_food' Database.

Part 3: Exploratory Analysis


### 2 Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.6 or higher
- PyMongo
- Pretty Print
- Pandas (for data analysis)


![Alt text](Images/2_libraries.png)

### 3 Data Sources


We get the data from establishments.json file using mongo import from terminal.


![Alt text](Images/3_import_establlishments_json_file.png)


![Alt text](Images/4_notebook_import.png)


### 4 Part 1:  Setup Notebook and Database


Create an instance of the Mongo Client to setup the database and comfirm the databse and it's collections created successfully.


![Alt text](Images/5_mongoclient.png)


Reveiw one document in the establishments collection to confirm data loaded properly.


![Alt text](Images/6_document.png)


Assign the establishments collection to a variable to prepare the collection for use.


![Alt text](Images/7_assign_collection.png)


### 5 Part 2:  Update the Database

An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked us to include it in our analysis. Add the following restaurant "Penang Flavours" to the database.


![Alt text](Images/8_insert_penang_flavours.png)


The magazine is not interested in any establishments in Dover, so checked how many documents contain the Dover Local Authority. Then, removed those establishments within the Dover Local Authority from the database, and checked the number of documents to ensure they were deleted.


![Alt text](Images/9_dover.png)


Some of the number values are stored as strings, when they should be stored as numbers.


![Alt text](Images/10_convert_data_types.png)


Confirms the coordinates and rating value are now numbers.


![Alt text](Images/11_confirm_data_types.png)


Display the remainig one document with field in the form of appropriate data types.


![Alt text](Images/12_confirm_data_types.png)



### 6 Part 3: Exploratory Analysis 

Performs exploratory analysis on the data using various queries, aggregations, and data manipulation techniques to answer specific questions related to the hygiene ratings of establishments.


![Alt text](Images/13_EDA.png)



Eat Safe, Love has specific questions they want the insights, which will help them find the locations they wish to visit and avoid.


![Alt text](Images/14_locations.png)


Some notes to be aware of while you are exploring the dataset:

- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.

- Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.

- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

#### 6.1 Research Questions & Insights

Which establishments have a hygiene score equal to 20?


![Alt text](Images/15_hygiene_20.png)


Convert the result ( establishments have a hygiene score equal to 20 ) to a Pandas DataFrame and display the first 10 rows.


![Alt text](Images/16_hygeine_results_df.png)



Which establishments in London have a RatingValue greater than or equal to 4?



![Alt text](Images/17_Local_Authority_London.png)


Convert the result ( establishments in London have a RatingValue greater than or equal to 4 ) to a Pandas DataFrame and display the first 10 rows.


![Alt text](Images/18_rating_value_results_df.png)



What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

We will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.


![Alt text](Images/19_top_five_establishments.png)


Convert the result ( top 5 establishments with a RatingValue of 5 ) to a Pandas DataFrame and display the first 5 rows. These establishments are nearest to the new restaurant added, "Penang Flavours"


![Alt text](Images/20_degree_search_df.png)


How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

Use the aggregation method to get the insights.


![Alt text](Images/mongo_aggregation.jpg)


These are the establishments in each Local Authority area have a hygiene score of 0.


![Alt text](Images/21_hygiene_score_zero.png)



Convert the result ( establishments in each Local Authority area have a hygiene score of 0) to a Pandas DataFrame and display the top ten rows.


![Alt text](Images/22_hygiene_score_zero_df.png)



### 7 Observation Analysis

-  The total number of documents with a hygiene score of 20 is  41. The first restaurant name is 'The Chase Rest Home' and it's busienss type is 'caring premises'. 

- The total number of establishments with London as the Local Authority and 'RatingValue' >= 4 is  33. The first name comes is 'Charlie's' i.e. and it's busienss type is 'other catering premises'.


- Here is the top 5 establishments with a RatingValue rating value of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours".

1  'BusinessName': 'Volunteer',     'BusinessType': 'Pub/bar/nightclub',

2  'BusinessName': 'Atlantic Fish Bar',    'BusinessType': 'Takeaway/sandwich shop',

3  'BusinessName': 'Iceland',  'BusinessType': 'Retailers - supermarkets/hypermarkets',

4  'BusinessName': 'TIWA N TIWA African Restaurant Ltd',   'BusinessType': 'Restaurant/Cafe/Canteen',

5  'BusinessName': 'Howe and Co Fish and Chips - Van 17',   'BusinessType': 'Mobile caterer',

- Number of establishments with a hygiene score of 0:  55

- We extracted the top ten best Establishments for our News letter are here:


![Alt text](Images/23_Top_ten_best_zero_hygiene.png)





