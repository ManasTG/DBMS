# HOMEWORK_1
# 02-02-2026

## 1. Create a database named iilm.
#Within this database, create a table called Student with appropriate columns, data types, and constraints.
#After creating the table, insert 5 records into it.
#Use the following command to view the tuples of the table.

# SELECT * FROM Student;

## Queries start

MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| comp_db            |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
6 rows in set (0.001 sec)


MariaDB [(none)]> CREATE DATABASE IILM;
Query OK, 1 row affected (0.003 sec)

MariaDB [iilm]> CREATE TABLE Student(
    -> student_id INT(10) PRIMARY KEY,
    -> student_name VARCHAR(50) NOT NULL,
    -> email VARCHAR(100) NOT NULL UNIQUE,
    -> dob DATE NOT NULL,
    -> course VARCHAR(50) NOT NULL,
    -> fees DECIMAL(8,2) CHECK(fees>0));
Query OK, 0 rows affected (0.037 sec)

MariaDB [iilm]> DESC student;
+--------------+--------------+------+-----+---------+-------+
| Field        | Type         | Null | Key | Default | Extra |
+--------------+--------------+------+-----+---------+-------+
| student_id   | int(10)      | NO   | PRI | NULL    |       |
| student_name | varchar(50)  | NO   |     | NULL    |       |
| email        | varchar(100) | NO   | UNI | NULL    |       |
| dob          | date         | NO   |     | NULL    |       |
| course       | varchar(50)  | NO   |     | NULL    |       |
| fees         | decimal(8,2) | YES  |     | NULL    |       |
+--------------+--------------+------+-----+---------+-------+
6 rows in set (0.017 sec)

MariaDB [iilm]> INSERT INTO student VALUES
    -> (31, 'MANAS', 'manas1.cs28@iilm.edu', '2006-07-02', 'DATA SCIENCE', 92000);
Query OK, 1 row affected (0.004 sec)

MariaDB [iilm]> INSERT INTO student VALUES
    -> (36, 'FAHIM', 'md.Fahim.cs28@iilm.edu', '2004-09-22', 'DATA SCIENCE', 92000),
    -> (45, 'SONAL', 'sonal.singh.cs28@iilm.edu', '2006-01-04', 'DATA SCIENCE', 84000),
    -> (12, 'DHRUV', 'dhruv.singh.pawar.cs28@iilm.edu', '2006-06-26', 'CLOUD COMPUTING', 92000),
    -> (42, 'ROHIT', 'rohit.kumar.cs28@iilm.edu', '2006-03-06', 'CLOUD COMPUTING', 92000);
Query OK, 4 rows affected (0.004 sec)
Records: 4  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT* FROM student;
+------------+--------------+---------------------------------+------------+-----------------+----------+
| student_id | student_name | email                           | dob        | course          | fees     |
+------------+--------------+---------------------------------+------------+-----------------+----------+
|         12 | DHRUV        | dhruv.singh.pawar.cs28@iilm.edu | 2006-06-26 | CLOUD COMPUTING | 92000.00 |
|         31 | MANAS        | manas1.cs28@iilm.edu            | 2006-07-02 | DATA SCIENCE    | 92000.00 |
|         36 | FAHIM        | md.Fahim.cs28@iilm.edu          | 2004-09-22 | DATA SCIENCE    | 92000.00 |
|         42 | ROHIT        | rohit.kumar.cs28@iilm.edu       | 2006-03-06 | CLOUD COMPUTING | 92000.00 |
|         45 | SONAL        | sonal.singh.cs28@iilm.edu       | 2006-01-04 | DATA SCIENCE    | 84000.00 |
+------------+--------------+---------------------------------+------------+-----------------+----------+
5 rows in set (0.000 sec)