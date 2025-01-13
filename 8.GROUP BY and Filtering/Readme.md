# GROUP BY and Filtering 

## 1. Introduction to GROUP BY
- **GROUP BY**: Used to group rows that have the same values in specified columns.
- Often used with aggregate functions (e.g., `COUNT()`, `SUM()`, `AVG()`) to perform calculations on each group.

### Syntax:
```sql
SELECT Column1, AggregateFunction(Column2)
FROM TableName
GROUP BY Column1;
```

### Example:
```sql
-- Calculate total sales for each product
SELECT ProductID, SUM(Sales) AS TotalSales
FROM Orders
GROUP BY ProductID;
```

---

## 2. Filtering with HAVING Clause
- **HAVING**: Filters groups created by `GROUP BY` based on a condition.
- Used after the `GROUP BY` clause (unlike `WHERE`, which filters rows before grouping).

### Syntax:
```sql
SELECT Column1, AggregateFunction(Column2)
FROM TableName
GROUP BY Column1
HAVING Condition;
```

### Example:
```sql
-- Find products with total sales greater than 5000
SELECT ProductID, SUM(Sales) AS TotalSales
FROM Orders
GROUP BY ProductID
HAVING SUM(Sales) > 5000;
```

---

## 3. Combining WHERE and GROUP BY
- **WHERE** filters rows before grouping.
- **HAVING** filters groups after aggregation.

### Example:
```sql
-- Find products with sales over 5000, sold in 2023
SELECT ProductID, SUM(Sales) AS TotalSales
FROM Orders
WHERE OrderYear = 2023
GROUP BY ProductID
HAVING SUM(Sales) > 5000;
```

---

## 4. Assignments

### Question 1:
Find the total number of employees in each department.

#### Answer:
```sql
SELECT DepartmentID, COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY DepartmentID;
```

### Question 2:
Calculate the total salary for each department where the total salary exceeds 100,000.

#### Answer:
```sql
SELECT DepartmentID, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY DepartmentID
HAVING SUM(Salary) > 100000;
```

### Question 3:
Find the average salary of employees in each job role.

#### Answer:
```sql
SELECT Job, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Job;
```

### Question 4:
List departments with more than 5 employees.

#### Answer:
```sql
SELECT DepartmentID, COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY DepartmentID
HAVING COUNT(*) > 5;
```

### Question 5:
Retrieve the total sales for each product where the product sales exceed 10,000.

#### Answer:
```sql
SELECT ProductID, SUM(Sales) AS TotalSales
FROM Orders
GROUP BY ProductID
HAVING SUM(Sales) > 10000;
```

### Question 6:
Find the maximum and minimum salary in each department.

#### Answer:
```sql
SELECT DepartmentID, MAX(Salary) AS MaxSalary, MIN(Salary) AS MinSalary
FROM Employees
GROUP BY DepartmentID;
```

### Question 7:
List job roles where the average salary is greater than 50,000.

#### Answer:
```sql
SELECT Job, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Job
HAVING AVG(Salary) > 50000;
```

### Question 8:
Find the total sales for each region, but only include regions with sales between 5,000 and 20,000.

#### Answer:
```sql
SELECT RegionID, SUM(Sales) AS TotalSales
FROM Orders
GROUP BY RegionID
HAVING SUM(Sales) BETWEEN 5000 AND 20000;
```

### Question 9:
Retrieve the number of orders placed in each month of the year 2023.

#### Answer:
```sql
SELECT MONTH(OrderDate) AS Month, COUNT(*) AS TotalOrders
FROM Orders
WHERE YEAR(OrderDate) = 2023
GROUP BY MONTH(OrderDate);
