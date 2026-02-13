# Assignment 06
# 13-02-2026

## 1. Display empno, ename, deptno from employee table. Insteadof display department numbers display the related department name (Use decode{case} function).
## 2. Display your age in days.
## 3. Display your age in months.
## 4. Display the current date as 15th August Friday Nineteen Ninety-Seven. (Cannot do in word)
## 5. Display the following output for each row from employee table.
## 6. Scott has joined the company on Wednesday 13th AugustNineteen Ninety
## 7. Find the date for nearest Saturday after current date.
## 8. Display current time.
## 9. Display the date three months Before the current date
## 10. Display those employees who joined in the company in the month of Dec.
## 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.
## 12. Display those employees whose 10% of salary is equal to the year of joining.
## 13. Display those employees who joined the company after 15 of the months.
## 14. Display those employees who has joined before 15th of the month
## 15. Display those employees whose joining DATE is available in deptno


# Table for Reference

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


# QUERIES

## 1. Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name (Use {decode} case function).




MariaDB [manas_db]> SELECT empno, ename,
    -> CASE deptno
    -> WHEN 10 THEN 'RESEARCH'
    -> WHEN 20 THEN 'ACCOUNTING'
    -> WHEN 30 THEN 'SALES'
    -> WHEN 40 THEN 'OPERATIONS'
    -> END AS DEPT_NAMES
    -> FROM emp;
+-------+--------+------------+
| empno | ename  | DEPT_NAMES |
+-------+--------+------------+
|  7369 | SMITH  | ACCOUNTING |
|  7499 | ALLEN  | SALES      |
|  7521 | WARD   | SALES      |
|  7566 | JONES  | ACCOUNTING |
|  7654 | MARTIN | SALES      |
|  7698 | BLAKE  | SALES      |
|  7782 | CLARK  | ACCOUNTING |
|  7788 | SCOTT  | OPERATIONS |
|  7839 | KING   | ACCOUNTING |
|  7844 | TURNER | SALES      |
|  7876 | ADAMS  | ACCOUNTING |
|  7900 | JAMES  | SALES      |
|  7902 | FORD   | ACCOUNTING |
|  7934 | MILLER | RESEARCH   |
+-------+--------+------------+
14 rows in set (0.001 sec)




## 2. Display your age in days.


MariaDB [manas_db]> SELECT DATEDIFF(CURDATE(), "2006-07-02") AS 'DOB in Days';
+-------------+
| DOB in Days |
+-------------+
|        7166 |
+-------------+
1 row in set (0.001 sec)




## 3. Display your age in months.



MariaDB [manas_db]> SELECT TIMESTAMPDIFF(MONTH, "2006-07-02", CURDATE()) AS 'DOB in Months';
+---------------+
| DOB in Months |
+---------------+
|           235 |
+---------------+
1 row in set (0.000 sec)




## 4. Display the current date as 15th August Friday Nineteen Ninety-Seven.(Cannot do in word)


MariaDB [manas_db]> SELECT DATE_FORMAT(CURDATE(), "%D %M %W %Y") AS 'Current Date';
+---------------------------+
| Current Date              |
+---------------------------+
| 13th February Friday 2026 |
+---------------------------+
1 row in set (0.000 sec)




## 5. Display the following output for each row from employee table.


MariaDB [manas_db]> SELECT CONCAT(
    -> ename,
    -> ' has joined the company on ',
    -> DATE_FORMAT(HIREDATE, "%D %M %W %Y")
    -> ) AS 'Required Format' FROM emp;
+--------------------------------------------------------------+
| Required Format                                              |
+--------------------------------------------------------------+
| SMITH has joined the company on 17th December Wednesday 1980 |
| ALLEN has joined the company on 20th February Friday 1981    |
| WARD has joined the company on 22nd February Sunday 1981     |
| JONES has joined the company on 2nd April Thursday 1981      |
| MARTIN has joined the company on 28th September Monday 1981  |
| BLAKE has joined the company on 1st May Friday 1981          |
| CLARK has joined the company on 9th June Tuesday 1981        |
| SCOTT has joined the company on 9th December Thursday 1982   |
| KING has joined the company on 17th November Tuesday 1981    |
| TURNER has joined the company on 8th September Tuesday 1981  |
| ADAMS has joined the company on 12th January Wednesday 1983  |
| JAMES has joined the company on 3rd December Thursday 1981   |
| FORD has joined the company on 3rd December Thursday 1981    |
| MILLER has joined the company on 23rd January Saturday 1982  |
+--------------------------------------------------------------+
14 rows in set (0.001 sec)



