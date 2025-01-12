# Functions

## 1. Introduction to SQL Functions
- **Functions** are pre-defined operations in SQL that perform calculations or transformations on data.
- They can be categorized as:
  - **Aggregate Functions**: Operate on multiple rows to return a single result.
  - **Scalar Functions**: Operate on individual values and return a single result for each input.

---

## 2. Types of SQL Functions

### 2.1 Aggregate Functions
- Perform operations on a set of rows and return a single result.

| Function   | Description                                   |
|------------|-----------------------------------------------|
| `COUNT()`  | Returns the number of rows.                  |
| `SUM()`    | Returns the total sum of a numeric column.    |
| `AVG()`    | Returns the average value of a numeric column.|
| `MIN()`    | Returns the smallest value in a column.       |
| `MAX()`    | Returns the largest value in a column.        |

#### Example:
```sql
SELECT COUNT(*) AS TotalEmployees, AVG(Salary) AS AverageSalary
FROM Employees;
```

### 2.2 Scalar Functions
- Perform operations on individual values and return a result for each input.

| Function       | Description                              |
|----------------|------------------------------------------|
| `LEN()`        | Returns the length of a string.          |
| `ROUND()`      | Rounds a numeric value to a specified precision.|
| `UPPER()`      | Converts a string to uppercase.          |
| `LOWER()`      | Converts a string to lowercase.          |
| `SUBSTRING()`  | Extracts a portion of a string.          |

#### Example:
```sql
SELECT Name, UPPER(Name) AS UpperCaseName
FROM Employees;
```

---

## 3. Examples of Common Functions

### 3.1 Aggregate Functions
```sql
-- Total number of employees
SELECT COUNT(*) AS TotalEmployees
FROM Employees;

-- Average salary of employees
SELECT AVG(Salary) AS AverageSalary
FROM Employees;

-- Maximum and minimum salary
SELECT MAX(Salary) AS MaxSalary, MIN(Salary) AS MinSalary
FROM Employees;
```

### 3.2 Scalar Functions
```sql
-- Convert names to uppercase
SELECT Name, UPPER(Name) AS UpperCaseName
FROM Employees;

-- Extract first 3 characters of a name
SELECT Name, SUBSTRING(Name, 1, 3) AS FirstThreeChars
FROM Employees;

-- Round salary to the nearest integer
SELECT Salary, ROUND(Salary, 0) AS RoundedSalary
FROM Employees;
```

---

## 4. Assignments

### Question 1:
Find the total number of employees and their average salary.

#### Answer:
```sql
SELECT COUNT(*) AS TotalEmployees, AVG(Salary) AS AverageSalary
FROM Employees;
```

### Question 2:
Find the highest and lowest salaries in the company.

#### Answer:
```sql
SELECT MAX(Salary) AS MaxSalary, MIN(Salary) AS MinSalary
FROM Employees;
```

### Question 3:
List all employees with their names in uppercase.

#### Answer:
```sql
SELECT Name, UPPER(Name) AS UpperCaseName
FROM Employees;
```

### Question 4:
Retrieve the first 5 characters of employee names.

#### Answer:
```sql
SELECT Name, SUBSTRING(Name, 1, 5) AS FirstFiveChars
FROM Employees;
```

### Question 5:
Round the salaries of all employees to the nearest integer and display them.

#### Answer:
```sql
SELECT Name, Salary, ROUND(Salary, 0) AS RoundedSalary
FROM Employees;
```

### Question 6:
Calculate the total and average salary for employees in department 10.

#### Answer:
```sql
SELECT SUM(Salary) AS TotalSalary, AVG(Salary) AS AverageSalary
FROM Employees
WHERE DepartmentID = 10;
