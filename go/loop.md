# Vòng lặp trong Go
Vòng lặp tương tự vòng lặp trong các ngôn ngữ khác, bao gồm:
- Init `optional` (trước lần duyệt vòng lặp đầu tiên)
- Condition `optional` (trước mỗi lần duyệt vòng lặp)
- Post `optional` (sau mỗi lần duyệt)

```go
// đầy đủ init, condition, post
for i := 0; i < 100; i++ {
  fmt.Println(i)
}

// bỏ qua init và post
for ; i < 100; {
  fmt.Println(i)
}

// bỏ qua init và post, dấu chấm phẩy
// sử dụng thay thế while
for i < 100 {
  fmt.Println(i)
}

// lặp vô hạn
for {
  
}
```