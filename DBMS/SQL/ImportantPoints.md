# Main Points

**SELECT CONVERT(VARCHAR, StartDate, 103) FROM Projects WHERE StartDate IS NOT NULL**

1. The CONVERT function is correctly used to convert StartDate to a VARCHAR type with a specific style (103 for dd/mm/yyyy).

**SELECT Name, TRY_CONVERT(INT, Age) AS IntegerAge FROM Employees WHERE Age IS NOT NULL;**

2. TRY_CONVERT is correctly used to attempt to convert Age to an INT type, returning NULL if the conversion fails.

3. COALESCE returns the first non-null value from the list of its arguments.

**SELECT COALESCE(Salary, 0) FROM Employees;**

4. COALESCE is correctly used to replace NULL in the Salary column with 0(returns zero value if salary is NULL).

**SELECT Name, NULLIF(Age, 30) FROM Employees WHERE Age IS NOT NULL;**

5. NULLIF is correctly used to return NULL if Age is 30; otherwise, it returns the Age.

**SELECT NVL(Salary, 'Not Provided') FROM Contractors;**

6. NVL is correctly used to replace NULL in the Salary column with 'Not Provided'.

**SELECT COALESCE(FirstName, LastName, 'Unknown') FROM Authors;** 7.

- If FirstName is not NULL, it is returned.
- If FirstName is NULL but LastName is not, LastName is returned.
- If both FirstName and LastName are NULL, 'Unknown' is returned.

**SELECT Name, NVL2(Salary, Salary \* 1.1, Salary) AS NewSalary FROM Employees;**

8. NVL2 is correctly used to return Salary \* 1.1 if Salary is not null; otherwise, it returns the NULL.

9. The CASE statement is used for creating conditional queries, similar to if-then-else logic.

**SELECT Name, CASE WHEN Age >= 18 THEN 'Adult' ELSE 'Minor' END FROM Employees;**

10. The CASE statement is correctly used to classify employees as 'Adult' or 'Minor' based on their age.

**SELECT Name, DATEDIFF(year, HireDate, GETDATE()) AS YearsWorked FROM Employees;**

- **DATEDIFF**: This function calculates the difference between two dates.
- **year**: Specifies that the difference should be measured in years.
- **HireDate**: The starting date for the calculation. This is the date the employee was hired.
- **GETDATE()**: The current date and time. This function returns the current system date and time.

**SELECT Name, DATEADD(MONTH, 6, HireDate) FROM Employees;**

12. DATEADD is correctly used to add 6 months to the HireDate.

**SELECT EXTRACT(MONTH FROM OrderDate) AS OrderMonth FROM Orders;**

13. EXTRACT is correctly used to get the month part from the OrderDate.

14. ROUND(Salary, 2): Rounds the Salary to two decimal places.
15. ROUND(Salary, -2): Rounds the Salary to the nearest hundred.(1243 = 1200, 1578 = 1600)

16. LOG( `LOG(Salary, 10)` ) is correctly used to calculate the base-10 logarithm of the Salary, provided Salary is positive.

17. SUBSTRING ( `SUBSTRING(Name, 1, 3)`) is correctly used to extract the first three characters from the Name column.

18. CHARINDEX ( `CHARINDEX('a', Name)` ) is correctly used to find the position of 'a' in the Name column.

19. A correlated subquery is one that refers to a column from a table in the outer query, thus depending on it.

20. The EXISTS clause is correctly used to check if there's a matching department for each employee.

21. A view is a virtual table in SQL that is based on the result-set of an SQL statement.

22. A materialized view is a view whose result set is physically stored, and can be refreshed from the original tables.

23. A module in Python is a file containing Python definitions and statements.

24.

```python

def greet(name, message):  # 'name' and 'message' are parameters
    print(f"{message}, {name}!")

greet('Alice', 'Hello')  # 'Alice' and 'Hello' are arguments

```

### File Modes:

- **`r`**: Read-only. File must exist.
- **`w`**: Write-only. Creates a new file if it doesn't exist or truncates the file if it does.
- **`a`**: Append-only. Creates a new file if it doesn't exist or appends to the end if it does.
- **`rb`**: Read-only in binary mode. File must exist.
- **`wb`**: Write-only in binary mode. Creates a new file if it doesn't exist or truncates the file if it does.
- **`ab`**: Append-only in binary mode. Creates a new file if it doesn't exist or appends to the end if it does.

### `+` Mode Variants:

- **`r+`**: Read and write. File must exist. The file pointer is at the beginning.
- **`w+`**: Read and write. Creates a new file if it doesn't exist or truncates the file if it does. The file pointer is at the beginning.
- **`a+`**: Read and write. Creates a new file if it doesn't exist or appends to the end if it does. The file pointer is at the end.
- **`rb+`**: Read and write in binary mode. File must exist. The file pointer is at the beginning.
- **`wb+`**: Read and write in binary mode. Creates a new file if it doesn't exist or truncates the file if it does. The file pointer is at the beginning.
- **`ab+`**: Read and write in binary mode. Creates a new file if it doesn't exist or appends to the end if it does. The file pointer is at the end.

25. A decorator in Python is a function that modifies the functionality of another function, method, or class.

26. A generator in Python is a tool for creating iterators. It allows you to declare a function that behaves like an iterator, i.e., it can be used in a for loop.

27. Generators differ from standard functions in that they yield values and maintain their state, allowing them to resume where they left off.

28. The main difference is that multiprocessing in Python uses separate memory spaces for each process, while threads in a multi-threaded application share memory.

29. Multiprocessing is often preferred for CPU-bound tasks where parallel execution of independent processes can lead to performance gains.

30. Generators are implemented using a function, whereas iterators are implemented using a class.

31. A TreeMap stores key-value pairs in a sorted order based on their natural ordering or a custom comparator.

32. TreeMap sorts the keys in natural order, so the output will be the entries sorted by key.

33. TreeSet does not allow the insertion of null elements, so adding null will throw a NullPointerException.

34. There is no error. HashMap allows null keys, and the second put operation replaces the first, so the output is 2.

35. The String Constant Pool is a special memory area in Java Heap where String literals and interned strings are stored for reuse.

36. Daemon threads are typically used for background supporting tasks and do not prevent the JVM from exiting once all user threads have completed.

37. The ls -a command in Linux lists all contents of a directory, including hidden files and directories. Hidden files are those whose names begin with a dot (.).

38. The `/etc` directory contains all the system-wide configuration files and shell scripts that are used to boot and initialize the system.

39. The ext4 (fourth extended filesystem) is the most commonly used file system type in modern Linux distributions due to its robustness and performance.

40. The man (manual) command is used to display the manual pages for other commands in Linux.

41. The -r (recursive) option in the rm command is used to remove directories and their contents recursively.

42. The du (disk usage) command estimates and displays the disk space used by files and directories.

43. If the number of inodes (which store file metadata) is exhausted, it can prevent new files from being created, causing the df command to show incorrect free space.

44. The init process is the first process started by the kernel and is responsible for initializing the system during the boot process.

45. A zombie process is a process that has completed execution but still has an entry in the process table, usually because its parent process has not read its exit status.

46. The `kill -9` command sends the SIGKILL signal to forcibly terminate the process with PID 1234.

47. A `shell script` is a text file containing a series of commands that are executed by the shell.

48. The `shebang (#!)` at the beginning of a shell script specifies the path to the interpreter that should be used to execute the script.
