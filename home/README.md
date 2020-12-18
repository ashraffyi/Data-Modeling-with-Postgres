### Sparkify Data Modelling ###

This is project 1/5 of Udacitys Data Engineering Nanodegree.

***Introduction***
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

***Project Description***
In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

***ETL Schema*** 

    Star: star schema is optimized for the follwong queries:

        SELECT s.song_id, a.artist_id FROM songs s JOIN artists a ON s.artist_id = a.artist_id WHERE s.title = (%s) AND a.name  = (%s) AND s.duration = (%s)


***Fact Table***
    
    songplays - records in log data associated with song plays i.e. records with page NextSong
                attributes: songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

***Dimension Tables***

    users - users in the app
                attributes: user_id, first_name, last_name, gender, level

    songs - songs in music database
                attributes: song_id, title, artist_id, year, duration

    artists - artists in music database
                attributes: artist_id, name, location, latitude, longitude

    time - timestamps of records in songplays broken down into specific units
                attributes: start_time, hour, day, week, month, year, weekday
                

***Files***

    create_tables.py - You run this file to reset your tables before each time you run your ETL scripts.
    etl.py - contains the code to extract the data from JSON files, and load into each table.
    test.ipynb - displays the first few rows of each table to let you check your database. This is used for testing the results from etl.py 
    data - folder contains the sparkify music streaming app data in JSON log and song file
    
***Dependencies***
    
    Python3
    psycopg2
    os
    glob
    pandas    
    
    
***Compling Data***

    Execute "create_tables.py" by running 'python create_tables.py in Terminal' which will create a reset all tables to empty tables.
    Execute "etl.py" by running 'python etl.py in Terminal' This will load the data into the tables
    
