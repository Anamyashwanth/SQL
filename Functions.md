# SQL Functions 

---

## 1. String Functions – Complete Example

```sql
SELECT  
    name,
    UPPER(name) AS UpperName,            -- convert to uppercase’
    LOWER(name) AS LowerName,            -- convert to lowercase
    LEN(name) AS NameLength,             -- length of string
    LEFT(name, 2) AS FirstTwo,           -- first characters
    RIGHT(name, 2) AS LastTwo,           -- last characters
    SUBSTRING(name, 2, 3) AS MiddlePart, -- extract part
    REPLACE(name, 'a', 'x') AS Replaced, -- replace text
    CONCAT(name, '_EMP') AS Concatenated, -- join strings
    LTRIM(name) AS LeftTrim,             -- remove left spaces
    RTRIM(name) AS RightTrim,            -- remove right spaces
    TRIM(name) AS Trimmed                -- remove spaces both sides
FROM tbl_emp;
```

---

## 2. Numeric Functions – Complete Example

```sql
SELECT  
    salary,
    ABS(salary - 50000) AS Difference,      -- absolute value
    ROUND(salary, -2) AS RoundedSalary,     -- round value
    CEILING(salary / 1000.0) AS CeilingVal, -- next higher integer
    FLOOR(salary / 1000.0) AS FloorVal,     -- next lower integer
    POWER(2, 3) AS PowerValue,              -- 2^3
    SQRT(salary) AS SquareRoot,             -- square root
    RAND() AS RandomNumber                  -- random value
FROM tbl_emp;
```

---

## 3. Date Functions – Complete Example

```sql
SELECT  
    join_date,
    GETDATE() AS CurrentDateTime,               -- current date & time
    CURRENT_TIMESTAMP AS SystemTime,            -- system timestamp
    YEAR(join_date) AS JoinYear,                -- extract year
    MONTH(join_date) AS JoinMonth,              -- extract month
    DAY(join_date) AS JoinDay,                  -- extract day
    DATEADD(MONTH, 6, join_date) AS After6Months, -- add interval
    DATEDIFF(YEAR, join_date, GETDATE()) AS ExperienceYears, -- difference
    DATENAME(MONTH, join_date) AS MonthName,    -- month name
    DATEPART(QUARTER, join_date) AS QuarterNo,  -- part as number
    EOMONTH(join_date) AS EndOfMonth            -- last day of month
FROM tbl_emp;
```

---

## 4. Aggregate Functions – Complete Example

```sql
SELECT  
    COUNT(*) AS TotalEmployees,            -- total rows
    COUNT(bonus) AS BonusCount,            -- non-null count
    COUNT(DISTINCT dept_id) AS DeptCount,  -- unique count
    SUM(salary) AS TotalSalary,            -- sum
    AVG(salary) AS AverageSalary,          -- average
    MIN(salary) AS MinimumSalary,          -- lowest
    MAX(salary) AS MaximumSalary           -- highest
FROM tbl_emp;
```

---

## 5. Conversion Functions – Complete Example

```sql
SELECT  
    salary,
    CAST(salary AS VARCHAR) AS SalaryText,           -- convert datatype
    CONVERT(VARCHAR, join_date, 105) AS FormattedDate, -- format date
    TRY_CAST('123' AS INT) AS TryCastExample,        -- safe conversion
    TRY_CONVERT(INT, 'ABC') AS TryConvertExample     -- returns NULL if fails
FROM tbl_emp;
```

---

## 6. NULL Handling Functions – Complete Example

```sql
SELECT  
    name,
    salary,
    bonus,
    ISNULL(bonus, 0) AS BonusValue,            -- replace NULL
    COALESCE(bonus, salary, 0) AS FirstNonNull, -- first non-null
    NULLIF(salary, bonus) AS NullIfEqual       -- NULL if equal
FROM tbl_emp;
```

---

## 7. System Functions – Complete Example

```sql
SELECT  
    GETDATE() AS CurrentDate,
    NEWID() AS UniqueID,
    DB_NAME() AS DatabaseName,
    USER_NAME() AS UserName,
    SUSER_NAME() AS LoginName,
    @@ROWCOUNT AS RowsAffected,
    @@VERSION AS SQLServerVersion;
```

---

## One-line Memory

Functions are used to manipulate, calculate, convert, and format data based on its type.
