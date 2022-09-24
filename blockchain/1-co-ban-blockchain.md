# Cơ bản về Blockchai
## Blockchain là gì?
Là một sổ cái (ledger) phi tập trung, ai cũng có thể sở hữu và có bản sao y hệt nhau, một database dạng phân tán có nhiều node y hệt nhau. Bitcoin là một implementation của công nghệ blockchain.

Blockchain là một chuỗi các khối được liên kết nhau theo một hàm mã hóa. Mỗi khối có chứa thông tin hash của khối trước nó. Khó thay đổi tác động dữ liệu đang có của blockchain, vì muốn thay đổi một khối phải thay đổi tất cả khối phía sau.

... <= [Node **3ded** - Node **1abc**] <= [Node **1abc** - Node **2be**] <= ...

Mỗi khối ban đầu chỉ chứa dữ liệu giao dịch chuyển tiền, sau này dùng nhiều loại dữ liệu khác.

**Chú ý**: Hệ thống blockchain không chứa địa chỉ, thông tin tất cả các ví. Blockchain chỉ chứa thông tin giao dịch giữa các ví, địa chỉ ví sẽ được tạo ra ngẫu nhiên.
## Proof-of-Work (PoW)

