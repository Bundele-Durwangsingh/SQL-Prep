# SQL Operators

## 1. Introduction to SQL Operators
- **Operators** are symbols or keywords used to perform specific operations on data.
- SQL supports different types of operators for performing arithmetic, comparison, logical, and other specialized operations.

---

## 2. Types of Operators in SQL

### 2.1 Arithmetic Operators
- Used to perform mathematical calculations.

| Operator | Description          |
|----------|----------------------|
| `+`      | Addition             |
| `-`      | Subtraction          |
| `*`      | Multiplication       |
| `/`      | Division             |

#### Example:
```sql
SELECT Salary, Salary + 500 AS IncrementedSalary
FROM Employees;
```

### 2.2 Comparison Operators
- Used to compare two values.

| Operator  | Description                       |
|-----------|-----------------------------------|
| `=`       | Equal to                         |
| `!=` or `<>` | Not equal to                |
| `>`       | Greater than                     |
| `<`       | Less than                        |
| `>=`      | Greater than or equal to         |
| `<=`      | Less than or equal to            |

#### Example:
```sql
SELECT *
FROM Products
WHERE Price > 100;
```

### 2.3 Logical Operators
- Combine multiple conditions.

| Operator | Description                   |
|----------|-------------------------------|
| `AND`    | All conditions must be true.  |
| `OR`     | At least one condition is true. |
| `NOT`    | Negates a condition.          |

#### Example:
```sql
SELECT *
FROM Employees
WHERE Salary > 30000 AND Department = 'HR';
```

### 2.4 Special Operators

| Operator   | Description                                |
|------------|--------------------------------------------|
| `IN`       | Checks if a value is in a list.            |
| `NOT IN`   | Checks if a value is not in a list.        |
| `BETWEEN`  | Checks if a value is within a range.       |
| `NOT BETWEEN` | Checks if a value is outside a range.  |
| `LIKE`     | Matches a pattern.                        |
| `NOT LIKE` | Does not match a pattern.                 |
| `IS NULL`  | Checks if a value is NULL.                |
| `IS NOT NULL` | Checks if a value is not NULL.         |

#### Examples:
1. **IN Operator**:
```sql
SELECT *
FROM Employees
WHERE Department IN ('HR', 'Finance');
```

2. **LIKE Operator**:
```sql
SELECT *
FROM Employees
WHERE Name LIKE 'A%';
```

3. **BETWEEN Operator**:
```sql
SELECT *
FROM Products
WHERE Price BETWEEN 100 AND 500;
```

---

## 3. Assignments

### Question 1:
List all employees whose commission is NULL.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Commission IS NULL;
```

### Question 2:
List all employees who don’t have a reporting manager.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE ManagerID IS NULL;
```

### Question 3:
List all salesmen in department 30 with a salary greater than 1500.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE DepartmentID = 30 AND Job = 'Salesman' AND Salary > 1500;
```

### Question 4:
List all employees whose name starts with ‘S’ or ‘A’.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Name LIKE 'S%' OR Name LIKE 'A%';
```

### Question 5:
List all employees except those working in departments 10 and 20.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE DepartmentID NOT IN (10, 20);
```

### Question 6:
List the employees whose name does not start with ‘S’.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Name NOT LIKE 'S%';
```

### Question 7:
List all employees whose commission is NULL and are working as clerks.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Commission IS NULL AND Job = 'Clerk';
```

### Question 8:
List all analysts in department 20 earning a salary greater than 2500.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Job = 'Analyst' AND DepartmentID = 20 AND Salary > 2500;
```

### Question 9:
Display all employees who joined after the year 1981.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE HireDate > '1981-12-31';
```

### Question 10:
Display all employees who joined in February.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE TO_CHAR(HireDate, 'MM') = '02';
```

### Question 11:
List employees who are not working as managers or clerks in departments 10 and 20, with a salary between 1000 and 3000.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE (Job NOT IN ('Manager', 'Clerk')) AND DepartmentID IN (10, 20) AND Salary BETWEEN 1000 AND 3000;
```

### Question 12:
Display employees who have a bonus greater than 10% of their salary.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Bonus > (Salary * 0.1);
```

### Question 13:
List employees who have a name with exactly 5 characters.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE LENGTH(Name) = 5;
```

### Question 14:
List employees hired between January 1, 1980, and December 31, 1990.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE HireDate BETWEEN '1980-01-01' AND '1990-12-31';
```

### Question 15:
Display employees whose salary is a multiple of 1000.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE MOD(Salary, 1000) = 0;
```

### Question 16:
List employees who are earning more than the average salary of all employees.

#### Answer:
```sql
SELECT *
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```
