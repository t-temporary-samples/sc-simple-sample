# Dependency

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>9.2.1.jre8</version>
</dependency>
```

# Sample Code

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class App {
    public static void main(String[] args) throws Exception {
        try (Connection connection = DriverManager.getConnection(System.getenv("AZURE_SQL_CONNECTIONSTRING"));
             Statement statement = connection.createStatement()) {
            String query = "Select ProductID,Name from [SalesLT].[Product]";
            ResultSet resultSet = statement.executeQuery(query);

            while (resultSet.next()) {
                System.out.println(resultSet.getInt(1) + " " + resultSet.getString(2));
            }
        }
    }
}
```

* for more sample, please refer https://docs.microsoft.com/sql/connect/jdbc/step-3-proof-of-concept-connecting-to-sql-using-java?view=sql-server-ver15
