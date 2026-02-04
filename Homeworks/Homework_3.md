# HOMEWORK_3
# 02-02-2026

## 1. Create a movie Table. 

## 2. Input the values given

## 3. Write the query to display the results of the above table:
	### a. List business done by the movies showing only MovieID, MovieName and BusinessCost.
	### b. List the different categories of movies. (USE THE DISTINCT KEYWORD)
	### c. Find the net profit of each movie showing its ID, Name and Net Profit. (Hint: Net Profit = BusinessCost – ProductionCost) 
	### d. Make sure that the new column name is labelled as NetProfit. Is this column now a part of the MOVIE relation. If no, then what name is coined for such columns? What can you say about the profit of a movie which has not yet released? Does your query result show profit as zero?
	### d. List all movies with ProductionCost greater than 80,000 and less than 1,25,000 showing ID, Name and ProductionCost.
	### e. List all movies which fall in the category of Comedy or Action. 
	### f. List the movies which have not been released yet.





## 1. Create a movie Table. 


MariaDB [iilm]> CREATE TABLE movie(
    -> movie_id INT(4) NOT NULL,
    -> movie_name VARCHAR(20),
    -> category VARCHAR(20),
    -> release_date DATE,
    -> production_cost INT(10),
    -> buissness_cost INT(10));
Query OK, 0 rows affected (0.011 sec)

MariaDB [iilm]> DESC movie;
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| movie_id        | int(4)      | NO   |     | NULL    |       |
| movie_name      | varchar(20) | YES  |     | NULL    |       |
| category        | varchar(20) | YES  |     | NULL    |       |
| release_date    | date        | YES  |     | NULL    |       |
| production_cost | int(10)     | YES  |     | NULL    |       |
| buissness_cost  | int(10)     | YES  |     | NULL    |       |
+-----------------+-------------+------+-----+---------+-------+
6 rows in set (0.020 sec)




## 2. Input the values given


MariaDB [iilm]> INSERT INTO movie VALUES
    -> (001, 'Hindi_Movie', 'Musical', '2018-04-23', 124500, 130000),
    -> (002, 'Tamil_Movie', 'Action', '2016-05-17', 112000, 118000),
    -> (003, 'English_Movie', 'Horror', '2017-08-06', 2450000, 360000),
    -> (004, 'Bengali_Movie', 'Adventure', '2017-01-04', 72000, 100000);
Query OK, 4 rows affected (0.004 sec)
Records: 4  Duplicates: 0  Warnings: 0

MariaDB [iilm]> INSERT INTO movie VALUES
    -> (005, 'Telugu_Movie', 'Action', NULL , 100000, NULL),
    -> (006, 'Punjabi_Movie', 'Comedy', NULL , 30500, NULL);
Query OK, 2 rows affected (0.004 sec)
Records: 2  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT* FROM movie;
+----------+---------------+-----------+--------------+-----------------+----------------+
| movie_id | movie_name    | category  | release_date | production_cost | buissness_cost |
+----------+---------------+-----------+--------------+-----------------+----------------+
|        1 | Hindi_Movie   | Musical   | 2018-04-23   |          124500 |         130000 |
|        2 | Tamil_Movie   | Action    | 2016-05-17   |          112000 |         118000 |
|        3 | English_Movie | Horror    | 2017-08-06   |         2450000 |         360000 |
|        4 | Bengali_Movie | Adventure | 2017-01-04   |           72000 |         100000 |
|        5 | Telugu_Movie  | Action    | NULL         |          100000 |           NULL |
|        6 | Punjabi_Movie | Comedy    | NULL         |           30500 |           NULL |
+----------+---------------+-----------+--------------+-----------------+----------------+
6 rows in set (0.000 sec)

MariaDB [iilm]> ALTER TABLE movie CHANGE buissness_cost buisness_cost INt;



## 3. Write the query to display the results of the above table:

### a. List business done by the movies showing only MovieID, MovieName and BusinessCost.


