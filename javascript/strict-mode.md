# Strict mode trong Javascript

Chế độ nghiêm ngặt trong Javascript

Hỗ trợ: từ ECMAScript 2015 (ES6)

## Cú pháp

Apply `strict mode` global bằng cách khai báo ở đầu file.

```javascript
"use strict";

```

Apply `strict mode` local bằng cách khai báo ở body của function, chỉ có tác dụng trong function đó.

```javascript
function func() {
  "use strict";
}
```

## Quy định

Không được gán giá trị cho một variable chưa được khai báo.

```javascript
"use strict";

a = 5; // chưa từng khai báo a trước đó
// ReferenceError: mistypeVariable is not defined
```

Những phép gán failed mà Javascript không báo lỗi bây giờ sẽ throw Error. Ví dụ những variable không cho phép ghi đè của Javascript như `NaN`, `undefined`, `Infinity`. Những thuộc tính không cho phép ghi đè (`non-writable`) hoặc chỉ đọc (`getter-only`) của `object`.

```javascript
"use strict";
var NaN = 5; // TypeError: Cannot assign to read only property 'NaN' of object '#<Object>'
var undefined = 5; // TypeError: Cannot assign to read only property 'undefined' of object '#<Object>'
var Infinity = 6; // TypeError: Cannot assign to read only property 'Infinity' of object '#<Object>'

var obj1 = {};
Object.defineProperty(obj1, "x", { value: 1, writable: false });
obj1.x = 5; // TypeError: Cannot assign to read only property 'x' of object '#<Object>'

var obj2 = {
  get x() {
    return 5;
  },
};
obj2.x = 6; // TypeError: Cannot set property x of #<Object> which has only a getter
```

Không cho phép `delete` những thuộc tính không thể delete.

```javascript
"use strict";

delete Array.prototype; // TypeError: Cannot delete property 'prototype' of function Array() { [native code] }
```

Không được duplicate tên đối số `parameter` trong function

```javascript
"use strict";
function hello(name, name) {
  "use strict";
  console.log("Hello", name);
}
// SyntaxError: Duplicate parameter name not allowed in this context
```

Không cho phép khai báo số bát phân (có tiền tố 0)

```javascript
"use strict";

var a = 010; // Octal literals are not allowed in strict mode.
var b = 0o10; // ES6 => worked well
```

Không cho phép gán thuộc tính mới cho những kiểu `primitive type`.

```javascript
"use strict";
false.true = 5; // Cannot create property 'true' on boolean 'false'
(14).sailing = "home"; // Cannot create property 'sailing' on number '14'
"with".you = "far away"; // Cannot create property 'you' on string 'with'
```
