# Data Query Language (DQL)

## 1. Overview of DQL
- **DQL**: A subset of SQL used to retrieve data from the database.
- Includes operations like:
  - **Projection**: Selecting specific columns.
  - **Selection**: Filtering rows.
  - **JOIN**: Combining data from multiple tables.

---

## 2. Key Concepts in DQL

### 2.1 Projection
- **Definition**: The process of selecting specific columns from a table.
- **Purpose**: To retrieve only the required data instead of fetching all columns.

#### Example:
```sql
SELECT Name, Age
FROM Students;
```

### 2.2 Selection
- **Definition**: The process of retrieving specific rows based on conditions.
- **Purpose**: To filter data and retrieve only relevant records.

#### Example:
```sql
SELECT *
FROM Products
WHERE Price > 100;
```

### 2.3 JOIN
- **Definition**: Combines rows from two or more tables based on a related column.
- **Purpose**: To fetch data spread across multiple tables by creating relationships.

#### Example:
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

---

## 3. SELECT Statement Syntax
```sql
SELECT [DISTINCT] Column_Name(s)
FROM Table_Name
[WHERE Condition];
```

### Explanation of Clauses:
- **SELECT**: Specifies the columns to retrieve.
- **FROM**: Specifies the table to retrieve data from.
- **WHERE**: Filters rows based on conditions (optional).

---

## 4. Assignments

### Question 1:
Write a query to display names and branches of all students.

#### Answer:
```sql
SELECT Name, Branch
FROM Students;
```

### Question 2:
Write a query to retrieve employee names with a salary greater than 50,000.

#### Answer:
```sql
SELECT Name
FROM Employees
WHERE Salary > 50000;
```

### Question 3:
Write a query to display employee names and department names using a JOIN.

#### Answer:
```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

---

# Expressions and Aliases

## 1. Overview of Expressions
- **Expressions**: A combination of operands and operators that evaluate to a value.
- Examples include arithmetic operations and logical conditions.

---

## 2. Arithmetic Expressions

### Examples:
#### Calculate annual salary:
```sql
SELECT Name, Salary * 12 AS AnnualSalary
FROM Employees;
```

#### Add bonus to salary:
```sql
SELECT Name, Salary + Bonus AS TotalCompensation
FROM Employees;
```

---

## 3. Aliases
- **Aliases**: Alternate names given to columns or expressions for better readability.

### Rules for Aliases:
- Use single words or enclose in double quotes.
- Can use the `AS` keyword (optional).

#### Example:
```sql
SELECT Name AS EmployeeName, Salary * 12 AS "Annual Salary"
FROM Employees;
```

---

## 4. Assignments

### Question 1:
Write a query to calculate annual salary of employees and assign an alias `AnnualSalary`.

#### Answer:
```sql
SELECT Name, Salary * 12 AS AnnualSalary
FROM Employees;
```

### Question 2:
Write a query to retrieve names and half-term salaries of employees, assigning an alias `HalfTermSalary`.

#### Answer:
```sql
SELECT Name, Salary * 6 AS HalfTermSalary
FROM Employees;
```

### Question 3:
Write a query to calculate salary with a 10% hike and display it with alias `HikedSalary`.

#### Answer:
```sql
SELECT Name, Salary + (Salary * 0.10) AS HikedSalary
FROM Employees;
```
