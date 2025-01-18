# Employee and Manager Relationship 

## Case 1: Manager Relationships

### 1. Name of Allen's Manager
```sql
SELECT ENAME
FROM EMP
WHERE EID = (
    SELECT MGR
    FROM EMP
    WHERE ENAME = 'ALLEN'
);
```

### 2. Name of Smith's Manager
```sql
SELECT ENAME
FROM EMP
WHERE EID = (
    SELECT MGR
    FROM EMP
    WHERE ENAME = 'SMITH'
);
```

### 3. Name of Smith's Manager's Manager
```sql
SELECT ENAME
FROM EMP
WHERE EID = (
    SELECT MGR
    FROM EMP
    WHERE EID = (
        SELECT MGR
        FROM EMP
        WHERE ENAME = 'SMITH'
    )
);
```

### 4. Department Name of King's Manager
```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM EMP
    WHERE EID = (
        SELECT MGR
        FROM EMP
        WHERE ENAME = 'KING'
    )
);
```

### 5. Location of Adams's Manager's Manager
```sql
SELECT LOC
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM EMP
    WHERE EID = (
        SELECT MGR
        FROM EMP
        WHERE EID = (
            SELECT MGR
            FROM EMP
            WHERE ENAME = 'ADAMS'
        )
    )
);
```

---

## Case 2: Employees Reporting to Managers

### 1. Names of Employees Reporting to King
```sql
SELECT ENAME
FROM EMP
WHERE MGR = (
    SELECT EID
    FROM EMP
    WHERE ENAME = 'KING'
);
```

### 2. Name and Salary of Employees Reporting to James
```sql
SELECT ENAME, SAL
FROM EMP
WHERE MGR = (
    SELECT EID
    FROM EMP
    WHERE ENAME = 'JAMES'
);
```

### 3. Department Name of Employees Reporting to the President
```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM EMP
    WHERE MGR = (
        SELECT EID
        FROM EMP
        WHERE JOB = 'PRESIDENT'
    )
);
```

### 4. Department Details of Employees Reporting to Miller
```sql
SELECT *
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM EMP
    WHERE MGR = (
        SELECT EID
        FROM EMP
        WHERE ENAME = 'MILLER'
    )
);
```

---

## Assignments on Employee and Manager Relationships

- WAQTD Smith's Reporting Manager's Name:
  ```sql
  SELECT ENAME
  FROM EMP
  WHERE EID = (
      SELECT MGR
      FROM EMP
      WHERE ENAME = 'SMITH'
  );
  ```

- WAQTD Adams's Manager's Manager's Name:
  ```sql
  SELECT ENAME
  FROM EMP
  WHERE EID = (
      SELECT MGR
      FROM EMP
      WHERE EID = (
          SELECT MGR
          FROM EMP
          WHERE ENAME = 'ADAMS'
      )
  );
  ```

- WAQTD Department Name of Jones's Manager:
  ```sql
  SELECT DNAME
  FROM DEPT
  WHERE DEPTNO = (
      SELECT DEPTNO
      FROM EMP
      WHERE EID = (
          SELECT MGR
          FROM EMP
          WHERE ENAME = 'JONES'
      )
  );
  ```

- WAQTD Miller's Manager's Salary:
  ```sql
  SELECT SAL
  FROM EMP
  WHERE EID = (
      SELECT MGR
      FROM EMP
      WHERE ENAME = 'MILLER'
  );
  ```

- WAQTD Location of Smith's Manager's Manager:
  ```sql
  SELECT LOC
  FROM DEPT
  WHERE DEPTNO = (
      SELECT DEPTNO
      FROM EMP
      WHERE EID = (
          SELECT MGR
          FROM EMP
          WHERE EID = (
              SELECT MGR
              FROM EMP
              WHERE ENAME = 'SMITH'
          )
      )
  );
  ```

- WAQTD Names of Employees Reporting to Blake:
  ```sql
  SELECT ENAME
  FROM EMP
  WHERE MGR = (
      SELECT EID
      FROM EMP
      WHERE ENAME = 'BLAKE'
  );
  ```

- WAQTD Number of Employees Reporting to King:
  ```sql
  SELECT COUNT(ENAME)
  FROM EMP
  WHERE MGR = (
      SELECT EID
      FROM EMP
      WHERE ENAME = 'KING'
  );
  ```

- WAQTD Details of Employees Reporting to Jones:
  ```sql
  SELECT *
  FROM EMP
  WHERE MGR = (
      SELECT EID
      FROM EMP
      WHERE ENAME = 'JONES'
  );
  ```

- WAQTD Enames of Employees Reporting to Blake's Manager:
  ```sql
  SELECT ENAME
  FROM EMP
  WHERE MGR = (
      SELECT MGR
      FROM EMP
      WHERE ENAME = 'BLAKE'
  );
  ```

- WAQTD Number of Employees Reporting to Ford's Manager:
  ```sql
  SELECT COUNT(ENAME)
  FROM EMP
  WHERE MGR = (
      SELECT MGR
      FROM EMP
      WHERE ENAME = 'FORD'
  );
  