## 6. Scott has joined the company on Wednesday 13th August Nineteen Ninety

-> Part of 5th Question


## 7. Find the date for nearest Saturday after current date.


MariaDB [manas_db]> SELECT DATE_ADD(
    -> CURDATE(),
    -> INTERVAL(5 - WEEKDAY(CURDATE())) DAY
    -> ) AS "Next Saturday";
+---------------+
| Next Saturday |
+---------------+
| 2026-02-14    |
+---------------+
1 row in set (0.000 sec)



## 8. Display current time.

MariaDB [manas_db]> SELECT CURTIME() AS 'Current Time';
+--------------+
| Current Time |
+--------------+
| 13:18:04     |
+--------------+
1 row in set (0.000 sec)


## 9. Display the date three months Before the current date


MariaDB [manas_db]> SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH)
    -> AS "Date Before 3 Months";
+----------------------+
| Date Before 3 Months |
+----------------------+
| 2025-11-13           |
+----------------------+
1 row in set (0.000 sec)




## 10. Display those employees who joined in the company in the month of Dec.


MariaDB [manas_db]> SELECT ename, hiredate
    -> FROM emp
    -> WHERE MONTH(hiredate) = 12;
+-------+------------+
| ename | hiredate   |
+-------+------------+
| SMITH | 1980-12-17 |
| SCOTT | 1982-12-09 |
| JAMES | 1981-12-03 |
| FORD  | 1981-12-03 |
+-------+------------+
4 rows in set (0.001 sec)


## 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.


MariaDB [manas_db]> SELECT ename, hiredate, sal
    -> FROM emp
    -> WHERE LEFT(DATE_FORMAT(hiredate, "%Y"), 2) = RIGHT(sal, 2);
Empty set (0.001 sec)



## 12. Display those employees whose 10% of salary is equal to the year of joining.


MariaDB [manas_db]> SELECT ename, sal, hiredate
    -> FROM emp
    -> WHERE (SAL*0.10) = YEAR(hiredate);
Empty set (0.000 sec)



## 13. Display those employees who joined the company after 15 of the months.


MariaDB [manas_db]> SELECT ename, hiredate
    -> FROM emp
    -> WHERE DAY(HIREDATE) > 15;
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| SMITH  | 1980-12-17 |
| ALLEN  | 1981-02-20 |
| WARD   | 1981-02-22 |
| MARTIN | 1981-09-28 |
| KING   | 1981-11-17 |
| MILLER | 1982-01-23 |
+--------+------------+
6 rows in set (0.001 sec)


## 14. Display those employees who has joined before 15th of the month


MariaDB [manas_db]> SELECT ename, hiredate
    -> FROM emp
    -> WHERE DAY(HIREDATE) < 15;
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| JONES  | 1981-04-02 |
| BLAKE  | 1981-05-01 |
| CLARK  | 1981-06-09 |
| SCOTT  | 1982-12-09 |
| TURNER | 1981-09-08 |
| ADAMS  | 1983-01-12 |
| JAMES  | 1981-12-03 |
| FORD   | 1981-12-03 |
+--------+------------+
8 rows in set (0.000 sec)


## 15. Display those employees whose joining DATE is available in deptno



MariaDB [manas_db]> SELECT ename, hiredate, deptno
    -> FROM emp
    -> WHERE deptno IS NOT NULL
    -> AND hiredate IS NOT NULL;
+--------+------------+--------+
| ename  | hiredate   | deptno |
+--------+------------+--------+
| SMITH  | 1980-12-17 |     20 |
| ALLEN  | 1981-02-20 |     30 |
| WARD   | 1981-02-22 |     30 |
| JONES  | 1981-04-02 |     20 |
| MARTIN | 1981-09-28 |     30 |
| BLAKE  | 1981-05-01 |     30 |
| CLARK  | 1981-06-09 |     20 |
| SCOTT  | 1982-12-09 |     40 |
| KING   | 1981-11-17 |     20 |
| TURNER | 1981-09-08 |     30 |
| ADAMS  | 1983-01-12 |     20 |
| JAMES  | 1981-12-03 |     30 |
| FORD   | 1981-12-03 |     20 |
| MILLER | 1982-01-23 |     10 |
+--------+------------+--------+
14 rows in set (0.000 sec)
