##Assignment 3 
##31-01-2026

#1. List all employees and jobs in Department 30 in descending order by salary.
#2. List job and Department Number of employees whose name
are five letters long begin with “A” and end with “N”.
#3. Display the name of employees whose name start with alphabet S.
#4. Display the names of employees whose name ends with alphabet S.
#5. Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks, salesman or analyst.
#6. Display employee number and names for employees who earn commission.
#7. Display employee number and total salary(sal+comision) for each employee.
#8. Display employee number and annual salary for each
employee.
#9. Display the names of all employees working as clerks and drawing a salary more than 3,000.
#10. Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3,000.



#1. List all employees and jobs in Department 30 in descending
order by salary.

MariaDB [comp_db]> SELECT ename, job FROM emp
    -> ORDER BY deptno DESC;
+--------+-----------+
| ename  | job       |
+--------+-----------+
| SCOTT  | ANALYST   |
| ALLEN  | SALESMAN  |
| WARD   | SALESMAN  |
| JAMES  | CLERK     |
| MARTIN | SALESMAN  |
| BLAKE  | MANAGER   |
| TURNER | SALESMAN  |
| SMITH  | CLERK     |
| ADAMS  | CLERK     |
| KING   | PRESIDENT |
| CLARK  | MANAGER   |
| JONES  | MANAGER   |
| FORD   | ANALYST   |
+--------+-----------+
13 rows in set (0.000 sec)


#2. List job and Department Number of employees whose name
are five letters long begin with “A” and end with “N”.

MariaDB [comp_db]> SELECT job, deptno
    -> FROM emp
    -> WHERE ename LIKE 'A___N';
+----------+--------+
| job      | deptno |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set (0.001 sec)


#3. Display the name of employees whose name start with
alphabet S.

MariaDB [comp_db]> SELECT ename FROM emp
    -> WHERE ename LIKE 'S%';
+-------+
| ename |
+-------+
| SMITH |
| SCOTT |
+-------+
2 rows in set (0.000 sec)


#4. Display the names of employees whose name ends with
alphabet S.

MariaDB [comp_db]> SELECT ename FROM emp
    -> WHERE ename LIKE '%S';
+-------+
| ename |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
3 rows in set (0.000 sec)


#5. Display the names of employees working in department
number 10 or 20 or 40 or employees working as clerks,
salesman or analyst.

MariaDB [comp_db]> SELECT ename FROM emp
    -> WHERE deptno IN (10,20,40)
    -> OR ename IN ('clerk', 'salesman', 'analyst');
+-------+
| ename |
+-------+
| SMITH |
| JONES |
| CLARK |
| SCOTT |
| KING  |
| ADAMS |
| FORD  |
+-------+
7 rows in set (0.000 sec)


#6. Display employee number and names for employees who earn
commission.
MariaDB [comp_db]> SELECT empno, ename FROM emp
    -> WHERE comm IS NOT NULL AND comm != 0;
+-------+--------+
| empno | ename  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
+-------+--------+
3 rows in set (0.000 sec)




#7. Display employee number and total salary for each employee.
MariaDB [comp_db]> SELECT empno, sal + IFNULL(comm, 0)
    -> AS 'SALARY' FROM emp;
+-------+--------+
| empno | SALARY |
+-------+--------+
|  7369 |    800 |
|  7499 |   1900 |
|  7521 |   1550 |
|  7566 |   2975 |
|  7654 |   2650 |
|  7698 |   2850 |
|  7782 |   2450 |
|  7788 |   3000 |
|  7839 |   5000 |
|  7844 |   1500 |
|  7876 |   1100 |
|  7900 |    950 |
|  7902 |   3000 |
+-------+--------+
13 rows in set (0.000 sec)



#8.Display employee number and annual salary for each
employee.

MariaDB [comp_db]> SELECT empno, sal*12 AS 'ANNUAL SALARY'
    -> FROM emp;
+-------+---------------+
| empno | ANNUAL SALARY |
+-------+---------------+
|  7369 |          9600 |
|  7499 |         19200 |
|  7521 |         15000 |
|  7566 |         35700 |
|  7654 |         15000 |
|  7698 |         34200 |
|  7782 |         29400 |
|  7788 |         36000 |
|  7839 |         60000 |
|  7844 |         18000 |
|  7876 |         13200 |
|  7900 |         11400 |
|  7902 |         36000 |
+-------+---------------+
13 rows in set (0.000 sec)



#9. Display the names of all employees working as clerks and
drawing a salary more than 3,000.

MariaDB [comp_db]> SELECT ename from emp
    -> WHERE job = 'clerk'
    -> AND sal > 3000;
Empty set (0.000 sec)



10.
MariaDB [comp_db]> SELECT ename from emp
    -> WHERE job IN ('clerk', 'salesman', 'analyst')
    -> AND sal > 3000;
Empty set (0.000 sec)