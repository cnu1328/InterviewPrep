### SQL Operators

SQL operators are symbols or keywords that are used to perform operations on data in a database. Here, we'll explore various SQL operators with examples and provide detailed explanations for each.

#### 1. **UNION and UNION ALL**

**Definition:** Combines the result sets of two or more `SELECT` queries. `UNION` removes duplicate rows, while `UNION ALL` includes duplicates.

**Example:**

```sql
SELECT name, city FROM customers
UNION
SELECT name, city FROM suppliers;
```

**Explanation:** This query combines rows from the `customers` and `suppliers` tables, returning unique name and city pairs.

**Tables:**

**customers**
| name | city   |
|------|--------|
| John | Boston |
| Jane | NY     |

**suppliers**
| name  | city   |
|-------|--------|
| Tom   | Boston |
| Jane  | NY     |
| Alice | LA     |

**Result with UNION:**
| name  | city   |
|-------|--------|
| John  | Boston |
| Jane  | NY     |
| Tom   | Boston |
| Alice | LA     |

**Result with UNION ALL:**
| name  | city   |
|-------|--------|
| John  | Boston |
| Jane  | NY     |
| Tom   | Boston |
| Jane  | NY     |
| Alice | LA     |

#### 2. **INTERSECT**

**Definition:** Returns the intersection of two result sets, i.e., rows that are common to both queries.

**Example:**

```sql
SELECT name, city FROM customers
INTERSECT
SELECT name, city FROM suppliers;
```

**Explanation:** This query returns rows that appear in both the `customers` and `suppliers` tables.

**Result:**
| name | city |
|------|------|
| Jane | NY   |

#### 3. **MINUS (EXCEPT)**

**Definition:** Returns rows from the first query that are not in the second query.

**Example:**

```sql
SELECT name, city FROM customers
MINUS
SELECT name, city FROM suppliers;
```

**Explanation:** This query returns rows that appear in the `customers` table but not in the `suppliers` table.

**Result:**
| name | city   |
|------|--------|
| John | Boston |

#### 4. **LIKE and NOT LIKE**

**Definition:** Used to query rows using pattern matching with `%` (any sequence of characters) and `_` (any single character).

**Example:**

```sql
SELECT name FROM customers
WHERE name LIKE 'J%';
```

**Explanation:** This query returns rows where the name starts with 'J'.

**Result:**
| name |
|------|
| John |
| Jane |

#### 5. **IN and NOT IN**

**Definition:** Checks if a value is within a specified set of values.

**Example:**

```sql
SELECT name FROM customers
WHERE city IN ('Boston', 'NY');
```

**Explanation:** This query returns rows where the city is either 'Boston' or 'NY'.

**Result:**
| name |
|------|
| John |
| Jane |

#### 6. **BETWEEN**

**Definition:** Queries rows within a range of values, inclusive.

**Example:**

```sql
SELECT name, age FROM employees
WHERE age BETWEEN 30 AND 40;
```

**Explanation:** This query returns employees whose age is between 30 and 40.

**Tables:**

**employees**
| name | age |
|------|-----|
| John | 35  |
| Jane | 28  |
| Tom  | 40  |
| Alice| 45  |

**Result:**
| name | age |
|------|-----|
| John | 35  |
| Tom  | 40  |

#### 7. **IS NULL and IS NOT NULL**

**Definition:** Checks if a value is NULL or not.

**Example:**

```sql
SELECT name FROM customers
WHERE city IS NULL;
```

**Explanation:** This query returns rows where the city is NULL.

**Tables:**

**customers**
| name | city   |
|------|--------|
| John | Boston |
| Jane | NY     |
| Tom  | NULL   |
| Alice| LA     |

**Result:**
| name |    
|------|
| Tom  |

### Summary of SQL Operators

- **UNION and UNION ALL:** Combine rows from two queries.
- **INTERSECT:** Return the intersection of two queries.
- **MINUS (EXCEPT):** Subtract a result set from another result set.
- **LIKE and NOT LIKE:** Query rows using pattern matching.
- **IN and NOT IN:** Query rows in a list.
- **BETWEEN:** Query rows between two values.
- **IS NULL and IS NOT NULL:** Check if values are NULL or not.

These SQL operators are fundamental for performing various data retrieval and manipulation tasks in relational databases. Understanding their usage and behavior helps in crafting efficient and effective SQL queries.