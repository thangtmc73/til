# Declarative programming và Imperative programming

## Declarative programming

Declarative programming là kiểu lập trình mô tả chúng ta cần cái gì, VD: chúng ta cần một cái Text, hiển thị ngay trong cái View đó.

```javascript
<View>
  <Text>text</Text>
</View>
```
Đặc điểm:
- Ngắn gọn dễ đọc
- Bản thân framework mà nó đang chạy trên phải biết chính xác nó cần làm gì (đẩy những việc phức tạo cho framework làm).

## Imperative programming

Imperative programming là kiểu lập trình mô tả từng bước cách mọi thứ hoạt động. VD: chúng ta khởi tạo 1 View => khởi tạo một Text => Add Text vào View => Add View vào cây DOM

```javascript
DOM dom = getDOM();
View view = new View();
Text text = new Text({ children: "text" });
view.add(text);
dom.add(view)
```

Đặc điểm:
- Phải đọc step-by-step từng bước
- Khó maintain khi codebase quy mô lớn
- Người lập trình biết rõ chính xác cái gì đang diễn ra.

## Các ví dụ khác
### Lowercase các phần tử trong một array kiểu chuỗi

Imperative programming:
- Tạo một `output` rỗng
- Duyệt ra các phần tử trong mảng `input` và push giá trị lowercase của phần tử đó vào `output`
- Trả về `output`
```javascript
function toLowerCase(input) {
  const output = [];
  for (let i = 0; i < input.length; i++) {
    output.push(input[i].toLowerCase());
  }
  return output;
}
```
Declarative programming:
- Các phần tử trong `input` đi qua hàm `map`, transfer thành giá trị lowercase và tự trả về array mới với giá trị đã transfer.
```javascript
function toLowerCase(input) {
  return input.map(item => item.toLowerCase());
}
```

## References:
React Design Patterns and Best Pratices