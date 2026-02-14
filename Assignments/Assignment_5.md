# ASSIGNMENT 05  
**Date:** 07-02-2026  

---

## 1. Display the total number of employees working in the company.

```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM emp;
```

```
+-----------------+
| TOTAL_EMPLOYEES |
+-----------------+
| 14              |
+-----------------+
```

---

## 2. Display the total salary being paid to all employees.

```sql
SELECT SUM(sal) AS TOTAL_SALARY
FROM emp;
```

```
+--------------+
| TOTAL_SALARY |
+--------------+
| 29025        |
+--------------+
```

---

## 3. Display the maximum salary from employee table.

```sql
SELECT MAX(sal) AS MAXIMUM_SALARY
FROM emp;
```

```
+----------------+
| MAXIMUM_SALARY |
+----------------+
| 5000           |
+----------------+
```

---

## 4. Display the minimum salary from employee table.

```sql
SELECT MIN(sal) AS MINIMUM_SALARY
FROM emp;
```

```
+----------------+
| MINIMUM_SALARY |
+----------------+
| 800            |
+----------------+
```

---

## 5. Display the average salary from employee table.

```sql
SELECT AVG(sal) AS AVERAGE_SALARY
FROM emp;
```

```
+----------------+
| AVERAGE_SALARY |
+----------------+
| 2073.2143      |
+----------------+
```

---

## 6. Display the maximum salary being paid to clerk.

```sql
SELECT MAX(sal) AS MAX_SAL_CLERK
FROM emp
WHERE job = 'CLERK';
```

```
+----------------+
| MAX_SAL_CLERK  |
+----------------+
| 1300           |
+----------------+
```

---

## 7. Display the maximum salary being paid in dept no 20.

```sql
SELECT MAX(sal) AS MAX_SAL_DEPT20
FROM emp
WHERE deptno = 20;
```

```
+------------------+
| MAX_SAL_DEPT20   |
+------------------+
| 5000             |
+------------------+
```

---

## 8. Display the minimum salary paid to any salesman.

```sql
SELECT MIN(sal) AS MIN_SAL_SALESMAN
FROM emp
WHERE job = 'SALESMAN';
```

```
+-------------------+
| MIN_SAL_SALESMAN  |
+-------------------+
| 1250              |
+-------------------+
```

---

## 9. Display the average salary drawn by managers.

```sql
SELECT AVG(sal) AS AVG_SAL_MANAGERS
FROM emp
WHERE job = 'MANAGER';
```

```
+--------------------+
| AVG_SAL_MANAGERS   |
+--------------------+
| 2758.3333          |
+--------------------+
```

---

## 10. Display the total salary drawn by analyst working in dept no 40.

```sql
SELECT SUM(sal) AS TOTAL_SAL_ANALYST
FROM emp
WHERE job = 'ANALYST' AND deptno = 40;
```

```
+--------------------+
| TOTAL_SAL_ANALYST  |
+--------------------+
| 3000               |
+--------------------+
```

---

## 11. Display the names of the employee in Uppercase.

```sql
SELECT UPPER(ename) AS UPPERCASE_NAME
FROM emp;
```

```
SMITH
ALLEN
WARD
JONES
MARTIN
BLAKE
CLARK
SCOTT
KING
TURNER
ADAMS
JAMES
FORD
MILLER
```

---

## 12. Display the names of the employee in Lowercase.

```sql
SELECT LOWER(ename) AS LOWERCASE_NAME
FROM emp;
```

```
smith
allen
ward
jones
martin
blake
clark
scott
king
turner
adams
james
ford
miller
```

---

## 13. Display the names of the employee in Proper case.

```sql
SELECT CONCAT(
       UPPER(SUBSTRING(ename,1,1)),
       LOWER(SUBSTRING(ename,2))
) AS PROPERCASE_NAME
FROM emp;
```

```
Smith
Allen
Ward
Jones
Martin
Blake
Clark
Scott
King
Turner
Adams
James
Ford
Miller
```

---

## 14. Display the length of your name using appropriate function.

```sql
SELECT LENGTH('Manas') AS LENGTH_OF_NAME;
```

```
+----------------+
| LENGTH_OF_NAME |
+----------------+
| 5              |
+----------------+
```

---

## 15. Display the length of all the employee names.

```sql
SELECT ename, LENGTH(ename) AS NAME_LENGTH
FROM emp;
```

```
+--------+-------------+
| ename  | NAME_LENGTH |
+--------+-------------+
| SMITH  | 5           |
| ALLEN  | 5           |
| WARD   | 4           |
| JONES  | 5           |
| MARTIN | 6           |
| BLAKE  | 5           |
| CLARK  | 5           |
| SCOTT  | 5           |
| KING   | 4           |
| TURNER | 6           |
| ADAMS  | 5           |
| JAMES  | 5           |
| FORD   | 4           |
| MILLER | 6           |
+--------+-------------+
```
