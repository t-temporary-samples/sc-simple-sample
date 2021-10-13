# Install Dependency

* https://docs.microsoft.com/en-us/sql/connect/php/step-1-configure-development-environment-for-php-development?view=sql-server-ver15

# Sample Code

```php
<?php
    $conn = sqlsrv_connect(getenv("AZURE_SQL_SERVERNAME"), array( "Database" => getenv("AZURE_SQL_DATABASE"), "UID" => getenv("AZURE_SQL_UID"), "PWD" => getenv("AZURE_SQL_PWD")));
    if( $conn === false ) {
        die( print_r( sqlsrv_errors(), true));
    }
    $sql = "SELECT ProductID, Name FROM SalesLT.Product";

    $result = sqlsrv_query($conn, $sql);
    if( $result === false ) {
        die( print_r( sqlsrv_errors(), true));
    }

    while ($row = sqlsrv_fetch_array($result, SQLSRV_FETCH_ASSOC)) {
        print_r($row);
    }
?>
```

* for more sample, please refer https://docs.microsoft.com/en-us/sql/connect/php/step-3-proof-of-concept-connecting-to-sql-using-php?view=sql-server-ver15
