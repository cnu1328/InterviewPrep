### SQL Joins Overview

SQL joins are used to combine rows from two or more tables based on a related column between them. Here is a detailed explanation of each type of join, including real-time examples and SQL queries.

### Types of Joins

1. **INNER JOIN**
2. **LEFT JOIN (or LEFT OUTER JOIN)**
3. **RIGHT JOIN (or RIGHT OUTER JOIN)**
4. **FULL JOIN (or FULL OUTER JOIN)**
5. **CROSS JOIN**
6. **SELF JOIN**

### Example Scenario

Let's use two tables for our examples:

**Employees Table:**
| EmployeeID | Name      | DepartmentID |
|------------|-----------|--------------|
| 1          | John      | 1            |
| 2          | Jane      | 2            |
| 3          | Mike      | 1            |
| 4          | Alice     | 3            |

**Departments Table:**
| DepartmentID | DepartmentName |
|--------------|----------------|
| 1            | HR             |
| 2            | IT             |
| 3            | Finance        |
| 4            | Marketing      |

### 1. INNER JOIN

**Description:** Returns records that have matching values in both tables.

**SQL Query:**
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| Name  | DepartmentName |
|-------|----------------|
| John  | HR             |
| Mike  | HR             |
| Jane  | IT             |
| Alice | Finance        |

**Record Count:** The number of records will be equal to the number of matching records between the two tables, which is at most the minimum of `n` and `m` records. In general, it depends on the specific matching criteria.

### 2. LEFT JOIN (or LEFT OUTER JOIN)

**Description:** Returns all records from the left table and the matched records from the right table. The result is NULL from the right side if there is no match.

**SQL Query:**
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| Name  | DepartmentName |
|-------|----------------|
| John  | HR             |
| Mike  | HR             |
| Jane  | IT             |
| Alice | Finance        |

**Record Count:** At least `n` records (all records from Table 1), and at most `n * m` if each row from Table 1 matches multiple rows in Table 2.

### 3. RIGHT JOIN (or RIGHT OUTER JOIN)

**Description:** Returns all records from the right table and the matched records from the left table. The result is NULL from the left side if there is no match.

**SQL Query:**
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| Name  | DepartmentName |
|-------|----------------|
| John  | HR             |
| Mike  | HR             |
| Jane  | IT             |
| Alice | Finance        |
| NULL  | Marketing      |


**Record Count:** At least `m` records (all records from Table 2), and at most `n * m` if each row from Table 2 matches multiple rows in Table 1.

### 4. FULL JOIN (or FULL OUTER JOIN)

**Description:** Returns all records when there is a match in either left or right table records.

**SQL Query:**
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
FULL JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

**Result:**
| Name  | DepartmentName |
|-------|----------------|
| John  | HR             |
| Mike  | HR             |
| Jane  | IT             |
| Alice | Finance        |
| NULL  | Marketing      |


**Record Count:** Up to `n + m` records if there are no matching records, and at least the maximum of `n` or `m`.

### 5. CROSS JOIN

**Description:** Returns the Cartesian product of the two tables.

**SQL Query:**
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
CROSS JOIN Departments;
```

**Result:**
| Name  | DepartmentName |
|-------|----------------|
| John  | HR             |
| John  | IT             |
| John  | Finance        |
| John  | Marketing      |
| Jane  | HR             |
| Jane  | IT             |
| Jane  | Finance        |
| Jane  | Marketing      |
| Mike  | HR             |
| Mike  | IT             |
| Mike  | Finance        |
| Mike  | Marketing      |
| Alice | HR             |
| Alice | IT             |
| Alice | Finance        |
| Alice | Marketing      |


**Record Count:** `n * m` records.

### 6. SELF JOIN

**Description:** A self join is a regular join but the table is joined with itself.

**SQL Query:**
```sql
SELECT A.Name AS Employee1, B.Name AS Employee2
FROM Employees A, Employees B
WHERE A.DepartmentID = B.DepartmentID
AND A.EmployeeID <> B.EmployeeID;
```

**Result:**
| Employee1 | Employee2 |
|-----------|-----------|
| John      | Mike      |
| Mike      | John      |

**Record Count:** Similar to an `INNER JOIN`, the number of records will depend on the number of matching records within the same table, which is at most `n`.


### Summary

- **INNER JOIN:** At most min(`n`, `m`) records.
- **LEFT JOIN:** At least `n` records, at most `n * m` records.
- **RIGHT JOIN:** At least `m` records, at most `n * m` records.
- **FULL JOIN:** At least max(`n`, `m`), up to `n + m` records.
- **CROSS JOIN:** `n * m` records.
- **SELF JOIN:** Depends on the specific matching criteria within the same table, similar to `INNER JOIN`.
