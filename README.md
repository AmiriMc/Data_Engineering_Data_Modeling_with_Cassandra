# Project 1B: Data Modeling with Apache Cassandra

## Introduction

This project was provided as part of Udacity's Data Engineering Nanodegree program.

A startup called *Sparkify* wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate results, since the data reside in a directory of __CSV files__ on user activity on the app. The CSV files are partitioned by date. 

They'd like a __data engineer__ to create an __Apache Cassandra database__ using __Python__ which can create queries on song play data to answer their questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

## Project Description

The goal of this project was to model the data by creating tables in Apache Cassandra to run queries on. I was provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables. The provided project template takes care of all the imports and provides a structure for an ETL pipeline that I needed to process this data.

### To run the .ipynb file, follow instructions below:

1. Load the Docker image using the instructions below.
2. Make sure the unzipped `event_data` folder is in the same directory as the "Project_1B_Data_Modeling_with_Cassandra.ipynb" file.
3. Run all cells in the "Project_1B_Data_Modeling_with_Cassandra.ipynb" file.
4. Verify that all three queries return the expected data based on the three query requirement questions in the notebook.

## ETL Pipeline
I was provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables. The provided project template takes care of all the imports and provides a structure for an ETL pipeline that I needed to process this data.

## Customer Requests on Data and Final Queries
I had to create the data tables in Apache Cassandra based on the queries and the queries are based on the customer's request for data. The completed __data model__ can be examined in the _Project_1B_Data_Modeling_with_Cassandra.ipynb_ Jupyter Notebook. 
1.   Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4:  `SELECT artist, song, length from songInfo_by_sessionId_and_itemInSession WHERE sessionId=338 AND itemInSession=4`
2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182: `SELECT artist, song, firstName, lastName from artist_and_song_by_user_and_session WHERE userId=10 AND sessionId=182 GROUP BY itemInSession, firstName, lastName`
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own': `SELECT song, firstName, lastName from userInfo_by_song WHERE song='All Hands Against His Own' GROUP BY firstName, lastName`

## Docker Image
A Docker image was used so that I could develop this project on my local machine, rather than on Udacity's internal system. Thank you to Ken Hanscombe for providing easy to follow instructions on how to pull, run, and connect to the Apache Cassandra image.

With Docker installed, pull the latest Apache Cassandra image and run a container as follows:
```
docker pull cassandra
docker run --name cassandra-container -p 9042:9042 -d cassandra:latest
```
This will allow you to develop the data model (i.e. work through the Jupyter notebook), without altering the provided connection code which connects to the localhost with default port 9042:
```
from cassandra.cluster import Cassandra
cluster = Cluster(['127.0.0.1'])
session = cluster.connect()
```
To stop and remove the container after the exercise:
```
docker stop cssandra-container
docker rm cassandra-container
```
