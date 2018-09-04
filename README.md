# cache.go

![](https://github.com/orca-zhang/cache.go/raw/master/doc/leetcode.png)

## usage

```go
	lc := lrucache.New(5)
	lc.Put(1, "1")
	lc.Put(2, "2")
	lc.Put(1, "3")
	lc.Put(3, "4")
	lc.Put(4, "5")
	lc.Put(5, "6")
	lc.Put(2, "7")
	lc.Put(6, "8")

	lc.Delete(5)

	i := 1
	for e := lc.Front(); e != nil; e = e.Next() {
		fmt.Printf("[%d] %d => %s\r\n", i, e.Key.(int), e.Value.(string))
		i++
	}
```

result:
```
[1] 6 => 8
[2] 2 => 7
[3] 4 => 5
[4] 3 => 4
```