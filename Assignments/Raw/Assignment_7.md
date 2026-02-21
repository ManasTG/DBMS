# Assingment 07
# 14-02-2026


## 1. Compute the no. of days remaining in this year.
## 2. Find the highest and lowest salaries and the difference between of them.
## 3. List employee whose commission is greater than 25 % of their salaries.
## 4. Make a query that displays salary in dollar format.
## 5. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.
## 6. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading.
## 7. Query to get the last Sunday of Any Month.
## 8. Display department numbers and total number of employees working in each department.
## 9. Display the various jobs and total number of employees within each job group.
## 10. Display the depart numbers and total salary for each department.



# Table For Reference



# QUERIES





## 1. Compute the no. of days remaining in this year.


MariaDB [manas_db]> SELECT DATEDIFF('2027-01-01', CURDATE())
    -> AS 'Days Remaning';
+---------------+
| Days Remaning |
+---------------+
|           314 |
+---------------+
1 row in set (0.000 sec)


## 2. Find the highest and lowest salaries and the difference between of them.



MariaDB [manas_db]> SELECT
    -> MAX(sal) AS 'max salary',
    -> MIN(sal) AS 'min salary',
    -> MAX(sal) - MIN(sal) AS Difference
    -> FROM emp;
+------------+------------+------------+
| max salary | min salary | Difference |
+------------+------------+------------+
|       5000 |        800 |       4200 |
+------------+------------+------------+
1 row in set (0.000 sec)



## 3. List employee whose commission is greater than 25 % of their salaries.


MariaDB [manas_db]> SELECT ename, sal, comm FROM emp
    -> WHERE comm > (sal*0.25);
+--------+------+------+
| ename  | sal  | comm |
+--------+------+------+
| MARTIN | 1250 | 1400 |
+--------+------+------+
1 row in set (0.000 sec)



## 4. Make a query that displays salary in dollar format.



MariaDB [manas_db]> SELECT ename,
    -> CONCAT('$', FORMAT(sal, 2)) AS 'Salary'
    -> FROM emp;
+--------+-----------+
| ename  | Salary    |
+--------+-----------+
| SMITH  | $800.00   |
| ALLEN  | $1,600.00 |
| WARD   | $1,250.00 |
| JONES  | $2,975.00 |
| MARTIN | $1,250.00 |
| BLAKE  | $2,850.00 |
| CLARK  | $2,450.00 |
| SCOTT  | $3,000.00 |
| KING   | $5,000.00 |
| TURNER | $1,500.00 |
| ADAMS  | $1,100.00 |
| JAMES  | $950.00   |
| FORD   | $3,000.00 |
| MILLER | $1,300.00 |
+--------+-----------+
14 rows in set (0.000 sec)




## 5. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.



MariaDB [manas_db]> SELECT job,
    -> SUM(CASE WHEN deptno = 10 THEN sal ELSE 0 END) AS 'Dept 10',
    -> SUM(CASE WHEN deptno = 20 THEN sal ELSE 0 END) AS 'Dept 20',
    -> SUM(CASE WHEN deptno = 30 THEN sal ELSE 0 END) AS 'Dept 30',
    -> SUM(sal) AS 'Total Salary'
    -> FROM emp
    -> GROUP BY job;
+-----------+---------+---------+---------+--------------+
| job       | Dept 10 | Dept 20 | Dept 30 | Total Salary |
+-----------+---------+---------+---------+--------------+
| ANALYST   |       0 |    3000 |       0 |         6000 |
| CLERK     |    1300 |    1900 |     950 |         4150 |
| MANAGER   |       0 |    5425 |    2850 |         8275 |
| PRESIDENT |       0 |    5000 |       0 |         5000 |
| SALESMAN  |       0 |       0 |    5600 |         5600 |
+-----------+---------+---------+---------+--------------+
5 rows in set (0.001 sec)




## 6. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading.


MariaDB [manas_db]> SELECT COUNT(*)
    -> AS 'Total Employees',
    -> SUM(CASE WHEN YEAR(hiredate) = 1981 THEN 1 ELSE 0 END) AS "1981",
    -> SUM(CASE WHEN YEAR(hiredate) = 1982 THEN 1 ELSE 0 END) AS "1982",
    -> SUM(CASE WHEN YEAR(hiredate) = 1983 THEN 1 ELSE 0 END) AS "1983"
    -> FROM emp;
+-----------------+------+------+------+
| Total Employees | 1981 | 1982 | 1983 |
+-----------------+------+------+------+
|              14 |   10 |    2 |    1 |
+-----------------+------+------+------+
1 row in set (0.001 sec)



## 7. Query to get the last Sunday of Any Month.



MariaDB [manas_db]> SELECT
    -> DATE_SUB(LAST_DAY(CURDATE()),
    -> INTERVAL (DAYOFWEEK(LAST_DAY(CURDATE())) - 1) DAY)
    -> AS 'Last Sunday of the month';
+--------------------------+
| Last Sunday of the month |
+--------------------------+
| 2026-02-22               |
+--------------------------+
1 row in set (0.000 sec)



## 8. Display department numbers and total number of employees working in each department.


MariaDB [manas_db]> SELECT deptno, COUNT(*) AS 'Total Employees'
    -> FROM emp
    -> GROUP BY deptno;
+--------+------------------+
| deptno | Total Employees  |
+--------+------------------+
|     10 |                1 |
|     20 |                6 |
|     30 |                6 |
|     40 |                1 |
+--------+------------------+
4 rows in set (0.000 sec)



## 9. Display the various jobs and total number of employees within each job group.



MariaDB [manas_db]> SELECT job, COUNT(*) as 'Total Emp'
    -> FROM emp GROUP BY job;
+-----------+-----------+
| job       | Total Emp |
+-----------+-----------+
| ANALYST   |         2 |
| CLERK     |         4 |
| MANAGER   |         3 |
| PRESIDENT |         1 |
| SALESMAN  |         4 |
+-----------+-----------+
5 rows in set (0.000 sec)




## 10. Display the depart numbers and total salary for each department.




MariaDB [manas_db]> SELECT deptno, SUM(sal) AS 'Total Sal'
    -> FROM emp
    -> GROUP BY deptno;
+--------+-----------+
| deptno | Total Sal |
+--------+-----------+
|     10 |      1300 |
|     20 |     15325 |
|     30 |      9400 |
|     40 |      3000 |
+--------+-----------+
4 rows in set (0.000 sec)



Name _ Manas
