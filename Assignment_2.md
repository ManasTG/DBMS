SELECT DISTINCT job
    -> FROM emp;

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| comp_db            |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
7 rows in set (0.005 sec)

MariaDB [(none)]> use comp_db;
Database changed
MariaDB [comp_db]> select* from emp;
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
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.005 sec)

MariaDB [comp_db]> show tables;
+-------------------+
| Tables_in_comp_db |
+-------------------+
| dept              |
| emp               |
| emp_mst           |
+-------------------+
3 rows in set (0.001 sec)

MariaDB [comp_db]> SELECT DISTINCT job
    -> FROM emp;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.001 sec)

MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE deptno = 30;
+-------+--------+----------+------+------------+------+------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+--------+----------+------+------------+------+------+--------+
6 rows in set (0.001 sec)

MariaDB [comp_db]> SELECT JOB FROM EMP
    -> WHERE dept > 20;
ERROR 1054 (42S22): Unknown column 'dept' in 'where clause'
MariaDB [comp_db]> SELECT JOB FROM EMP
    -> WHERE deptno > 20;
+----------+
| JOB      |
+----------+
| SALESMAN |
| SALESMAN |
| SALESMAN |
| MANAGER  |
| ANALYST  |
| SALESMAN |
| CLERK    |
+----------+
7 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = MANAGER AND CLERK, AND deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ' AND deptno = 30' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = MANAGER AND CLERK AND deptno = 30;
ERROR 1054 (42S22): Unknown column 'MANAGER' in 'where clause'
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = MANAGER CLERK AND deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'CLERK AND deptno = 30' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = MANAGER, CLERK AND deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ' CLERK AND deptno = 30' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = ('MANAGER", "CLERK") AND deptno = 30;
    '> '
    -> "
    "> ;
    "> ;
    "> "
    -> l
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'l' at line 4
MariaDB [comp_db]> WHERE job = MANAGER, CLERK AND deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'WHERE job = MANAGER, CLERK AND deptno = 30' at line 1
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = ('Manager', 'clerk'), deptno = 3-;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ' deptno = 3-' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = ('Manager', 'clerk'), deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ' deptno = 30' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = ('Manager', 'clerk'), deptno = 30;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ' deptno = 30' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job IN ('Manager', 'clerk')
    -> AND deptno = 30;
+-------+-------+---------+------+------------+------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+-------+---------+------+------------+------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT empno, ename, job
    -> FROM emp
    -> WHERE job = CLERK;
ERROR 1054 (42S22): Unknown column 'CLERK' in 'where clause'
MariaDB [comp_db]> SELECT empno, ename, job
    -> FROM emp
    -> WHERE job = 'CLERK';
+-------+-------+-------+
| empno | ename | job   |
+-------+-------+-------+
|  7369 | SMITH | CLERK |
|  7876 | ADAMS | CLERK |
|  7900 | JAMES | CLERK |
+-------+-------+-------+
3 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE job = 'Manager'
    -> AND deptno != 30;
+-------+-------+---------+------+------------+------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+-------+---------+------+------------+------+------+--------+
|  7566 | JONES | MANAGER | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 1981-06-09 | 2450 | NULL |     20 |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE JOB NOTIN ('manager', 'clerk')
    -> AND deptno = 10;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'NOTIN ('manager', 'clerk')
AND deptno = 10' at line 2
MariaDB [comp_db]> SELECT* FROM emp
    -> WHERE JOB NOT IN ('manager', 'clerk')
    -> AND deptno = 10;
Empty set (0.000 sec)

MariaDB [comp_db]> SELECT ename, job
    -> WHERE sal BETWEEN 1200 AND 1400;
ERROR 1054 (42S22): Unknown column 'ename' in 'field list'
MariaDB [comp_db]> SELECT ename, job from emp
    -> WHERE sal BETWEEN 1200 AND 1400;
+--------+----------+
| ename  | job      |
+--------+----------+
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
+--------+----------+
2 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT ename, depno
    -> WHERE job IN ('clerk', 'analyst', 'salesman');
ERROR 1054 (42S22): Unknown column 'ename' in 'field list'
MariaDB [comp_db]> SELECT ename, depno FROM emp
    -> WHERE job IN ('clerk', 'analyst', 'salesman');
ERROR 1054 (42S22): Unknown column 'depno' in 'field list'
MariaDB [comp_db]> SELECT ename, deptno FROM emp
    -> WHERE job IN ('clerk', 'analyst', 'salesman');
+--------+--------+
| ename  | deptno |
+--------+--------+
| SMITH  |     20 |
| ALLEN  |     30 |
| WARD   |     30 |
| MARTIN |     30 |
| SCOTT  |     40 |
| TURNER |     30 |
| ADAMS  |     20 |
| JAMES  |     30 |
| FORD   |     20 |
+--------+--------+
9 rows in set (0.000 sec)

MariaDB [comp_db]> SELECT ename, deptno
    -> FROM emp
    -> WHERE ename = M%;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 3
MariaDB [comp_db]> SELECT ename, deptno
    -> FROM emp
    -> WHERE ename M%;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'M%' at line 3
MariaDB [comp_db]> SELECT ename, deptno
    -> FROM emp
    -> WHERE ename LIKE M%;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 3
MariaDB [comp_db]> SELECT ename, deptno
    -> FROM emp
    -> WHERE ename LIKE 'M%';
+--------+--------+
| ename  | deptno |
+--------+--------+
| MARTIN |     30 |
+--------+--------+
1 row in set (0.000 sec)

MariaDB [comp_db]>
yes