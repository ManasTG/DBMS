# ASSIGNMENT 4
# 6-2-2026

## 1. Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81.
## 2. Display the names of employees whose names have second alphabet A in their names.
## 3. Display the names of employees whose name is exactly five characters in length
## 4. Display the names of employees whose names have second alphabet A in their names.
## 5. Display the names of employees who are not working as salesman or clerk or analyst.
## 6. Display the name of the employee along with their annual salary (sal*12). The name of the employee earning highest salary should appear first.
## 7. Display name, sal, hra, pf, da, totalsal for each employee. The output should be in the order of total sal, hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf.
## 8. Update the salary of each employee by 10% increment who are not eligible for commission.
## 9. Display those employees whose salary is more than 3000 after giving 20% increment.
## 10. Display those employees whose salary contains atleast 3 digits.





# QUERIES

## 1. Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81.


MariaDB [manas_db]> SELECT ename, hiredate FROM emp
    -> WHERE hiredate > '1981-12-31' OR hiredate < '1980-06-30';
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| SCOTT  | 1982-12-09 |
| ADAMS  | 1983-01-12 |
| MILLER | 1982-01-23 |
+--------+------------+
3 rows in set (0.001 sec)


## 2. Display the names of employees whose names have second alphabet A in their names.


MariaDB [manas_db]> SELECT ename FROM emp
    -> WHERE ename LIKE '_A%';
+--------+
| ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.001 sec)



## 3. Display the names of employees whose name is exactly five characters in length


MariaDB [manas_db]> SELECT ename FROM emp
    -> WHERE LENGTH(ename) = 5;
+-------+
| ename |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
8 rows in set (0.000 sec)



## 4. Display the names of employees whose names have second alphabet A in their names. (DIFFERENT WAY- SubString)(x, m, n) [x- column, m- where we need to find, n- noumber of substring]


MariaDB [manas_db]> SELECT ename FROM emp
    -> WHERE SUBSTRING(ename, 2, 1) = 'A';
+--------+
| ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.000 sec)



## 5. Display the names of employees who are not working as salesman or clerk or analyst.



MariaDB [manas_db]> SELECT ename, job FROM emp
    -> WHERE job NOT IN ('salesman', 'clerk', 'analyst');
+-------+-----------+
| ename | job       |
+-------+-----------+
| JONES | MANAGER   |
| BLAKE | MANAGER   |
| CLARK | MANAGER   |
| KING  | PRESIDENT |
+-------+-----------+
4 rows in set (0.000 sec)




## 6. Display the name of the employee along with their annual salary (sal*12). The name of the employee earning highest salary should appear first.




MariaDB [manas_db]> SELECT ename, sal*12 AS 'Annual Salary'
    -> FROM emp
    -> ORDER BY sal*12 DESC;
+--------+---------------+
| ename  | Annual Salary |
+--------+---------------+
| KING   |         60000 |
| SCOTT  |         36000 |
| FORD   |         36000 |
| JONES  |         35700 |
| BLAKE  |         34200 |
| CLARK  |         29400 |
| ALLEN  |         19200 |
| TURNER |         18000 |
| MILLER |         15600 |
| MARTIN |         15000 |
| WARD   |         15000 |
| ADAMS  |         13200 |
| JAMES  |         11400 |
| SMITH  |          9600 |
+--------+---------------+
14 rows in set (0.000 sec)



## 7. Display name, sal, hra, pf, da, totalsal for each employee. The output should be in the order of total sal, hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf. [hra - house allowance, ]


MariaDB [manas_db]> SELECT ename,
    -> (sal + sal*0.15 + sal*0.10) - sal*0.05 AS 'Total Salary',
    -> sal*0.15 AS HRA,
    -> sal*0.10 AS DA,
    -> sal*0.05 AS PF
    -> FROM emp;
+--------+--------------+--------+--------+--------+
| ename  | Total Salary | HRA    | DA     | PF     |
+--------+--------------+--------+--------+--------+
| SMITH  |       960.00 | 120.00 |  80.00 |  40.00 |
| ALLEN  |      1920.00 | 240.00 | 160.00 |  80.00 |
| WARD   |      1500.00 | 187.50 | 125.00 |  62.50 |
| JONES  |      3570.00 | 446.25 | 297.50 | 148.75 |
| MARTIN |      1500.00 | 187.50 | 125.00 |  62.50 |
| BLAKE  |      3420.00 | 427.50 | 285.00 | 142.50 |
| CLARK  |      2940.00 | 367.50 | 245.00 | 122.50 |
| SCOTT  |      3600.00 | 450.00 | 300.00 | 150.00 |
| KING   |      6000.00 | 750.00 | 500.00 | 250.00 |
| TURNER |      1800.00 | 225.00 | 150.00 |  75.00 |
| ADAMS  |      1320.00 | 165.00 | 110.00 |  55.00 |
| JAMES  |      1140.00 | 142.50 |  95.00 |  47.50 |
| FORD   |      3600.00 | 450.00 | 300.00 | 150.00 |
| MILLER |      1560.00 | 195.00 | 130.00 |  65.00 |
+--------+--------------+--------+--------+--------+
14 rows in set (0.001 sec)



## 8. Update the salary of each employee by 10% increment who are not eligible for commission.


MariaDB [manas_db]> CREATE TABLE emp_cpy1
    -> SELECT* FROM emp;
Query OK, 14 rows affected (0.019 sec)
Records: 14  Duplicates: 0  Warnings: 0

MariaDB [manas_db]> UPDATE emp_cpy1
    -> SET sal = sal*1.1
    -> WHERE comm IS NULL OR 0;
Query OK, 10 rows affected (0.005 sec)
Rows matched: 10  Changed: 10  Warnings: 0

MariaDB [manas_db]> SELECT* FROM emp_cpy1;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3300 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.000 sec)

[OG sal]
MariaDB [manas_db]> SELECT* FROM emp;
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
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+


## 9. Display those employees whose salary is more than 3000 after giving 20% increment.


MariaDB [manas_db]> CREATE TABLE emp_cpy2
    -> SELECT* FROM emp;
Query OK, 14 rows affected (0.020 sec)
Records: 14  Duplicates: 0  Warnings: 0

MariaDB [manas_db]> SELECT ename,
    -> sal,
    -> sal*1.20 AS Updated_sal
    -> FROM emp_cpy2
    -> WHERE sal*1.20 > 3000;
+-------+------+-------------+
| ename | sal  | Updated_sal |
+-------+------+-------------+
| JONES | 2975 |     3570.00 |
| BLAKE | 2850 |     3420.00 |
| SCOTT | 3000 |     3600.00 |
| KING  | 5000 |     6000.00 |
| FORD  | 3000 |     3600.00 |
+-------+------+-------------+
5 rows in set (0.000 sec)



## 10. Display those employees whose salary contains atleast 3 digits.



ariaDB [manas_db]> SELECT ename, sal FROM emp
    -> WHERE LENGTH(sal) > 3;
+--------+------+
| ename  | sal  |
+--------+------+
| ALLEN  | 1600 |
| WARD   | 1250 |
| JONES  | 2975 |
| MARTIN | 1250 |
| BLAKE  | 2850 |
| CLARK  | 2450 |
| SCOTT  | 3000 |
| KING   | 5000 |
| TURNER | 1500 |
| ADAMS  | 1100 |
| FORD   | 3000 |
| MILLER | 1300 |
+--------+------+
12 rows in set (0.000 sec)

