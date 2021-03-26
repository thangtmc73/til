# Truthy Value và Falsy Value

## Falsy value

Falsy value là những giá trị trong Javascript trong bối cảnh bị ép kiểu về `boolean` (câu lệnh điều kiện hoặc vòng lặp) sẽ có giá trị `false`.

Tất cả falsy value:

```javascript
false;
0, -0, 0n, -0n, 0x0n / -0x0n; // (Number, BigInt)
undefined;
null;
NaN;
"", "", ``; // empty string
```

## Truthy value

Truthy value tương tự như falsy value nhưng sẽ có giá trị `true`

Ví dụ: những trường hợp còn lại

## Lưu ý

- Các giá trị falsy rất nguy hiểm khi so sánh với nhau (nên tra cứu và thử để đảm bảo). Prefer sử dụng toán tử `===` thay vì `==`

```javascript
false == 0; // (true);
false === 0; // (false);
```

- Cố gắng đưa về kiểu `boolean` khi cần thiết bằng toán tử `!!` hoặc constructor của kiểu `boolean`: `Boolean()`

### References

[Truthy & Falsey
](https://j11y.io/javascript/truthy-falsey/)

[Falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)

[Truthy and Falsy: When All is Not Equal in JavaScript](https://www.sitepoint.com/javascript-truthy-falsy/)
