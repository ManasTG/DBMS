# Assignment 3  
**Date:** 31-01-2026  

---

## 1. List all employees and jobs in Department 30 in descending order by salary.

```sql
SELECT ename, job 
FROM emp
WHERE deptno = 30
ORDER BY sal DESC;
```

```
+--------+----------+
| ename  | job      |
+--------+----------+
| BLAKE  | MANAGER  |
| ALLEN  | SALESMAN |
| TURNER | SALESMAN |
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| JAMES  | CLERK    |
+--------+----------+
```

---

## 2. List job and Department Number of employees whose name are five letters long, begin with “A” and end with “N”.

```sql
SELECT job, deptno
FROM emp
WHERE ename LIKE 'A___N';
```

```
+----------+--------+
| job      | deptno |
+----------+--------+
| SALESMAN | 30     |
+----------+--------+
```

---

## 3. Display the name of employees whose name starts with alphabet S.

```sql
SELECT ename 
FROM emp
WHERE ename LIKE 'S%';
```

```
+-------+
| ename |
+-------+
| SMITH |
| SCOTT |
+-------+
```

---

## 4. Display the names of employees whose name ends with alphabet S.

```sql
SELECT ename 
FROM emp
WHERE ename LIKE '%S';
```

```
+-------+
| ename |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
```

---

## 5. Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks, salesman or analyst.

```sql
SELECT ename 
FROM emp
WHERE deptno IN (10,20,40)
OR job IN ('CLERK','SALESMAN','ANALYST');
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
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
```

---

## 6. Display employee number and names for employees who earn commission.

```sql
SELECT empno, ename 
FROM emp
WHERE comm IS NOT NULL AND comm != 0;
```

```
+-------+--------+
| empno | ename  |
+-------+--------+
| 7499  | ALLEN  |
| 7521  | WARD   |
| 7654  | MARTIN |
+-------+--------+
```

---

## 7. Display employee number and total salary for each employee.

```sql
SELECT empno, sal + IFNULL(comm, 0) AS SALARY
FROM emp;
```

```
+-------+--------+
| empno | SALARY |
+-------+--------+
| 7369  | 800    |
| 7499  | 1900   |
| 7521  | 1550   |
| 7566  | 2975   |
| 7654  | 2650   |
| 7698  | 2850   |
| 7782  | 2450   |
| 7788  | 3000   |
| 7839  | 5000   |
| 7844  | 1500   |
| 7876  | 1100   |
| 7900  | 950    |
| 7902  | 3000   |
| 7934  | 1300   |
+-------+--------+
```

---

## 8. Display employee number and annual salary for each employee.

```sql
SELECT empno, sal * 12 AS ANNUAL_SALARY
FROM emp;
```

```
+-------+---------------+
| empno | ANNUAL_SALARY |
+-------+---------------+
| 7369  | 9600          |
| 7499  | 19200         |
| 7521  | 15000         |
| 7566  | 35700         |
| 7654  | 15000         |
| 7698  | 34200         |
| 7782  | 29400         |
| 7788  | 36000         |
| 7839  | 60000         |
| 7844  | 18000         |
| 7876  | 13200         |
| 7900  | 11400         |
| 7902  | 36000         |
| 7934  | 15600         |
+-------+---------------+
```

---

## 9. Display the names of all employees working as clerks and drawing a salary more than 3,000.

```sql
SELECT ename 
FROM emp
WHERE job = 'CLERK'
AND sal > 3000;
```

```
Empty set
```

---

## 10. Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3,000.

```sql
SELECT ename 
FROM emp
WHERE job IN ('CLERK','SALESMAN','ANALYST')
AND sal > 3000;
```

```
Empty set
```
