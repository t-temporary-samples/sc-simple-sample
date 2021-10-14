# Dependency

```xml
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>3.6.3</version>
</dependency>
```

# Sample Code

```java
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisShardInfo;

public class App {
    public static void main(String[] args) throws Exception {
        JedisShardInfo info = new JedisShardInfo(System.getenv("AZURE_REDIS_CONNECTIONSTRING"));
        Jedis jedis = new Jedis(info);
        System.out.println(jedis.set("key", "value"));
        System.out.println(jedis.get("key"));
    }
}
```