+----------+---------------+---------------+
| movie_id | movie_name    | buisness_cost |
+----------+---------------+---------------+
|        1 | Hindi_Movie   |        130000 |
|        2 | Tamil_Movie   |        118000 |
|        3 | English_Movie |        360000 |
|        4 | Bengali_Movie |        100000 |
|        5 | Telugu_Movie  |          NULL |
|        6 | Punjabi_Movie |          NULL |
+----------+---------------+---------------+
6 rows in set (0.001 sec)



## b. List the different categories of movies. (USE THE DISTINCT KEYWORD)
	


MariaDB [iilm]> SELECT DISTINCT category FROM movie;
+-----------+
| category  |
+-----------+
| Musical   |
| Action    |
| Horror    |
| Adventure |
| Comedy    |
+-----------+
5 rows in set (0.000 sec)




## c. Find the net profit of each movie showing its ID, Name and Net Profit. (Hint: Net Profit = BusinessCost – ProductionCost) 


MariaDB [iilm]> UPDATE movie
    -> SET production_cost = 245000
    -> WHERE movie_id = 3;
Query OK, 1 row affected (0.004 sec)
Rows matched: 1  Changed: 1  Warnings: 0




MariaDB [iilm]> SELECT movie_id, movie_name, (BUISNESS_COST - PRODUCTION_COST) AS netProfit
    -> FROM movie;
+----------+---------------+-----------+
| movie_id | movie_name    | netProfit |
+----------+---------------+-----------+
|        1 | Hindi_Movie   |      5500 |
|        2 | Tamil_Movie   |      6000 |
|        3 | English_Movie |    115000 |
|        4 | Bengali_Movie |     28000 |
|        5 | Telugu_Movie  |      NULL |
|        6 | Punjabi_Movie |      NULL |
+----------+---------------+-----------+
6 rows in set (0.000 sec)


MariaDB [iilm]> ALTER TABLE movie
    -> ADD COLUMN net_profit INT(10) AS (buisness_cost - production_cost);
Query OK, 0 rows affected (0.017 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT* FROM movie;
+----------+---------------+-----------+--------------+-----------------+---------------+------------+
| movie_id | movie_name    | category  | release_date | production_cost | buisness_cost | net_profit |
+----------+---------------+-----------+--------------+-----------------+---------------+------------+
|        1 | Hindi_Movie   | Musical   | 2018-04-23   |          124500 |        130000 |       5500 |
|        2 | Tamil_Movie   | Action    | 2016-05-17   |          112000 |        118000 |       6000 |
|        3 | English_Movie | Horror    | 2017-08-06   |          245000 |        360000 |     115000 |
|        4 | Bengali_Movie | Adventure | 2017-01-04   |           72000 |        100000 |      28000 |
|        5 | Telugu_Movie  | Action    | NULL         |          100000 |          NULL |       NULL |
|        6 | Punjabi_Movie | Comedy    | NULL         |           30500 |          NULL |       NULL |
+----------+---------------+-----------+--------------+-----------------+---------------+------------+
6 rows in set (0.000 sec)




### d. List all movies with ProductionCost greater than 80,000 and less than 1,25,000 showing ID, Name and ProductionCost.
	

MariaDB [iilm]> SELECT movie_name FROM movie
    -> WHERE production_cost BETWEEN 80000 AND 125000;
+--------------+
| movie_name   |
+--------------+
| Hindi_Movie  |
| Tamil_Movie  |
| Telugu_Movie |
+--------------+
3 rows in set (0.000 sec)




### e. List all movies which fall in the category of Comedy or Action. 
	

MariaDB [iilm]> SELECT movie_name FROM movie
    -> WHERE category IN ('Action', 'comedy');
+---------------+
| movie_name    |
+---------------+
| Tamil_Movie   |
| Telugu_Movie  |
| Punjabi_Movie |
+---------------+
3 rows in set (0.000 sec)




### f. List the movies which have not been released yet.

MariaDB [iilm]> SELECT movie_name FROM movie
    -> WHERE release_date IS NULL;
+---------------+
| movie_name    |
+---------------+
| Telugu_Movie  |
| Punjabi_Movie |
+---------------+
2 rows in set (0.000 sec)
