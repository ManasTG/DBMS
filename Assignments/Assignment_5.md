# Assignment 05
# 07-02-2026

## 1. Display the total number of employee working in the company.
## 2. Display the total salary being paid to all employees.
## 3. Display the maximum salary from employee table.
## 4. Display the minimum salary from employee table.
## 5. Display the average salary from employee table
## 6. Display the maximum salary being paid to clerk.
## 7. Display the maximum salary being paid in dept no 20.
## 8. Display the minimum salary paid to any salesman.
## 9. Display the average salary drawn by managers.
## 10. Display the total salary drawn by analyst working in dept no 40.
## 11. Display the names of the employee in Uppercase.
## 12. Display the names of the employee in Lowercase.
## 13. Display the names of the employee in Proper case.
## 14. Display the length of Your name using appropriate function.
## 15. Display the length of all the employee names.


# Table for Reference

MariaDB [manas_db]> SELECT * FROM emp;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.000 sec)



# QUERIES	


## 1. Display the total number of employee working in the company.



MariaDB [manas_db]> SELECT COUNT(*) AS 'Total number of emp'
    -> FROM emp;
+---------------------+
| Total number of emp |
+---------------------+
|                  14 |
+---------------------+
1 row in set (0.001 sec)



## 2. Display the total salary being paid to all employees.



MariaDB [manas_db]> SELECT SUM(sal) AS 'Total Salary'
    -> FROM emp;
+--------------+
| Total Salary |
+--------------+
|        29025 |
+--------------+
1 row in set (0.000 sec)




## 3. Display the maximum salary from employee table.



MariaDB [manas_db]> SELECT MAX(sal) AS 'Maximum Salary'
    -> FROM emp;
+----------------+
| Maximum Salary |
+----------------+
|           5000 |
+----------------+
1 row in set (0.001 sec)



## 4. Display the minimum salary from employee table.



MariaDB [manas_db]> SELECT MIN(sal) AS 'Minimum Salary'
    -> FROM emp;
+----------------+
| Minimum Salary |
+----------------+
|            800 |
+----------------+
1 row in set (0.000 sec)



## 5. Display the average salary from employee table



MariaDB [manas_db]> SELECT AVG(sal) AS 'Average Salary'
    -> FROM emp;
+----------------+
| Average Salary |
+----------------+
|      2073.2143 |
+----------------+
1 row in set (0.000 sec)



## 6. Display the maximum salary being paid to clerk.



MariaDB [manas_db]> SELECT MAX(sal) AS 'Maximum Sal to clerk'
    -> FROM emp
    -> WHERE job = 'clerk';
+----------------------+
| Maximum Sal to clerk |
+----------------------+
|                 1300 |
+----------------------+
1 row in set (0.000 sec)



## 7. Display the maximum salary being paid in dept no 20.


MariaDB [manas_db]> SELECT MAX(sal) AS 'Max. sal paid to deptno 20'
    -> FROM emp
    -> WHERE deptno = 20;
+----------------------------+
| Max. sal paid to deptno 20 |
+----------------------------+
|                       5000 |
+----------------------------+
1 row in set (0.000 sec)



## 8. Display the minimum salary paid to any salesman.



MariaDB [manas_db]> SELECT MAX(sal) AS 'Max. sal paid to salesman'
    -> FROM emp
    -> WHERE job = 'salesman';
+---------------------------+
| Max. sal paid to salesman |
+---------------------------+
|                      1600 |
+---------------------------+
1 row in set (0.000 sec)



## 9. Display the average salary drawn by managers.



MariaDB [manas_db]> SELECT AVG(sal) AS 'Avg sal of managers'
    -> FROM emp
    -> WHERE job = 'manager';
+---------------------+
| Avg sal of managers |
+---------------------+
|           2758.3333 |
+---------------------+
1 row in set (0.000 sec)



## 10. Display the total salary drawn by analyst working in dept no 40.



MariaDB [manas_db]> SELECT SUM(sal) AS 'Total sal of analyst'
    -> FROM emp
    -> WHERE job = 'analyst' AND deptno = '40';
+----------------------+
| Total sal of analyst |
+----------------------+
|                 3000 |
+----------------------+
1 row in set (0.000 sec)



## 11. Display the names of the employee in Uppercase.



MariaDB [manas_db]> SELECT UPPER(ename) AS 'Uppercase emp name'
    -> FROM emp;
+--------------------+
| Uppercase emp name |
+--------------------+
| SMITH              |
| ALLEN              |
| WARD               |
| JONES              |
| MARTIN             |
| BLAKE              |
| CLARK              |
| SCOTT              |
| KING               |
| TURNER             |
| ADAMS              |
| JAMES              |
| FORD               |
| MILLER             |
+--------------------+
14 rows in set (0.000 sec)



## 12. Display the names of the employee in Lowercase.



MariaDB [manas_db]> SELECT LOWER(ename) AS 'Uppercase emp name'
    -> FROM emp;
+--------------------+
| Uppercase emp name |
+--------------------+
| smith              |
| allen              |
| ward               |
| jones              |
| martin             |
| blake              |
| clark              |
| scott              |
| king               |
| turner             |
| adams              |
| james              |
| ford               |
| miller             |
+--------------------+
14 rows in set (0.000 sec)



## 13. Display the names of the employee in Proper case.


MariaDB [manas_db]> SELECT CONCAT(
    -> UPPER(SUBSTRING(ename, 1, 1)), LOWER(SUBSTRING(ename, 2)))
    -> AS 'Employee name in Propercase'
    -> FROM emp;
+-----------------------------+
| Employee name in Propercase |
+-----------------------------+
| Smith                       |
| Allen                       |
| Ward                        |
| Jones                       |
| Martin                      |
| Blake                       |
| Clark                       |
| Scott                       |
| King                        |
| Turner                      |
| Adams                       |
| James                       |
| Ford                        |
| Miller                      |
+-----------------------------+
14 rows in set (0.001 sec)



## 14. Display the length of Your name using appropriate function.



MariaDB [manas_db]> SELECT LENGTH('Manas') AS 'Length of Name';
+----------------+
| Length of Name |
+----------------+
|              5 |
+----------------+
1 row in set (0.000 sec)



## 15. Display the length of all the employee names



MariaDB [manas_db]> SELECT ename, LENGTH(ename) AS 'Length of the ename'
    -> FROM emp;
+--------+---------------------+
| ename  | Length of the ename |
+--------+---------------------+
| SMITH  |                   5 |
| ALLEN  |                   5 |
| WARD   |                   4 |
| JONES  |                   5 |
| MARTIN |                   6 |
| BLAKE  |                   5 |
| CLARK  |                   5 |
| SCOTT  |                   5 |
| KING   |                   4 |
| TURNER |                   6 |
| ADAMS  |                   5 |
| JAMES  |                   5 |
| FORD   |                   4 |
| MILLER |                   6 |
+--------+---------------------+
14 rows in set (0.000 sec)


