# Lexical Scope

// cần coi lại nhiều lần hơn để hiểu sâu sắc

Là phạm vi một identifier có thể truy cập được

## Quá nhiều tổng kết

- Compiler của Javascript mỗi khi nó đến bắt gặp một `function` hoặc một `block scope {}` nó sẽ tạo ra một `scope` mới nằm trong `scope` đang có.

- Mỗi khi scope có `Scope Manager`, quản lý các chứa các identifier được khai báo trong scope đó. Mỗi lần thực thi scope sẽ khởi tạo một instance `Scope Manager` hoàn toàn riêng biệt.

- Mỗi khi trong một `scope` không tìm thấy một identifier (không tính trường hợp khởi tạo identifier mới thông qua keyword `var` hoặc `function`), Compiler sẽ tiếp tục tìm ở scope cha của scope hiện tại, tìm cho đến khi ra thì thôi. Không tìm ra, throw Error (tùy, có thể identifier undefined hoặc identifier undeclared).

- Cẩn thận trường hợp variable là target và không dùng `strict mode`

## Đoạn code

```javascript
//global scope
var students = [
  { id: 14, name: "Kyle" },
  { id: 73, name: "Suzy" },
  { id: 112, name: "Frank" },
  { id: 6, name: "Sarah" },
];

function getStudentName(studentID) {
  // function scope

  for (let student of students) {
    // loop scope

    if (student.id == studentID) {
      return student.name;
    }
  }
}

var nextStudent = getStudentName(73);
console.log(nextStudent); // Suzy
```

Vậy ta có:

```
global scope > function scope > loop scope
```

Trong suốt quá trình Compiler generate ra code để máy tính đọc hiểu nó sẽ lần lượt làm các thao tác:

Ta phân tách code ra từng đoạn:

```javascript
// global scope
var students = [
  { id: 14, name: "Kyle" },
  { id: 73, name: "Suzy" },
  { id: 112, name: "Frank" },
  { id: 6, name: "Sarah" },
];
function getStudentName/...
```

Scope hiện tại: `global scope`

- Xác định identifier `student` đi kèm `var`, đã khởi tạo chưa => chưa khởi tạo => khởi tạo `student` với giá trị khởi tạo.
- Xác định identifier `getStudentName` đi kèm `function` (khởi tạo function), đã khởi tạo chưa => chưa khởi tạo => khởi tạo `getStudentName`
- `getStudentName` là một funciton => khởi tạo một scope mới nằm trong `global scope hiện tại` => `function scope`

```javascript
// getStudentName thuộc global scope, không thuộc function scope
// params và những phần bên trong block scope mới thuộc function scope
function getStudentName(studentID) {
  // function scope

  for (let student of students) {
    // loop scope

    if (student.id == studentID) {
      return student.name;
    }
  }
}
```

Scope hiện tại: `function scope`

- Xác định identifier `studentID` nằm trong phần khai báo params, kiểm tra đã khởi tạo chưa => chưa khởi tạo => khởi tạo `studentID` trong `function scope`
- Xác định một vòng lặp `for` với `block scope` đi kèm, khởi tạo một scope mới bên trong `function scope` => `loop scope`

Scope hiện tại: `loop scope`

- Xác định identifier `student` đã khởi tạo chưa => nếu chưa (vòng lặp nên sẽ chưa khởi tạo ở lần duyệt đầu tiên) thì khởi tạo `student`
- Xác định identifier `student` đã khởi tạo chưa => chưa khởi tạo => tìm scope cha bên ngoài (`function scope`) => chưa khởi tạo => tìm scope cha bên ngoài (`global scope`) => đã khởi tạo, trả về kết quả của `students`
- ...
