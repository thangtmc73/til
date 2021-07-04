# Filter boolean

Đây là một trick được tìm thấy khi đọc config Webpack của Create React App được thực hiện để filter loại bỏ các phần tử mang giá trị `falsy value`.

```javascript
const items = ["abc", null, 123, undefined, NaN];
const parsedItems = items.filter(Boolean);
console.log(parsedItems);
```

Kết quả in ra
```
["abc", 123]
```

## Cách hoạt động
- Duyệt từng phần tử trong mảng `items` và truyền nó vào hàm khởi tạo object `Boolean`.
- Hàm khởi tạo object `Boolean` sẽ ép kiểu giá trị truyền vào về kiểu `Boolean`, với những giá trị `truthy value` sẽ trả về `true` và những giá trị `falsy value` sẽ trả về `false`.
- Phần `filter` sẽ lọc về những giá trị có thể trả về `true`.
## Công dụng
Trong một số trường hợp, giá trị của mảng ta có thể bao gồm những phần tử không phù hợp như `null`  hay `undefined` dẫn đến gây khó khăn trong quá trình duyệt các phần tử trong mảng

Hãy tưởng tượng tình huống sau:
```javascript
const backendSuppliers = [
  {
    id: 1,
    name: "Company A",
  },
  null,
  {
    id: 2,
    name: "Company B",
  },
  undefined,
];

const displayedSupplierNames = backendSuppliers.map(supplier => {
  const { name } = supplier; 
  return name;
});
```
Kết quả:
```
Cannot read property "name" of null.
Cannot read property "name" of undefined.
```

Thay vào đó chúng ta có thể làm như sau:
```javascript
// ...backendSuppliers
const displayedSuppliers = backendSuppliers.filter(Boolean);
const displayedSupplierNames = displayedSuppliers.map(supplier => {
  const { name } = supplier; 
  return name;
});
```