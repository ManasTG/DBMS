# ASSIGNMENT 4  
**Date:** 06-02-2026  

---

## 1. Display the list of employees who have joined the company before 30th June 1980 or after 31st Dec 1981.

```sql
SELECT ename, hiredate
FROM emp
WHERE hiredate < '1980-06-30'
OR hiredate > '1981-12-31';
```

```
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| SCOTT  | 1982-12-09 |
| ADAMS  | 1983-01-12 |
| MILLER | 1982-01-23 |
+--------+------------+
```

---

## 2. Display the names of employees whose names have second alphabet A.

```sql
SELECT ename
FROM emp
WHERE ename LIKE '_A%';
```

```
+--------+
| ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
```

---

## 3. Display the names of employees whose name is exactly five characters in length.

```sql
SELECT ename
FROM emp
WHERE LENGTH(ename) = 5;
```

```
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
```

---

## 4. Display the names of employees whose names have second alphabet A (Using SUBSTRING).

```sql
SELECT ename
FROM emp
WHERE SUBSTRING(ename, 2, 1) = 'A';
```

```
+--------+
| ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
```

---

## 5. Display the names of employees who are not working as salesman, clerk or analyst.

```sql
SELECT ename, job
FROM emp
WHERE job NOT IN ('SALESMAN','CLERK','ANALYST');
```

```
+-------+-----------+
| ename | job       |
+-------+-----------+
| JONES | MANAGER   |
| BLAKE | MANAGER   |
| CLARK | MANAGER   |
| KING  | PRESIDENT |
+-------+-----------+
```

---

## 6. Display the name of the employee along with their annual salary (sal * 12). The highest salary should appear first.

```sql
SELECT ename, sal * 12 AS ANNUAL_SALARY
FROM emp
ORDER BY sal * 12 DESC;
```

```
+--------+---------------+
| ename  | ANNUAL_SALARY |
+--------+---------------+
| KING   | 60000         |
| SCOTT  | 36000         |
| FORD   | 36000         |
| JONES  | 35700         |
| BLAKE  | 34200         |
| CLARK  | 29400         |
| ALLEN  | 19200         |
| TURNER | 18000         |
| MILLER | 15600         |
| MARTIN | 15000         |
| WARD   | 15000         |
| ADAMS  | 13200         |
| JAMES  | 11400         |
| SMITH  | 9600          |
+--------+---------------+
```

---

## 7. Display name, sal, hra, da, pf, total salary for each employee.  
(HRA = 15% of sal, DA = 10% of sal, PF = 5% of sal)  
Total Salary = (sal + hra + da) - pf

```sql
SELECT ename,
       sal,
       sal * 0.15 AS HRA,
       sal * 0.10 AS DA,
       sal * 0.05 AS PF,
       (sal +
