# Cơ bản về Blockchain
## Blockchain là gì?
Là một sổ cái (ledger) phi tập trung, ai cũng có thể sở hữu và có bản sao y hệt nhau, một database dạng phân tán có nhiều node y hệt nhau. Bitcoin là một implementation của công nghệ blockchain.

Blockchain là một chuỗi các khối (block - chain) được liên kết nhau theo một hàm mã hóa. Mỗi khối có chứa thông tin hash của khối trước nó. Khó thay đổi tác động dữ liệu đang có của blockchain, vì muốn thay đổi một khối phải thay đổi tất cả khối phía sau.

... <= [Node **3ded** - Node **1abc**] <= [Node **1abc** - Node **2be**] <= ...

Mỗi khối ban đầu chỉ chứa dữ liệu giao dịch chuyển tiền, sau này dùng nhiều loại dữ liệu khác.

**Chú ý**: Hệ thống blockchain không chứa địa chỉ, thông tin tất cả các ví. Blockchain chỉ chứa thông tin giao dịch giữa các ví, địa chỉ ví sẽ được tạo ra ngẫu nhiên.
## Cơ chế Proof-of-Work (PoW)
Là cơ chế đồng thuận đầu tiên và phổ biến trong blockchain.

Các giao dịch mới được tạo ra thì hệ thống blockchain cần liên tục tạo ra các block mới để chứa. Các block này được tạo bởi các miner.

Miner là những người tham gia vào blockchain để kiếm token thưởng hoặc coin thưởng bằng cách tạo và xác thực block. Với PoW, miner cần một máy tính đủ mạnh để chạy một hàm mã hóa, tìm x khi biết hàm số f(x) = y. Máy tính của miner lần lượt thử đi thử lại hàng tỉ phép tính để tìm ra x thỏa mãn y với hàm f(x) = y. Tìm được x => miner được thưởng token.

Còn nhiều cơ chế khác như PoS, PoA, ...

### Ưu điểm
- Đơn giản, dễ dàng trong việc xác thực block.

### Nhược điểm:
- Tiêu tốn quá nhiều điện năng cho các thiết bị máy tính mạnh của miner để tìm ra đáp án đảm bảo tính bảo mật của hệ thống.
- Có khả năng bị tấn công 51%.

## References
- 200Lab
- 
