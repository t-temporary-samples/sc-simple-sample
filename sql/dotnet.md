# Dependency

```xml
<PackageReference Include="Microsoft.Data.SqlClient" Version="2.1.2" />
```

# Sample Code

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Data.SqlClient;

namespace test
{
    public class Program
    {
        public static void Main()
        {
            main().Wait();
        }

        public static async Task main()
        {
            string connStr = System.Environment.GetEnvironmentVariable("AZURE_SQL_CONNECTIONSTRING");
            using (var conn = new SqlConnection(connStr))
            {
                await conn.OpenAsync().ConfigureAwait(false);
                string commandStr = "Select ProductID,Name from [SalesLT].[Product]";
                using (var command = new SqlCommand(commandStr, conn))
                {
                    using (var reader = await command.ExecuteReaderAsync().ConfigureAwait(false))
                    {
                        while (await reader.ReadAsync())
                        {
                            Console.WriteLine(reader["ProductID"] + " " + reader["Name"]);
                        }
                    }
                }
            }
        }
    }
}
```

* for more sample, please refer https://docs.microsoft.com/sql/connect/ado-net/step-3-connect-sql-ado-net?view=sql-server-ver15
