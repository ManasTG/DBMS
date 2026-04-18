# Assingment 10
# 09-04-2026

## 1. Display the names of employees from department number 10 with salary greater than that of any employee working in other departments.
## 2. Display the names of employee from department number 10 with salary greater than that of all employee working in other departments.
## 3. Display the details of employees who are in sales dept and grade is C.
## 4. Display those who are not managers and who are managers anyone.
## 5. Display those employees whose manager name is jones.
## 6. Display ename who are working in sales dept.
## 7. Display employee name, deptname, salary and comm. For those sal in between 2000 to 5000 while location is Chennai.
## 8 .Display those employees whose salary greater than his manager salary.
## 9. Display those employees who are working in the same dept where his manager is working.
## 10. Display grade and employees name for the dept no 10 or 30 but grade is not D, while joined the company before 31-dec-82.

---
# Queries


## 1. Display the names of employees from department number 10 with salary greater than that of any employee working in other departments.
```sql
SELECT ename FROM emp
WHERE deptno = 10
AND sal > ANY(
SELECT sal
FROM emp
WHERE deptno <> 10);
```
```
+--------+
| ename  |
+--------+
| MILLER |
+--------+
1 row in set
Time: 0.014s
```
---

## 2. Display the names of employee from department number 10 with salary greater than that of all employee working in other departments.
```sql
SELECT ename FROM emp
WHERE deptno = 10
AND sal > ALL(
SELECT sal 
FROM emp
WHERE deptno <> 10);
```
```
+-------+
| ename |
+-------+
+-------+
0 rows in set
Time: 0.027s
```
---

## 3. Display the details of employees who are in sales dept and grade is C.
```sql
SELECT e.*
FROM emp e
JOIN dept d ON e.deptno = d.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE d.dname = 'SALES'
AND s.grade = 'C';
```
```
+-------+--------+----------+------+------------+------+------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+----------+------+------------+------+------+--------+
| 7499  | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0    | 30     |
+-------+--------+----------+------+------------+------+------+--------+
2 rows in set
Time: 0.009s
```
---

## 4. Display those who are not managers and who are managers anyone.
```sql
SELECT *
FROM emp
WHERE empno NOT IN (
SELECT DISTINCT mgr
FROM emp
WHERE mgr IS NOT NULL);
```
```
+-------+--------+----------+------+------------+------+--------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal  | comm   | deptno |
+-------+--------+----------+------+------------+------+--------+--------+
| 7369  | SMITH  | CLERK    | 7902 | 1980-12-17 | 800  | <null> | 20     |
| 7499  | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 | 300    | 30     |
| 7521  | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 | 300    | 30     |
| 7654  | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400   | 30     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0      | 30     |
| 7876  | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1100 | <null> | 20     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | <null> | 30     |
| 7934  | MILLER | CLERK    | 7782 | 1982-01-23 | 1300 | <null> | 10     |
+-------+--------+----------+------+------------+------+--------+--------+
8 rows in set
Time: 0.016s
```
---

## 5. Display those employees whose manager name is jones.
```sql
SELECT e.ename
FROM emp e
JOIN emp m ON e.mgr = m.empno
WHERE m.ename = 'JONES';
```
```
+-------+
| ename |
+-------+
| SCOTT |
| FORD  |
+-------+
2 rows in set
Time: 0.009s
```
---

## 6. Display ename who are working in sales dept.
```sql
SELECT e.ename
FROM emp e
JOIN dept d ON e.deptno = d.deptno
WHERE d.dname = 'SALES';
```
```
+--------+
| ename  |
+--------+
| ALLEN  |
| WARD   |
| MARTIN |
| BLAKE  |
| TURNER |
| JAMES  |
+--------+
6 rows in set
Time: 0.034s
```
---

## 7. Display employee name, deptname, salary and comm. For those sal in between 2000 to 5000 while location is Chennai.
```sql
SELECT e.ename, d.dname, e.sal, e.comm
FROM emp e
JOIN dept d ON e.deptno = d.deptno
WHERE e.sal BETWEEN 2000 AND 5000
AND d.location = 'Chennai';
```
```
+-------+------------+------+--------+
| ename | dname      | sal  | comm   |
+-------+------------+------+--------+
| JONES | ACCOUNTING | 2975 | <null> |
| CLARK | ACCOUNTING | 2450 | <null> |
| KING  | ACCOUNTING | 5000 | <null> |
| FORD  | ACCOUNTING | 3000 | <null> |
+-------+------------+------+--------+
4 rows in set
Time: 0.015s
```
---

## 8 .Display those employees whose salary greater than his manager salary.
```sql
SELECT e.ename
FROM emp e
JOIN emp m ON e.mgr = m.empno
WHERE e.sal > m.sal;
```
```
+-------+
| ename |
+-------+
| SCOTT |
| FORD  |
+-------+
2 rows in set
Time: 0.034s
```

## 9. Display those employees who are working in the same dept where his manager is working.
```sql
SELECT e.ename
FROM emp e
JOIN emp m ON e.mgr = m.empno
WHERE e.deptno = m.deptno;
```
```
+--------+
| ename  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| TURNER |
| JAMES  |
| FORD   |
+--------+
9 rows in set
Time: 0.009s
```
---

## 10. Display grade and employees name for the dept no 10 or 30 but grade is not D, while joined the company before 31-dec-82.
```sql
SELECT s.grade, e.ename
FROM emp e
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE e.deptno IN (10, 30)
AND s.grade <> 'D'
AND e.hiredate < '1982-12-31';
```
```
+-------+--------+
| grade | ename  |
+-------+--------+
| C     | ALLEN  |
| B     | WARD   |
| B     | MARTIN |
| C     | TURNER |
| A     | JAMES  |
| B     | MILLER |
+-------+--------+
6 rows in set
Time: 0.012s
```
---

