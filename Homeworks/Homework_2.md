##HOMEWORK_2
##02-02-2026

#1. Create an Student table.. 
#Done Already in Homework 1

#2. Create Employee Table 
#DOne Already in Assignment 0

#3. Drop/Truncate
#Done Already in Assignment 1

#4. Table Alteration - ALTER Add a column, MODIFY column to store decimal values, RENAME a table

#5. Table Removal - Truscate and Drop




#4. Table Alteration - ALTER Add a column, MODIFY column to store decimal values, RENAME a table


#4.1- ALTER Add a column

MariaDB [iilm]> ALTER TABLE student
    -> ADD `exists` VARCHAR(5) DEFAULT('yes');
Query OK, 0 rows affected (0.010 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT* FROM student;
+------------+--------------+---------------------------------+------------+-----------------+----------+--------+
| student_id | student_name | email                           | dob        | course          | fees     | exists |
+------------+--------------+---------------------------------+------------+-----------------+----------+--------+
|         12 | DHRUV        | dhruv.singh.pawar.cs28@iilm.edu | 2006-06-26 | CLOUD COMPUTING | 92000.00 | yes    |
|         31 | MANAS        | manas1.cs28@iilm.edu            | 2006-07-02 | DATA SCIENCE    | 92000.00 | yes    |
|         36 | FAHIM        | md.Fahim.cs28@iilm.edu          | 2004-09-22 | DATA SCIENCE    | 92000.00 | yes    |
|         42 | ROHIT        | rohit.kumar.cs28@iilm.edu       | 2006-03-06 | CLOUD COMPUTING | 92000.00 | yes    |
|         45 | SONAL        | sonal.singh.cs28@iilm.edu       | 2006-01-04 | DATA SCIENCE    | 84000.00 | yes    |
+------------+--------------+---------------------------------+------------+-----------------+----------+--------+
5 rows in set (0.000 sec)


#4.2 - MODIFY column to store decimal values


MariaDB [iilm]> ALTER TABLE student
    -> MODIFY fees DECIMAL(8,1);
Query OK, 5 rows affected (0.078 sec)
Records: 5  Duplicates: 0  Warnings: 0

MariaDB [iilm]> SELECT* FROM student;
+------------+--------------+---------------------------------+------------+-----------------+---------+--------+
| student_id | student_name | email                           | dob        | course          | fees    | exists |
+------------+--------------+---------------------------------+------------+-----------------+---------+--------+
|         12 | DHRUV        | dhruv.singh.pawar.cs28@iilm.edu | 2006-06-26 | CLOUD COMPUTING | 92000.0 | yes    |
|         31 | MANAS        | manas1.cs28@iilm.edu            | 2006-07-02 | DATA SCIENCE    | 92000.0 | yes    |
|         36 | FAHIM        | md.Fahim.cs28@iilm.edu          | 2004-09-22 | DATA SCIENCE    | 92000.0 | yes    |
|         42 | ROHIT        | rohit.kumar.cs28@iilm.edu       | 2006-03-06 | CLOUD COMPUTING | 92000.0 | yes    |
|         45 | SONAL        | sonal.singh.cs28@iilm.edu       | 2006-01-04 | DATA SCIENCE    | 84000.0 | yes    |
+------------+--------------+---------------------------------+------------+-----------------+---------+--------+
5 rows in set (0.002 sec)



#4.3 - RENAME a table


MariaDB [iilm]> ALTER TABLE student
    -> RENAME student_list;
Query OK, 0 rows affected (0.011 sec)

MariaDB [iilm]> SHOW TABLES;
+----------------+
| Tables_in_iilm |
+----------------+
| student_list   |
+----------------+
1 row in set (0.000 sec)




#5. Table Deletion

#5.1 Truncate

MariaDB [iilm]> CREATE TABLE temp_student
    -> SELECT* FROM student_list;
Query OK, 5 rows affected (0.018 sec)
Records: 5  Duplicates: 0  Warnings: 0

MariaDB [iilm]> TRUnCATE TABLE temp_student;
Query OK, 0 rows affected (0.033 sec)



#5.2 - Drop

MariaDB [iilm]> SHOW TABLES;
+----------------+
| Tables_in_iilm |
+----------------+
| student_list   |
| temp_student   |
+----------------+
2 rows in set (0.001 sec)

MariaDB [iilm]> DROP TABLE temp_student;
Query OK, 0 rows affected (0.010 sec)

MariaDB [iilm]> SHOW TABLES;
+----------------+
| Tables_in_iilm |
+----------------+
| student_list   |
+----------------+
1 row in set (0.001 sec)


