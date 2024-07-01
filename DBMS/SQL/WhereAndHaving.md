The `WHERE` and `HAVING` clauses in SQL are both used to filter data, but they serve different purposes and are used in different contexts. Here's a detailed explanation of each:

### `WHERE` Clause
- **Purpose**: The `WHERE` clause is used to filter rows before any groupings are made.
- **Context**: It is used to filter records from a table or view.
- **Usage**: It can be used with `SELECT`, `UPDATE`, `DELETE`, etc.
- **When**: It filters rows before any aggregation (like `GROUP BY`).

**Example**:
```sql
SELECT * FROM employees
WHERE salary > 50000;
```
This query selects all employees with a salary greater than 50,000.

### `HAVING` Clause
- **Purpose**: The `HAVING` clause is used to filter groups after the `GROUP BY` clause has been applied.
- **Context**: It is used to filter records from the result set of a `GROUP BY` operation.
- **Usage**: It is used only with `SELECT` statements.
- **When**: It filters aggregated results.

**Example**:
```sql
SELECT department, COUNT(*) AS num_employees
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```
This query groups employees by department and then selects only those departments that have more than 5 employees.

### Key Differences
1. **Stage of Filtering**:
   - `WHERE` filters rows before any grouping is done.
   - `HAVING` filters groups after the `GROUP BY` operation has been performed.

2. **Use with Aggregates**:
   - `WHERE` cannot be used with aggregate functions like `SUM()`, `COUNT()`, `AVG()`, etc.
   - `HAVING` is used specifically for conditions involving aggregate functions.

### Combined Usage
You can use both `WHERE` and `HAVING` in the same query, where `WHERE` filters rows before grouping and `HAVING` filters the groups formed after `GROUP BY`.

**Example**:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING AVG(salary) > 50000;
```
In this query:
- `WHERE salary > 30000` filters rows to include only those employees with a salary greater than 30,000.
- `GROUP BY department` groups the remaining rows by department.
- `HAVING AVG(salary) > 50000` filters those groups to include only departments where the average salary is greater than 50,000.
