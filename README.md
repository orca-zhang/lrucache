# cache.go

[![license](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](https://github.com/orca-zhang/cache.go/blob/master/LICENSE)
[![Go Report Card](https://goreportcard.com/badge/github.com/orca-zhang/cache.go)](https://goreportcard.com/report/github.com/orca-zhang/cache.go)

- Other Language
  - [JavaScript](https://github.com/orca-zhang/cache.js)
  - [C++](https://github.com/ez8-co/linked_hash)

## Result at leetcode.com

![](https://github.com/orca-zhang/cache.go/raw/master/doc/leetcode.png)

## Usage

```go
	lc := lrucache.New(5)
	lc.Put(4, "1")
	lc.Put(1, "2")
	lc.Put(2, "3")
	lc.Put(3, "4")
	lc.Put(4, "5")

	fmt.Println("Range demo:")
	i := 1
	lc.Range(func(key, value interface{}) bool {
		fmt.Printf("[%d] %d => %s\r\n", i, key.(int), value.(string))
		i++
		return true
	})

	fmt.Println("Get demo:")
	if e, ok := lc.Get(1); ok {
		fmt.Printf("%d => %s\r\n", 1, e.(string))
	}

	fmt.Println("Reverse iteration after Get demo:")
	i = 1
	for e := lc.Back(); e != nil; e = e.Prev() {
		fmt.Printf("[%d] %d => %s\r\n", lc.Len()-i+1, e.Key.(int), e.Value.(string))
		i++
	}

	lc.Delete(4)
	fmt.Println("Iteration after Delete demo:")
	i = 1
	for e := lc.Front(); e != nil; e = e.Next() {
		fmt.Printf("[%d] %d => %s\r\n", i, e.Key.(int), e.Value.(string))
		i++
	}
```

Output:
```

Range demo:
[1] 4 => 5
[2] 3 => 4
[3] 2 => 3
[4] 1 => 2
Get demo:
1 => 2
Reverse iteration after Get demo:
[4] 2 => 3
[3] 3 => 4
[2] 4 => 5
[1] 1 => 2
Iteration after Delete demo:
[1] 1 => 2
[2] 3 => 4
[3] 2 => 3

```
