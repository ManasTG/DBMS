# ASSIGNMENT 06  
**Date:** 13-02-2026  

---

## 1. Display empno, ename, deptno with department names instead of numbers (using CASE function).

```sql
SELECT empno, ename,
       CASE deptno
           WHEN 10 THEN 'RESEARCH'
           WHEN 20 THEN 'ACCOUNTING'
           WHEN 30 THEN 'SALES'
           WHEN 40 THEN 'OPERATIONS'
       END AS DEPT_NAMES
FROM emp;
```

```
+-------+--------+------------+
| empno | ename  | DEPT_NAMES |
+-------+--------+------------+
| 7369  | SMITH  | ACCOUNTING |
| 7499  | ALLEN  | SALES      |
| 7521  | WARD   | SALES      |
| 7566  | JONES  | ACCOUNTING |
| 7654  | MARTIN | SALES      |
| 7698  | BLAKE  | SALES      |
| 7782  | CLARK  | ACCOUNTING |
| 7788  | SCOTT  | OPERATIONS |
| 7839  | KING   | ACCOUNTING |
| 7844  | TURNER | SALES      |
| 7876  | ADAMS  | ACCOUNTING |
| 7900  | JAMES  | SALES      |
| 7902  | FORD   | ACCOUNTING |
| 7934  | MILLER | RESEARCH   |
+-------+--------+------------+
```

---

## 2. Display your age in days.

```sql
SELECT DATEDIFF(CURDATE(), '2006-07-02') AS DOB_IN_DAYS;
```

```
+-------------+
| DOB_IN_DAYS |
+-------------+
| 7166        |
+-------------+
```

---

## 3. Display your age in months.

```sql
SELECT TIMESTAMPDIFF(MONTH, '2006-07-02', CURDATE()) AS DOB_IN_MONTHS;
```

```
+---------------+
| DOB_IN_MONTHS |
+---------------+
| 235           |
+---------------+
```

---

## 4. Display the current date in format "15th August Friday 1997" (date formatting only).

```sql
SELECT DATE_FORMAT(CURDATE(), "%D %M %W %Y") AS CURRENT_DATE;
```

```
+---------------------------+
| CURRENT_DATE              |
+---------------------------+
| 13th February Friday 2026 |
+---------------------------+
```

---

## 5. Display “ename has joined the company on hiredate” for each employee.

```sql
SELECT CONCAT(
       ename,
       ' has joined the company on ',
       DATE_FORMAT(hiredate, "%D %M %W %Y")
) AS REQUIRED_FORMAT
FROM emp;
```

```
+--------------------------------------------------------------+
| REQUIRED_FORMAT                                              |
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
```

---

## 6. Scott joined the company on Wednesday 13th August 1990  

- Covered in Query 5 formatting.

---

## 7. Find the date for nearest Saturday after current date.

```sql
SELECT DATE_ADD(CURDATE(), INTERVAL (5 - WEEKDAY(CURDATE())) DAY) AS NEXT_SATURDAY;
```

```
+---------------+
| NEXT_SATURDAY |
+---------------+
| 2026-02-14    |
+---------------+
```

---

## 8. Display current time.

```sql
SELECT CURTIME() AS CURRENT_TIME;
```

```
+--------------+
| CURRENT_TIME |
+--------------+
| 13:18:04     |
+--------------+
```

---

## 9. Display the date three months before the current date.

```sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS DATE_BEFORE_3_MONTHS;
```

```
+----------------------+
| DATE_BEFORE_3_MONTHS |
+----------------------+
| 2025-11-13           |
+----------------------+
```

---

## 10. Display employees who joined in December.

```sql
SELECT ename, hiredate
FROM emp
WHERE MONTH(hiredate) = 12;
```

```
+-------+------------+
| ename | hiredate   |
+-------+------------+
| SMITH | 1980-12-17 |
| SCOTT | 1982-12-09 |
| JAMES | 1981-12-03 |
| FORD  | 1981-12-03 |
+-------+------------+
```

---

## 11. Employees whose first 2 characters of year from hiredate = last 2 digits of salary.

```sql
SELECT ename, hiredate, sal
FROM emp
WHERE LEFT(DATE_FORMAT(hiredate, "%Y"), 2) = RIGHT(sal, 2);
```

```
Empty set
```

---

## 12. Employees whose 10% of salary = year of joining.

```sql
SELECT ename, sal, hiredate
FROM emp
WHERE (sal * 0.10) = YEAR(hiredate);
```

```
Empty set
```

---

## 13. Employees who joined after 15th of the month.

```sql
SELECT ename, hiredate
FROM emp
WHERE DAY(hiredate) > 15;
```

```
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
```

---

## 14. Employees who joined before 15th of the month.

```sql
SELECT ename, hiredate
FROM emp
WHERE DAY(hiredate) < 15;
```

```
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
```

---

## 15. Employees whose joining date and deptno are available.

```sql
SELECT ename, hiredate, deptno
FROM emp
WHERE deptno IS NOT NULL
AND hiredate IS NOT NULL;
```

```
+--------+------------+--------+
| ename  | hiredate   | deptno |
+--------+------------+--------+
| SMITH  | 1980-12-17 | 20     |
| ALLEN  | 1981-02-20 | 30     |
| WARD   | 1981-02-22 | 30     |
| JONES  | 1981-04-02 | 20     |
| MARTIN | 1981-09-28 | 30     |
| BLAKE  | 1981-05-01 | 30     |
| CLARK  | 1981-06-09 | 20     |
| SCOTT  | 1982-12-09 | 40     |
| KING   | 1981-11-17 | 20     |
| TURNER | 1981-09-08 | 30     |
| ADAMS  | 1983-01-12 | 20     |
| JAMES  | 1981-12-03 | 30     |
| FORD   | 1981-12-03 | 20     |
| MILLER | 1982-01-23 | 10     |
+--------+------------+--------+
```

