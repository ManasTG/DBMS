# Exercise 02 
**Date- 26-03-2026**

---

## 1. Find the movies with a row id of 6

```sql
SELECT Title FROM movies
WHERE id = 6;
```

---

## 2. Find the movies released in the years between 2000 and 2010

```sql
SELECT Title FROM movies
WHERE year BETWEEN 2000 AND 2010;
```

---

## 3. Find the movies not released in the years between 2000 and 2010

```sql
SELECT Title FROM movies
WHERE year NOT BETWEEN 2000 AND 2010;
```

---

## 4. Find the first 5 Pixar movies and their release year

```sql
SELECT Title, Year FROM movies
WHERE id BETWEEN 1 AND 5;
```

---
