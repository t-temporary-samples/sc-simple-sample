# Install Dependency

* https://docs.microsoft.com/en-us/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development?view=sql-server-ver15

# Sample Code

```js
const { Connection, Request } = require("tedious");

const config = {
    authentication: {
        options: {
            userName: process.env.AZURE_SQL_USERNAME,
            password: process.env.AZURE_SQL_PASSWORD,
        },
        type: "default",
    },
    server: process.env.AZURE_SQL_SERVER,
    options: {
        database: process.env.AZURE_SQL_DATABASE,
        encrypt: true,
        port: parseInt(process.env.AZURE_SQL_PORT),
    }
};

const connection = new Connection(config);

connection.on("connect", err => {
    if (err) {
        console.error(err.message);
    } else {
        query();
    }
});

connection.connect();

function query() {
    const req = new Request("SELECT ProductID, Name FROM SalesLT.Product", (err, rowCount, rows) => {
        if (err) {
            console.error(err.message);
        } else {
            console.log(`${rowCount} rows`);
        }
    });
    req.on("row", (columns) => {
        columns.forEach((column) => {
            console.log(`${column.metadata.colName}\t${column.value}`);
        })
    })

    req.on("requestCompleted", () => {
        connection.close();
    })

    connection.execSql(req);
}
```

* for more sample, please refer https://docs.microsoft.com/en-us/sql/connect/node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js?view=sql-server-ver15
