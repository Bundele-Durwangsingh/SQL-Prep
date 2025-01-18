# Subqueries and Nested Subqueries

## 1. Introduction to Subqueries
- **Subqueries**: A query inside another query.
- Types:
  1. **Single-row Subquery**: Returns exactly one value.
  2. **Multi-row Subquery**: Returns more than one value.
- Operators used:
  - Single-row: `=`, `<`, `>`
  - Multi-row: `IN`, `ALL`, `ANY`

---

## 2. Single-row Subquery
- Used when the subquery returns only one value.

#### Example:
```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM EMP
    WHERE ENAME = 'ALLEN'
);
```

---

## 3. Multi-row Subquery
- Used when the subquery returns multiple values.
- Requires special operators like `IN`, `ANY`, `ALL`.

#### Example:
```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO IN (
    SELECT DEPTNO
    FROM EMP
    WHERE ENAME IN ('ALLEN', 'SMITH')
);
```

---

## 4. Subquery Operators
1. **ALL**: Compares a value with all values returned by the subquery.
   ```sql
   SELECT ENAME, SAL
   FROM EMP
   WHERE SAL > ALL (
       SELECT SAL
       FROM EMP
       WHERE DEPTNO = 10
   );
   ```

2. **ANY**: Compares a value with any one of the values returned by the subquery.
   ```sql
   SELECT ENAME, SAL
   FROM EMP
   WHERE SAL > ANY (
       SELECT SAL
       FROM EMP
       WHERE DEPTNO = 10
   );
   ```

---

## 5. Nested Subqueries
- A subquery inside another subquery.
- SQL allows nesting up to 255 subqueries.

#### Example:
1. Second Maximum Salary:
   ```sql
   SELECT MAX(SAL)
   FROM EMP
   WHERE SAL < (
       SELECT MAX(SAL)
       FROM EMP
   );
   ```

2. Third Maximum Salary:
   ```sql
   SELECT MAX(SAL)
   FROM EMP
   WHERE SAL < (
       SELECT MAX(SAL)
       FROM EMP
       WHERE SAL < (
           SELECT MAX(SAL)
           FROM EMP
       )
   );
   ```

---

## 6. Assignments on Subqueries

### Types of Subqueries:
WAQTD name of employees earning more than salesmen:

   ```sql
    SELECT ENAME
    FROM EMP
    WHERE SAL > ALL (
        SELECT SAL
        FROM EMP
        WHERE JOB = 'SALESMAN'
    );
   ```

WAQTD details of employees hired after all clerks:

   ```sql
    SELECT *
    FROM EMP
    WHERE HIREDATE > ALL (
        SELECT HIREDATE
        FROM EMP
        WHERE JOB = 'CLERK'
    );
   ```

WAQTD name and salary of employees earning less than at least one manager:

   ```sql
    SELECT ENAME, SAL
    FROM EMP
    WHERE SAL < ANY (
        SELECT SAL
        FROM EMP
        WHERE JOB = 'MANAGER'
    );
   ```

WAQTD name and hire date of employees hired before all managers:

   ```sql
    SELECT ENAME, HIREDATE
    FROM EMP
    WHERE HIREDATE < ALL (
        SELECT HIREDATE
        FROM EMP
        WHERE JOB = 'MANAGER'
    );
   ```

WAQTD names of employees hired after all managers and earning more than all clerks:

   ```sql
    SELECT ENAME
    FROM EMP
    WHERE HIREDATE > ALL (
        SELECT HIREDATE
        FROM EMP
        WHERE JOB = 'MANAGER'
    )
    AND SAL > ALL (
        SELECT SAL
        FROM EMP
        WHERE JOB = 'CLERK'
    );
   ```

### Nested Subqueries:
WAQTD 2nd minimum salary:

   ```sql
   SELECT MIN(SAL)
    FROM EMP
    WHERE SAL > (
        SELECT MIN(SAL)
        FROM EMP
    );
   ```

WAQTD 5th maximum salary:

   ```sql
    SELECT MAX(SAL)
    FROM EMP
    WHERE SAL < (
        SELECT MAX(SAL)
        FROM EMP
        WHERE SAL < (
            SELECT MAX(SAL)
            FROM EMP
            WHERE SAL < (
                SELECT MAX(SAL)
                FROM EMP
                WHERE SAL < (
                    SELECT MAX(SAL)
                    FROM EMP
                )
            )
        )
    );
   ```

WAQTD name of the employee earning 3rd maximum salary:
   ```sql
    SELECT ENAME
    FROM EMP
    WHERE SAL = (
        SELECT MAX(SAL)
        FROM EMP
        WHERE SAL < (
            SELECT MAX(SAL)
            FROM EMP
            WHERE SAL < (
                SELECT MAX(SAL)
                FROM EMP
            )
        )
    );
   ```

WAQTD department name of an employee getting 4th maximum salary:
   ```sql
    SELECT DNAME
    FROM DEPT
    WHERE DEPTNO = (
        SELECT DEPTNO
        FROM EMP
        WHERE SAL = (
            SELECT MAX(SAL)
            FROM EMP
            WHERE SAL < (
                SELECT MAX(SAL)
                FROM EMP
                WHERE SAL < (
                    SELECT MAX(SAL)
                    FROM EMP
                    WHERE SAL < (
                        SELECT MAX(SAL)
                        FROM EMP
                    )
                )
            )
        )
    );
   ```

---

**Remember:**
- Use `ALL` for comparing with all returned values.
- Use `ANY` for comparing with any one returned value.
- Nest subqueries carefully for multi-level conditions.
