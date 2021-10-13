# Sample Code

```golang
package main

import (
	"database/sql"
	"fmt"
	"os"

	_ "github.com/denisenkom/go-mssqldb"
)

func main() {
	db, err := sql.Open("sqlserver", os.Getenv("AZURE_SQL_CONNECTIONSTRING"))
	if err != nil {
		panic(err)
	}
	row, err := db.Query("Select ProductID,Name from [SalesLT].[Product]")
	if err != nil {
		panic(err)
	}
	for row.Next() {
		var id int
		var name string
		err = row.Scan(&id, &name)
		if err != nil {
			panic(err)
		}
		fmt.Printf("%d %s\n", id, name)
	}
}
```