# Install Dependency

* https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development?view=sql-server-ver15

# Sample Code

```python
#!/usr/bin/env python3
import os
import pyodbc

conn = pyodbc.connect(driver = 'ODBC Driver 17 for SQL Server', server = os.getenv("AZURE_SQL_SERVER"), port = os.getenv("AZURE_SQL_PORT"), database = os.getenv("AZURE_SQL_DATABASE"), user = os.getenv("AZURE_SQL_USER"), password = os.getenv("AZURE_SQL_PASSWORD"))

cursor = conn.cursor()
cursor.execute('Select ProductID,Name from [SalesLT].[Product]')

row = cursor.fetchone()
while row:
    print(row)
    row = cursor.fetchone()

conn.close()
```

* for more sample, please refer https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc?view=sql-server-ver15
