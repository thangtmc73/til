# defer trong Go
`defer` là 1 keyword trong Go, trì hoãn việc thực thi function đi kèm nó cho đến khi hàm chứa nó kết thúc.

```go
package main

import "fmt"

func main() {
  i := 0
	defer fmt.Println("world")

	fmt.Println("hello")
}

// in ra hello trước, world sau
```

Params của function được `defer` sẽ lấy giá trị tại thời điểm nó được gọi.

```go
package main

import "fmt"

func main() {
  i := 0
	defer fmt.Println(i)
  i = 1
}
// 0
```
Các function được `defer` sẽ được đưa vào một `stack`. Function được `defer` sau cùng sẽ được gọi trước, `last in, first out`

```go
package main

import "fmt"

func funcA() {
	defer fmt.Println("funcA deferred 1")
	fmt.Println("funcA non-deferred 1")
	defer fmt.Println("funcA deferred 2")
	fmt.Println("funcA non-deferred 2")
}

func main() {
	defer fmt.Println("main deferred 1")
	defer funcA()
	defer fmt.Println("main deferred 2");
	fmt.Println("done")
}
```
Result:
```
done
main deferred 2
funcA non-deferred 1
funcA non-deferred 2
funcA deferred 2
funcA deferred 1
main deferred 1
```