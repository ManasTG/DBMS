# Assignment 07
**Date:** 14-02-2026  

---

## 1. Compute the number of days remaining in this year.

```sql
SELECT DATEDIFF('2027-01-01', CURDATE()) AS 'Days Remaining';
```

---

## 2. Find the highest and lowest salaries and the difference between them.

```sql
SELECT 
    MAX(sal) AS 'Max Salary',
    MIN(sal) AS 'Min Salary',
    MAX(sal) - MIN(sal) AS 'Difference'
FROM emp;
```

---

## 3. List employees whose commission is greater than 25% of their salaries.

```sql
SELECT ename, sal, comm
FROM emp
WHERE comm > (sal * 0.25);
```

---

## 4. Make a query that displays salary in dollar format.

```sql
SELECT 
    ename,
    CONCAT('$', FORMAT(sal, 2)) AS 'Salary'
FROM emp;
```

---

## 5. Create a matrix query to display the job, salary based on department number, and total salary.

```sql
SELECT 
    job,
    SUM(CASE WHEN deptno = 10 THEN sal ELSE 0 END) AS 'Dept 10',
    SUM(CASE WHEN deptno = 20 THEN sal ELSE 0 END) AS 'Dept 20',
    SUM(CASE WHEN deptno = 30 THEN sal ELSE 0 END) AS 'Dept 30',
    SUM(CASE WHEN deptno = 40 THEN sal ELSE 0 END) AS 'Dept 40',
    SUM(sal) AS 'Total Salary'
FROM emp
GROUP BY job;
```

---

## 6. Display total employees and number hired in 1980, 1981, 1982 and 1983.

```sql
SELECT 
    COUNT(*) AS 'Total Employees',
    SUM(CASE WHEN YEAR(hiredate) = 1980 THEN 1 ELSE 0 END) AS '1980',
    SUM(CASE WHEN YEAR(hiredate) = 1981 THEN 1 ELSE 0 END) AS '1981',
    SUM(CASE WHEN YEAR(hiredate) = 1982 THEN 1 ELSE 0 END) AS '1982',
    SUM(CASE WHEN YEAR(hiredate) = 1983 THEN 1 ELSE 0 END) AS '1983'
FROM emp;
```

---

## 7. Query to get the last Sunday of any month (current month).

```sql
SELECT 
    DATE_SUB(
        LAST_DAY(CURDATE()),
        INTERVAL (DAYOFWEEK(LAST_DAY(CURDATE())) - 1) DAY
    ) AS 'Last Sunday of Month';
```

---

## 8. Display department numbers and total employees in each department.

```sql
SELECT 
    deptno, 
    COUNT(*) AS 'Total Employees'
FROM emp
GROUP BY deptno;
```

---

## 9. Display various jobs and total employees in each job group.

```sql
SELECT 
    job, 
    COUNT(*) AS 'Total Employees'
FROM emp
GROUP BY job;
```

---

## 10. Display department numbers and total salary for each department.

```sql
SELECT 
    deptno, 
    SUM(sal) AS 'Total Salary'
FROM emp
GROUP BY deptno;
```