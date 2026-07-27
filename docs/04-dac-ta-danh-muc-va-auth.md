# Đặc tả UC gọn — Danh mục & Xác thực

> Các use case **hỗ trợ** (không phải 4 module được phân công). Chỉ cần đặc tả UC gọn (không cần đủ 6 biểu đồ như 4 module chính). Truy vết: đề bài (thuộc tính từng thực thể) + [01-dac-ta-yeu-cau.md](01-dac-ta-yeu-cau.md) + [03-lop-thuc-the-va-csdl.md](03-lop-thuc-the-va-csdl.md).
>
> Mọi bảng đặc tả dưới đây theo đúng mẫu **6 dòng**: `Use case | Actor | Tiền điều kiện | Hậu điều kiện | Kịch bản chính | Ngoại lệ`. Kịch bản chính đánh số 1, 2, 3…; ngoại lệ đánh số theo bước của kịch bản chính. Dữ liệu minh họa lấy từ bộ dữ liệu mẫu mùa giải 2025 ở `03-lop-thuc-the-va-csdl.md` mục 5.

## 1. Đăng nhập / Đổi mật khẩu (actor: Thành viên)

| Mục | Nội dung — UC Đăng nhập | Nội dung — UC Đổi mật khẩu |
|---|---|---|
| **Use case** | Đăng nhập | Đổi mật khẩu |
| **Actor** | Thành viên (Nhân viên hoặc Quản lý) | Thành viên (Nhân viên hoặc Quản lý) |
| **Tiền điều kiện** | Tài khoản đã tồn tại trong hệ thống | Thành viên đã đăng nhập |
| **Hậu điều kiện** | Phiên đăng nhập được tạo; thành viên được phân quyền theo vai trò (Nhân viên / Quản lý) | Mật khẩu mới được lưu; các lần đăng nhập sau phải dùng mật khẩu mới |
| **Kịch bản chính** | 1. Thành viên mở phần mềm.<br>2. Hệ thống hiển thị màn hình đăng nhập: ô "Tên đăng nhập" và ô "Mật khẩu" đang rỗng, có nút [Đăng nhập].<br>3. Thành viên nhập tên đăng nhập `nv01`, mật khẩu và click [Đăng nhập].<br>4. Hệ thống kiểm tra tên đăng nhập tồn tại và mật khẩu khớp, đọc vai trò của tài khoản.<br>5. Hệ thống tạo phiên đăng nhập và hiển thị màn hình chính của vai trò Nhân viên, gồm các menu: Quản lý mùa giải, Quản lý tay đua, Quản lý đội đua, Quản lý chặng đua, Đăng ký đội tham gia mùa giải, Ký hợp đồng, Đăng ký chặng, Nhập kết quả chặng, Đổi mật khẩu, Đăng xuất. | 1. Thành viên chọn menu "Đổi mật khẩu".<br>2. Hệ thống hiển thị màn hình đổi mật khẩu: dòng chữ "Tài khoản: `nv01`" ở đầu màn hình; ba ô "Mật khẩu cũ", "Mật khẩu mới", "Nhập lại mật khẩu mới" đang rỗng; nút [Lưu] **chưa được active**.<br>3. Thành viên nhập mật khẩu cũ, mật khẩu mới, nhập lại mật khẩu mới; nút [Lưu] được active.<br>4. Thành viên click [Lưu].<br>5. Hệ thống kiểm tra mật khẩu cũ khớp với mật khẩu đang lưu và hai ô mật khẩu mới giống nhau.<br>6. Hệ thống lưu mật khẩu mới, hiển thị thông báo "Đổi mật khẩu thành công" và quay về màn hình chính. |
| **Ngoại lệ** | 4a. Tên đăng nhập không tồn tại hoặc mật khẩu sai → hệ thống báo lỗi "Tên đăng nhập hoặc mật khẩu không đúng", xóa ô mật khẩu và giữ nguyên màn hình đăng nhập, quay lại bước 3.<br>4b. Tài khoản có vai trò Quản lý → bước 5 hiển thị màn hình chính chỉ gồm các menu: Quyết toán và trao giải, Đổi mật khẩu, Đăng xuất. | 5a. Mật khẩu cũ không đúng → hệ thống báo lỗi "Mật khẩu cũ không đúng", xóa cả ba ô, quay lại bước 3.<br>5b. Hai ô mật khẩu mới khác nhau → hệ thống báo lỗi "Nhập lại mật khẩu mới không khớp", xóa hai ô mật khẩu mới, quay lại bước 3.<br>5c. Mật khẩu mới trùng mật khẩu cũ → hệ thống báo lỗi "Mật khẩu mới phải khác mật khẩu cũ", quay lại bước 3. |

> **Ghi chú.** Tài khoản gồm các thuộc tính: tên đăng nhập, mật khẩu, họ tên. Hai vai trò Nhân viên và Quản lý kế thừa từ lớp Thành viên, phân quyền được xác định ngay tại bước 4 của UC Đăng nhập. "Đã đăng nhập" là **tiền điều kiện** của mọi use case còn lại trong hệ thống, không lặp lại UC Đăng nhập ở các use case đó.

