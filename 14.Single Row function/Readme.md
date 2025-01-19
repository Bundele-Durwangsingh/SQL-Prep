#  Single Row Functions

## What are Single Row Functions?
Single Row Functions in SQL operate on single rows and return one result per row. These functions can be categorized into:
- **String Functions**
- **Numeric Functions**
- **Date Functions**

---

## String Functions

### 1. `LENGTH()`
- **Description**: Counts the number of characters in a string.
- **Syntax**: `LENGTH('string')`
- **Examples**:
    ```sql
    SELECT LENGTH('SMITH') FROM DUAL; -- Output: 5
    SELECT LENGTH('HELLO WORLD') FROM DUAL; -- Output: 11
    ```

### 2. `CONCAT()`
- **Description**: Joins two strings.
- **Syntax**: `CONCAT('string1', 'string2')`
- **Examples**:
    ```sql
    SELECT CONCAT('Mr. ', ENAME) FROM EMP WHERE ENAME = 'SMITH';
    ```

### 3. `UPPER()` / `LOWER()` / `INITCAP()`
- **Description**:
  - `UPPER()`: Converts a string to uppercase.
  - `LOWER()`: Converts a string to lowercase.
  - `INITCAP()`: Converts the first letter of each word to uppercase.
- **Examples**:
    ```sql
    SELECT UPPER('smith') FROM DUAL; -- Output: SMITH
    SELECT LOWER('SMITH') FROM DUAL; -- Output: smith
    SELECT INITCAP('SMITH') FROM DUAL; -- Output: Smith
    ```

### 4. `REVERSE()`
- **Description**: Reverses the string.
- **Syntax**: `REVERSE('string')`
- **Example**:
    ```sql
    SELECT REVERSE('SMITH') FROM DUAL; -- Output: HTIMS
    ```

### 5. `SUBSTR()`
- **Description**: Extracts a portion of a string.
- **Syntax**: `SUBSTR('Original_String', Position [, Length])`
- **Examples**:
    ```sql
    SELECT SUBSTR('QSPIDER', 2, 3) FROM DUAL; -- Output: SPI
    SELECT SUBSTR('QSPIDER', -3) FROM DUAL; -- Output: DER
    ```

### 6. `REPLACE()`
- **Description**: Replaces occurrences of a substring within a string.
- **Syntax**: `REPLACE('Original_String', 'search_string', 'replacement_string')`
- **Examples**:
    ```sql
    SELECT REPLACE('BANANA', 'A', 'C') FROM DUAL; -- Output: BCNCNC
    SELECT REPLACE('BANANA', 'N', 'ABC') FROM DUAL; -- Output: BAABCAABCA
    ```

### 7. `INSTR()`
- **Description**: Finds the position of a substring in a string.
- **Syntax**: `INSTR('Original_String', 'String', Position [, Occurrence])`
- **Examples**:
    ```sql
    SELECT INSTR('BANANA', 'A', 1, 1) FROM DUAL; -- Output: 2
    SELECT INSTR('BANANA', 'A', 1, 2) FROM DUAL; -- Output: 4
    ```

---

## Numeric Functions

### 8. `MOD()`
- **Description**: Returns the remainder of a division.
- **Syntax**: `MOD(m, n)`
- **Examples**:
    ```sql
    SELECT MOD(5, 2) FROM DUAL; -- Output: 1
    SELECT * FROM EMP WHERE MOD(EID, 2) = 1; -- Employees with odd EIDs
    ```

### 9. `ROUND()`
- **Description**: Rounds a number to a specified decimal place.
- **Syntax**: `ROUND(Number [, Scale])`
- **Examples**:
    ```sql
    SELECT ROUND(5.6) FROM DUAL; -- Output: 6
    SELECT ROUND(8421.12, -1) FROM DUAL; -- Output: 8420
    ```

### 10. `TRUNC()`
- **Description**: Truncates a number to a specified decimal place without rounding.
- **Syntax**: `TRUNC(Number [, Scale])`
- **Examples**:
    ```sql
    SELECT TRUNC(5.6) FROM DUAL; -- Output: 5
    SELECT TRUNC(8421.12, -1) FROM DUAL; -- Output: 8420
    ```

---

## Date Functions

### 11. `SYSDATE`, `CURRENT_DATE`, and `SYSTIMESTAMP`
- **Description**: Used to fetch the current system date and time.
- **Examples**:
    ```sql
    SELECT SYSDATE FROM DUAL; -- Current date
    SELECT CURRENT_DATE FROM DUAL; -- Current date with timezone
    SELECT SYSTIMESTAMP FROM DUAL; -- Current timestamp
    ```

### 12. `MONTHS_BETWEEN()`
- **Description**: Finds the number of months between two dates.
- **Syntax**: `MONTHS_BETWEEN(Date1, Date2)`
- **Example**:
    ```sql
    SELECT MONTHS_BETWEEN(SYSDATE, HIREDATE) FROM EMP;
    ```

### 13. `LAST_DAY()`
- **Description**: Returns the last day of the month for a given date.
- **Syntax**: `LAST_DAY(Date)`
- **Example**:
    ```sql
    SELECT LAST_DAY(SYSDATE) FROM DUAL; -- Last day of the current month
    ```

---

## Examples and Assignments

1. **List employees whose name has exactly 4 characters**:
    ```sql
    SELECT * FROM EMP WHERE LENGTH(ENAME) = 4;
    ```

2. **Find out how many times the letter 'S' occurs in 'SPIDERS'**:
    ```sql
    SELECT LENGTH('QSPIDERS') - LENGTH(REPLACE('SPIDERS', 'S')) FROM DUAL;
    ```

3. **Display names of employees hired on a Sunday**:
    ```sql
    SELECT * FROM EMP WHERE TO_CHAR(HIREDATE, 'DAY') = 'SUNDAY';
    ```

4. **Display department names with the letter 'O'**:
    ```sql
    SELECT DNAME FROM DEPT WHERE INSTR(DNAME, 'O') > 0;
    ```

5. **Display names whose job ends with 'MAN'**:
    ```sql
    SELECT * FROM EMP WHERE SUBSTR(JOB, -3) = 'MAN';
    ```
