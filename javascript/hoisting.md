# Hoisting

Hoisting sẽ đưa phần khai báo variable và function vào memory trước khi thực thi những phần code khác.

Javascript chỉ hoisting phần khai báo (declaration) không phải phần khởi tạo (initialization). Nếu không được khởi tạo với giá trị có sẵn, mặc định hoisting một variable có giá trị `undefined`.

Chỉ có variable định nghĩa với `var` mới hoisting được, `let` và `const` không được hoisting.

Hỗ trợ: từ ECMAScript 2015 (ES6).

Ví dụ với `function`

```javascript
helloWorld("Thang");

function helloWorld(name) {
  console.log(name, "hello world");
}
```

Ví dụ với variable

```javascript
x = 1; // khởi tạo x = 1;
console.log(x);
console.log(y);
console.log(z);
var x = 2; // hoisting x
var y = 3; // hoisting y
let z = 4; // not hoisting z
```

Kết quả

```
1
undefined
ReferenceError: Cannot access 'z' before initialization
```

Trường hợp `function` được khai báo bằng biểu thức hàm `function expression`

```javascript
func();

var func = function () {
  console.log("Hello world");
};
```

Kết quả:

```
TypeError: func is not a function
```
