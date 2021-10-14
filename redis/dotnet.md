# Dependency

```xml
<PackageReference Include="StackExchange.Redis" Version="2.2.50" />
```

# Sample Code

```cs
using System;
using System.Threading.Tasks;
using StackExchange.Redis;

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
            using (var redis = await ConnectionMultiplexer.ConnectAsync(System.Environment.GetEnvironmentVariable("AZURE_REDIS_CONNECTIONSTRING")).ConfigureAwait(false))
            {
                var db = redis.GetDatabase();
                if (!await db.StringSetAsync(new RedisKey("key"), new RedisValue("value")).ConfigureAwait(false))
                {
                    throw new Exception("Can't set key successfully");
                }
                var value = await db.StringGetAsync(new RedisKey("key")).ConfigureAwait(false);
                Console.WriteLine(value);
            }
        }
    }
}
```