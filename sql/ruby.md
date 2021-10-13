# Install Dependency

* https://docs.microsoft.com/en-us/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development?view=sql-server-ver15

# Sample Code

```ruby
require "tiny_tds"

client = TinyTds::Client.new(username: ENV["AZURE_SQL_USERNAME"], password: ENV["AZURE_SQL_PASSWORD"], host: ENV["AZURE_SQL_HOST"], port: ENV["AZURE_SQL_PORT"], database: ENV["AZURE_SQL_DATABASE"], azure:true)
results = client.execute("SELECT ProductID, Name FROM SalesLT.Product")

results.each do |row|
    puts row
end
```

* for more sample, please refer https://docs.microsoft.com/en-us/sql/connect/ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby?view=sql-server-ver15
