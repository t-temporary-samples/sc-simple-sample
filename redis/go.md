# Sample Code

```go
package main

import (
	"fmt"
	"os"

	"github.com/go-redis/redis"
)

func main() {
	opt, err := redis.ParseURL(os.Getenv("AZURE_REDIS_CONNECTIONSTRING"))
	if err != nil {
		panic(err)
	}
	client := redis.NewClient(opt)
	err = client.Set("key", "value", 0).Err()
	if err != nil {
		panic(err)
	}

	val, err := client.Get("key").Result()
	if err != nil {
		panic(err)
	}
	fmt.Println(val)
}
```