## 2. Quản lý danh mục (actor: Nhân viên)

Use case trừu tượng **Quản lý danh mục** là use case cha (quan hệ kế thừa) của bốn use case: **Quản lý mùa giải**, **Quản lý tay đua**, **Quản lý đội đua**, **Quản lý chặng đua**. Bốn use case con có cùng luồng thao tác tìm / thêm / sửa / xóa, chỉ khác ở tập thuộc tính của đối tượng và ở điều kiện chặn xóa. Kịch bản dưới đây minh họa bằng use case con **Quản lý tay đua**.

| Mục | Nội dung |
|---|---|
| **Use case** | Quản lý danh mục *(use case trừu tượng; các use case con: Quản lý mùa giải, Quản lý tay đua, Quản lý đội đua, Quản lý chặng đua)* |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập. Riêng use case con *Quản lý chặng đua* còn đòi hỏi đã có ít nhất một mùa giải trong danh mục. |
| **Hậu điều kiện** | Bản ghi danh mục được thêm mới, cập nhật hoặc xóa khỏi cơ sở dữ liệu; bảng danh sách trên màn hình hiển thị lại theo dữ liệu mới |
| **Kịch bản chính** | 1. Nhân viên chọn menu "Quản lý tay đua".<br>2. Hệ thống hiển thị màn hình danh mục tay đua: ô nhập "Tên tay đua" đang rỗng, nút [Tìm], nút [Thêm mới]; bảng danh sách gồm các cột Mã \| Tên \| Ngày sinh \| Quốc tịch \| Tiểu sử, mỗi dòng có nút [Sửa] và nút [Xóa].<br>3. Nhân viên nhập `Hamilton` và click [Tìm].<br>4. Hệ thống hiển thị bảng kết quả có 1 dòng: `HAM \| Lewis Hamilton \| 07/01/1985 \| Anh \| Bảy lần vô địch thế giới`.<br>5. Nhân viên click [Thêm mới].<br>6. Hệ thống hiển thị biểu mẫu nhập gồm các ô Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử đang rỗng và nút [Lưu].<br>7. Nhân viên nhập `ANT`, `Andrea Kimi Antonelli`, `25/08/2006`, `Ý`, tiểu sử rồi click [Lưu].<br>8. Hệ thống kiểm tra mã tay đua chưa tồn tại và các ô bắt buộc (mã, tên) đã được nhập.<br>9. Hệ thống lưu tay đua mới và hiển thị lại bảng danh sách, có thêm dòng `ANT \| Andrea Kimi Antonelli \| 25/08/2006 \| Ý \| …`.<br>*(Lặp lại các bước 5–9 cho đến khi nhập xong tất cả tay đua cần thêm.)* |
| **Ngoại lệ** | 4a. Không có bản ghi nào khớp từ khóa → hệ thống hiển thị bảng rỗng kèm dòng chữ "Không tìm thấy tay đua nào", quay lại bước 3.<br>5a. **Sửa:** nhân viên click [Sửa] trên dòng `HAM` → hệ thống hiển thị biểu mẫu đã điền sẵn dữ liệu của Lewis Hamilton → nhân viên sửa rồi click [Lưu] → hệ thống kiểm tra như bước 8 rồi cập nhật và quay lại bước 4.<br>5b. **Xóa:** nhân viên click [Xóa] trên dòng `HAM` → hệ thống hiển thị hộp xác nhận "Bạn có chắc muốn xóa tay đua Lewis Hamilton?" với nút [Đồng ý] và [Hủy] → nhân viên click [Đồng ý] → hệ thống kiểm tra tham chiếu rồi xóa và quay lại bước 4; nếu click [Hủy] thì quay lại bước 4 mà không xóa.<br>5c. Đối tượng đang được đối tượng khác tham chiếu (tay đua đã có hợp đồng, đã đăng ký chặng hoặc đã được trao giải) → hệ thống **từ chối xóa**, báo lỗi "Không thể xóa: tay đua đang có hợp đồng với Ferrari", quay lại bước 4.<br>8a. Mã tay đua đã tồn tại → hệ thống báo lỗi "Mã tay đua ANT đã tồn tại", giữ nguyên dữ liệu đã nhập trên biểu mẫu, quay lại bước 7.<br>8b. Thiếu ô bắt buộc → hệ thống báo lỗi "Vui lòng nhập đủ mã và tên tay đua", quay lại bước 7. |

