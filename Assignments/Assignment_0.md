##Assignment_0
##01-02-2026

#Creation of comp_db database and emp and dept table with there values inserted
1.

MariaDB [(none)]> drop database comp_db;
Query OK, 3 rows affected (0.035 sec)

MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
6 rows in set (0.001 sec)

2.
MariaDB [(none)]> CREATE DATABASE comp_db;
Query OK, 1 row affected (0.001 sec)

MariaDB [(none)]> SHOW DATABASES;
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
7 rows in set (0.001 sec)

MariaDB [(none)]> CREATE TABLE dept(
    -> deptno INT(2) Primary Key,
    -> dname VARCHAR(15) NOT NULL);
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> USE comp_db;
Database changed
MariaDB [comp_db]> CREATE TABLE dept(
    -> deptno INT(2) Primary Key,
    -> dname VARCHAR(15) NOT NULL);
Query OK, 0 rows affected (0.015 sec)



MariaDB [comp_db]> DESC dept;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(2)      | NO   | PRI | NULL    |       |
| dname  | varchar(15) | NO   |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.016 sec)




MariaDB [comp_db]> INSERT INTO dept VALUES
    -> (10, 'RESEARCH'),
    -> (20, 'ACCOUNTING'),
    -> (30, 'SALES'),
    -> (40, 'OPERATIONS');
Query OK, 4 rows affected (0.006 sec)
Records: 4  Duplicates: 0  Warnings: 0





MariaDB [comp_db]> SELECT* FROM dept;
+--------+------------+
| deptno | dname      |
+--------+------------+
|     10 | RESEARCH   |
|     20 | ACCOUNTING |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.000 sec)



MariaDB [comp_db]> CREATE TABLE emp(
    -> empno INT(4) Primary Key,
    -> ename VARCHAR(20) NOT NULL,
    -> job VARCHAR(20),
    -> mgr INT(4),
    -> hiredate DATE,
    -> sal INT(10),
    -> comm INT(7),
    -> deptno INT(2),
    -> FOREIGN KEY (deptno) REFERENCES dept(deptno));
Query OK, 0 rows affected (0.032 sec)



MariaDB [comp_db]> DESC emp;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(4)      | NO   | PRI | NULL    |       |
| ename    | varchar(20) | NO   |     | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| mgr      | int(4)      | YES  |     | NULL    |       |
| hiredate | date        | YES  |     | NULL    |       |
| sal      | int(10)     | YES  |     | NULL    |       |
| comm     | int(7)      | YES  |     | NULL    |       |
| deptno   | int(2)      | YES  | MUL | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.018 sec)



MariaDB [comp_db]> INSERT INTO emp VALUES
    -> (7369, 'SMITH', 'CLERK', 7902, '1980-12-17', 800,  NULL, 20),
    -> (7499, 'ALLEN', 'SALESMAN', 7698, '1981-02-20', 1600, 300, 30),
    -> (7521, 'WARD', 'SALESMAN', 7698, '1981-02-22', 1250, 300, 30),
    -> (7566, 'JONES', 'MANAGER', 7839, '1981-04-02', 2975, NULL, 20),
    -> (7654, 'MARTIN', 'SALESMAN', 7698, '1981-09-28', 1250, 1400, 30),
    -> (7698, 'BLAKE', 'MANAGER', 7839, '1981-05-01', 2850, NULL, 30),
    -> (7782, 'CLARK', 'MANAGER', 7839, '1981-06-09', 2450, NULL, 20),
    -> (7788, 'SCOTT', 'ANALYST', 7566, '1982-12-09', 3000, NULL, 20),
    -> (7839, 'KING', 'PRESIDENT', NULL, '1981-11-17', 5000, NULL, 20),
    -> (7844, 'TURNER', 'SALESMAN', 7698, '1981-09-08', 1500, 0,    30),
    -> (7876, 'ADAMS', 'CLERK', 7788, '1983-01-12', 1100, NULL, 20),
    -> (7900, 'JAMES', 'CLERK', 7698, '1981-12-03', 950,  NULL, 30),
    -> (7902, 'FORD', 'ANALYST', 7566, '1981-12-03', 3000, NULL, 20),
    -> (7934, 'MILLER', 'CLERK', 7782, '1982-01-23', 1300, NULL, 10);
Query OK, 14 rows affected (0.009 sec)
Records: 14  Duplicates: 0  Warnings: 0

MariaDB [comp_db]> SELECT* FROM emp;
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
14 rows in set (0.000 sec)