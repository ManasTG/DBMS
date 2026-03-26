# Exercise 03 
**Date- 26-03-2026**

---

## 1. Find all the Toy Story movies

```sql
SELECT title, director FROM movies 
WHERE title LIKE "Toy Story%";
```

---

## 2. Find all movies directed by John Lasseter

```sql
SELECT title FROM movies 
WHERE director = 'John Lasseter'
```

---

## 3. Find all the movies (and director) not directed by John Lasseter

```sql
SELECT title FROM movies 
WHERE director != 'John Lasseter'
```

---

## 4. Find all Wall-* movies

```sql
SELECT title FROM movies 
WHERE title like 'Wall-%';
```

---
