# Create database
``` sql
Create database database_name;
```

# Show databases
``` sql
select name
from sys.databases;
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