> **Ghi chú 1 — thuộc tính của từng danh mục** (thay cho dòng "Thuộc tính" đã bỏ khỏi bảng đặc tả để giữ đúng mẫu 6 dòng):
> - **Mùa giải:** tên, năm, trạng thái
> - **Tay đua:** mã, tên, ngày sinh, quốc tịch, tiểu sử
> - **Đội đua:** mã, tên, hãng, mô tả
> - **Chặng đua:** mã, tên, số vòng, địa điểm, thời gian, mô tả (thuộc một mùa giải — biểu mẫu có thêm ô chọn Mùa giải)
>
> **Ghi chú 2 — điều kiện chặn xóa của từng use case con** (chi tiết hóa ngoại lệ 5c):
> - *Quản lý mùa giải:* chặn xóa khi mùa giải đã có chặng đua, đã có đội tham gia hoặc đã có bản ghi trao giải.
> - *Quản lý tay đua:* chặn xóa khi tay đua đã có hợp đồng, đã đăng ký chặng hoặc đã được trao giải.
> - *Quản lý đội đua:* chặn xóa khi đội đã tham gia mùa giải, đã có hợp đồng với tay đua hoặc đã đăng ký chặng.
> - *Quản lý chặng đua:* chặn xóa khi chặng đã có tay đua đăng ký hoặc đã có kết quả.
>
> **Ghi chú 3 — ràng buộc riêng của use case con *Quản lý chặng đua*:** số vòng phải là số nguyên dương; thời gian chặng phải nằm trong khoảng thời gian của mùa giải được chọn. Vi phạm thì hệ thống báo lỗi ở bước 8 và quay lại bước 7.

## 3. Đăng ký đội tham gia mùa giải (actor: Nhân viên)

| Mục | Nội dung |
|---|---|
| **Use case** | Đăng ký đội tham gia mùa giải |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập; danh mục đã có ít nhất một mùa giải và một đội đua |
| **Hậu điều kiện** | Các bản ghi tham gia (mùa giải ↔ đội đua) được lưu vào cơ sở dữ liệu, làm nguồn dữ liệu cho ô chọn đội đua ở use case *Ký hợp đồng tay đua với đội đua* và *Đăng ký tay đua tham gia chặng đua* |
| **Kịch bản chính** | 1. Nhân viên chọn menu "Đăng ký đội tham gia mùa giải".<br>2. Hệ thống hiển thị màn hình đăng ký: ô chọn "Mùa giải" (danh sách thả xuống) đang rỗng, bảng danh sách đội đang rỗng, nút [Lưu] **chưa được active**.<br>3. Nhân viên chọn mùa giải `2025 — FIA Formula One World Championship`.<br>4. Hệ thống hiển thị bảng toàn bộ đội đua trong danh mục, gồm các cột (ô tick) \| Mã \| Tên đội \| Hãng \| Trạng thái, ví dụ 6 dòng: `FER \| Ferrari \| Ferrari \| chưa tham gia`, `RBR \| Red Bull \| Honda RBPT \| chưa tham gia`, `MER \| Mercedes \| Mercedes \| chưa tham gia`, `MCL \| McLaren \| Mercedes \| chưa tham gia`, `AST \| Aston Martin \| Mercedes \| chưa tham gia`, `WIL \| Williams \| Mercedes \| chưa tham gia`; nút [Lưu] được active.<br>5. Nhân viên tick chọn 6 đội: Ferrari, Red Bull, Mercedes, McLaren, Aston Martin, Williams.<br>6. Nhân viên click [Lưu].<br>7. Hệ thống kiểm tra ràng buộc "một đội chỉ tham gia một mùa giải một lần", bỏ qua các đội đã có bản ghi tham gia.<br>8. Hệ thống sinh bản ghi tham gia cho từng đội mới được tick và lưu vào cơ sở dữ liệu.<br>9. Hệ thống hiển thị lại bảng danh sách với cột Trạng thái của 6 dòng chuyển thành "đã tham gia" và thông báo "Đã đăng ký 6 đội tham gia mùa giải 2025". |
| **Ngoại lệ** | 4a. Mùa giải đã có đội tham gia từ trước → các đội đó được **tick sẵn**, cột Trạng thái ghi "đã tham gia" và ô tick bị khóa, nhân viên chỉ tick thêm được các đội chưa tham gia.<br>4b. Toàn bộ đội trong danh mục đều đã tham gia mùa giải được chọn → hệ thống hiển thị bảng với tất cả ô tick bị khóa và dòng chữ "Tất cả đội đã tham gia mùa giải này", nút [Lưu] không được active.<br>6a. Nhân viên click [Lưu] khi chưa tick đội nào mới → hệ thống báo lỗi "Vui lòng chọn ít nhất một đội đua", quay lại bước 5.<br>7a. Một đội được tick nhưng trong lúc thao tác đã bị người dùng khác đăng ký cho cùng mùa giải → hệ thống bỏ qua đội đó, không tạo bản ghi trùng, và ghi rõ trong thông báo ở bước 9. |

> **Ghi chú — ràng buộc** (thay cho dòng "Ràng buộc" đã bỏ khỏi bảng đặc tả để giữ đúng mẫu 6 dòng): một đội đua chỉ được tham gia một mùa giải **một lần duy nhất**; ràng buộc này được bảo đảm ở hai mức — hệ thống khóa ô tick của các đội đã tham gia (bước 4a) và kiểm tra lại trước khi lưu (bước 7). Bản ghi tham gia không có thuộc tính riêng, chỉ nối mùa giải với đội đua.
