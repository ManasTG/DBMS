##Assignment_2

#Perform Following Query using Employee Table. (Retrieving Data)
#1. List all distinct job in Employee.
#2. List all information about employee in Department Number 30.
#3. Find all department number with department names greater than 20.
#4. Find all information about all the managers as well as the clerks in department 30.
#5. List the Employee name, Employee numbers and department of all clerks.
#6. Find all managers not in department 30.
#7. List information about all Employees in department 10 who are not manager or clerks.
#8. Find Employees and jobs earning between 1200 and 1400.
#9. List Name and Department Number of employee who are clerks, analyst or salesman.
#10. List Name and Department Number of employee whose names began with M.able.


# Performing Queries on EMP Table (Retrieving Data)

## 1. List all distinct jobs in Employee.

MariaDB [comp_db]> SELECT DISTINCT job FROM emp;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+


## 2. List all information about employees in Department Number 30.

MariaDB [comp_db]> SELECT * FROM emp WHERE deptno = 30;
+-------+--------+----------+------+------------+------+------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+----------+------+------------+------+------+--------+
| 7499  | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 | 300  | 30     |
| 7654  | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 | 30     |
| 7698  | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+--------+----------+------+------------+------+------+--------+


## 3. Find all jobs of employees working in departments greater than 20.

MariaDB [comp_db]> SELECT job FROM emp WHERE deptno > 20;
+----------+
| job      |
+----------+
| SALESMAN |
| SALESMAN |
| SALESMAN |
| MANAGER  |
| SALESMAN |
| CLERK    |
+----------+


## 4. Find all information about managers as well as clerks in department 30.

MariaDB [comp_db]> SELECT * FROM emp
-> WHERE job IN ('MANAGER','CLERK')
-> AND deptno = 30;
+-------+-------+---------+------+------------+------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+-------+---------+------+------------+------+------+--------+
| 7698  | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7900  | JAMES | CLERK   | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+-------+---------+------+------------+------+------+--------+


## 5. List employee name, employee number and department of all clerks.

MariaDB [comp_db]> SELECT empno, ename, deptno FROM emp WHERE job = 'CLERK';
+-------+-------+--------+
| empno | ename | deptno |
+-------+-------+--------+
| 7369  | SMITH | 20     |
| 7876  | ADAMS | 20     |
| 7900  | JAMES | 30     |
+-------+-------+--------+


## 6. Find all managers not in department 30.

MariaDB [comp_db]> SELECT * FROM emp
-> WHERE job = 'MANAGER'
-> AND deptno != 30;
+-------+-------+---------+------+------------+------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+-------+---------+------+------------+------+------+--------+
| 7566  | JONES | MANAGER | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7782  | CLARK | MANAGER | 7839 | 1981-06-09 | 2450 | NULL | 20     |
+-------+-------+---------+------+------------+------+------+--------+


## 7. List employees in department 10 who are not managers or clerks.

MariaDB [comp_db]> SELECT * FROM emp
-> WHERE deptno = 10
-> AND job NOT IN ('MANAGER','CLERK');
Empty set (0.000 sec)


## 8. Find employees and jobs earning between 1200 and 1400.

MariaDB [comp_db]> SELECT ename, job
-> FROM emp
-> WHERE sal BETWEEN 1200 AND 1400;
+--------+----------+
| ename  | job      |
+--------+----------+
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
+--------+----------+


## 9. List name and department number of clerks, analysts or salesmen.

MariaDB [comp_db]> SELECT ename, deptno
-> FROM emp
-> WHERE job IN ('CLERK','ANALYST','SALESMAN');
+--------+--------+
| ename  | deptno |
+--------+--------+
| SMITH  | 20     |
| ALLEN  | 30     |
| WARD   | 30     |
| MARTIN | 30     |
| SCOTT  | 40     |
| TURNER | 30     |
| ADAMS  | 20     |
| JAMES  | 30     |
| FORD   | 20     |
+--------+--------+


## 10. List name and department number of employees whose names begin with M.

MariaDB [comp_db]> SELECT ename, deptno
-> FROM emp
-> WHERE ename LIKE 'M%';
+--------+--------+
| ename  | deptno |
+--------+--------+
| MARTIN | 30     |
+--------+--------+
