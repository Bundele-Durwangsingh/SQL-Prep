# Subqueries 

##  Subqueries in SQL

### 1. What are Subqueries?
- A **subquery** is a query nested inside another query.
- Used to perform operations that require multiple steps or intermediate results.

### 2. Types of Subqueries
1. **Single-row Subquery**:
   - Returns only one row.
   - Often used with operators like `=`, `<`, `>`, etc.

   #### Example:
   ```sql
   SELECT Name, Salary
   FROM Employees
   WHERE Salary > (SELECT AVG(Salary) FROM Employees);
   ```

2. **Multi-row Subquery**:
   - Returns multiple rows.
   - Used with operators like `IN`, `ANY`, `ALL`.

   #### Example:
   ```sql
   SELECT Name, DepartmentID
   FROM Employees
   WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE Location = 'Mumbai');
   ```

3. **Correlated Subquery**:
   - A subquery that uses values from the outer query.

   #### Example:
   ```sql
   SELECT Name
   FROM Employees E1
   WHERE Salary > (SELECT AVG(Salary) FROM Employees E2 WHERE E1.DepartmentID = E2.DepartmentID);
   ```

---

### 3. Assignments

#### Question 1:
Retrieve the names of employees earning more than the average salary of their department.

##### Answer:
```sql
SELECT Name
FROM Employees E1
WHERE Salary > (SELECT AVG(Salary) FROM Employees E2 WHERE E1.DepartmentID = E2.DepartmentID);
```

#### Question 2:
List all products whose price is higher than the average price of all products.

##### Answer:
```sql
SELECT ProductName, Price
FROM Products
WHERE Price > (SELECT AVG(Price) FROM Products);
```

#### Question 3:
Find the departments where no employees are earning more than 50,000.

##### Answer:
```sql
SELECT DepartmentID
FROM Departments
WHERE DepartmentID NOT IN (
    SELECT DepartmentID
    FROM Employees
    WHERE Salary > 50000
);
```

---

## Advanced Filtering in SQL

### 1. Introduction to Advanced Filtering
- **Advanced filtering** involves using complex conditions and multiple clauses to retrieve specific subsets of data.
- Common techniques include:
  - Combining `WHERE` with multiple conditions.
  - Using pattern matching (`LIKE` and wildcards).
  - Applying set-based filtering (`IN`, `NOT IN`).

### 2. Pattern Matching with `LIKE`
- Matches data based on patterns.
- Wildcards:
  - `%`: Matches zero or more characters.
  - `_`: Matches exactly one character.

#### Examples:
```sql
-- Names starting with 'A'
SELECT Name
FROM Employees
WHERE Name LIKE 'A%';

-- Names with exactly 5 characters
SELECT Name
FROM Employees
WHERE Name LIKE '_____';
```

### 3. Filtering with `BETWEEN`
- Retrieves values within a specific range.

#### Example:
```sql
SELECT Name, Salary
FROM Employees
WHERE Salary BETWEEN 30000 AND 60000;
```

### 4. Combining Multiple Conditions
- Use logical operators (`AND`, `OR`, `NOT`) for complex filters.

#### Example:
```sql
-- Employees in department 10 or earning more than 50,000
SELECT Name, DepartmentID, Salary
FROM Employees
WHERE DepartmentID = 10 OR Salary > 50000;
```

---

### 5. Assignments

#### Question 1:
List all employees whose name starts with 'S' and whose salary is greater than 40,000.

##### Answer:
```sql
SELECT Name, Salary
FROM Employees
WHERE Name LIKE 'S%' AND Salary > 40000;
```

#### Question 2:
Retrieve employees hired between January 1, 2020, and December 31, 2022.

##### Answer:
```sql
SELECT Name, HireDate
FROM Employees
WHERE HireDate BETWEEN '2020-01-01' AND '2022-12-31';
```

#### Question 3:
Find products whose names contain the word 'Pro'.

##### Answer:
```sql
SELECT ProductName
FROM Products
WHERE ProductName LIKE '%Pro%';
```

#### Question 4:
List employees who do not work in departments 10 or 20.

##### Answer:
```sql
SELECT Name, DepartmentID
FROM Employees
WHERE DepartmentID NOT IN (10, 20);
```

#### Question 5:
Find employees whose names contain exactly 5 characters and are earning more than the average salary.

##### Answer:
```sql
SELECT Name, Salary
FROM Employees
WHERE LENGTH(Name) = 5 AND Salary > (SELECT AVG(Salary) FROM Employees);
```

#### Question 6:
Retrieve departments where the total salary exceeds 100,000.

##### Answer:
```sql
SELECT DepartmentID, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY DepartmentID
HAVING SUM(Salary) > 100000;
```
