# How to disable button in Flutter

## Thực trạng

Các widget hỗ trợ button của Flutter không có thuộc tính `disabled` tương tự `TouchableOpacity` trong React Native.

Trong phần xử lý handler sự kiện có thể validate điều kiện disabled, tuy nhiên phần UI và hiệu ứng khi tap vào sẽ không tắt được. Vậy nên bắt buộc phải có phần disable button riêng.

## Cách giải quyết

Set thuộc tính `onPressed` và `onLongPress` (có thể có nếu button có handle `onLongPress`) giá trị `null` để disable nó.

## Hiện thực

```dart
//...
void doSomething() { /* do something */ }
//...
TextButton(
  onPressed: condition ? null : doSomething(),
  child: Text("TextButton")
)
//...
ElevatedButton(
  onPressed: null,
  child: Text('ElevatedButton'),
  style: ButtonStyle(
    backgroundColor: MaterialStateProperty.resolveWith<Color>(
      (Set<MaterialState> states) {
        if (states.)
        if (states.contains(MaterialState.pressed)) // when user is touching
          return Colors.blue;
        else if (states.contains(MaterialState.disabled)) // onPressed null
          return Colors.green;
        return null; // Use the component's default.
      }
    ),
  ),
),
//...
OutlinedButton(
  onPressed: condition ? null : doSomething(),
  child: Text("OutlinedButton")
)
//...
```
