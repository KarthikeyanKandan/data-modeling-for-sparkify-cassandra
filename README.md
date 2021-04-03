# Data Modeling with Apache Cassandra for music streaming app 'Sparkify'

## Objective: To create an Apache Cassandra database with tables designed to answer queries on song play analysis

### Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

As a data engineer, I've created an Apache Cassandra database with tables designed which can create queries on song play data to answer the questions. My role is to create a database and ETL pipeline for this analysis, test the database I created and ETL pipeline by running queries given to me by the analytics team from Sparkify and compare my results with their expected results.

### Files

1. [`Project_1B_ Project_Template.ipynb`](Project_1B_Project_Template.ipynb)

### The Keyspace for the Song Play Analysis

Using the events datasets, I've created a cassandra keyspace called 'Sparkify' for queries on song play analysis. This includes the following tables for the following queries.

#### Query 1 : Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4

1. `music_app_history` - Table with records from event_datafile_new.csv with PRIMARY KEY(sessionId, itemInSession) for the given query
     - session_id, itemInSession, artist, song_title, length

#### Query 2: Give me the name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182

1. `user_songs` - users in the app with associated song data
    - user_id, session_id, itemInSession, first_name, last_name, artist, song_title

#### Query 3: Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

1. `user_data` - users in the app with associated song data
    - user_id, first_name, last_name, song_title


## Steps in Project_1B_Project_Template.ipynb

### Modeling our NoSQL database or Apache Cassandra database

1. Design tables to answer the queries given
2. Written Apache Cassandra CREATE KEYSPACE and SET KEYSPACE statements
3. Developed CREATE statement for each of the tables to address each question
4. Loaded the data with INSERT statement for each of the tables
5. Included IF NOT EXISTS clauses in our CREATE statements to create tables only if the tables do not already exist.
6. Included DROP TABLE statement for each table, this way we can run drop and create tables whenever we want to reset our database and test our ETL pipeline
7. Tested by running the proper select statements with the correct WHERE clause

### Build ETL Pipeline
1. Implemented the logic in section Part I of the notebook template to iterate through each event file in event_data to process and create a new CSV file in Python
2. Made necessary edits to Part II of the notebook template to include Apache Cassandra CREATE and INSERT statements to load processed records into relevant tables in our data model
3. Tested by running SELECT statements after running the queries on our database
