

# Create database
``` sql
Create database database_name;
```

# To view all the databases in system
``` sql
select name
from sysdatabases;
```

# To view all system user details
``` sql
select name
from sysusers;
```

# To view all login details
``` sql
select name
from syslogins;
```

# To view all object details in the system
``` sql
select name
from sysobjects;
```

# view the information of database.
``` sql
sp_helpdb Yashwanth;
```
# Rename database.
```sql
sp_renamedb old_database_name,new_database_name;
```

# Use database
``` sql
USE database_name;
```

# Drop database
``` sql
Drop database database_name;

DROP DATABASE IF EXISTS Database_Name;

```

# complete flow in one script
```sql
CREATE DATABASE CollegeDB;
GO

USE CollegeDB;
GO

CREATE TABLE Students (
    StudentID INT,
    StudentName VARCHAR(50),
    Marks INT
);
GO

INSERT INTO Students VALUES
(1, 'Abc', 85),
(2, 'Def', 72),
(3, 'fgh', 90);
GO

SELECT * FROM Students;

```
