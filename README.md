# Project: Data Modeling with Apache Cassandra

## Introduction

This project was provided as part of Udacity's Data Engineering Nanodegree program.

A startup called *Sparkify* wants to analyze the data they've been colelcting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate results, since the data reside in a directory of __CSV files__ on user activity on the app. 

They'd like a __data engineer__ to create an __Apache Cassandra database__ which can create queries on song play data to answer their questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

## Project Description

The goal of this project was to model the data by creating tables in Apache Cassandra to run queries. I was provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables. The provided project template takes care of all the imports and provides a structure for an ETL pipeline that I needed to process this data.

### To run the Python scripts, follow instructions below:

1. Make sure the unzipped Data folder is in the same directory as the scripts.
2. Run all cells in the "Project_1B_Data_Modeling_with_Cassandra.ipynb" file.
3. Verify that all three queries return the expected data based on the three query requirement questions in the notebook.

## ETL Pipeline
I was provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables. The provided project template takes care of all the imports and provides a structure for an ETL pipeline that I needed to process this data.

## Example Query
* Get name of artist, song and user (first and last name) and sort by itemInSession and user (first name and last name): `SELECT * from artist_by_user_and_session WHERE userId=10 AND sessionId=182 GROUP BY itemInSession, firstName, lastName`


