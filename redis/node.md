# Install Dependency

```bash
npm install redis@3
```

# Sample Code

```js
var redis = require("redis");

(async () => {
    const client = redis.createClient(process.env.AZURE_REDIS_CONNECTIONSTRING)
    client.set("key", "value", redis.print)
    client.get("key", redis.print)
})();
```
