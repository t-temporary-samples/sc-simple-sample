# Install Dependency

```bash
pip3 install redis
```

# Sample Code

```python
#!/usr/bin/env python3
import os
import redis

r = redis.Redis.from_url(os.getenv("AZURE_REDIS_CONNECTIONSTRING"), socket_timeout = 10, retry_on_timeout = False)

print(r.set("key", "value"))
print(r.get("key"))
```
