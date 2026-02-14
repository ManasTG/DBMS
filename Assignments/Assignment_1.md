# Assignment 1  
**Date:** 01-02-2026  

## 1. Create Employee_master table with data using Employee table.  
## 2. Delete all records from Employee_master where DeptNo is 10.  
## 3. Update 10% increase in salary for DeptNo 20 in Employee_master.  
## 4. Alter SAL column to size 10,2 in Employee_master.  
## 5. Drop Employee_master table.  

---

## 1. Create Employee_master table with data using Employee table

```sql
CREATE TABLE emp_mst 
SELECT * FROM emp;
```

```sql
SELECT * FROM emp_mst;
```

---

## 2. Delete all records from Employee_master where DeptNo is 10

```sql
DELETE FROM emp_mst
WHERE deptno = 10;
```

```sql
SELECT * FROM emp_mst;
```

---

## 3. Update 10% increase in salary for DeptNo 20

```sql
UPDATE emp_mst
SET sal = sal * 1.10
WHERE deptno = 20;
```

```sql
SELECT * FROM emp_mst;
```

---

## 4. Alter SAL column to size 10,2

```sql
ALTER TABLE emp_mst
MODIFY sal DECIMAL(10,2);
```

```sql
SELECT * FROM emp_mst;
```

---

## 5. Drop Employee_master table

```sql
DROP TABLE emp_mst;
```

```sql
SELECT * FROM emp_mst;
```
