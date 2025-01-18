# JOINS

## 1. Introduction to Joins
- **Joins**: The process of retrieving data from multiple tables simultaneously.
- Types of Joins:
  1. Cartesian Join / Cross Join
  2. Inner Join / Equi Join
  3. Outer Join
     - Left Outer Join
     - Right Outer Join
     - Full Outer Join
  4. Self Join
  5. Natural Join

---

## 2. Cartesian Join / Cross Join
- In a Cartesian Join, each record from Table 1 is merged with all records from Table 2.

#### Formula:
- **Number of Columns** = Columns in Table 1 + Columns in Table 2.
- **Number of Rows** = Rows in Table 1 × Rows in Table 2.

#### Syntax:
```sql
-- ANSI Syntax
SELECT Column_Name
FROM Table_Name1 CROSS JOIN Table_Name2;

-- Oracle Syntax
SELECT Column_Name
FROM Table_Name1, Table_Name2;
```

#### Example:
```sql
-- WAQTD ename and dept name for all the employees
SELECT ENAME, DNAME
FROM EMP, DEPT;

SELECT ENAME, DNAME
FROM EMP CROSS JOIN DEPT;
```

---

## 3. Inner Join
- Retrieves only matching records (records with a pair).

#### Syntax:
```sql
-- ANSI Syntax
SELECT Column_Name
FROM Table_Name1 INNER JOIN Table_Name2
ON <JOIN_CONDITION>;

-- Oracle Syntax
SELECT Column_Name
FROM Table_Name1, Table_Name2
WHERE <JOIN_CONDITION>;
```

#### Example:
```sql
-- WAQTD ename and dept name for all employees
SELECT ENAME, DNAME
FROM EMP INNER JOIN DEPT
ON EMP.DEPTNO = DEPT.DEPTNO;

SELECT ENAME, DNAME
FROM EMP, DEPT
WHERE EMP.DEPTNO = DEPT.DEPTNO;
```

---

## 4. Outer Joins

### 4.1 Left Outer Join
- Retrieves unmatched records from the left table along with matching records.

#### Syntax:
```sql
-- ANSI Syntax
SELECT Column_Name
FROM Table_Name1 LEFT [OUTER] JOIN Table_Name2
ON <JOIN_CONDITION>;

-- Oracle Syntax
SELECT Column_Name
FROM Table_Name1, Table_Name2
WHERE Table1.Col_Name = Table2.Col_Name(+);
```

#### Example:
```sql
-- WAQTD names and dnames of all employees even if they don’t work in any department
SELECT ENAME, DNAME
FROM EMP LEFT JOIN DEPT
ON EMP.DEPTNO = DEPT.DEPTNO;
```

### 4.2 Right Outer Join
- Retrieves unmatched records from the right table along with matching records.

#### Syntax:
```sql
-- ANSI Syntax
SELECT Column_Name
FROM Table_Name1 RIGHT [OUTER] JOIN Table_Name2
ON <JOIN_CONDITION>;

-- Oracle Syntax
SELECT Column_Name
FROM Table_Name1, Table_Name2
WHERE Table1.Col_Name(+) = Table2.Col_Name;
```

#### Example:
```sql
-- WAQTD names and dnames of all departments even if there are no employees
SELECT ENAME, DNAME
FROM EMP RIGHT JOIN DEPT
ON EMP.DEPTNO = DEPT.DEPTNO;
```

### 4.3 Full Outer Join
- Retrieves unmatched records from both tables along with matching records.

#### Syntax:
```sql
SELECT Column_Name
FROM Table_Name1 FULL [OUTER] JOIN Table_Name2
ON <JOIN_CONDITION>;
```

#### Example:
```sql
-- WAQTD names and dnames of all employees and departments even if unmatched
SELECT ENAME, DNAME
FROM EMP FULL OUTER JOIN DEPT
ON EMP.DEPTNO = DEPT.DEPTNO;
```

---

## 5. Self Join
- Joins a table with itself.
- **Why?** When data is stored in the same table but in different rows.

#### Syntax:
```sql
SELECT Column_Name
FROM Table_Name1 T1 JOIN Table_Name2 T2
ON <JOIN_CONDITION>;
```

#### Example:
```sql
-- WAQTD ename and manager's name for all employees
SELECT E1.ENAME, E2.ENAME AS Manager_Name
FROM EMP E1, EMP E2
WHERE E1.MGR = E2.EID;
```

---

## 6. Natural Join
- Behaves like an Inner Join if a relation exists between the two tables.
- Behaves like a Cross Join if no relation exists.

#### Syntax:
```sql
SELECT Column_Name
FROM Table_Name1 NATURAL JOIN Table_Name2;
```

---

## Assignments

### Inner Join Assignments:
1. WAQTD ename and loc for all employees.
   ```sql
   SELECT ENAME, LOC
   FROM EMP, DEPT
   WHERE EMP.DEPTNO = DEPT.DEPTNO;
   ```

2. WAQTD dname and salary for all employees working in accounting.
   ```sql
   SELECT DNAME, SAL
   FROM EMP, DEPT
   WHERE EMP.DEPTNO = DEPT.DEPTNO
   AND DNAME = 'ACCOUNTING';
   ```

3. WAQTD dname and annual salary for employees earning more than 2340.
   ```sql
   SELECT DNAME, SAL * 12 AS Annual_Salary
   FROM EMP, DEPT
   WHERE EMP.DEPTNO = DEPT.DEPTNO
   AND SAL > 2340;
   ```

4. WAQTD ename and dname for employees having character 'A' in their dname.
   ```sql
   SELECT ENAME, DNAME
   FROM EMP, DEPT
   WHERE EMP.DEPTNO = DEPT.DEPTNO
   AND DNAME LIKE '%A%';
   ```

### Self Join Assignments:
1. WAQTD name of the employee and their manager's name if the employee is a clerk.
   ```sql
   SELECT E1.ENAME, E2.ENAME AS Manager_Name
   FROM EMP E1, EMP E2
   WHERE E1.MGR = E2.EID
   AND E1.JOB = 'CLERK';
   ```

2. WAQTD employee name and manager's job if the manager works in dept 10 or 20.
   ```sql
   SELECT E1.ENAME, E2.JOB
   FROM EMP E1, EMP E2
   WHERE E1.MGR = E2.EID
   AND E2.DEPTNO IN (10, 20);
   ```

3. WAQTD employee name and manager's salary if both earn more than 2300.
   ```sql
   SELECT E1.ENAME, E2.SAL
   FROM EMP E1, EMP E2
   WHERE E1.MGR = E2.EID
   AND E1.SAL > 2300 AND E2.SAL > 2300;
   
