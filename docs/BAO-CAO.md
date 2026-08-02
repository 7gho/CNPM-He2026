# BÁO CÁO ĐỒ ÁN MÔN NHẬP MÔN CÔNG NGHỆ PHẦN MỀM

## Đề tài: Quản lý giải đua xe F1

**Nhóm:** Nhóm 3 — Học viện Công nghệ Bưu chính Viễn thông

**Giảng viên hướng dẫn:** Đào Ngọc Phong

| Thành viên | MSSV | Vai trò | Phần phụ trách (use case) |
|---|---|---|---|
| Khuất Anh Quân | B22DCVT421 | Trưởng nhóm | Module 1 — Ký hợp đồng tay đua với đội đua |
| Trần Xuân Kiên | B22DCVT269 | Thành viên | Module 2 — Đăng ký tay đua tham gia chặng đua |
| Nguyễn Minh Kiệt | B22DCVT270 | Thành viên | Module 3 — Cập nhật kết quả chặng đua |
| Phùng Tuấn Thành | B22DCVT517 | Thành viên | Module 4 — Quyết toán và trao giải cuối mùa |

---

## Mục lục

**PHẦN 1 — CÔNG VIỆC CHUNG CỦA NHÓM**

- **CHƯƠNG 1: Mô tả yêu cầu bài toán, yêu cầu người dùng**
  - 1.1. Giới thiệu — mục đích hệ thống
  - 1.2. Phạm vi hệ thống
  - 1.3. Mô tả chi tiết hoạt động nghiệp vụ của từng chức năng
  - 1.4. Các đối tượng được quản lý và thuộc tính
  - 1.5. Quan hệ số lượng giữa các đối tượng
  - 1.6. Các ràng buộc nghiệp vụ
- **CHƯƠNG 2: Mô tả yêu cầu phần mềm**
  - 2.1. Phân tích và xác định actor
  - 2.2. Yêu cầu chức năng — danh sách use case
  - 2.3. Yêu cầu phi chức năng
  - 2.4. Biểu đồ Use Case tổng quát
- **CHƯƠNG 3: Xây dựng biểu đồ lớp thực thể**
  - 3.1. Phân tích và xác định các thực thể (trích danh từ)
  - 3.2. Mô tả thực thể (thuộc tính, phương thức)
  - 3.3. Quan hệ giữa các lớp thực thể
  - 3.4. Biểu đồ lớp thực thể — pha phân tích
  - 3.5. Biểu đồ lớp thực thể — pha thiết kế
  - 3.6. Thiết kế cơ sở dữ liệu (kèm biểu đồ CSDL)
  - 3.7. Thiết kế triển khai (package view / dao / model)

**PHẦN 2 — KẾT QUẢ TỪNG THÀNH VIÊN**

- **CHƯƠNG 4: Module 1 — Ký hợp đồng tay đua với đội đua (Khuất Anh Quân)**
  - 4.1. Biểu đồ Use Case chi tiết · 4.2. Đặc tả Use Case · 4.3. Biểu đồ trạng thái (phân tích hoạt động) · 4.4. Biểu đồ lớp phân tích · 4.5. Biểu đồ lớp thiết kế · 4.6. Biểu đồ hoạt động (pha thiết kế) · 4.7. Thuyết minh (kịch bản phiên bản 3) · 4.8. Biểu đồ tuần tự · 4.9. Test case
- **CHƯƠNG 5: Module 2 — Đăng ký tay đua tham gia chặng đua (Trần Xuân Kiên)**
  - 5.1. Biểu đồ Use Case chi tiết · 5.2. Đặc tả Use Case · 5.3. Biểu đồ trạng thái (phân tích hoạt động) · 5.4. Biểu đồ lớp phân tích · 5.5. Biểu đồ lớp thiết kế · 5.6. Biểu đồ hoạt động (pha thiết kế) · 5.7. Thuyết minh (kịch bản phiên bản 3) · 5.8. Biểu đồ tuần tự · 5.9. Test case
- **CHƯƠNG 6: Module 3 — Cập nhật kết quả chặng đua (Nguyễn Minh Kiệt)**
  - 6.1. Biểu đồ Use Case chi tiết · 6.2. Đặc tả Use Case · 6.3. Biểu đồ trạng thái (phân tích hoạt động) · 6.4. Biểu đồ lớp phân tích · 6.5. Biểu đồ lớp thiết kế · 6.6. Biểu đồ hoạt động (pha thiết kế) · 6.7. Thuyết minh (kịch bản phiên bản 3) · 6.8. Biểu đồ tuần tự · 6.9. Test case
- **CHƯƠNG 7: Module 4 — Quyết toán và trao giải cuối mùa (Phùng Tuấn Thành)**
  - 7.1. Biểu đồ Use Case chi tiết · 7.2. Đặc tả Use Case · 7.3. Biểu đồ trạng thái (phân tích hoạt động) · 7.4. Biểu đồ lớp phân tích · 7.5. Biểu đồ lớp thiết kế · 7.6. Biểu đồ hoạt động (pha thiết kế) · 7.7. Thuyết minh (kịch bản phiên bản 3) · 7.8. Biểu đồ tuần tự · 7.9. Test case
- **CHƯƠNG 8: Kết luận**

---

# PHẦN 1 — CÔNG VIỆC CHUNG CỦA NHÓM

## CHƯƠNG 1: MÔ TẢ YÊU CẦU BÀI TOÁN, YÊU CẦU NGƯỜI DÙNG

### 1.1. Giới thiệu — mục đích hệ thống

Giải đua xe Công thức 1 (Formula 1 — F1) là giải đấu thể thao tốc độ thường niên quy mô toàn cầu: mỗi năm có một giải vô địch, mỗi giải gồm nhiều chặng đua diễn ra khắp thế giới với nhiều đội đua tham gia, mỗi đội đua có nhiều tay đua.

Mục đích của hệ thống **Quản lý giải đua xe F1** là hỗ trợ ban tổ chức giải quản lý toàn bộ vòng đời một mùa giải: khai báo danh mục nền (mùa giải, chặng đua, đội đua, tay đua), ghi nhận việc các đội đăng ký tham gia mùa giải, quản lý hợp đồng giữa tay đua và đội đua, đăng ký tay đua tham gia từng chặng đua, cập nhật kết quả và tính điểm sau mỗi chặng, và cuối cùng là quyết toán, xếp hạng, trao giải cá nhân và đồng đội khi mùa giải kết thúc.

Trước khi có phần mềm, các công việc trên được làm thủ công trên giấy tờ và bảng tính, dẫn tới ba khó khăn chính: (a) khó kiểm soát ràng buộc "tại một thời điểm một tay đua chỉ thuộc một đội" khi tay đua chuyển đội giữa mùa; (b) dễ sai sót khi cộng dồn điểm của hàng chục tay đua qua hàng chục chặng; (c) khó phân định thứ hạng khi hai tay đua hoặc hai đội bằng điểm. Hệ thống được xây dựng để tự động hóa và kiểm soát chặt ba điểm này.

Hệ thống gồm 4 phân hệ (module) nghiệp vụ chính, mỗi thành viên phụ trách một phân hệ: (1) Ký hợp đồng tay đua với đội đua, (2) Đăng ký tay đua tham gia chặng đua, (3) Cập nhật kết quả chặng đua, (4) Quyết toán và trao giải cuối mùa.

### 1.2. Phạm vi hệ thống

Hệ thống có hai nhóm người dùng, đều là thành viên có tài khoản đăng nhập: **Nhân viên** (ban tổ chức) và **Quản lý**. Mỗi vai trò được thực hiện các chức năng sau:

| Người dùng (actor) | Được thực hiện các chức năng |
|---|---|
| **Thành viên** (vai trò trừu tượng, cha của hai vai trò dưới) | 1. Đăng nhập<br>2. Đổi mật khẩu |
| **Nhân viên** (kế thừa Thành viên) | 3. Quản lý mùa giải<br>4. Quản lý tay đua<br>5. Quản lý đội đua<br>6. Quản lý chặng đua<br>7. Đăng ký đội tham gia mùa giải<br>8. Ký hợp đồng tay đua với đội đua *(Module 1)*<br>9. Đăng ký tay đua tham gia chặng đua *(Module 2)*<br>10. Cập nhật kết quả chặng đua *(Module 3)* |
| **Quản lý** (kế thừa Thành viên) | 11. Quyết toán và trao giải cuối mùa *(Module 4)* |

Bốn chức năng 3–6 có cùng dạng thao tác: tìm / thêm / sửa / xóa trên một danh mục.

Ngoài hai vai trò trên, hệ thống không phục vụ trực tiếp đối tượng nào khác. Đội đua và tay đua chỉ **tham gia gián tiếp**: họ gửi yêu cầu (yêu cầu ký hợp đồng, yêu cầu đăng ký thi đấu) cho nhân viên, còn thao tác trên phần mềm do nhân viên thực hiện. Khán giả và báo chí không có tài khoản, không xem được dữ liệu qua hệ thống này.

> **Những chức năng không đề cập đến thì mặc định là không thuộc phạm vi của hệ thống.**

Cụ thể, các nội dung sau **không** thuộc phạm vi: bán vé và quản lý khán giả; quản lý hãng sản xuất xe và thông số kỹ thuật xe; quản lý nhân sự kỹ thuật của đội đua; tính toán thời gian vòng chạy trực tuyến trong lúc đua; xử phạt và khiếu nại của ban trọng tài; thanh toán tiền thưởng thực tế qua ngân hàng (hệ thống chỉ lưu quyết định trao giải và số tiền thưởng).

### 1.3. Mô tả chi tiết hoạt động nghiệp vụ của từng chức năng

#### 1.3.1. Đăng nhập

Thành viên mở phần mềm → hệ thống hiển thị màn hình đăng nhập gồm ô nhập **Tên đăng nhập**, ô nhập **Mật khẩu** (hiển thị dạng dấu chấm) và nút **Đăng nhập**; các ô đang rỗng → thành viên nhập tên đăng nhập (ví dụ `nv01`) và mật khẩu, click **Đăng nhập** → hệ thống **kiểm tra tên đăng nhập có tồn tại không và mật khẩu có khớp không** → nếu sai, hệ thống báo lỗi "Tên đăng nhập hoặc mật khẩu không đúng", giữ nguyên màn hình đăng nhập và xóa ô mật khẩu, yêu cầu nhập lại → nếu đúng, hệ thống tạo phiên đăng nhập, đọc vai trò của tài khoản → nếu vai trò là **Nhân viên**, hệ thống hiển thị màn hình chính với các menu: Quản lý mùa giải, Quản lý tay đua, Quản lý đội đua, Quản lý chặng đua, Đăng ký đội tham gia mùa giải, Ký hợp đồng, Đăng ký chặng, Nhập kết quả chặng, Đổi mật khẩu, Đăng xuất → nếu vai trò là **Quản lý**, hệ thống hiển thị màn hình chính với các menu: Quyết toán và trao giải, Đổi mật khẩu, Đăng xuất.

#### 1.3.2. Đổi mật khẩu

Thành viên đã đăng nhập chọn menu **Đổi mật khẩu** → hệ thống hiển thị màn hình đổi mật khẩu gồm dòng chữ hiển thị họ tên và tên đăng nhập của người đang đăng nhập, ba ô nhập **Mật khẩu cũ**, **Mật khẩu mới**, **Nhập lại mật khẩu mới** và nút **Lưu**; ba ô đang rỗng → thành viên nhập mật khẩu cũ, nhập mật khẩu mới, nhập lại mật khẩu mới rồi click **Lưu** → hệ thống **kiểm tra mật khẩu cũ có khớp với mật khẩu đang lưu không** → nếu không khớp, báo lỗi "Mật khẩu cũ không đúng", xóa ba ô và yêu cầu nhập lại → hệ thống **kiểm tra hai ô mật khẩu mới có giống nhau không** → nếu khác nhau, báo lỗi "Nhập lại mật khẩu mới không khớp" → nếu hợp lệ, hệ thống lưu mật khẩu mới cho tài khoản, hiển thị thông báo "Đổi mật khẩu thành công" và quay về màn hình chính; lần đăng nhập sau thành viên phải dùng mật khẩu mới.

#### 1.3.3. Quản lý mùa giải

Nhân viên chọn menu **Quản lý mùa giải** → hệ thống hiển thị màn hình danh mục mùa giải gồm ô nhập **Năm** hoặc **Tên giải** để tìm, nút **Tìm**, nút **Thêm mới**, và bảng danh sách mùa giải với các cột: Năm, Tên giải, Trạng thái, Số chặng, kèm hai nút **Sửa** và **Xóa** trên mỗi dòng; ban đầu bảng hiển thị toàn bộ mùa giải đang có, ví dụ một dòng `2025 | FIA Formula One World Championship | Đang diễn ra | 24` → nhân viên nhập từ khóa và click **Tìm** → hệ thống hiển thị các mùa giải có năm hoặc tên chứa từ khóa.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu nhập gồm các ô: Tên giải, Năm, Trạng thái và nút **Lưu**; các ô đang rỗng → nhân viên nhập `FIA Formula One World Championship`, `2026`, `Đang diễn ra` rồi click **Lưu** → hệ thống **kiểm tra năm đã tồn tại chưa và các ô bắt buộc đã nhập chưa** → nếu năm đã có, báo lỗi "Mùa giải năm 2026 đã tồn tại" → nếu hợp lệ, hệ thống lưu mùa giải mới và hiển thị lại bảng danh sách có thêm dòng vừa nhập.
- **Sửa:** nhân viên click **Sửa** trên một dòng → hệ thống hiển thị biểu mẫu đã điền sẵn dữ liệu của dòng đó → nhân viên sửa và click **Lưu** → hệ thống kiểm tra như khi thêm mới rồi cập nhật, hiển thị lại bảng danh sách.
- **Xóa:** nhân viên click **Xóa** trên một dòng → hệ thống hiển thị hộp xác nhận "Bạn có chắc muốn xóa mùa giải 2026?" với nút **Đồng ý** và **Hủy** → nhân viên click **Đồng ý** → hệ thống **kiểm tra mùa giải có chặng đua, có đội tham gia hoặc đã có bản ghi trao giải hay không** → nếu có, hệ thống từ chối và báo lỗi "Không thể xóa: mùa giải đang có 24 chặng đua" → nếu không, hệ thống xóa và hiển thị lại bảng danh sách.

#### 1.3.4. Quản lý tay đua

Nhân viên chọn menu **Quản lý tay đua** → hệ thống hiển thị màn hình danh mục tay đua gồm ô nhập **Tên tay đua**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử, kèm nút **Sửa** và **Xóa** trên mỗi dòng → nhân viên nhập `Hamilton` và click **Tìm** → hệ thống hiển thị các tay đua có tên chứa từ khóa, ví dụ một dòng `HAM | Lewis Hamilton | 07/01/1985 | Anh | Bảy lần vô địch thế giới`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm các ô: Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử và nút **Lưu** → nhân viên nhập `ANT`, `Andrea Kimi Antonelli`, `25/08/2006`, `Ý`, tiểu sử rồi click **Lưu** → hệ thống **kiểm tra mã tay đua đã tồn tại chưa và các ô bắt buộc (mã, tên) đã nhập chưa** → nếu mã trùng, báo lỗi "Mã tay đua ANT đã tồn tại" → nếu hợp lệ, hệ thống lưu và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa** trên một dòng → hệ thống hiển thị biểu mẫu điền sẵn dữ liệu → nhân viên sửa (ví dụ bổ sung tiểu sử) và click **Lưu** → hệ thống cập nhật và hiển thị lại bảng.
- **Xóa:** nhân viên click **Xóa** → hệ thống hỏi xác nhận → nhân viên đồng ý → hệ thống **kiểm tra tay đua đã có hợp đồng, đã đăng ký chặng hoặc đã được trao giải hay chưa** → nếu có, từ chối và báo lỗi "Không thể xóa: tay đua đang có hợp đồng với Ferrari" → nếu không, hệ thống xóa và hiển thị lại bảng.

#### 1.3.5. Quản lý đội đua

Nhân viên chọn menu **Quản lý đội đua** → hệ thống hiển thị màn hình danh mục đội đua gồm ô nhập **Tên đội**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên, Hãng, Mô tả, kèm nút **Sửa** và **Xóa** trên mỗi dòng → nhân viên nhập `Ferrari` và click **Tìm** → hệ thống hiển thị dòng `FER | Ferrari | Ferrari | Đội đua lâu đời nhất F1`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm các ô: Mã, Tên, Hãng, Mô tả và nút **Lưu** → nhân viên nhập `MCL`, `McLaren`, `Mercedes`, mô tả rồi click **Lưu** → hệ thống **kiểm tra mã đội đã tồn tại chưa và các ô bắt buộc đã nhập chưa** → nếu hợp lệ, hệ thống lưu và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa**, hệ thống hiển thị biểu mẫu điền sẵn → nhân viên sửa hãng hoặc mô tả rồi click **Lưu** → hệ thống cập nhật.
- **Xóa:** nhân viên click **Xóa**, xác nhận → hệ thống **kiểm tra đội đã tham gia mùa giải nào, đã có hợp đồng với tay đua nào hoặc đã đăng ký chặng nào chưa** → nếu có, từ chối và báo lỗi cụ thể → nếu không, hệ thống xóa.

#### 1.3.6. Quản lý chặng đua

Nhân viên chọn menu **Quản lý chặng đua** → hệ thống hiển thị màn hình danh mục chặng đua gồm ô chọn **Mùa giải** (danh sách thả xuống, mặc định chọn mùa giải hiện tại `2025`), ô nhập **Tên chặng**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên chặng, Số vòng, Địa điểm, Thời gian, Mô tả, kèm nút **Sửa** và **Xóa** trên mỗi dòng → hệ thống hiển thị các chặng của mùa giải đang chọn, sắp xếp tăng dần theo thời gian, ví dụ `R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | ...`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm ô chọn Mùa giải và các ô: Mã, Tên chặng, Số vòng, Địa điểm, Thời gian, Mô tả và nút **Lưu** → nhân viên nhập `R02`, `Chinese Grand Prix`, `56`, `Thượng Hải`, `23/03/2025`, mô tả rồi click **Lưu** → hệ thống **kiểm tra mã chặng đã tồn tại chưa, số vòng có phải số nguyên dương không, thời gian chặng có nằm trong mùa giải đã chọn không** → nếu vi phạm, báo lỗi tương ứng và yêu cầu nhập lại → nếu hợp lệ, hệ thống lưu chặng đua thuộc mùa giải đã chọn và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa** → hệ thống hiển thị biểu mẫu điền sẵn → nhân viên sửa (ví dụ đổi thời gian chặng) rồi click **Lưu** → hệ thống kiểm tra như trên rồi cập nhật.
- **Xóa:** nhân viên click **Xóa**, xác nhận → hệ thống **kiểm tra chặng đã có tay đua đăng ký hoặc đã có kết quả hay chưa** → nếu có, từ chối và báo lỗi "Không thể xóa: chặng đã có kết quả thi đấu" → nếu không, hệ thống xóa.

#### 1.3.7. Đăng ký đội tham gia mùa giải

Nhân viên chọn menu **Đăng ký đội tham gia mùa giải** → hệ thống hiển thị màn hình đăng ký gồm ô chọn **Mùa giải** (danh sách thả xuống) và một bảng rỗng, nút **Lưu** chưa được active → nhân viên chọn mùa giải `2025` → hệ thống hiển thị bảng danh sách toàn bộ đội đua trong danh mục, mỗi dòng gồm ô tick, Mã, Tên đội, Hãng và cột **Trạng thái** ghi "đã tham gia" hoặc "chưa tham gia" mùa giải đang chọn; các đội đã tham gia được tick sẵn và không cho bỏ tick; nút **Lưu** được active → nhân viên tick chọn các đội đăng ký tham gia mùa giải (ví dụ tick `Ferrari`, `Red Bull`, `Mercedes`, `McLaren`, `Aston Martin`, `Williams`) → nhân viên click **Lưu** → hệ thống **kiểm tra ràng buộc: một đội chỉ được tham gia một mùa giải một lần** (bỏ qua các đội đã có bản ghi tham gia, không tạo bản ghi trùng) → hệ thống sinh bản ghi tham gia cho từng đội mới được tick, lưu vào cơ sở dữ liệu → hệ thống hiển thị lại bảng danh sách với cột Trạng thái đã cập nhật và thông báo "Đã đăng ký 6 đội tham gia mùa giải 2025"; danh sách này là nguồn dữ liệu cho ô chọn đội đua ở các chức năng ký hợp đồng và đăng ký chặng.

#### 1.3.8. Ký hợp đồng tay đua với đội đua (Module 1)

*Mô tả nghiệp vụ:* Nhân viên quản lý giải ghi nhận việc ký hợp đồng mới hoặc chuyển đội của tay đua với các đội đua, bảo đảm ràng buộc "tại một thời điểm tay đua chỉ thuộc một đội".

*Luồng nghiệp vụ:* Nhân viên chọn chức năng **Ký hợp đồng** → hệ thống hiển thị màn hình tìm tay đua theo tên → nhân viên nhập tên và click **Tìm** → hệ thống hiển thị danh sách tay đua có tên chứa từ khóa, mỗi dòng gồm mã, tên, ngày sinh, quốc tịch, đội hiện tại; nếu tay đua chưa có trong hệ thống thì nhân viên thêm mới tay đua ngay tại màn hình này (mã, tên, ngày sinh, quốc tịch, tiểu sử) → nhân viên click chọn đúng tay đua → hệ thống hiển thị màn hình nhập hợp đồng kèm lịch sử thi đấu của tay đua, mỗi dòng một giai đoạn gồm tên đội, ngày bắt đầu, ngày kết thúc (**dòng có ngày kết thúc trống là hợp đồng đang hiệu lực**) → nhân viên chọn đội đua từ danh sách thả xuống và **chỉ nhập ngày bắt đầu hiệu lực** (hợp đồng mở, ngày kết thúc để trống), rồi click **Lưu** → hệ thống **kiểm tra ràng buộc: tại một thời điểm tay đua chỉ thuộc một đội** — nếu tay đua còn hợp đồng đang hiệu lực thì **tự động đóng hợp đồng cũ** bằng ngày liền trước ngày bắt đầu mới; nếu ngày bắt đầu chồng lấn khoảng thời gian của một hợp đồng **đã đóng** trong lịch sử thì báo lỗi và yêu cầu nhập lại → hệ thống lưu hợp đồng mới vào cơ sở dữ liệu, in phiếu xác nhận hợp đồng và hiển thị lại lịch sử thi đấu đã cập nhật.

#### 1.3.9. Đăng ký tay đua tham gia chặng đua (Module 2)

*Mô tả nghiệp vụ:* Trước mỗi chặng đua, nhân viên chốt danh sách tay đua thi đấu của từng đội theo yêu cầu của đội đua.

*Luồng nghiệp vụ:* Nhân viên chọn chức năng **Đăng ký thi đấu** → hệ thống hiển thị màn hình chọn chặng và đội → nhân viên chọn chặng đua từ danh sách thả xuống và chọn đội đua từ danh sách thả xuống, rồi click **Tiếp tục** → hệ thống hiển thị danh sách các tay đua **đang có hợp đồng hiệu lực với đội tại thời điểm diễn ra chặng** (dữ liệu kế thừa từ Module 1), **sắp xếp theo thứ tự alphabet của tên**, kèm cột trạng thái "đã đăng ký chặng này cho đội khác hay chưa" → nhân viên tick chọn tay đua theo yêu cầu của đội → nhân viên click **Lưu** → hệ thống **kiểm tra ràng buộc: tối đa 2 tay đua/đội/chặng và mỗi tay đua chỉ được đăng ký 1 lần trong một chặng** (vi phạm thì báo lỗi ngay, không cho lưu) → hệ thống lưu danh sách đăng ký và hiển thị danh sách xuất phát (start list) của chặng, mỗi dòng gồm tên đội và các tay đua đã đăng ký, cho phép in gửi ban tổ chức → trước ngày đua, nhân viên có thể mở lại chặng và đội để thay tay đua; hệ thống kiểm tra lại các ràng buộc như trên.

#### 1.3.10. Cập nhật kết quả chặng đua (Module 3)

*Mô tả nghiệp vụ:* Sau khi chặng đua kết thúc, nhân viên nhập kết quả thi đấu thực tế để hệ thống tự động xếp hạng và tính điểm.

*Luồng nghiệp vụ:* Nhân viên chọn chức năng **Cập nhật kết quả chặng đua** → hệ thống hiển thị màn hình chọn chặng → nhân viên chọn chặng đua từ danh sách thả xuống và click **Tiếp tục** → hệ thống hiển thị bảng các tay đua đã đăng ký chặng (dữ liệu từ Module 2), mỗi dòng có ô nhập: thời gian về đích, số vòng hoàn thành và ô chọn trạng thái "Hoàn thành / Bỏ cuộc–tai nạn (DNF) / Bị loại (DSQ)" → nhân viên nhập đủ kết quả cho tất cả tay đua rồi click **Tính kết quả** → hệ thống **tự động xếp hạng theo thời gian về đích** (tay đua DNF hoặc DSQ xếp cuối) và **gán điểm cho top 10 theo thứ tự 25, 18, 15, 12, 10, 8, 6, 4, 2, 1**; tay đua nằm trong top 10 nhưng DNF hoặc DSQ nhận 0 điểm → hệ thống hiển thị bảng kết quả chặng để đối soát (hạng, tên tay đua, tên đội, thời gian, số vòng, trạng thái, điểm) → nhân viên kiểm tra và click **Lưu** → nếu chặng đã có kết quả cũ, hệ thống **cảnh báo ghi đè**, xóa kết quả cũ và tính lại điểm toàn bộ chặng; hệ thống lưu kết quả và điểm của từng tay đua vào cơ sở dữ liệu rồi in bảng kết quả chặng.

#### 1.3.11. Quyết toán và trao giải cuối mùa (Module 4)

*Mô tả nghiệp vụ:* Quản lý xem bảng xếp hạng cá nhân và bảng xếp hạng đội tính đến chặng bất kỳ, xem chi tiết kết quả từng chặng của một tay đua/đội (drill-down); khi mùa giải kết thúc và đủ kết quả, quản lý thực hiện quyết toán: chốt bảng tổng sắp cuối mùa, nhập mức thưởng, tính tiền thưởng và lưu quyết định trao giải.

*Luồng nghiệp vụ:* Quản lý chọn chức năng **Quyết toán mùa giải** → hệ thống lấy mùa giải hiện tại và hiển thị màn hình **Bảng tổng sắp** gồm ô chọn **Chặng đua** (danh sách thả xuống các chặng của mùa, mặc định là chặng gần nhất đã có kết quả), hai bảng xếp hạng và nút **Tiếp tục** chưa được active → quản lý chọn một chặng (ví dụ chọn Abu Dhabi Grand Prix — chặng cuối — để xem bảng cuối mùa) → hệ thống **cộng dồn tổng điểm, tổng thời gian và số lần đạt từng thứ hạng của mỗi tay đua và mỗi đội tính từ chặng đầu mùa đến hết chặng được chọn**, trong đó điểm của tay đua ở mỗi chặng được cộng cho **đội mà tay đua đã đăng ký tại chặng đó** (xử lý đúng trường hợp đổi đội giữa mùa) → hệ thống sắp xếp theo **ba tầng tiêu chí: giảm dần tổng điểm; nếu bằng điểm thì countback — so số lần về nhất, vẫn bằng thì số lần về nhì, rồi về ba…; nếu countback vẫn bằng thì tăng dần tổng thời gian** → hệ thống hiển thị bảng xếp hạng cá nhân (Hạng, Tên tay đua, Quốc tịch, Tên đội, Tổng điểm, Tổng thời gian) và bảng xếp hạng đội (Hạng, Tên đội, Hãng, Tổng điểm, Tổng thời gian) → quản lý có thể **click vào một dòng tay đua hoặc một dòng đội** → hệ thống hiển thị màn hình **Chi tiết theo chặng**: với tay đua là bảng (Tên chặng, Hạng về đích, Điểm, Thời gian về đích), với đội là bảng (Tên chặng, Tổng điểm, Tổng thời gian của 2 tay đua), kèm nút **Quay lại** để trở về bảng tổng sắp → khi mùa giải ở trạng thái "Đã kết thúc", chặng được chọn là chặng cuối và hệ thống **kiểm tra tất cả các chặng đã có kết quả** (còn chặng chưa nhập kết quả thì báo lỗi kèm tên chặng và từ chối quyết toán), nút **Tiếp tục** được active → quản lý click **Tiếp tục** → hệ thống hiển thị màn hình **Trao giải**: sáu ô nhập mức thưởng (cá nhân hạng 1, 2, 3 và đội hạng 1, 2, 3) đang rỗng, bảng Danh sách trao giải 6 dòng với **cột Tiền thưởng rỗng**, nút **Tính thưởng** active và nút **Lưu** chưa active → quản lý nhập mức thưởng cho từng hạng rồi click **Tính thưởng** → hệ thống **kiểm tra mức thưởng là số không âm** → nếu vi phạm, báo lỗi và giữ nguyên màn hình → hợp lệ thì hệ thống **tính tiền thưởng tương ứng cho từng tay đua/đội theo hạng đạt được**, điền cột Tiền thưởng và bật nút **Lưu** (quản lý có thể lặp lại bước nhập – tính thưởng nhiều lần) → quản lý click **Lưu** → nếu mùa giải đã có quyết định trao giải trước đó, hệ thống cảnh báo và hỏi xác nhận ghi đè → hệ thống lưu các bản ghi trao giải vào cơ sở dữ liệu và in danh sách trao giải mùa giải (hạng, tên tay đua/đội, tổng điểm, tiền thưởng).

### 1.4. Các đối tượng được quản lý và thuộc tính

**a. Nhóm con người**

| Đối tượng | Thuộc tính |
|---|---|
| **Tay đua** | mã, tên, ngày sinh, quốc tịch, tiểu sử |
| **Thành viên** (tài khoản người dùng) | tên đăng nhập, mật khẩu, họ tên |
| **Nhân viên** | kế thừa Thành viên |
| **Quản lý** | kế thừa Thành viên |

**b. Nhóm đơn vị tổ chức**

| Đối tượng | Thuộc tính |
|---|---|
| **Đội đua** | mã, tên, hãng, mô tả |

> Đề bài có nhắc tới **hãng** xe của đội đua. Vì hệ thống không có chức năng quản lý hãng đua (không thuộc phạm vi ở mục 1.2), hãng được giữ làm **thuộc tính** của đội đua chứ không tách thành đối tượng riêng.

**c. Nhóm chuyên môn vận hành**

| Đối tượng | Thuộc tính |
|---|---|
| **Mùa giải** | tên, năm, trạng thái |
| **Chặng đua** | mã, tên, số vòng, địa điểm, thời gian, mô tả |
| **Hợp đồng** | ngày bắt đầu, ngày kết thúc (để trống = đang hiệu lực) |
| **Tham gia** (đội tham gia mùa giải) | không có thuộc tính riêng, chỉ nối mùa giải với đội đua |
| **Đăng ký chặng** | không có thuộc tính riêng, chỉ nối chặng đua với tay đua và đội đua |

**d. Nhóm kết quả**

| Đối tượng | Thuộc tính |
|---|---|
| **Kết quả** | thời gian, số vòng hoàn thành, trạng thái (Hoàn thành / DNF / DSQ), hạng, điểm |
| **Trao giải** | loại (cá nhân / đồng đội), hạng, tiền thưởng |

### 1.5. Quan hệ số lượng giữa các đối tượng

- Một **mùa giải** có nhiều **chặng đua**; một chặng đua chỉ thuộc về một mùa giải.
- Một **mùa giải** có nhiều bản ghi **tham gia**; một bản ghi tham gia chỉ thuộc về một mùa giải.
- Một **đội đua** có nhiều bản ghi **tham gia** (tham gia nhiều mùa giải khác nhau); một bản ghi tham gia chỉ ứng với một đội đua.
- Một **tay đua** có nhiều **hợp đồng** (qua các thời kỳ khác nhau); một hợp đồng chỉ của một tay đua.
- Một **đội đua** có nhiều **hợp đồng**; một hợp đồng chỉ với một đội đua.
- Một **chặng đua** có nhiều bản ghi **đăng ký chặng**; một bản ghi đăng ký chặng chỉ thuộc về một chặng đua.
- Một **tay đua** có nhiều bản ghi **đăng ký chặng** (đăng ký nhiều chặng trong mùa); một bản ghi đăng ký chặng chỉ ứng với một tay đua.
- Một **đội đua** có nhiều bản ghi **đăng ký chặng**; một bản ghi đăng ký chặng chỉ ứng với một đội đua. Trong cùng một chặng, một đội có **tối đa 2** bản ghi đăng ký.
- Một bản ghi **đăng ký chặng** có **nhiều nhất một** **kết quả** (chưa có kết quả khi chặng chưa diễn ra); một kết quả chỉ thuộc về một bản ghi đăng ký chặng.
- Một **mùa giải** có nhiều bản ghi **trao giải**; một bản ghi trao giải chỉ thuộc về một mùa giải.
- Một **tay đua** có nhiều bản ghi **trao giải** (qua các mùa giải); một bản ghi trao giải cá nhân chỉ ứng với một tay đua.
- Một **đội đua** có nhiều bản ghi **trao giải**; một bản ghi trao giải đồng đội chỉ ứng với một đội đua.
- **Thành viên** là đối tượng cha; **nhân viên** và **quản lý** kế thừa thành viên.

Ba quan hệ nhiều–nhiều được tách bằng đối tượng trung gian: mùa giải – đội đua tách bằng **tham gia**; tay đua – đội đua (theo thời gian) tách bằng **hợp đồng**; chặng đua – tay đua tách bằng **đăng ký chặng**.

### 1.6. Các ràng buộc nghiệp vụ (business rules)

**a. Ràng buộc mùa giải và chặng đua:**
- Mỗi năm chỉ có đúng một giải vô địch (mùa giải). Một mùa giải gồm nhiều chặng đua diễn ra khắp thế giới (mã chặng đua, tên, số vòng đua, địa điểm, thời gian, mô tả).
- Mỗi mùa giải có nhiều đội đua tham gia (mã, tên, hãng, mô tả); mỗi đội đua có nhiều tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử).

**b. Ràng buộc hợp đồng tay đua – đội đua:**
- Tính duy nhất tại một thời điểm: tại bất kỳ thời điểm nào, một tay đua chỉ được có hợp đồng hiệu lực với **duy nhất một đội đua**; qua các khoảng thời gian khác nhau, tay đua có thể thi đấu cho nhiều đội.
- Hợp đồng có **ngày kết thúc để trống là hợp đồng đang hiệu lực**; khi ký hợp đồng mới, hợp đồng đang hiệu lực (nếu có) được tự động đóng bằng ngày liền trước ngày bắt đầu mới.
- Ngày bắt đầu của hợp đồng mới không được chồng lấn khoảng thời gian của các hợp đồng đã đóng trong lịch sử.

**c. Ràng buộc đăng ký thi đấu chặng:**
- Trong mỗi chặng đua, mỗi đội đua chỉ được đăng ký **tối đa 2 tay đua** tham gia thi đấu.
- Mỗi tay đua chỉ được đăng ký **1 lần trong một chặng** (không thể đăng ký cho hai đội trong cùng chặng).
- Tay đua được đăng ký phải đang có hợp đồng hiệu lực với đội đua tại thời điểm diễn ra chặng.

**d. Ràng buộc tính điểm chặng đua:**
- Kết quả chặng xếp hạng theo thứ tự về đích (thời gian hoàn thành tăng dần); tay đua DNF hoặc DSQ xếp cuối.
- Điểm chỉ tính cho **top 10**, lần lượt theo thứ tự về đích: 25 — 18 — 15 — 12 — 10 — 8 — 6 — 4 — 2 — 1; từ vị trí 11 trở đi không có điểm.
- Tay đua nằm trong top 10 nhưng không hoàn thành chặng đua (DNF do bỏ cuộc hoặc tai nạn) hoặc bị loại vì vi phạm kỹ thuật (DSQ) nhận **0 điểm** tại chặng đó.

**e. Ràng buộc tính điểm tổng kết mùa giải:**
- Điểm mùa giải cá nhân = tổng điểm tích lũy của tay đua qua tất cả các chặng trong mùa (tay đua chuyển đội giữa mùa vẫn bảo lưu điểm cá nhân).
- Điểm mùa giải của đội = tổng điểm các tay đua ghi được **khi đại diện cho đội đó tại từng chặng** (tay đua chuyển đội giữa mùa thì điểm ở mỗi chặng tính cho đội mà tay đua đăng ký ở chặng đó).
- Xếp hạng chung cuộc (cá nhân và đội) theo **ba tầng tiêu chí**: (1) giảm dần tổng điểm; (2) nếu bằng điểm thì phân định bằng **countback** — so số lần về nhất, rồi số lần về nhì, rồi về ba… cho đến khi phân định được (tầng bổ sung theo luật FIA); (3) nếu countback vẫn bằng thì xếp theo **tăng dần tổng thời gian** (theo mô tả bài toán). Tổng thời gian luôn được hiển thị trên bảng xếp hạng.

---

## CHƯƠNG 2: MÔ TẢ YÊU CẦU PHẦN MỀM

### 2.1. Phân tích và xác định actor

Hệ thống chỉ được dùng bởi hai vai người dùng thật: người vận hành giải hằng ngày (ký hợp đồng, đăng ký chặng, nhập kết quả) và người quản lý giải (quyết toán, trao giải cuối mùa). Cả hai đều có tài khoản, đều đăng nhập và đổi mật khẩu, nên phần chung được tách thành **actor trừu tượng `ThanhVien`**; `NhanVien` và `QuanLy` kế thừa `ThanhVien`.

| Actor | Loại | Mô tả | Kế thừa |
|---|---|---|---|
| `ThanhVien` | **trừu tượng** | Người dùng đã có tài khoản trong hệ thống. Không có người dùng thật nào chỉ là `ThanhVien` — lớp actor này chỉ giữ phần chung (đăng nhập, đổi mật khẩu). | — |
| `NhanVien` | cụ thể | Nhân viên vận hành giải: ký hợp đồng, đăng ký tay đua vào chặng, cập nhật kết quả chặng, quản lý các danh mục. | `ThanhVien` |
| `QuanLy` | cụ thể | Quản lý giải: quyết toán và trao giải cuối mùa. | `ThanhVien` |

**Actor gián tiếp.** Các bên liên quan còn lại trong mô tả bài toán:

| Bên liên quan | Tham gia gián tiếp vào use case nào | Vai trò |
|---|---|---|
| **Đội đua** | `Ký hợp đồng tay đua với đội đua`, `Đăng ký tay đua tham gia chặng đua`, `Quyết toán và trao giải cuối mùa` | Là **actor gián tiếp**. Đội đua không có tài khoản, không có màn hình nào trong hệ thống — mọi thao tác đều do `NhanVien` nhập hộ theo văn bản đội gửi. |
| **Ban tổ chức** | `Đăng ký tay đua tham gia chặng đua`, `Cập nhật kết quả chặng đua`, `Xem bảng tổng sắp` | "Ban tổ chức" chính là **tên gọi nghiệp vụ của vai `NhanVien`**. |
| **Tay đua** | `Ký hợp đồng tay đua với đội đua`, `Quyết toán và trao giải cuối mùa` | Là **actor gián tiếp**. Tay đua là **đối tượng được quản lý** (lớp thực thể `TayDua`), không đăng nhập, không thao tác trên hệ thống. |

### 2.2. Yêu cầu chức năng — danh sách use case

| Use case | Actor | Mô tả ngắn |
|---|---|---|
| Đăng nhập | Thành viên | Đăng nhập vào hệ thống bằng tên đăng nhập và mật khẩu, được phân quyền theo vai trò |
| Đổi mật khẩu | Thành viên | Đổi mật khẩu của tài khoản đang đăng nhập |
| **Quản lý danh mục** *(use case trừu tượng)* | Nhân viên | Use case cha, gộp bốn use case danh mục có cùng dạng thao tác tìm / thêm / sửa / xóa |
| Quản lý mùa giải | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho mùa giải |
| Quản lý tay đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho tay đua |
| Quản lý đội đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho đội đua |
| Quản lý chặng đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho chặng đua |
| Đăng ký đội tham gia mùa giải | Nhân viên | Chọn mùa giải, tick các đội đua tham gia, lưu bản ghi tham gia |
| **Ký hợp đồng tay đua với đội đua** *(Module 1)* | Nhân viên | Tìm tay đua, xem lịch sử hợp đồng, ký hợp đồng mới với một đội đua |
| **Đăng ký tay đua tham gia chặng đua** *(Module 2)* | Nhân viên | Chọn chặng và đội, tick tay đua đang có hợp đồng hiệu lực để đăng ký thi đấu |
| **Cập nhật kết quả chặng đua** *(Module 3)* | Nhân viên | Nhập thời gian, số vòng, trạng thái của từng tay đua; hệ thống xếp hạng và tính điểm |
| **Quyết toán và trao giải cuối mùa** *(Module 4)* | Quản lý | Xem bảng tổng sắp tính đến chặng bất kỳ, xem chi tiết theo chặng của một tay đua/đội, nhập mức thưởng, lưu quyết định trao giải |

#### 2.2.1. Chi tiết yêu cầu chức năng

**FR0 — Xác thực và tài khoản (chung)**
- FR0.1 Đăng nhập bằng tài khoản (tên đăng nhập, mật khẩu).
- FR0.2 Đổi mật khẩu cá nhân (kiểm tra mật khẩu cũ, xác nhận mật khẩu mới hai lần).
- FR0.3 Phân quyền theo vai trò: **Nhân viên** (danh mục + Module 1/2/3), **Quản lý** (Module 4).

**FR1 — Quản lý danh mục (chung, hỗ trợ)**
- FR1.1 Tìm/thêm/sửa/xóa **tay đua** (mã, tên, ngày sinh, quốc tịch, tiểu sử).
- FR1.2 Tìm/thêm/sửa/xóa **đội đua** (mã, tên, hãng, mô tả).
- FR1.3 Tìm/thêm/sửa/xóa **chặng đua** (mã, tên, số vòng, địa điểm, thời gian, mô tả) thuộc một mùa giải.
- FR1.4 Tìm/thêm/sửa/xóa **mùa giải** (tên, năm, trạng thái).
- FR1.5 **Đăng ký đội tham gia mùa giải**: chọn mùa giải, tick chọn các đội đua tham gia, hệ thống sinh bản ghi tham gia (một đội chỉ tham gia một mùa giải một lần).
- FR1.6 **Ràng buộc xóa:** không cho xóa đối tượng đang được đối tượng khác tham chiếu (mùa giải đã có chặng, tay đua đã có hợp đồng, đội đã tham gia mùa giải, chặng đã có đăng ký hoặc kết quả).

**FR2 — Ký hợp đồng tay đua với đội đua (Module 1)**
- FR2.1 Tìm tay đua theo tên; hiển thị danh sách hợp đồng cũ của tay đua được chọn.
- FR2.1b **Thêm mới tay đua ngay trong luồng ký hợp đồng:** nếu tìm không thấy tay đua trong hệ thống, nhân viên được phép thêm mới tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử) ngay tại màn hình tìm kiếm, sau đó tiếp tục ký hợp đồng cho tay đua vừa thêm mà không phải rời khỏi chức năng.
- FR2.2 Ký hợp đồng mới: chọn đội, **chỉ nhập ngày bắt đầu hiệu lực** (ngày kết thúc để trống = hợp đồng đang hiệu lực).
- FR2.3 **Ràng buộc (tại một thời điểm tay đua chỉ thuộc 1 đội):** (a) nếu tay đua còn hợp đồng đang hiệu lực → hệ thống **tự động đóng** hợp đồng cũ (đặt ngày kết thúc = ngày liền trước ngày bắt đầu mới), không báo lỗi; (b) nếu ngày bắt đầu mới **chồng lấn khoảng thời gian của hợp đồng đã đóng** (lịch sử) → báo lỗi, yêu cầu nhập lại.
- FR2.4 Lưu và in hợp đồng; hiển thị lại lịch sử hợp đồng đã cập nhật.

**FR3 — Đăng ký tay đua tham gia chặng đua (Module 2)**
- FR3.1 Chọn chặng đua và đội đua.
- FR3.2 Hiển thị danh sách tay đua đang có hợp đồng hiệu lực với đội tại thời điểm chặng, **sắp xếp theo alphabet của tên**, kèm **cột trạng thái** "đã đăng ký chặng này cho đội khác hay chưa".
- FR3.3 Tick chọn tay đua đăng ký.
- FR3.4 **Ràng buộc:** mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ đăng ký 1 lần trong chặng.
- FR3.5 Lưu và in phiếu đăng ký (danh sách xuất phát).
- FR3.6 **Chỉnh sửa đăng ký trước ngày đua**: mở lại chặng + đội, hệ thống hiển thị lại danh sách với các tay đua đang đăng ký được tick sẵn; nhân viên thay tay đua (bỏ tick / tick lại), hệ thống kiểm tra lại ràng buộc FR3.4 rồi lưu.

**FR4 — Cập nhật kết quả chặng đua (Module 3)**
- FR4.1 Chọn chặng; hiển thị bảng tay đua đã đăng ký để nhập **thời gian về đích**, **số vòng hoàn thành** và **trạng thái**. Trạng thái nhận một trong ba giá trị: **Hoàn thành**, **DNF** (bỏ cuộc hoặc tai nạn), **DSQ** (bị loại vì vi phạm kỹ thuật).
- FR4.2 **Tính điểm:** xếp hạng các tay đua trạng thái *Hoàn thành* theo thứ tự tăng dần thời gian về đích; tay đua **DNF hoặc DSQ xếp cuối bảng và nhận 0 điểm**. Gán điểm cho top 10 theo thứ tự 25/18/15/12/10/8/6/4/2/1; tay đua nằm trong top 10 nhưng DNF hoặc DSQ vẫn nhận 0 điểm.
- FR4.3 Hiển thị bảng kết quả chặng để đối soát (hạng, tên tay đua, tên đội, thời gian, số vòng, trạng thái, điểm); lưu kết quả + điểm và in bảng kết quả chặng.
- FR4.4 **Ghi đè kết quả cũ:** nếu chặng được chọn **đã có kết quả** từ lần nhập trước, hệ thống phải **cảnh báo ghi đè** trước khi lưu; nếu nhân viên xác nhận, hệ thống xóa toàn bộ kết quả cũ của chặng và **tính lại điểm cho toàn bộ chặng** theo dữ liệu mới.

**FR5 — Quyết toán và trao giải cuối mùa (Module 4)**
- FR5.1 **Ràng buộc:** chỉ quyết toán khi tất cả chặng trong mùa đã có kết quả; nếu còn chặng chưa nhập kết quả thì báo lỗi và từ chối quyết toán.
- FR5.2 Cộng dồn điểm và thời gian của từng tay đua và từng đội qua các chặng; xếp hạng cá nhân và xếp hạng đội theo **ba tầng tiêu chí**: (1) **giảm dần tổng điểm**; (2) nếu **bằng điểm** thì phân định bằng **countback** — so sánh **số lần về nhất**, nếu vẫn bằng thì **số lần về nhì**, rồi **số lần về ba**… cho đến khi phân định được; (3) nếu countback vẫn bằng thì xếp theo **tăng dần tổng thời gian**. Trong đó countback là tầng bổ sung theo luật FIA thật, còn tổng thời gian là quy tắc gốc của đề bài, được giữ làm tiêu chí phân định cuối cùng. **Tổng thời gian luôn được hiển thị trên bảng xếp hạng.**
- FR5.2b **Xem bảng xếp hạng tính đến chặng bất kỳ:** quản lý chọn một chặng từ danh sách thả xuống; hệ thống tổng hợp bảng xếp hạng cá nhân và bảng xếp hạng đội **tính từ chặng đầu mùa đến hết chặng được chọn**, xem được ở bất kỳ thời điểm nào trong mùa. Chức năng trao giải chỉ được kích hoạt khi chặng được chọn là chặng cuối và mọi chặng đã có kết quả (FR5.1).
- FR5.2c **Xem chi tiết theo chặng (drill-down):** quản lý click vào một dòng trên bảng xếp hạng; hệ thống hiển thị bảng chi tiết kết quả từng chặng của tay đua đó (Tên chặng | Hạng về đích | Điểm | Thời gian về đích) hoặc của đội đó (Tên chặng | Tổng điểm | Tổng thời gian của 2 tay đua), kèm nút quay lại bảng xếp hạng.
- FR5.3 Điểm của tay đua được cộng cho **đội mà tay đua đăng ký thi đấu tại chặng đó**, không phải đội hiện tại của tay đua (xử lý đúng trường hợp tay đua đổi đội giữa mùa).
- FR5.4 Nhập mức thưởng theo hạng (hạng 1, 2, 3 cá nhân và hạng 1, 2, 3 đội); hệ thống tính tiền thưởng tương ứng cho từng tay đua/đội theo hạng đạt được.
- FR5.5 Lưu quyết định trao giải và in danh sách trao giải (hạng, tên tay đua/đội, tổng điểm, tiền thưởng).

### 2.3. Yêu cầu phi chức năng

| # | Loại | Yêu cầu |
|---|---|---|
| NFR1 | Bảo mật | Đăng nhập bằng tài khoản; phân quyền theo vai trò (Nhân viên/Quản lý). |
| NFR2 | Tính đúng đắn | Các phép tính điểm, xếp hạng (kể cả countback), tiền thưởng phải chính xác theo luật F1 trong đề bài. |
| NFR3 | Toàn vẹn dữ liệu | Kiểm tra ràng buộc (chồng lấn hợp đồng, ≤2 tay đua/đội/chặng, cảnh báo ghi đè kết quả, đủ kết quả trước khi quyết toán) trước khi lưu. |
| NFR4 | Khả dụng | Giao diện tiếng Việt, thao tác tìm kiếm → chọn → lưu rõ ràng; thông báo lỗi cụ thể khi vi phạm ràng buộc. |
| NFR5 | Hiệu năng | Danh sách (tay đua, kết quả, xếp hạng) hiển thị < 2 giây với quy mô một mùa giải. |
| NFR6 | Khả bảo trì | **Kiến trúc phân tầng view (.jsp) / dao / model**: tầng `view` là các trang `.jsp` hiển thị và nhận dữ liệu, tầng `dao` là các lớp truy xuất dữ liệu, tầng `model` là các lớp thực thể. Mỗi tầng chỉ gọi tầng ngay dưới nó, giúp dễ sửa và mở rộng. |
| NFR7 | Khả chuyển | Chạy trên trình duyệt web thông dụng. |

### 2.4. Biểu đồ Use Case tổng quát

Biểu đồ tổng quát đặt toàn bộ use case trong khung hệ thống `Hệ thống quản lý giải đua F1`, các actor nằm ngoài khung.

**Actor:** `ThanhVien` là actor trừu tượng, cha của `NhanVien` và `QuanLy`. Hai actor con kế thừa quyền dùng `Đăng nhập` và `Đổi mật khẩu`.

**Use case:** `Đăng nhập`, `Đổi mật khẩu` (actor `ThanhVien`); use case trừu tượng `Quản lý danh mục` là cha (generalization) của `Quản lý mùa giải`, `Quản lý tay đua`, `Quản lý đội đua`, `Quản lý chặng đua`; `Đăng ký đội tham gia mùa giải`, `Ký hợp đồng tay đua với đội đua` (M1), `Đăng ký tay đua tham gia chặng đua` (M2), `Cập nhật kết quả chặng đua` (M3) — actor `NhanVien`; `Quyết toán và trao giải cuối mùa` (M4) — actor `QuanLy`.

![Biểu đồ Use Case tổng quát](<hinh/uc-tongquat.png>)

*Hình 2.1 — Biểu đồ Use Case tổng quát*

---

## CHƯƠNG 3: XÂY DỰNG BIỂU ĐỒ LỚP THỰC THỂ

### 3.1. Phân tích và xác định các thực thể (phương pháp trích danh từ)

#### 3.1.1. Đoạn văn mô tả hệ thống

Mỗi **năm** có một **mùa giải** (giải vô địch) mang một **tên giải** riêng và có **trạng thái** cho biết mùa giải đang diễn ra, đã kết thúc hay đã quyết toán. Một mùa giải gồm nhiều **chặng đua** diễn ra khắp **thế giới**; mỗi chặng đua có **mã chặng đua**, **tên chặng**, **số vòng đua**, **địa điểm**, **thời gian** diễn ra và **mô tả**. Mỗi mùa giải có nhiều **đội đua** đăng ký **tham gia**; mỗi đội đua có **mã đội**, **tên đội**, **hãng** và **mô tả**.

Mỗi đội đua có nhiều **tay đua**; mỗi tay đua có **mã**, **tên**, **ngày sinh**, **quốc tịch** và **tiểu sử**. Một tay đua có thể thi đấu cho nhiều đội đua ở các **thời điểm** khác nhau nhưng tại một thời điểm chỉ thi đấu cho một đội; mỗi giai đoạn thi đấu được ghi nhận bằng một **hợp đồng** có **ngày bắt đầu** và **ngày kết thúc** (bỏ trống nghĩa là đang hiệu lực). Toàn bộ hợp đồng của một tay đua tạo thành **lịch sử thi đấu** của tay đua đó. Sau khi ký, hệ thống in **phiếu xác nhận hợp đồng**.

Trước mỗi chặng đua, **nhân viên** thực hiện **đăng ký** tay đua tham gia chặng theo **yêu cầu của đội đua**; mỗi đội chỉ được cho tối đa hai tay đua tham gia một chặng và mỗi tay đua chỉ được đăng ký một lần trong một chặng — đây là các **ràng buộc** nghiệp vụ. Hệ thống hiển thị **trạng thái đăng ký** của từng tay đua và in **danh sách xuất phát** gửi **ban tổ chức**.

Sau khi chặng đua kết thúc, nhân viên nhập **kết quả** của chặng: **thời gian hoàn thành**, **số vòng chạy được** và **trạng thái** (hoàn thành, **bỏ cuộc**/**tai nạn** — DNF, hoặc bị loại do **vi phạm kỹ thuật** — DSQ). Hệ thống xếp **thứ hạng** theo thời gian về đích và gán **điểm** cho **top 10** theo thứ tự 25, 18, 15, 12, 10, 8, 6, 4, 2, 1.

Cuối mùa, **quản lý** quyết toán mùa giải: hệ thống cộng dồn **tổng điểm** và **tổng thời gian** của từng tay đua, từng đội qua tất cả các chặng để lập **bảng xếp hạng cuối mùa** gồm **xếp hạng cá nhân** và **xếp hạng đội**; khi bằng điểm thì phân định bằng **countback**, nếu countback vẫn bằng thì theo **tổng thời gian** tăng dần. Quản lý nhập **mức tiền thưởng** cho từng hạng, hệ thống tính **tiền thưởng** và lưu **quyết định trao giải** cho **giải cá nhân** và **giải đồng đội**, sau đó in **danh sách trao giải**.

Người sử dụng **hệ thống** là các **thành viên** có **tên đăng nhập**, **mật khẩu** và **họ tên**; thành viên gồm hai loại là nhân viên và quản lý.

#### 3.1.2. Bảng trích danh từ và đánh giá

Mỗi danh từ chỉ tính một lần. Cột "Nhóm" phân loại theo người / vật / thông tin. Cột "Kết luận" cho biết danh từ trở thành lớp thực thể, trở thành thuộc tính của một lớp, hay bị loại.

| Danh từ | Nhóm (người / vật / thông tin) | Kết luận |
|---|---|---|
| mùa giải (giải vô địch) | Vật (sự kiện) | → lớp thực thể `MuaGiai` |
| giải đấu | Vật (sự kiện) | Loại vì trùng nghĩa với "mùa giải" — mỗi danh từ chỉ tính một lần |
| năm | Thông tin | → thuộc tính `nam` của `MuaGiai` |
| tên giải | Thông tin | → thuộc tính `ten` của `MuaGiai` |
| trạng thái mùa giải | Thông tin | → thuộc tính `trangThai` của `MuaGiai` (đang diễn ra / đã kết thúc / đã quyết toán) |
| chặng đua | Vật (sự kiện) | → lớp thực thể `ChangDua` |
| mã chặng đua | Thông tin | → thuộc tính `ma` của `ChangDua` |
| tên chặng | Thông tin | → thuộc tính `ten` của `ChangDua` |
| số vòng đua | Thông tin | → thuộc tính `soVong` của `ChangDua` |
| địa điểm | Thông tin | → thuộc tính `diaDiem` của `ChangDua` |
| thời gian diễn ra chặng | Thông tin | → thuộc tính `thoiGian` của `ChangDua` |
| mô tả chặng | Thông tin | → thuộc tính `moTa` của `ChangDua` |
| thế giới | Vật | Loại vì ngoài phạm vi — hệ thống không quản lý thông tin địa lý |
| đội đua | Vật (đơn vị tổ chức) | → lớp thực thể `DoiDua` |
| mã đội | Thông tin | → thuộc tính `ma` của `DoiDua` |
| tên đội | Thông tin | → thuộc tính `ten` của `DoiDua` |
| hãng | Vật (đơn vị tổ chức) | → thuộc tính `hang` của `DoiDua` |
| mô tả đội | Thông tin | → thuộc tính `moTa` của `DoiDua` |
| tay đua | Người | → lớp thực thể `TayDua` |
| mã tay đua | Thông tin | → thuộc tính `ma` của `TayDua` |
| tên tay đua | Thông tin | → thuộc tính `ten` của `TayDua` |
| ngày sinh | Thông tin | → thuộc tính `ngaySinh` của `TayDua` |
| quốc tịch | Thông tin | → thuộc tính `quocTich` của `TayDua` |
| tiểu sử | Thông tin | → thuộc tính `tieuSu` của `TayDua` |
| tham gia (đội tham gia mùa giải) | Thông tin | → lớp thực thể trung gian `ThamGia` (tách quan hệ n-n `MuaGiai` – `DoiDua`) |
| hợp đồng | Thông tin | → lớp thực thể `HopDong` (tách quan hệ n-n theo thời gian `TayDua` – `DoiDua`) |
| ngày bắt đầu | Thông tin | → thuộc tính `ngayBatDau` của `HopDong` |
| ngày kết thúc | Thông tin | → thuộc tính `ngayKetThuc` của `HopDong` (để trống = đang hiệu lực) |
| thời điểm | Thông tin | Loại vì trừu tượng — đã được cụ thể hoá bằng `ngayBatDau` / `ngayKetThuc` |
| lịch sử thi đấu | Thông tin | Loại — chính là tập các `HopDong` của một tay đua, không sinh thực thể mới |
| phiếu xác nhận hợp đồng | Thông tin | Loại — là bản in kết xuất từ `HopDong`, không lưu trữ riêng |
| đăng ký (tham gia chặng) | Thông tin | → lớp thực thể trung gian `DangKyChang` (tách quan hệ n-n `ChangDua` – `TayDua`) |
| yêu cầu của đội đua | Thông tin | Loại vì trừu tượng — là lý do nghiệp vụ, không lưu trữ |
| ràng buộc | Thông tin | Loại vì trừu tượng — cài đặt bằng phương thức kiểm tra của lớp thực thể |
| trạng thái đăng ký | Thông tin | Loại — dẫn xuất, tra cứu trực tiếp trên `DangKyChang` khi hiển thị |
| danh sách xuất phát (start list) | Thông tin | Loại — bản in kết xuất từ `DangKyChang` |
| ban tổ chức | Người | Loại vì ngoài phạm vi — actor gián tiếp nhận bản in, hệ thống không quản lý hồ sơ ban tổ chức |
| kết quả | Thông tin | → lớp thực thể `KetQua` |
| thời gian hoàn thành | Thông tin | → thuộc tính `thoiGian` của `KetQua` |
| số vòng chạy được | Thông tin | → thuộc tính `soVongHoanThanh` của `KetQua` |
| trạng thái kết quả (bỏ cuộc, tai nạn, vi phạm kỹ thuật) | Thông tin | → thuộc tính `trangThai` của `KetQua` (HoanThanh / DNF / DSQ) |
| thứ hạng về đích | Thông tin | → thuộc tính `hang` của `KetQua` |
| điểm | Thông tin | → thuộc tính `diem` của `KetQua` |
| top 10 | Thông tin | Loại vì trừu tượng — là luật tính điểm 25…1, cài trong `KetQua.xepHangVaTinhDiem()` |
| tổng điểm | Thông tin | Loại — thuộc tính dẫn xuất, cộng dồn từ `KetQua` (xem mục 3.6.5) |
| tổng thời gian | Thông tin | Loại — thuộc tính dẫn xuất, cộng dồn từ `KetQua` (xem mục 3.6.5) |
| bảng xếp hạng cuối mùa (xếp hạng cá nhân, xếp hạng đội) | Thông tin | Loại — bảng tổng hợp dẫn xuất, tính lúc chạy từ `KetQua` |
| countback | Thông tin | Loại vì trừu tượng — là tầng 2 của quy tắc xếp hạng ba tầng, cài trong `KetQua.sapXepBangXepHang()` |
| trao giải (quyết định trao giải) | Thông tin | → lớp thực thể `TraoGiai` |
| giải cá nhân / giải đồng đội | Thông tin | → thuộc tính `loai` của `TraoGiai` |
| hạng được trao giải | Thông tin | → thuộc tính `hang` của `TraoGiai` |
| mức tiền thưởng / tiền thưởng | Thông tin | → thuộc tính `tienThuong` của `TraoGiai` |
| danh sách trao giải | Thông tin | Loại — bản in kết xuất từ `TraoGiai` |
| thành viên | Người | → lớp thực thể trừu tượng `ThanhVien` |
| tên đăng nhập | Thông tin | → thuộc tính `tenDangNhap` của `ThanhVien` |
| mật khẩu | Thông tin | → thuộc tính `matKhau` của `ThanhVien` |
| họ tên | Thông tin | → thuộc tính `hoTen` của `ThanhVien` |
| nhân viên | Người | → lớp thực thể `NhanVien`, kế thừa `ThanhVien` |
| quản lý | Người | → lớp thực thể `QuanLy`, kế thừa `ThanhVien` |
| hệ thống, giao diện, danh sách thả xuống, cơ sở dữ liệu | Vật | Loại vì ngoài phạm vi — thuộc về phần mềm/kỹ thuật, không phải đối tượng nghiệp vụ |

#### 3.1.3. Danh sách lớp thực thể

Sau khi đánh giá, hệ thống có **12 lớp thực thể**, trong đó 9 lớp nghiệp vụ, 1 lớp trừu tượng và 2 lớp kế thừa:

`MuaGiai` · `ChangDua` · `DoiDua` · `TayDua` · `ThamGia` · `HopDong` · `DangKyChang` · `KetQua` · `TraoGiai` · `ThanhVien` (trừu tượng) · `NhanVien` · `QuanLy`.

Ba lớp `ThamGia`, `HopDong`, `DangKyChang` là **lớp trung gian** của các quan hệ nhiều–nhiều (mục 3.3).

### 3.2. Mô tả thực thể (thuộc tính, phương thức)

#### 3.2.1. Thuộc tính — pha phân tích

Ở pha phân tích, thuộc tính **chưa cần kiểu dữ liệu** và các lớp thực thể **chưa có thuộc tính `id`**.

| Lớp | Thuộc tính (pha phân tích) | Ý nghĩa |
|---|---|---|
| `MuaGiai` | `ten`, `nam`, `trangThai` | Một mùa giải ứng với một năm. `trangThai`: đang diễn ra / đã kết thúc / đã quyết toán |
| `ChangDua` | `ma`, `ten`, `soVong`, `diaDiem`, `thoiGian`, `moTa` | Một chặng đua thuộc đúng một mùa giải |
| `DoiDua` | `ma`, `ten`, `hang`, `moTa` | Đội đua tham gia giải |
| `TayDua` | `ma`, `ten`, `ngaySinh`, `quocTich`, `tieuSu` | Tay đua, tồn tại độc lập với đội |
| `ThamGia` | (không có thuộc tính riêng) | Lớp trung gian `MuaGiai` – `DoiDua`: một đội tham gia một mùa giải |
| `HopDong` | `ngayBatDau`, `ngayKetThuc` | Lớp trung gian `TayDua` – `DoiDua` (Module 1). `ngayKetThuc` để trống = hợp đồng đang hiệu lực |
| `DangKyChang` | (không có thuộc tính riêng) | Lớp trung gian `ChangDua` – `TayDua` – `DoiDua` (Module 2) |
| `KetQua` | `thoiGian`, `soVongHoanThanh`, `trangThai`, `hang`, `diem` | Kết quả của một lượt đăng ký sau khi chặng đua kết thúc (Module 3). `trangThai` khác `HoanThanh` (DNF/DSQ) thì xếp cuối và nhận 0 điểm |
| `TraoGiai` | `loai`, `hang`, `tienThuong` | Quyết định trao giải cuối mùa (Module 4). `loai`: giải cá nhân hoặc giải đồng đội |
| `ThanhVien` | `tenDangNhap`, `matKhau`, `hoTen` | **Lớp trừu tượng** — tài khoản đăng nhập chung |
| `NhanVien` | (kế thừa `ThanhVien`) | Thực hiện Module 1, 2, 3 |
| `QuanLy` | (kế thừa `ThanhVien`) | Thực hiện Module 4 |

**Tách `ThanhVien` thành cây kế thừa.** Nhân viên và quản lý dùng chung ba thuộc tính `tenDangNhap`, `matKhau`, `hoTen` và dùng chung use case `Đăng nhập`, `Đổi mật khẩu`, nhưng khác nhau về quyền thực hiện chức năng. Nhóm khai báo `ThanhVien` là **lớp trừu tượng** làm cha, `NhanVien` và `QuanLy` **kế thừa** (`ThanhVien <|-- NhanVien`, `ThanhVien <|-- QuanLy`). Cách này **bỏ được thuộc tính `vaiTro` kiểu chuỗi** — vốn là cách mô phỏng kế thừa bằng dữ liệu — và tạo ra quan hệ generalization giữa ba lớp. Theo quy tắc thiết kế, **hai lớp con kế thừa không được bổ sung thuộc tính `id`** mà dùng chung định danh của lớp cha.

#### 3.2.2. Phương thức nghiệp vụ gán cho lớp thực thể

Hệ thống **không có lớp Control** — toàn bộ nghiệp vụ nằm ở lớp thực thể.

| Lớp | Phương thức | Module dùng |
|---|---|---|
| `TayDua` | `getTayDuaTheoTen(ten)`, `themTayDua()` | M1 |
| `DoiDua` | `getDSDoiDua()` | M1, M2 |
| `HopDong` | `getHopDongCuaTayDua(tayDuaId)`, `kiemTraChongLan(tayDuaId, ngayBatDau)`, `dongHopDongCu(tayDuaId, ngayBatDau)`, `luuHopDong()`, `getTayDuaHieuLuc(doiDuaId, thoiGianChang)` | M1, M2 |
| `ChangDua` | `getDSChangDua()` | M2, M3 |
| `DangKyChang` | `demSoTayDua(changDuaId, doiDuaId)`, `daDangKy(changDuaId, tayDuaId)`, `luuDangKy()`, `getDangKyCuaChang(changDuaId)` | M2, M3 |
| `KetQua` | `kiemTraKetQuaCu(changDuaId)`, `xoaKetQuaCu(changDuaId)`, `xepHangVaTinhDiem(changDuaId)`, `luuKetQua()`, `tongHopCaNhan(muaGiaiId, changDuaId)`, `tongHopDoi(muaGiaiId, changDuaId)`, `sapXepBangXepHang(ds)`, `getChiTietTheoTayDua(muaGiaiId, tayDuaId, changDuaId)`, `getChiTietTheoDoi(muaGiaiId, doiDuaId, changDuaId)` | M3, M4 |
| `MuaGiai` | `getMuaGiaiHienTai()` | M4 |
| `TraoGiai` | `tinhTienThuong(hang, mucThuong)`, `luuTraoGiai()` | M4 |

- `xepHangVaTinhDiem(changDuaId)` — đầu ra là danh sách kết quả đã xếp hạng và gán điểm, thuộc `KetQua` ⇒ gán cho `KetQua`.
- `getChiTietTheoTayDua(muaGiaiId, tayDuaId, changDuaId)` và `getChiTietTheoDoi(muaGiaiId, doiDuaId, changDuaId)` (bảng chi tiết theo chặng ở Module 4) — đầu ra là danh sách bản ghi `KetQua` của từng chặng ⇒ gán cho `KetQua`, dù tham số vào là mùa giải và tay đua/đội.
- `getTayDuaHieuLuc(doiDuaId, thoiGianChang)` — đầu ra là danh sách tay đua nhưng được lọc theo điều kiện hợp đồng; cả hai tham số vào đều so khớp trên dữ liệu của hợp đồng (`doiDua`, `ngayBatDau`/`ngayKetThuc`) ⇒ gán cho `HopDong`, thực thể nhỏ nhất chứa được nhiều tham số nhất.

### 3.3. Quan hệ giữa các lớp thực thể

#### 3.3.1. Quan hệ số lượng và ba lớp trung gian

Ba quan hệ nhiều–nhiều được tách bằng lớp trung gian:

| Quan hệ n-n | Lớp trung gian | Tách thành | Ý nghĩa của một bản ghi |
|---|---|---|---|
| `MuaGiai` – `DoiDua` | **`ThamGia`** | `MuaGiai "1" – "n" ThamGia` và `DoiDua "1" – "n" ThamGia` | Một đội đua đăng ký tham gia một mùa giải |
| `TayDua` – `DoiDua` | **`HopDong`** | `TayDua "1" – "n" HopDong` và `DoiDua "1" – "n" HopDong` | Một giai đoạn tay đua thi đấu cho một đội, có `ngayBatDau` và `ngayKetThuc` (Module 1) |
| `ChangDua` – `TayDua` | **`DangKyChang`** | `ChangDua "1" – "n" DangKyChang`, `TayDua "1" – "n" DangKyChang` và `DoiDua "1" – "n" DangKyChang` | Một tay đua được một đội đăng ký thi đấu ở một chặng (Module 2) |

> `DangKyChang` thực chất tách một quan hệ **ba ngôi** `ChangDua` – `TayDua` – `DoiDua` thành ba quan hệ 1-n. `DoiDua` được giữ ở đây thay vì tra ngược qua `HopDong`, vì tay đua có thể **đổi đội giữa mùa**: điểm của chặng phải cộng cho đội tại **thời điểm diễn ra chặng**, tức đội ghi trong `DangKyChang`, không phải đội hiện tại.

Sau bước này, **không còn quan hệ n-n nào** giữa các lớp thực thể.

#### 3.3.2. Quan hệ đối tượng

Các liên kết được chuyển thành quan hệ **hợp thành** (`*--`), **thành phần** (`o--`) và **kế thừa** (`<|--`):

| Quan hệ | Loại |
|---|---|
| `MuaGiai` – `ChangDua` | **Hợp thành `*--`** |
| `ChangDua` – `DangKyChang` | **Hợp thành `*--`** |
| `DangKyChang` – `KetQua` | **Hợp thành `*--`, bội số 1 – 0..1** |
| `MuaGiai` – `TraoGiai` | **Hợp thành `*--`** |
| `MuaGiai` – `ThamGia`, `DoiDua` – `ThamGia` | **Thành phần `o--`** |
| `TayDua` – `HopDong`, `DoiDua` – `HopDong` | **Thành phần `o--`** |
| `TayDua` – `DangKyChang`, `DoiDua` – `DangKyChang` | **Thành phần `o--`** |
| `TayDua` – `TraoGiai`, `DoiDua` – `TraoGiai` | **Thành phần `o--`** |
| `ThanhVien` – `NhanVien`, `ThanhVien` – `QuanLy` | **Kế thừa `<\|--`** |

Bội số giữa `DangKyChang` và `KetQua` là **1 – 0..1**: bản đăng ký được tạo trước ngày đua, kết quả chỉ phát sinh sau khi chặng kết thúc. Hai lớp giữ riêng, không gộp.

### 3.4. Biểu đồ lớp thực thể — pha phân tích

![Biểu đồ lớp thực thể pha phân tích](<hinh/lop-thucthe-phantich.png>)

*Hình 3.1 — Biểu đồ lớp thực thể, pha phân tích*

### 3.5. Biểu đồ lớp thực thể — pha thiết kế

Đầu vào là biểu đồ pha phân tích ở mục 3.4. Ngôn ngữ lập trình đã chọn: **Java**. Bốn bước bổ sung:

**Bước 1 — Bổ sung thuộc tính `id`** cho 10 lớp: `MuaGiai`, `ChangDua`, `DoiDua`, `TayDua`, `ThamGia`, `HopDong`, `DangKyChang`, `KetQua`, `TraoGiai`, `ThanhVien`. **Không thêm `id` cho `NhanVien` và `QuanLy`** vì hai lớp này kế thừa `ThanhVien` và dùng chung định danh của lớp cha.

**Bước 2 — Bổ sung kiểu dữ liệu** theo kiểu của Java: `integer`, `String`, `float`, `Date`.

| Thuộc tính | Kiểu | Ghi chú |
|---|---|---|
| mọi `id` | `integer` | khoá chính |
| `ten`, `ma`, `trangThai`, `moTa`, `hang` (hãng của `DoiDua`), `quocTich`, `tieuSu`, `loai`, `tenDangNhap`, `matKhau`, `hoTen` | `String` | |
| `nam`, `soVong`, `soVongHoanThanh`, `hang` (thứ hạng của `KetQua` và `TraoGiai`), `diem` | `integer` | Hai thuộc tính cùng tên `hang` khác nghĩa và khác kiểu: `DoiDua.hang` là hãng xe, `KetQua.hang` / `TraoGiai.hang` là thứ hạng |
| `thoiGian` của `KetQua`, `tienThuong` | `float` | thời gian hoàn thành tính bằng giây, có phần thập phân |
| `ngaySinh`, `ngayBatDau`, `ngayKetThuc` | `Date` | |
| `thoiGian` của `ChangDua` | `Date` | ngày giờ diễn ra chặng |

**Bước 3 — Chuyển association thành aggregation/composition.** Đã làm ở mục 3.3.2; biểu đồ thiết kế dùng đúng bộ quan hệ đó.

**Bước 4 — Bổ sung thuộc tính kiểu đối tượng.** Lớp nào chứa lớp kia thì khai báo tường minh thuộc tính có kiểu là lớp kia; kiểu mảng `[]` nếu phía bên kia là "n", số ít nếu là "1" hoặc "0..1".

| Lớp | Thuộc tính kiểu đối tượng |
|---|---|
| `MuaGiai` | `dsChangDua : ChangDua[]`, `dsThamGia : ThamGia[]`, `dsTraoGiai : TraoGiai[]` |
| `ThamGia` | `muaGiai : MuaGiai`, `doiDua : DoiDua` |
| `HopDong` | `tayDua : TayDua`, `doiDua : DoiDua` |
| `ChangDua` | `muaGiai : MuaGiai`, `dsDangKy : DangKyChang[]` |
| `DangKyChang` | `changDua : ChangDua`, `tayDua : TayDua`, `doiDua : DoiDua`, `ketQua : KetQua` |
| `KetQua` | `dangKyChang : DangKyChang` |
| `TraoGiai` | `muaGiai : MuaGiai`, `tayDua : TayDua`, `doiDua : DoiDua` |

![Biểu đồ lớp thực thể pha thiết kế](<hinh/lop-thucthe-thietke.png>)

*Hình 3.2 — Biểu đồ lớp thực thể, pha thiết kế*

### 3.6. Thiết kế cơ sở dữ liệu

#### 3.6.1. Bước 1 — Mỗi lớp thực thể thành một bảng

Mười hai bảng: `tblMuaGiai`, `tblChangDua`, `tblDoiDua`, `tblTayDua`, `tblThamGia`, `tblHopDong`, `tblDangKyChang`, `tblKetQua`, `tblTraoGiai`, `tblThanhVien`, `tblNhanVien`, `tblQuanLy`.

Cây kế thừa `ThanhVien` được ánh xạ thành **bảng cha + hai bảng con**: `tblNhanVien` và `tblQuanLy` không có `id` riêng mà dùng khoá ngoại `tblThanhVienid` vừa làm khoá chính vừa tham chiếu `tblThanhVien`.

#### 3.6.2. Bước 2 — Bỏ qua thuộc tính kiểu đối tượng

Các thuộc tính kiểu đối tượng thêm ở mục 3.5 **không trở thành cột**: `dsChangDua`, `dsThamGia`, `dsTraoGiai`, `dsDangKy`, `muaGiai`, `doiDua`, `tayDua`, `changDua`, `dangKyChang`, `ketQua`. Chúng được thay bằng **khoá ngoại** ở bước 4.

#### 3.6.3. Bước 3 — Đối chiếu quan hệ số lượng

- Toàn bộ quan hệ **1-n** được giữ nguyên thành cặp bảng cha – bảng con.
- **Không còn quan hệ n-n** nào (đã tách bằng `ThamGia`, `HopDong`, `DangKyChang` ngay từ pha phân tích).
- Quan hệ **1 – 0..1** giữa `tblDangKyChang` và `tblKetQua`: **giữ hai bảng riêng**.

#### 3.6.4. Bước 4 — Bổ sung khoá chính và khoá ngoại

Khoá chính là cột `id`. Với quan hệ 1 `tblA` – n `tblB`, bảng `tblB` có khoá ngoại **`tblAid`** tham chiếu tới `tblA.id`.

| Bảng | Cột và kiểu dữ liệu | Khoá |
|---|---|---|
| `tblMuaGiai` | `id integer(10)`, `ten varchar(255)`, `nam integer(10)`, `trangThai varchar(255)` | PK: `id` |
| `tblDoiDua` | `id integer(10)`, `ma varchar(255)`, `ten varchar(255)`, `hang varchar(255)`, `moTa varchar(255)` | PK: `id` |
| `tblTayDua` | `id integer(10)`, `ma varchar(255)`, `ten varchar(255)`, `ngaySinh date`, `quocTich varchar(255)`, `tieuSu varchar(255)` | PK: `id` |
| `tblChangDua` | `id integer(10)`, `ma varchar(255)`, `ten varchar(255)`, `soVong integer(10)`, `diaDiem varchar(255)`, `thoiGian datetime`, `moTa varchar(255)`, `tblMuaGiaiid integer(10)` | PK: `id` · FK: `tblMuaGiaiid` → `tblMuaGiai.id` |
| `tblThamGia` | `id integer(10)`, `tblMuaGiaiid integer(10)`, `tblDoiDuaid integer(10)` | PK: `id` · FK: `tblMuaGiaiid` → `tblMuaGiai.id`, `tblDoiDuaid` → `tblDoiDua.id` |
| `tblHopDong` | `id integer(10)`, `ngayBatDau date`, `ngayKetThuc date` (cho phép NULL), `tblTayDuaid integer(10)`, `tblDoiDuaid integer(10)` | PK: `id` · FK: `tblTayDuaid` → `tblTayDua.id`, `tblDoiDuaid` → `tblDoiDua.id` |
| `tblDangKyChang` | `id integer(10)`, `tblChangDuaid integer(10)`, `tblTayDuaid integer(10)`, `tblDoiDuaid integer(10)` | PK: `id` · FK: `tblChangDuaid` → `tblChangDua.id`, `tblTayDuaid` → `tblTayDua.id`, `tblDoiDuaid` → `tblDoiDua.id` · UNIQUE (`tblChangDuaid`, `tblTayDuaid`) |
| `tblKetQua` | `id integer(10)`, `thoiGian float(10)`, `soVongHoanThanh integer(10)`, `trangThai varchar(255)`, `hang integer(10)`, `diem integer(10)`, `tblDangKyChangid integer(10)` | PK: `id` · FK: `tblDangKyChangid` → `tblDangKyChang.id` |
| `tblTraoGiai` | `id integer(10)`, `loai varchar(255)`, `hang integer(10)`, `tienThuong float(10)`, `tblMuaGiaiid integer(10)`, `tblTayDuaid integer(10)` (NULL nếu là giải đồng đội), `tblDoiDuaid integer(10)` (NULL nếu là giải cá nhân) | PK: `id` · FK: `tblMuaGiaiid` → `tblMuaGiai.id`, `tblTayDuaid` → `tblTayDua.id`, `tblDoiDuaid` → `tblDoiDua.id` |
| `tblThanhVien` | `id integer(10)`, `tenDangNhap varchar(255)`, `matKhau varchar(255)`, `hoTen varchar(255)` | PK: `id` · UNIQUE (`tenDangNhap`) |
| `tblNhanVien` | `tblThanhVienid integer(10)` | PK đồng thời là FK: `tblThanhVienid` → `tblThanhVien.id` |
| `tblQuanLy` | `tblThanhVienid integer(10)` | PK đồng thời là FK: `tblThanhVienid` → `tblThanhVien.id` |

> **Ghi chú ràng buộc:**
> - `tblDangKyChang` có `UNIQUE(tblChangDuaid, tblTayDuaid)`: mỗi tay đua chỉ đăng ký một lần trong một chặng.
> - Ràng buộc "tối đa 2 tay đua/đội/chặng" là **ràng buộc nghiệp vụ**, không thể hiện được bằng khoá. Hệ thống kiểm ràng buộc này trong **phương thức `demSoTayDua(changDuaId, doiDuaId)` của lớp thực thể `DangKyChang`**. Tương tự, `daDangKy(changDuaId, tayDuaId)` kiểm tra trùng đăng ký trước khi lưu.
> - `tblHopDong.ngayKetThuc` để NULL nghĩa là hợp đồng đang hiệu lực. Ràng buộc "một tay đua tại một thời điểm chỉ thuộc một đội" được kiểm bằng `HopDong.kiemTraChongLan(tayDuaId, ngayBatDau)`.
> - `tblKetQua.trangThai` nhận một trong ba giá trị `HoanThanh`, `DNF`, `DSQ`; hai giá trị sau kéo theo `hang` xếp cuối và `diem` = 0.
> - `tblTraoGiai.loai` nhận `CaNhan` hoặc `Doi`; đúng một trong hai cột `tblTayDuaid` / `tblDoiDuaid` có giá trị, cột còn lại để NULL.
> - Bảng `tblThanhVien` **không có cột `vaiTro`**: vai trò được thể hiện bằng quan hệ kế thừa, tức bằng sự có mặt của bản ghi tương ứng trong `tblNhanVien` hoặc `tblQuanLy`.

#### 3.6.5. Bước 5 — Loại bỏ thuộc tính gây dư thừa dữ liệu (thuộc tính dẫn xuất)

**Đã loại bỏ:**

| Thuộc tính bỏ đi | Bảng | Lý do |
|---|---|---|
| `tongDiem` | `tblTraoGiai` | Dẫn xuất — tổng `tblKetQua.diem` của tay đua hoặc của đội trong mùa |
| `tongThoiGian` | `tblTraoGiai` | Dẫn xuất — tổng `tblKetQua.thoiGian` |
| Bảng xếp hạng cá nhân, bảng xếp hạng đội | — | Không tạo bảng nào cho hai bảng xếp hạng cuối mùa; chúng được tổng hợp lúc chạy bằng `KetQua.tongHopCaNhan(muaGiaiId)` và `KetQua.tongHopDoi(muaGiaiId)`; bảng chi tiết theo chặng của một tay đua/đội (drill-down ở Module 4) cũng tổng hợp lúc chạy bằng `KetQua.getChiTietTheoTayDua(muaGiaiId, tayDuaId)` / `KetQua.getChiTietTheoDoi(muaGiaiId, doiDuaId)` |

Cách tính lúc chạy: tổng điểm cá nhân = `SUM(tblKetQua.diem)` gộp theo `tblDangKyChang.tblTayDuaid`; tổng điểm đội = `SUM(tblKetQua.diem)` gộp theo `tblDangKyChang.tblDoiDuaid` (gộp theo đội ghi trong bản đăng ký nên tay đua đổi đội giữa mùa vẫn cộng đúng cho đội tại thời điểm chặng). Tie-break cũng tính lúc chạy, không lưu cột nào — theo **quy tắc xếp hạng ba tầng**: bằng điểm thì **countback** (đếm `COUNT(tblKetQua.hang = 1)`, nếu bằng nhau thì `COUNT(tblKetQua.hang = 2)`, rồi `COUNT(tblKetQua.hang = 3)`…); nếu countback vẫn bằng thì so `SUM(tblKetQua.thoiGian)` tăng dần.

`tblKetQua.hang`, `tblKetQua.diem` và `tblTraoGiai.hang`, `tienThuong`, `loai` **được giữ**: đây là kết quả đã công bố của chặng và quyết định trao giải đã chốt của mùa giải, không phải giá trị tính lại được.

#### 3.6.6. Biểu đồ thiết kế cơ sở dữ liệu

Kết quả của năm bước trên: **12 bảng, 14 khoá ngoại, 2 ràng buộc UNIQUE** (`tblDangKyChang(tblChangDuaid, tblTayDuaid)` và `tblThanhVien(tenDangNhap)`) và **3 cột cho phép NULL** (`tblHopDong.ngayKetThuc`, `tblTraoGiai.tblTayDuaid`, `tblTraoGiai.tblDoiDuaid`).

![Biểu đồ thiết kế cơ sở dữ liệu](<hinh/csdl.png>)

*Hình 3.3 — Biểu đồ thiết kế cơ sở dữ liệu*

### 3.7. Thiết kế triển khai (package view / dao / model)

Lớp thực thể vào gói **`model`**, lớp truy xuất dữ liệu vào gói **`dao`**, trang jsp vào gói **`view`** (chia nhỏ theo nhóm người dùng).

| Gói | Thành phần |
|---|---|
| `view.thanhvien` | `gdDangNhap.jsp`, `gdDoiMatKhau.jsp` (các trang dùng chung) |
| `view.nhanvien` | `gdChinhNV.jsp` (trang chính của nhân viên) · `gdTimTayDua.jsp`, `gdNhapHopDong.jsp`, `doLuuHopDong.jsp` (M1) · `gdChonChangDoi.jsp`, `gdDangKyTayDua.jsp`, `doLuuDangKy.jsp` (M2) · `gdChonChang.jsp`, `gdNhapKetQua.jsp`, `doLuuKetQua.jsp` (M3) |
| `view.quanly` | `gdChinhQL.jsp` (trang chính của quản lý) · `gdXepHang.jsp`, `gdChiTietXepHang.jsp`, `gdTraoGiai.jsp`, `doLuuTraoGiai.jsp` (M4) · các trang quản lý danh mục |
| `dao` | `DAO` (lớp cha) · `TayDuaDAO`, `DoiDuaDAO`, `HopDongDAO`, `ChangDuaDAO`, `DangKyChangDAO`, `KetQuaDAO`, `MuaGiaiDAO`, `TraoGiaiDAO` |
| `model` | `MuaGiai`, `ChangDua`, `DoiDua`, `TayDua`, `ThamGia`, `HopDong`, `DangKyChang`, `KetQua`, `TraoGiai`, `ThanhVien`, `NhanVien`, `QuanLy` |

**Lớp cha `DAO`.** Mọi lớp `XxxDAO` đều kế thừa lớp `DAO`; lớp cha này giữ **cơ chế kết nối cơ sở dữ liệu dùng chung**: mở kết nối, đóng kết nối, thực thi câu lệnh.

**Ánh xạ sang mô hình MVC.** Kiến trúc trên vẫn là MVC, với cách phân vai:

| Thành phần MVC | Trong hệ thống | Giải thích |
|---|---|---|
| **M** — Model | Các lớp thực thể trong gói `model` | Mang dữ liệu và các phương thức nghiệp vụ ở mục 3.2.2; đóng gói thông tin lấy từ cơ sở dữ liệu |
| **V** — View | Các trang `.jsp` trong gói `view` | Nhận dữ liệu người dùng nhập và hiển thị kết quả. Trang `gdXxx.jsp` là **màn hình hiển thị**; trang `doXxx.jsp` chỉ **xử lý** rồi chuyển tiếp, không phải màn hình |
| **C** — Control | Các lớp `XxxDAO` trong gói `dao` | Là *các lớp tầng điều khiển*: nhận yêu cầu từ trang jsp, gọi phương thức nghiệp vụ, truy xuất cơ sở dữ liệu rồi trả kết quả về cho jsp |

**Hệ thống không có lớp `XxxController` riêng.** Vai trò điều khiển do các lớp `XxxDAO` đảm nhiệm. Vì vậy trong toàn bộ tài liệu: biểu đồ lớp phân tích chỉ có hai tầng (lớp biên `GDxxx` và lớp thực thể), biểu đồ lớp thiết kế có ba tầng (`jsp` – `DAO` – `model`), và biểu đồ tuần tự **không có lifeline Controller, không có lifeline cơ sở dữ liệu**.

![Biểu đồ package thiết kế triển khai](<hinh/package-trienkhai.png>)

*Hình 3.4 — Thiết kế triển khai: package `view` → `dao` → `model`*

---

# PHẦN 2 — KẾT QUẢ TỪNG THÀNH VIÊN

## CHƯƠNG 4: MODULE 1 — KÝ HỢP ĐỒNG TAY ĐUA VỚI ĐỘI ĐUA

**Thành viên thực hiện:** Khuất Anh Quân — **Use case:** Ký hợp đồng tay đua với đội đua

### 4.1. Biểu đồ Use Case chi tiết

Module 1 có **2 màn hình hiển thị**, ứng với 2 use case con quan hệ `include`: **Tìm tay đua** và **Nhập thông tin hợp đồng**.

Ngoài ra có một use case mở rộng: khi nhân viên tìm mà không thấy tay đua trong hệ thống, nhân viên được phép thêm tay đua mới ngay trên **màn hình Tìm tay đua**. `Thêm tay đua` là use case mở rộng (**extend**) của `Tìm tay đua`, dùng lại màn hình Tìm tay đua.

Đăng nhập là chức năng dùng chung của toàn hệ thống: use case `Đăng nhập` gắn với actor cha **Thành viên**, use case `NV đăng nhập` **kế thừa** `Đăng nhập`, và use case chính **include** `NV đăng nhập`.

![Biểu đồ Use Case chi tiết Module 1](<../Module 1 - Quan/hinh/m1-uc-chitiet.png>)

*Hình 4.1 — Biểu đồ Use Case chi tiết Module 1*

### 4.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| **Use case** | Ký hợp đồng tay đua với đội đua |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập thành công vào hệ thống; danh mục đội đua của mùa giải 2025 đã được khai báo |
| **Hậu điều kiện** | Một hợp đồng mới hợp lệ được lưu vào hệ thống với ngày kết thúc để trống (đang hiệu lực); hợp đồng cũ đang hiệu lực của tay đua (nếu có) được đóng lại; hợp đồng mới được in ra |

**Kịch bản chính**

1. Nhân viên (đã đăng nhập) chọn menu **Ký hợp đồng** trên trang chính `gdChinhNV.jsp`.
2. Hệ thống hiển thị màn hình **Tìm tay đua** (`gdTimTayDua.jsp`): ô nhập "Tên tay đua" đang rỗng, nút [Tìm] luôn active, nút [+ Thêm tay đua mới]; bảng kết quả đang rỗng và form thêm tay đua chưa hiện.

   **Màn hình *Tìm tay đua* (`gdTimTayDua.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Tên tay đua | ô nhập | rỗng, con trỏ đặt sẵn |
   | [Tìm] | nút | active |
   | [+ Thêm tay đua mới] | nút | active |
   | [Về trang chủ] | nút | active |
   | Kết quả tìm kiếm | bảng | rỗng — nội dung hiện ở bước 4, mỗi dòng có nút [Chọn] |
   | Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử (form thêm tay đua) | ô nhập | chưa hiện, chỉ hiện khi click [+ Thêm tay đua mới] |
   | [Lưu tay đua] | nút | chưa hiện; khi hiện thì chưa active cho tới khi nhập đủ mã, tên, ngày sinh, quốc tịch |

3. Nhân viên nhập tên `Hamilton` và click [Tìm].
4. Hệ thống hiển thị bảng kết quả tìm kiếm, mỗi dòng có nút [Chọn]; cột "Đội hiện tại" lấy từ hợp đồng có ngày kết thúc trống của tay đua:

   | TT | Mã | Tên | Ngày sinh | Quốc tịch | Đội hiện tại | Thao tác |
   |---|---|---|---|---|---|---|
   | 1 | HAM | Lewis Hamilton | 07/01/1985 | Anh | Mercedes | [Chọn] |

5. Nhân viên click [Chọn] ở dòng `HAM`.
6. Hệ thống hiển thị màn hình **Nhập hợp đồng** (`gdNhapHopDong.jsp`): vùng chỉ đọc ghi `HAM — Lewis Hamilton — 07/01/1985 — Anh`; ô chọn "Đội đua" (danh sách thả xuống gồm Ferrari, Red Bull, McLaren, Mercedes, Aston Martin, Williams) và ô "Ngày bắt đầu" đang rỗng; màn hình **không có ô nhập Ngày kết thúc** — hợp đồng mới luôn được lưu ở trạng thái mở, hệ thống tự đóng khi tay đua ký hợp đồng tiếp theo; nút [Lưu] **chưa được active**.

   **Màn hình *Nhập hợp đồng* (`gdNhapHopDong.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Tay đua | vùng chỉ đọc | `HAM — Lewis Hamilton — 07/01/1985 — Anh` |
   | Hợp đồng cũ | bảng | nội dung ở bảng ngay dưới |
   | Đội đua | danh sách thả xuống | `-- chọn đội đua --`; 6 đội của mùa giải |
   | Ngày bắt đầu | ô nhập | rỗng |
   | Ngày kết thúc | — | không có trên màn hình — hợp đồng mới luôn lưu ở trạng thái mở |
   | [Lưu] | nút | chưa active cho tới khi chọn đủ đội đua và ngày bắt đầu |
   | [Quay lại] | nút | active |

   Bảng "Hợp đồng cũ" của tay đua `HAM — Lewis Hamilton` lúc mới mở màn hình — **dòng có ngày kết thúc trống là hợp đồng đang hiệu lực**:

   | TT | Đội đua | Ngày bắt đầu | Ngày kết thúc |
   |---|---|---|---|
   | 1 | Mercedes | 01/01/2013 | (trống) |

7. Nhân viên chọn `Ferrari` trong ô "Đội đua" và nhập "Ngày bắt đầu" = `01/01/2025`; nút [Lưu] **chuyển sang active**.
8. Nhân viên click [Lưu]; màn hình gửi dữ liệu sang trang xử lý `doLuuHopDong.jsp`.
9. Hệ thống kiểm tra ngày `01/01/2025` không rơi vào khoảng thời gian của bất kỳ hợp đồng đã đóng nào của Lewis Hamilton.
10. Hệ thống tự động đóng hợp đồng đang hiệu lực với Mercedes: đặt ngày kết thúc = `31/12/2024` (ngày liền trước ngày bắt đầu mới).
11. Hệ thống lưu hợp đồng mới: `Lewis Hamilton — Ferrari — 01/01/2025 — ngày kết thúc để trống`.
12. Hệ thống hiển thị thông báo màu xanh "Lưu hợp đồng thành công" kèm bản in hợp đồng; bảng "Hợp đồng cũ" nạp lại thành 2 dòng:

    | TT | Đội đua | Ngày bắt đầu | Ngày kết thúc |
    |---|---|---|---|
    | 1 | Mercedes | 01/01/2013 | 31/12/2024 |
    | 2 | Ferrari | 01/01/2025 | (trống) |

13. Nhân viên click [OK]; hệ thống quay về trang chính của nhân viên.

*(Lặp lại từ bước 1 cho từng tay đua cần ký hợp đồng, cho đến khi nhân viên ký xong toàn bộ.)*

**Ngoại lệ**

- **4a.** Không tìm thấy tay đua nào khớp từ khóa (ví dụ nhập `Antonelli`) → hệ thống hiển thị dòng "Không tìm thấy tay đua nào", nút [+ Thêm tay đua mới] vẫn hiển thị; nhân viên click [+ Thêm tay đua mới] để mở form thêm ngay trên màn hình này, nhập Mã `ANT`, Tên `Andrea Kimi Antonelli`, Ngày sinh `25/08/2006`, Quốc tịch `Ý`, Tiểu sử rồi click [Lưu tay đua] — nút [Lưu tay đua] **chỉ chuyển sang active** khi đã nhập đủ mã, tên, ngày sinh và quốc tịch; lưu xong form đóng lại và hệ thống quay lại bước 4 với bảng kết quả có 1 dòng `ANT`, `Andrea Kimi Antonelli`, `25/08/2006`, `Ý`, `(chưa có)`.
- **7a.** Nhân viên chưa chọn đội đua hoặc chưa nhập ngày bắt đầu → nút [Lưu] vẫn **chưa được active**, không thể chuyển sang bước 8.
- **9a.** Ngày bắt đầu rơi vào khoảng thời gian của một hợp đồng **đã đóng** (ví dụ Carlos Sainz có hợp đồng Ferrari `01/01/2021–31/12/2024`, nhân viên nhập ngày bắt đầu `01/06/2023`) → hệ thống hiện thông báo lỗi màu đỏ ngay dưới form: "Tay đua đã có hợp đồng trong khoảng thời gian này", không lưu, màn hình giữ nguyên dữ liệu đã nhập và quay lại bước 7.
- **9b.** Ngày bắt đầu mới nhỏ hơn hoặc bằng ngày bắt đầu của hợp đồng đang hiệu lực (ví dụ nhập `01/01/2010` trong khi hợp đồng Mercedes bắt đầu `01/01/2013`) → hệ thống báo lỗi "Ngày bắt đầu phải sau ngày bắt đầu của hợp đồng đang hiệu lực", không lưu, quay lại bước 7.
- **10a.** Tay đua chưa có hợp đồng nào đang hiệu lực (ví dụ Oscar Piastri) → bảng "Hợp đồng cũ" ở bước 6 rỗng; hệ thống bỏ qua bước 10 và chuyển thẳng sang bước 11.

> Luồng chuyển màn: **Trang chính → Tìm tay đua → Nhập hợp đồng → (lưu) → Trang chính**.

### 4.3. Biểu đồ trạng thái (phân tích hoạt động)

Biểu đồ bắt đầu từ trạng thái hiển thị **giao diện chính của nhân viên** và kết thúc sau khi nhân viên xác nhận thông báo lưu thành công:

- `Hiển thị GD chính NV` —`[click Ký hợp đồng]`→ `Hiển thị GD tìm tay đua`
- `Hiển thị GD tìm tay đua` có **cung tự quay** `[click Tìm]` (nhân viên tìm nhiều lần đến khi thấy tay đua cần ký)
- `Hiển thị GD tìm tay đua` —`[chọn 1 tay đua]`→ `Hiển thị GD nhập hợp đồng`
- `Hiển thị GD nhập hợp đồng` —`[click Lưu, dữ liệu hợp lệ]`→ `Hiển thị thông báo và in hợp đồng`
- `Hiển thị thông báo và in hợp đồng` —`[click OK]`→ Kết thúc

![Biểu đồ trạng thái Module 1](<../Module 1 - Quan/hinh/m1-trangthai.png>)

*Hình 4.2 — Biểu đồ trạng thái Module 1 (phân tích hoạt động)*

### 4.4. Biểu đồ lớp phân tích

**Lớp biên:**

| Lớp biên | Thuộc tính | Ý nghĩa |
|---|---|---|
| `GDChinhNV` | `-subKyHopDong` | liên kết "Ký hợp đồng" trên trang chính (trang chủ chung của hệ thống) |
| `GDTimTayDua` | `-inTenTayDua` | ô nhập tên tay đua |
| | `-subTim` | nút [Tìm] |
| | `-outsubDSTayDua` | bảng kết quả vừa hiện vừa cho chọn |
| | `-subThemTayDua` | nút [+ Thêm tay đua mới] |
| | `-inMaTayDua` | ô nhập mã tay đua mới (form thêm tay đua) |
| | `-inTenTayDuaMoi` | ô nhập tên tay đua mới (form thêm tay đua) |
| | `-inNgaySinh` | ô nhập ngày sinh (form thêm tay đua) |
| | `-inQuocTich` | ô nhập quốc tịch (form thêm tay đua) |
| | `-inTieuSu` | ô nhập tiểu sử (form thêm tay đua) |
| | `-subLuuTayDua` | nút [Lưu tay đua] (form thêm tay đua) |
| | `-subVeTrangChu` | nút [Về trang chủ] |
| `GDNhapHopDong` | `-outTayDua` | vùng hiện thông tin tay đua đã chọn |
| | `-outDSHopDongCu` | bảng hiện danh sách hợp đồng cũ |
| | `-inDoiDua` | ô chọn đội đua |
| | `-inNgayBatDau` | ô nhập ngày bắt đầu |
| | `-subLuu` | nút [Lưu] |
| | `-subQuayLai` | nút [Quay lại] |

**Phương thức nghiệp vụ gán cho lớp thực thể:**

| Chức năng ở tầng dưới giao diện | Gán cho lớp thực thể | Phương thức |
|---|---|---|
| Tìm tay đua theo tên | `TayDua` | `getTayDuaTheoTen(ten)` |
| Thêm tay đua mới | `TayDua` | `themTayDua()` |
| Lấy danh sách đội đua để chọn | `DoiDua` | `getDSDoiDua()` |
| Lấy hợp đồng cũ của tay đua | `HopDong` | `getHopDongCuaTayDua(tayDuaId)` |
| Kiểm tra chồng lấn thời gian | `HopDong` | `kiemTraChongLan(tayDuaId, ngayBatDau)` |
| Đóng hợp đồng cũ đang hiệu lực | `HopDong` | `dongHopDongCu(tayDuaId, ngayBatDau)` |
| Lưu hợp đồng mới | `HopDong` | `luuHopDong()` |

![Biểu đồ lớp phân tích Module 1](<../Module 1 - Quan/hinh/m1-lop-phantich.png>)

*Hình 4.3 — Biểu đồ lớp phân tích Module 1*

### 4.5. Biểu đồ lớp thiết kế (view `.jsp` / `DAO` / `model`)

- **View (jsp):** `gdChinhNV.jsp` (trang chính của nhân viên), `gdTimTayDua.jsp` (màn hình hiển thị), `gdNhapHopDong.jsp` (màn hình hiển thị), `doLuuHopDong.jsp` (trang xử lý, không hiển thị)
- **DAO:** lớp cha `DAO`; các lớp con `TayDuaDAO`, `DoiDuaDAO`, `HopDongDAO`
- **Model:** `TayDua`, `DoiDua`, `HopDong`, `ThanhVien`, `NhanVien` (đối tượng phiên của các trang jsp)

![Biểu đồ lớp thiết kế Module 1](<../Module 1 - Quan/hinh/m1-lop-mvc.png>)

*Hình 4.4 — Biểu đồ lớp thiết kế Module 1 (view `.jsp` / `DAO` / `model`)*

### 4.6. Biểu đồ hoạt động (pha thiết kế)

![Biểu đồ hoạt động Module 1](<../Module 1 - Quan/hinh/m1-hoatdong.png>)

*Hình 4.5 — Biểu đồ hoạt động Module 1 (pha thiết kế)*

### 4.7. Thuyết minh (kịch bản phiên bản 3)

Luồng chính: Lewis Hamilton đang có hợp đồng hiệu lực với Mercedes, ký hợp đồng mới với Ferrari từ `01/01/2025`. Luồng mở đầu và kết thúc tại **trang chính của nhân viên** `gdChinhNV.jsp`; **luồng lưu**: lớp thực thể `HopDong` tự gọi `setter()` đóng gói dữ liệu nhập **trước**, sau đó trang xử lý mới gọi các hàm của `HopDongDAO` (không gọi constructor thực thể ở luồng lưu). Mỗi dòng thuyết minh tương ứng đúng một message trong biểu đồ tuần tự ở mục 4.8.

1. Nhân viên click [Ký hợp đồng] trên trang chính `gdChinhNV.jsp`.
2. Trang `gdChinhNV.jsp` gọi trang `gdTimTayDua.jsp`.
3. Trang `gdTimTayDua.jsp` hiển thị màn hình tìm tay đua cho nhân viên.
4. Nhân viên nhập tên `Hamilton` và click [Tìm] trên trang `gdTimTayDua.jsp`.
5. Trang `gdTimTayDua.jsp` gọi lớp `TayDuaDAO` yêu cầu tìm tay đua theo tên.
6. Lớp `TayDuaDAO` gọi hàm `getTayDuaTheoTen()`.
7. Hàm `getTayDuaTheoTen()` gọi lớp `TayDua` để đóng gói thông tin.
8. Lớp `TayDua` đóng gói thông tin thực thể.
9. Lớp `TayDua` trả kết quả về cho hàm `getTayDuaTheoTen()`.
10. Hàm `getTayDuaTheoTen()` trả kết quả cho trang `gdTimTayDua.jsp`.
11. Trang `gdTimTayDua.jsp` hiển thị danh sách tay đua tìm được cho nhân viên.
12. Nhân viên chọn tay đua `Lewis Hamilton` trên trang `gdTimTayDua.jsp`.
13. Trang `gdTimTayDua.jsp` gọi trang `gdNhapHopDong.jsp`.
14. Trang `gdNhapHopDong.jsp` gọi lớp `HopDongDAO` yêu cầu tìm danh sách hợp đồng cũ của tay đua.
15. Lớp `HopDongDAO` gọi hàm `getHopDongCuaTayDua()`.
16. Hàm `getHopDongCuaTayDua()` gọi lớp `HopDong` để đóng gói thông tin.
17. Lớp `HopDong` đóng gói thông tin thực thể.
18. Lớp `HopDong` trả kết quả về cho hàm `getHopDongCuaTayDua()`.
19. Hàm `getHopDongCuaTayDua()` trả kết quả cho trang `gdNhapHopDong.jsp`.
20. Trang `gdNhapHopDong.jsp` gọi lớp `DoiDuaDAO` yêu cầu tìm danh sách đội đua.
21. Lớp `DoiDuaDAO` gọi hàm `getDSDoiDua()`.
22. Hàm `getDSDoiDua()` gọi lớp `DoiDua` để đóng gói thông tin.
23. Lớp `DoiDua` đóng gói thông tin thực thể.
24. Lớp `DoiDua` trả kết quả về cho hàm `getDSDoiDua()`.
25. Hàm `getDSDoiDua()` trả kết quả cho trang `gdNhapHopDong.jsp`.
26. Trang `gdNhapHopDong.jsp` hiển thị màn hình nhập hợp đồng cho nhân viên.
27. Nhân viên chọn đội đua `Ferrari` trên trang `gdNhapHopDong.jsp`.
28. Nhân viên nhập ngày bắt đầu `01/01/2025` trên trang `gdNhapHopDong.jsp`.
29. Nhân viên click [Lưu] trên trang `gdNhapHopDong.jsp`.
30. Trang `gdNhapHopDong.jsp` gọi trang `doLuuHopDong.jsp`.
31. Trang `doLuuHopDong.jsp` gọi lớp `HopDong` để đóng gói dữ liệu hợp đồng vừa nhập.
32. Lớp `HopDong` gọi hàm `setter()` tự đóng gói dữ liệu (tay đua, đội đua, ngày bắt đầu).
33. Lớp `HopDong` trả đối tượng đã đóng gói về cho trang `doLuuHopDong.jsp`.
34. Trang `doLuuHopDong.jsp` gọi lớp `HopDongDAO` yêu cầu kiểm tra chồng lấn thời gian hợp đồng.
35. Lớp `HopDongDAO` gọi hàm `kiemTraChongLan()`.
36. Hàm `kiemTraChongLan()` trả kết quả kiểm tra cho trang `doLuuHopDong.jsp`.
37. Trang `doLuuHopDong.jsp` gọi lớp `HopDongDAO` yêu cầu đóng hợp đồng cũ đang hiệu lực.
38. Lớp `HopDongDAO` gọi hàm `dongHopDongCu()`.
39. Hàm `dongHopDongCu()` trả kết quả cho trang `doLuuHopDong.jsp`.
40. Trang `doLuuHopDong.jsp` gọi lớp `HopDongDAO` yêu cầu lưu hợp đồng mới.
41. Lớp `HopDongDAO` gọi hàm `luuHopDong()` lưu đối tượng hợp đồng đã đóng gói.
42. Hàm `luuHopDong()` trả kết quả cho trang `doLuuHopDong.jsp`.
43. Trang `doLuuHopDong.jsp` thông báo lưu hợp đồng thành công (kèm bản in hợp đồng) cho nhân viên.
44. Nhân viên click [OK] trên thông báo của trang `doLuuHopDong.jsp`.
45. Trang `doLuuHopDong.jsp` gọi trang chính `gdChinhNV.jsp`.
46. Trang `gdChinhNV.jsp` hiển thị trang chính cho nhân viên.

*(Lặp lại các bước 1–46 cho đến khi nhân viên ký xong hợp đồng cho tất cả tay đua cần ký.)*

### 4.8. Biểu đồ tuần tự

![Biểu đồ tuần tự Module 1](<../Module 1 - Quan/hinh/m1-tuantu.png>)

*Hình 4.6 — Biểu đồ tuần tự Module 1*

### 4.9. Test case

#### 4.9.1. Data test (bước 3 quy trình test)

`tblTayDua`

| id | ma | ten | ngaySinh | quocTich | tieuSu |
|---|---|---|---|---|---|
| 1 | LEC | Charles Leclerc | 16/10/1997 | Monaco | Trưởng thành từ học viện Ferrari |
| 2 | HAM | Lewis Hamilton | 07/01/1985 | Anh | Bảy lần vô địch thế giới |
| 5 | NOR | Lando Norris | 13/11/1999 | Anh | Lên F1 từ mùa 2019 |
| 6 | PIA | Oscar Piastri | 06/04/2001 | Úc | Vô địch F2 mùa 2021 |
| 12 | SAI | Carlos Sainz | 01/09/1994 | Tây Ban Nha | Từng thi đấu cho Ferrari |

`tblDoiDua`

| id | ma | ten | hang | moTa |
|---|---|---|---|---|
| 1 | FER | Ferrari | Ferrari | Đội đua lâu đời nhất |
| 2 | RBR | Red Bull | Honda RBPT | Trụ sở tại Milton Keynes |
| 3 | MCL | McLaren | Mercedes | Trụ sở tại Woking |
| 4 | MER | Mercedes | Mercedes | Nhà vô địch giai đoạn 2014-2021 |
| 5 | AST | Aston Martin | Mercedes | Đội đua của hãng xe Anh |
| 6 | WIL | Williams | Mercedes | Đội đua tư nhân của Anh |

`tblHopDong`

| id | tblTayDuaid | tblDoiDuaid | ngayBatDau | ngayKetThuc |
|---|---|---|---|---|
| 1 | 2 (HAM) | 4 (Mercedes) | 01/01/2013 | (trống) |
| 2 | 1 (LEC) | 1 (Ferrari) | 01/01/2019 | (trống) |
| 3 | 5 (NOR) | 3 (McLaren) | 01/01/2019 | (trống) |
| 4 | 12 (SAI) | 1 (Ferrari) | 01/01/2021 | 31/12/2024 |

> Tay đua `PIA — Oscar Piastri` (id = 6) chưa có dòng nào trong `tblHopDong`; trong `tblTayDua` không có tay đua nào tên chứa `Antonelli`.

#### 4.9.2. Bảng test case

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|
| | **Giao diện — màn Tìm tay đua** | | |
| KHD_1 | Kiểm tra tổng thể giao diện màn Tìm tay đua | 1. Mở màn Tìm tay đua.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| KHD_2 | Kiểm tra bố cục màn Tìm tay đua | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Ký hợp đồng tay đua với đội đua — Bước 1: Tìm tay đua`.<br>2. Focus được đặt vào ô nhập "Tên tay đua".<br>3. Hiển thị đầy đủ các trường: Tên tay đua (ô nhập) · Bảng kết quả tìm kiếm (bảng: TT, Mã, Tên, Ngày sinh, Quốc tịch, Đội hiện tại, Thao tác) · Form thêm tay đua gồm Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử (ô nhập, ban đầu ẩn).<br>4. Button: [Tìm], [+ Thêm tay đua mới], [Lưu tay đua] (trong form thêm), [Về trang chủ].<br>5. Liên kết click được: nút [Chọn] trên từng dòng bảng kết quả. |
| KHD_3 | Kiểm tra màn Tìm tay đua khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| KHD_4 | Kiểm tra thứ tự phím Tab màn Tìm tay đua | 1. Focus vào màn Tìm tay đua.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| KHD_5 | Kiểm tra thứ tự phím Shift-Tab màn Tìm tay đua | 1. Focus vào màn Tìm tay đua.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| KHD_6 | Kiểm tra phím Enter màn Tìm tay đua | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| | **Giao diện — màn Nhập hợp đồng** | | |
| KHD_7 | Kiểm tra tổng thể giao diện màn Nhập hợp đồng | 1. Mở màn Nhập hợp đồng.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| KHD_8 | Kiểm tra bố cục màn Nhập hợp đồng | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Ký hợp đồng tay đua với đội đua — Bước 2: Nhập thông tin hợp đồng`.<br>2. Focus được đặt vào ô chọn "Đội đua".<br>3. Hiển thị đầy đủ các trường: Tay đua (vùng chỉ đọc) · Bảng "Hợp đồng cũ" (bảng: TT, Đội đua, Ngày bắt đầu, Ngày kết thúc) · Đội đua (danh sách thả xuống) · Ngày bắt đầu (ô nhập); màn hình không có ô nhập Ngày kết thúc.<br>4. Button: [Lưu], [Quay lại]. |
| KHD_9 | Kiểm tra màn Nhập hợp đồng khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| KHD_10 | Kiểm tra thứ tự phím Tab màn Nhập hợp đồng | 1. Focus vào màn Nhập hợp đồng.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| KHD_11 | Kiểm tra thứ tự phím Shift-Tab màn Nhập hợp đồng | 1. Focus vào màn Nhập hợp đồng.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| KHD_12 | Kiểm tra phím Enter màn Nhập hợp đồng | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| KHD_13 | Màn Tìm tay đua hiển thị đúng khi CSDL có dữ liệu | 1. Nhập `Hamilton`, click [Tìm]. | Danh sách khớp các bản ghi trong `tblTayDua` có tên chứa `Hamilton`: 1 dòng `HAM \| Lewis Hamilton \| 07/01/1985 \| Anh \| Mercedes`; cột "Đội hiện tại" đối chiếu đúng dòng `tblHopDong` có `ngayKetThuc` trống của tay đua |
| KHD_14 | Màn Tìm tay đua khi không có dữ liệu khớp | 1. Nhập `Schumacher`, click [Tìm]. | Bảng kết quả hiện dòng "Không tìm thấy tay đua nào" (trong `tblTayDua` không có bản ghi tên chứa `Schumacher`); nút [+ Thêm tay đua mới] vẫn hiển thị |
| KHD_15 | Màn Nhập hợp đồng hiển thị đúng dữ liệu tay đua có hợp đồng | 1. Tìm và chọn `HAM`. | Bảng "Hợp đồng cũ" khớp các bản ghi trong `tblHopDong` của tay đua id = 2: 1 dòng `Mercedes \| 01/01/2013 \| (trống)`; ô chọn "Đội đua" chứa đủ 6 đội khớp `tblDoiDua` (Ferrari, Red Bull, McLaren, Mercedes, Aston Martin, Williams) |
| KHD_16 | Màn Nhập hợp đồng khi tay đua chưa có hợp đồng | 1. Tìm và chọn `PIA`. | Bảng "Hợp đồng cũ" **rỗng** (trong `tblHopDong` không có bản ghi nào của tay đua id = 6); hai ô nhập rỗng; nút [Lưu] chưa được active |
| KHD_17 | Ký hợp đồng mới cho tay đua tự do — chưa có hợp đồng nào (ca chuẩn) | 1. Tại trang chính click [Ký hợp đồng].<br>2. Nhập `Piastri`, click [Tìm] — bảng hiện 1 dòng `PIA \| Oscar Piastri \| 06/04/2001 \| Úc \| (chưa có)`.<br>3. Click [Chọn] ở dòng `PIA` — bảng "Hợp đồng cũ" rỗng, nút [Lưu] chưa active.<br>4. Chọn đội đua `McLaren`, nhập ngày bắt đầu `01/01/2025` — nút [Lưu] chuyển sang active.<br>5. Click [Lưu]. | Thông báo xanh "Lưu hợp đồng thành công" kèm bản in hợp đồng `Oscar Piastri — McLaren — từ 01/01/2025`; bảng "Hợp đồng cũ" nạp lại 1 dòng `McLaren \| 01/01/2025 \| (trống)`. **CSDL:** `tblHopDong` thêm bản ghi mới `id = 5 \| 6 (PIA) \| 3 (McLaren) \| 01/01/2025 \| (trống)`; `tblTayDua`, `tblDoiDua` không thay đổi |
| KHD_18 | Ký hợp đồng khi tay đua đang có hợp đồng hiệu lực — hệ thống tự đóng hợp đồng cũ | 1. Nhập `Hamilton`, click [Tìm], click [Chọn] ở dòng `HAM` — bảng "Hợp đồng cũ" có 1 dòng `Mercedes \| 01/01/2013 \| (trống)`.<br>2. Chọn đội đua `Ferrari`, nhập ngày bắt đầu `01/01/2025`.<br>3. Click [Lưu]. | Thông báo "Lưu hợp đồng thành công" kèm bản in `Lewis Hamilton — Ferrari — từ 01/01/2025`; bảng "Hợp đồng cũ" nạp lại 2 dòng. **CSDL:** `tblHopDong`: hợp đồng cũ id = 1 (HAM — Mercedes) được tự động đóng với `ngayKetThuc = 31/12/2024`; thêm bản ghi mới `HAM — Ferrari — 01/01/2025 — (trống)` |
| KHD_19 | Ngày bắt đầu chồng lấn hợp đồng đã đóng — báo lỗi, không lưu | 1. Nhập `Sainz`, click [Tìm], click [Chọn] ở dòng `SAI` — bảng "Hợp đồng cũ" có 1 dòng `Ferrari \| 01/01/2021 \| 31/12/2024`.<br>2. Chọn đội đua `Williams`, nhập ngày bắt đầu `01/06/2023`.<br>3. Click [Lưu]. | Thông báo lỗi màu đỏ ngay dưới form: "Tay đua đã có hợp đồng trong khoảng thời gian này"; dữ liệu đã nhập giữ nguyên trên form để sửa lại. **CSDL: không bảng nào thay đổi** — `tblHopDong` vẫn giữ đúng 4 bản ghi như Data test |
| KHD_20 | Không tìm thấy tay đua — thêm tay đua mới rồi ký hợp đồng | 1. Nhập `Antonelli`, click [Tìm] — hiện "Không tìm thấy tay đua nào".<br>2. Click [+ Thêm tay đua mới] — form thêm tay đua hiện ra, nút [Lưu tay đua] chưa active.<br>3. Nhập Mã `ANT`, Tên `Andrea Kimi Antonelli`, Ngày sinh `25/08/2006`, Quốc tịch `Ý`, Tiểu sử `Tay đua trẻ của học viện Mercedes`, click [Lưu tay đua].<br>4. Bảng kết quả nạp lại dòng `ANT`; click [Chọn].<br>5. Chọn đội đua `Mercedes`, nhập ngày bắt đầu `01/01/2025`, click [Lưu]. | Sau bước 3: tay đua mới được lưu, bảng kết quả có 1 dòng `ANT \| Andrea Kimi Antonelli \| 25/08/2006 \| Ý \| (chưa có)`. Sau bước 5: thông báo "Lưu hợp đồng thành công" kèm bản in `Andrea Kimi Antonelli — Mercedes — từ 01/01/2025`. **CSDL:** `tblTayDua` thêm bản ghi mới `ANT — Andrea Kimi Antonelli — 25/08/2006 — Ý`; `tblHopDong` thêm bản ghi mới `ANT — Mercedes — 01/01/2025 — (trống)` |

---

## CHƯƠNG 5: MODULE 2 — ĐĂNG KÝ TAY ĐUA THAM GIA CHẶNG ĐUA

**Thành viên thực hiện:** Trần Xuân Kiên — **Use case:** Đăng ký tay đua tham gia chặng đua

### 5.1. Biểu đồ Use Case chi tiết

Use case chính của module là **`Đăng ký tay đua tham gia chặng đua`**, do actor **Nhân viên** thực hiện. Đăng nhập là chức năng dùng chung của toàn hệ thống nên biểu đồ tách thành use case `Đăng nhập` gắn với actor cha **Thành viên**, còn use case `NV đăng nhập` **kế thừa** `Đăng nhập` cho vai trò Nhân viên; use case chính **include** `NV đăng nhập`.

| Màn hình | Use case con | Quan hệ với UC chính |
|---|---|---|
| (dùng chung toàn hệ thống) | `NV đăng nhập` — kế thừa `Đăng nhập` | include |
| Chọn chặng và đội | `Chọn chặng và đội` | include |
| Đăng ký tay đua | `Chọn tay đua đăng ký` | include |

Ghi chú:

![Biểu đồ Use Case chi tiết Module 2](<../Module 2 - Kin/hinh/m2-uc-chitiet.png>)

*Hình 5.1 — Biểu đồ Use Case chi tiết Module 2*

### 5.2. Đặc tả Use Case

Luồng màn hình: **Chọn chặng và đội → Đăng ký tay đua**; phác thảo của mỗi màn đặt ngay dưới bước hệ thống hiển thị màn đó. Điểm vào của luồng là trang chính `gdChinhNV.jsp` (lớp biên `GDChinhNV`) chứa liên kết "Đăng ký thi đấu"; trang này dùng chung cho mọi module nên không phác thảo lại ở đây.

| Mục | Nội dung |
|---|---|
| **Use case** | Đăng ký tay đua tham gia chặng đua |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập hệ thống. Mùa giải 2025 đang ở trạng thái "Đang diễn ra". Chặng đua và đội đua đã có trong danh mục. Hợp đồng giữa tay đua và đội đua đã được nhập ở module "Ký hợp đồng tay đua với đội đua". |
| **Hậu điều kiện** | Danh sách đăng ký (tối đa 2 tay đua) của đội cho chặng đua được lưu vào CSDL; hệ thống hiển thị lại danh sách xuất phát của chặng để nhân viên đối soát và in cho ban tổ chức. |

**Kịch bản chính**

1. Nhân viên (sau khi đăng nhập) đang ở trang chính `gdChinhNV.jsp` của hệ thống, click chức năng "Đăng ký thi đấu".
2. Hệ thống hiển thị màn hình **Chọn chặng và đội** (trang `gdChonChangDoi.jsp`): ô chọn "Chặng đua" đang rỗng, ô chọn "Đội đua" đang rỗng, nút [Tiếp tục] **chưa được active** — nút chỉ chuyển sang active khi cả hai ô chọn đã có giá trị.

   **Màn hình *Chọn chặng và đội* (`gdChonChangDoi.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Chặng đua | danh sách thả xuống | chưa chọn giá trị nào; nội dung ở bảng ngay dưới |
   | Đội đua | danh sách thả xuống | chưa chọn giá trị nào; nội dung ở bảng ngay dưới |
   | [Tiếp tục] | nút | chưa active, chỉ active khi cả hai ô chọn đã có giá trị |
   | [Về trang chủ] | nút | active |

   Nội dung danh sách thả xuống **Chặng đua** — chỉ lấy chặng của mùa giải đang diễn ra (2025), sắp xếp tăng dần theo thời gian, mỗi dòng hiển thị dạng `Mã - Tên chặng - Địa điểm - Thời gian`:

   | TT | Mã | Tên chặng | Địa điểm | Thời gian |
   |---|---|---|---|---|
   | 1 | R01 | Australian Grand Prix | Melbourne | 16/03/2025 |
   | 2 | R02 | Chinese Grand Prix | Thượng Hải | 23/03/2025 |
   | 3 | R06 | Monaco Grand Prix | Monte Carlo | 25/05/2025 |
   | 4 | R10 | British Grand Prix | Silverstone | 06/07/2025 |
   | 5 | R16 | Italian Grand Prix | Monza | 07/09/2025 |
   | 6 | R24 | Abu Dhabi Grand Prix | Yas Marina | 07/12/2025 |

   Nội dung danh sách thả xuống **Đội đua** — liệt kê theo thứ tự `id` của `tblDoiDua`, mỗi dòng hiển thị dạng `Tên đội (Hãng)`:

   | TT | Tên đội | Hãng | Dòng hiển thị |
   |---|---|---|---|
   | 1 | Ferrari | Ferrari | Ferrari (Ferrari) |
   | 2 | Red Bull | Honda RBPT | Red Bull (Honda RBPT) |
   | 3 | McLaren | Mercedes | McLaren (Mercedes) |
   | 4 | Mercedes | Mercedes | Mercedes (Mercedes) |
   | 5 | Aston Martin | Mercedes | Aston Martin (Mercedes) |
   | 6 | Williams | Mercedes | Williams (Mercedes) |

3. Nhân viên chọn chặng `R06 - Monaco Grand Prix - Monte Carlo - 25/05/2025` và chọn đội `Red Bull (Honda RBPT)`; nút [Tiếp tục] **chuyển sang active**.
4. Nhân viên click [Tiếp tục]; hệ thống chuyển sang màn hình tiếp theo, mang theo chặng và đội vừa chọn.
5. Hệ thống hiển thị màn hình **Đăng ký tay đua** (trang `gdDangKyTayDua.jsp`) với tiêu đề `Chặng R06 - Monaco Grand Prix - 25/05/2025 — Đội Red Bull`; bảng tay đua gồm 6 cột **Chọn**, **Mã**, **Tên**, **Ngày sinh**, **Quốc tịch**, **Trạng thái đăng ký**, chỉ liệt kê tay đua đang có hợp đồng hiệu lực với Red Bull tại ngày 25/05/2025 và **sắp xếp tăng dần theo alphabet của cột Tên** (`Max Verstappen` trước `Yuki Tsunoda`); lúc mới vào màn mọi ô tick đều trống, cột Trạng thái đăng ký ghi `Chưa đăng ký`, bảng danh sách xuất phát chưa hiện, nút [Lưu] và nút [Sửa] đều **chưa được active**, nút [OK] **chưa hiện**.

   **Màn hình *Đăng ký tay đua* (`gdDangKyTayDua.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Tiêu đề chặng và đội | vùng chỉ đọc | `Chặng R06 - Monaco Grand Prix - 25/05/2025 — Đội Red Bull` |
   | Danh sách tay đua | bảng có ô tick | nội dung ở bảng 1 dưới đây; mọi ô tick đang trống, cột Trạng thái đăng ký ghi `Chưa đăng ký` |
   | Danh sách xuất phát của chặng | bảng | chưa hiện, chỉ hiện sau khi lưu thành công |
   | [Quay lại] | nút | active |
   | [Sửa] | nút | chưa active |
   | [Lưu] | nút | chưa active, chỉ active khi có ít nhất một dòng được tick |
   | [OK] | nút | chưa hiện, chỉ hiện cùng thông báo lưu thành công |

   Bảng 1 — **Danh sách tay đua** của đội Red Bull có hợp đồng hiệu lực tại ngày 25/05/2025, sắp xếp A → Z theo cột Tên; minh hoạ trạng thái sau khi nhân viên đã tick chọn 2 tay đua ở bước 6–7 — đây cũng là **số lượng tối đa** được phép tick:

   | Chọn | Mã | Tên | Ngày sinh | Quốc tịch | Trạng thái đăng ký |
   |---|---|---|---|---|---|
   | [x] | VER | Max Verstappen | 30/09/1997 | Hà Lan | Chưa đăng ký |
   | [x] | TSU | Yuki Tsunoda | 11/05/2000 | Nhật Bản | Chưa đăng ký |

   Cột **Trạng thái đăng ký** nhận một trong ba giá trị `Chưa đăng ký`, `Đã đăng ký (<tên đội đang xem>)` hoặc `Đã đăng ký (<tên đội khác>)` — giá trị cuối là cảnh báo trực quan cho ràng buộc trùng đăng ký.

6. Nhân viên tick chọn dòng `VER - Max Verstappen`; nút [Lưu] **chuyển sang active** (nút [Lưu] active ngay khi có ít nhất một dòng được tick).
7. Nhân viên tick chọn dòng `TSU - Yuki Tsunoda`.

   *(Lặp lại bước 6–7 cho đến khi tick xong các tay đua mà đội yêu cầu, nhiều nhất 2 tay đua.)*

8. Nhân viên click [Lưu]; dữ liệu được gửi sang trang xử lý `doLuuDangKy.jsp`.
9. Hệ thống kiểm tra lần lượt: số tay đua được tick là 2 (≤ 2 — hợp lệ); `Max Verstappen` và `Yuki Tsunoda` đều chưa đăng ký chặng R06 cho đội nào khác (hợp lệ); ngày hiện tại 20/05/2025 vẫn trước thời gian diễn ra chặng 25/05/2025 (hợp lệ).
10. Hệ thống lưu 2 dòng đăng ký vào CSDL rồi **quay lại chính màn hình Đăng ký tay đua**: cột **Trạng thái đăng ký** của 2 dòng vừa lưu đổi thành `Đã đăng ký (Red Bull)`; phía dưới hiện bảng 2 — **danh sách xuất phát** của chặng R06 gồm 3 cột **Đội**, **Tay đua 1**, **Tay đua 2** — kèm thông báo "Đã lưu đăng ký cho đội Red Bull ở chặng R06"; nút [Sửa] **chuyển sang active**, nút [OK] **hiện ra** cùng thông báo.

    | Đội | Tay đua 1 | Tay đua 2 |
    |---|---|---|
    | Red Bull | Max Verstappen | Yuki Tsunoda |

11. Nhân viên đối soát danh sách xuất phát, in gửi ban tổ chức rồi click [OK]; hệ thống quay về trang chính `gdChinhNV.jsp`.

**Ngoại lệ**

- **5a.** Đội được chọn không có tay đua nào có hợp đồng hiệu lực tại thời điểm chặng (ví dụ chọn `R06 - Monaco Grand Prix` và đội `Aston Martin` khi chưa nhập hợp đồng nào cho đội này) → bảng tay đua rỗng, hệ thống hiển thị thông báo "Đội Aston Martin không có tay đua nào có hợp đồng hiệu lực tại thời điểm chặng R06", nút [Lưu] vẫn chưa được active; nhân viên click [Quay lại] để trở về màn hình Chọn chặng và đội, hệ thống giữ nguyên chặng đang chọn để nhân viên chọn đội khác.
- **5b.** Chặng và đội được chọn đã có đăng ký từ trước (ví dụ `R06` + `Red Bull` đã đăng ký `Max Verstappen`, `Yuki Tsunoda`) → hệ thống hiển thị bảng tay đua với các tay đua đang đăng ký **được tick sẵn**, cột Trạng thái đăng ký ghi `Đã đăng ký (Red Bull)`; nút [Sửa] **đang active** (nút [Sửa] chỉ active khi chặng và đội đang xem đã có đăng ký trong CSDL). Nhân viên click [Sửa] để mở khoá các ô tick, bỏ tick `Yuki Tsunoda` (chấn thương), rồi click [Lưu] để lưu lại danh sách mới — đây là luồng thay tay đua trước ngày đua.
- **9a.** Số tay đua được tick lớn hơn 2 (ví dụ tại chặng `R10 - British Grand Prix - 06/07/2025`, đội `Ferrari` có 3 tay đua hợp đồng hiệu lực là `Charles Leclerc`, `Lewis Hamilton` và `Carlos Sainz` — Sainz vừa ký hợp đồng mới với Ferrari giữa mùa — nhân viên tick cả 3) → trang xử lý `doLuuDangKy.jsp` báo lỗi "Mỗi đội chỉ được đăng ký tối đa 2 tay đua trong một chặng", không ghi dòng nào, giữ nguyên màn hình để nhân viên bỏ bớt tick rồi lưu lại.
- **9b.** Một tay đua được tick đã được đăng ký chặng này cho đội khác (ví dụ `Carlos Sainz` đã được đăng ký chặng `R10` cho `Williams` trước khi chuyển sang `Ferrari`, nhân viên vẫn tick `Carlos Sainz` ở màn đăng ký của đội `Ferrari`) → hệ thống báo lỗi "Tay đua Carlos Sainz đã được đăng ký cho đội Williams ở chặng R10", không lưu dòng nào.
- **9c.** Ngày hiện tại đã qua thời gian diễn ra chặng (ví dụ sửa đăng ký chặng `R01 - 16/03/2025` vào ngày 20/05/2025) → hệ thống báo lỗi "Chặng đã diễn ra, không được thay đổi danh sách đăng ký", không lưu.

> Luồng chuyển màn: **Trang chính → Chọn chặng và đội → Đăng ký tay đua → (lưu qua `doLuuDangKy.jsp`) → Đăng ký tay đua (hiển thị lại kèm danh sách xuất phát) → Trang chính**.

### 5.3. Biểu đồ trạng thái (phân tích hoạt động)

Biểu đồ bắt đầu từ trạng thái hiển thị **giao diện chính** của nhân viên: `Hiển thị GD chính NV` —`[click Đăng ký thi đấu]`→ `Hiển thị GD chọn chặng và đội` (cung tự quay `[chọn chặng / chọn đội]`) —`[click Tiếp tục]`→ `Hiển thị GD đăng ký tay đua` (cung tự quay `[tick chọn tay đua]`, cung `[click Quay lại]` trở về màn chọn chặng và đội) —`[click Lưu, hợp lệ]`→ `Hiển thị thông báo + danh sách xuất phát` —`[click OK]`→ Kết thúc.

![Biểu đồ trạng thái Module 2](<../Module 2 - Kin/hinh/m2-trangthai.png>)

*Hình 5.2 — Biểu đồ trạng thái Module 2 (phân tích hoạt động)*

### 5.4. Biểu đồ lớp phân tích

Biểu đồ chỉ gồm **hai tầng**: lớp biên và lớp thực thể. Không có lớp điều khiển; nghiệp vụ được gán thẳng cho lớp thực thể.

**Lớp biên** (mỗi màn hình một lớp, chỉ có thuộc tính, đặt tên theo chức năng dữ liệu `in / out / inout / sub / outsub`):

| Lớp biên | Màn hình | Thuộc tính |
|---|---|---|
| `GDChinhNV` | Trang chính của nhân viên (trang chủ chung hệ thống) | `-subDangKyChang` |
| `GDChonChangDoi` | Chọn chặng và đội | `-inChangDua`, `-inDoiDua`, `-subTiepTuc`, `-subVeTrangChu` |
| `GDDangKyTayDua` | Đăng ký tay đua | `-outsubDSTayDua`, `-subLuu`, `-subSua`, `-outDSXuatPhat`, `-subQuayLai`, `-subOK` |

**Phương thức nghiệp vụ gán cho lớp thực thể:**

| Chức năng cần thực hiện dưới tầng giao diện | Gán cho lớp | Phương thức |
|---|---|---|
| Lấy danh sách chặng đua của mùa giải | `ChangDua` | `getDSChangDua()` |
| Lấy danh sách đội đua | `DoiDua` | `getDSDoiDua()` |
| Tìm tay đua có hợp đồng hiệu lực với đội tại thời điểm chặng | `HopDong` | `getTayDuaHieuLuc(doiDuaId, thoiGianChang)` |
| Đếm số tay đua đội đã đăng ký trong chặng (ràng buộc ≤ 2) | `DangKyChang` | `demSoTayDua(changDuaId, doiDuaId)` |
| Kiểm tra tay đua đã đăng ký chặng này chưa (ràng buộc trùng) | `DangKyChang` | `daDangKy(changDuaId, tayDuaId)` |
| Lưu một dòng đăng ký | `DangKyChang` | `luuDangKy()` |
| Lấy danh sách xuất phát của chặng | `DangKyChang` | `getDangKyCuaChang(changDuaId)` |

![Biểu đồ lớp phân tích Module 2](<../Module 2 - Kin/hinh/m2-lop-phantich.png>)

*Hình 5.3 — Biểu đồ lớp phân tích Module 2*

### 5.5. Biểu đồ lớp thiết kế (view `.jsp` / `DAO` / `model`)

- **Tầng view** — các trang jsp: `gdChinhNV.jsp` (trang chính), `gdChonChangDoi.jsp` (màn hình 1), `gdDangKyTayDua.jsp` (màn hình 2), `doLuuDangKy.jsp` (trang xử lý lưu, không hiển thị giao diện). Mỗi trang có thuộc tính **kèm kiểu control** (`Select` — danh sách thả xuống, `Table` — bảng, `link` — liên kết, `submit` — nút bấm) và các **thuộc tính ẩn**: đối tượng phiên `-nv : NhanVien` và dữ liệu truyền giữa các trang (`-changDua : ChangDua`, `-doiDua : DoiDua`, `-listTayDua : TayDua[]`, `-listDangKy : DangKyChang[]`).
- **Tầng dao** — lớp cha `DAO` giữ kết nối CSDL dùng chung (`-con : Connection`); các lớp `MuaGiaiDAO`, `ChangDuaDAO`, `DoiDuaDAO`, `HopDongDAO`, `DangKyChangDAO` **kế thừa** lớp `DAO`, mỗi lớp có **constructor** và các phương thức ghi **đầy đủ chữ ký** (tham số : kiểu, kiểu trả về — mảng `Xxx[]` cho thao tác đọc danh sách, `boolean` cho thao tác ghi), ví dụ `+getTayDuaHieuLuc(doiDuaId : int, thoiGianChang : Date) : TayDua[]`, `+luuDangKy(dk : DangKyChang) : boolean`.
- **Tầng model** — các lớp thực thể: `MuaGiai`, `ChangDua`, `DoiDua`, `TayDua`, `HopDong`, `DangKyChang`, `ThanhVien`, `NhanVien` (đối tượng phiên của các trang jsp).

![Biểu đồ lớp thiết kế Module 2](<../Module 2 - Kin/hinh/m2-lop-mvc.png>)

*Hình 5.4 — Biểu đồ lớp thiết kế Module 2 (view `.jsp` / `DAO` / `model`)*

### 5.6. Biểu đồ hoạt động (pha thiết kế)

![Biểu đồ hoạt động Module 2](<../Module 2 - Kin/hinh/m2-hoatdong.png>)

*Hình 5.5 — Biểu đồ hoạt động Module 2 (pha thiết kế)*

### 5.7. Thuyết minh (kịch bản phiên bản 3)

Kịch bản dưới đây chỉ mô tả **luồng chính**; các ngoại lệ đã nêu ở đặc tả use case mục 5.2. Mỗi dòng tương ứng với một message trong biểu đồ tuần tự ở mục 5.8 (64 dòng — 64 message). Luồng **đọc** dữ liệu giữ chuỗi 7 message (DAO self-call tên hàm + lớp thực thể self-call constructor); luồng **lưu**: lớp thực thể tự đóng gói dữ liệu nhập bằng `setter()` **trước**, rồi trang xử lý mới gọi DAO lưu (DAO không gọi lại lớp thực thể nữa).

1. Nhân viên (sau khi đăng nhập) đang ở trang chính gdChinhNV.jsp, click chức năng "Đăng ký thi đấu".
2. Trang gdChinhNV.jsp gọi trang gdChonChangDoi.jsp.
3. Trang gdChonChangDoi.jsp gọi lớp MuaGiaiDAO yêu cầu lấy mùa giải đang diễn ra.
4. Lớp MuaGiaiDAO gọi hàm getMuaGiaiHienTai().
5. Hàm getMuaGiaiHienTai() gọi lớp MuaGiai để đóng gói thông tin.
6. Lớp MuaGiai đóng gói thông tin thực thể.
7. Lớp MuaGiai trả kết quả về cho hàm getMuaGiaiHienTai().
8. Hàm getMuaGiaiHienTai() trả kết quả cho trang gdChonChangDoi.jsp.
9. Trang gdChonChangDoi.jsp gọi lớp ChangDuaDAO yêu cầu lấy danh sách chặng đua của mùa giải đang diễn ra.
10. Lớp ChangDuaDAO gọi hàm getDSChangDua().
11. Hàm getDSChangDua() gọi lớp ChangDua để đóng gói thông tin.
12. Lớp ChangDua đóng gói thông tin thực thể.
13. Lớp ChangDua trả kết quả về cho hàm getDSChangDua().
14. Hàm getDSChangDua() trả kết quả cho trang gdChonChangDoi.jsp.
15. Trang gdChonChangDoi.jsp gọi lớp DoiDuaDAO yêu cầu lấy danh sách đội đua.
16. Lớp DoiDuaDAO gọi hàm getDSDoiDua().
17. Hàm getDSDoiDua() gọi lớp DoiDua để đóng gói thông tin.
18. Lớp DoiDua đóng gói thông tin thực thể.
19. Lớp DoiDua trả kết quả về cho hàm getDSDoiDua().
20. Hàm getDSDoiDua() trả kết quả cho trang gdChonChangDoi.jsp.
21. Trang gdChonChangDoi.jsp hiển thị hai danh sách thả xuống cho nhân viên.
22. Nhân viên chọn chặng đua "R06 - Monaco Grand Prix - 25/05/2025".
23. Nhân viên chọn đội đua "Red Bull".
24. Nhân viên click nút [Tiếp tục].
25. Trang gdChonChangDoi.jsp gọi trang gdDangKyTayDua.jsp.
26. Trang gdDangKyTayDua.jsp gọi lớp HopDongDAO yêu cầu tìm các tay đua có hợp đồng hiệu lực với đội tại thời điểm chặng.
27. Lớp HopDongDAO gọi hàm getTayDuaHieuLuc().
28. Hàm getTayDuaHieuLuc() gọi lớp TayDua để đóng gói thông tin.
29. Lớp TayDua đóng gói thông tin thực thể.
30. Lớp TayDua trả kết quả về cho hàm getTayDuaHieuLuc().
31. Hàm getTayDuaHieuLuc() trả kết quả cho trang gdDangKyTayDua.jsp.
32. Trang gdDangKyTayDua.jsp gọi lớp DangKyChangDAO yêu cầu kiểm tra trạng thái đăng ký của từng tay đua trong chặng.
33. Lớp DangKyChangDAO gọi hàm daDangKy().
34. Hàm daDangKy() gọi lớp DangKyChang để đóng gói thông tin.
35. Lớp DangKyChang đóng gói thông tin thực thể.
36. Lớp DangKyChang trả kết quả về cho hàm daDangKy().
37. Hàm daDangKy() trả kết quả cho trang gdDangKyTayDua.jsp.
38. Trang gdDangKyTayDua.jsp hiển thị bảng tay đua (sắp xếp theo alphabet của cột Tên) cho nhân viên.
39. Nhân viên tick chọn một tay đua (lặp lại cho đến khi chọn xong các tay đua đội yêu cầu, nhiều nhất 2).
40. Nhân viên click nút [Lưu].
41. Trang gdDangKyTayDua.jsp gọi trang doLuuDangKy.jsp.
42. Trang doLuuDangKy.jsp gọi lớp DangKyChangDAO yêu cầu đếm số tay đua mà đội đã đăng ký trong chặng.
43. Lớp DangKyChangDAO gọi hàm demSoTayDua().
44. Hàm demSoTayDua() gọi lớp DangKyChang để đóng gói thông tin.
45. Lớp DangKyChang đóng gói thông tin thực thể.
46. Lớp DangKyChang trả kết quả về cho hàm demSoTayDua().
47. Hàm demSoTayDua() trả kết quả cho trang doLuuDangKy.jsp.
48. Trang doLuuDangKy.jsp gọi lớp DangKyChang yêu cầu đóng gói dữ liệu một dòng đăng ký (lặp lại các bước 48–53 cho từng tay đua được chọn).
49. Lớp DangKyChang gọi hàm setter() tự đóng gói dữ liệu đăng ký vừa nhập.
50. Lớp DangKyChang trả về cho trang doLuuDangKy.jsp.
51. Trang doLuuDangKy.jsp gọi lớp DangKyChangDAO yêu cầu lưu dòng đăng ký.
52. Lớp DangKyChangDAO gọi hàm luuDangKy().
53. Hàm luuDangKy() trả kết quả cho trang doLuuDangKy.jsp.
54. Trang doLuuDangKy.jsp gọi lớp DangKyChangDAO yêu cầu lấy danh sách xuất phát của chặng.
55. Lớp DangKyChangDAO gọi hàm getDangKyCuaChang().
56. Hàm getDangKyCuaChang() gọi lớp DangKyChang để đóng gói thông tin.
57. Lớp DangKyChang đóng gói thông tin thực thể.
58. Lớp DangKyChang trả kết quả về cho hàm getDangKyCuaChang().
59. Hàm getDangKyCuaChang() trả kết quả cho trang doLuuDangKy.jsp.
60. Trang doLuuDangKy.jsp trả kết quả kèm thông báo thành công cho trang gdDangKyTayDua.jsp.
61. Trang gdDangKyTayDua.jsp hiển thị thông báo thành công và danh sách xuất phát cho nhân viên đối soát.
62. Nhân viên click nút [OK].
63. Trang gdDangKyTayDua.jsp gọi trang gdChinhNV.jsp.
64. Trang gdChinhNV.jsp hiển thị cho nhân viên.

### 5.8. Biểu đồ tuần tự

![Biểu đồ tuần tự Module 2](<../Module 2 - Kin/hinh/m2-tuantu.png>)

*Hình 5.6 — Biểu đồ tuần tự Module 2*

### 5.9. Test case

#### 5.9.1. Data test (bước 3 quy trình test)

Toàn bộ các ca dùng chung bộ dữ liệu mùa giải F1 2025 đã thống nhất của nhóm; đây là tiền đề chung cho nhóm **Luồng nghiệp vụ**.

`tblMuaGiai`

| id | ten | nam | trangThai |
|---|---|---|---|
| 1 | FIA Formula One World Championship | 2025 | Đang diễn ra |

`tblDoiDua`

| id | ma | ten | hang | moTa |
|---|---|---|---|---|
| 1 | FER | Ferrari | Ferrari | Scuderia Ferrari |
| 2 | RBR | Red Bull | Honda RBPT | Oracle Red Bull Racing |
| 3 | MCL | McLaren | Mercedes | McLaren Formula 1 Team |
| 4 | MER | Mercedes | Mercedes | Mercedes-AMG Petronas F1 Team |
| 5 | AST | Aston Martin | Mercedes | Aston Martin Aramco F1 Team |
| 6 | WIL | Williams | Mercedes | Williams Racing |

`tblTayDua`

| id | ma | ten | ngaySinh | quocTich | tieuSu |
|---|---|---|---|---|---|
| 1 | LEC | Charles Leclerc | 16/10/1997 | Monaco | (…) |
| 2 | HAM | Lewis Hamilton | 07/01/1985 | Anh | (…) |
| 3 | VER | Max Verstappen | 30/09/1997 | Hà Lan | (…) |
| 4 | TSU | Yuki Tsunoda | 11/05/2000 | Nhật Bản | (…) |
| 5 | NOR | Lando Norris | 13/11/1999 | Anh | (…) |
| 6 | PIA | Oscar Piastri | 06/04/2001 | Úc | (…) |
| 7 | RUS | George Russell | 15/02/1998 | Anh | (…) |
| 8 | ANT | Andrea Kimi Antonelli | 25/08/2006 | Ý | (…) |
| 9 | ALO | Fernando Alonso | 29/07/1981 | Tây Ban Nha | (…) |
| 10 | STR | Lance Stroll | 29/10/1998 | Canada | (…) |
| 11 | ALB | Alexander Albon | 23/03/1996 | Thái Lan | (…) |
| 12 | SAI | Carlos Sainz | 01/09/1994 | Tây Ban Nha | (…) |

`tblChangDua`

| id | ma | ten | soVong | diaDiem | thoiGian | moTa | tblMuaGiaiid |
|---|---|---|---|---|---|---|---|
| 1 | R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | (…) | 1 |
| 2 | R02 | Chinese Grand Prix | 56 | Thượng Hải | 23/03/2025 | (…) | 1 |
| 3 | R06 | Monaco Grand Prix | 78 | Monte Carlo | 25/05/2025 | (…) | 1 |
| 4 | R10 | British Grand Prix | 52 | Silverstone | 06/07/2025 | (…) | 1 |
| 5 | R16 | Italian Grand Prix | 53 | Monza | 07/09/2025 | (…) | 1 |
| 6 | R24 | Abu Dhabi Grand Prix | 58 | Yas Marina | 07/12/2025 | (…) | 1 |

`tblHopDong`

| id | tblTayDuaid | tblDoiDuaid | ngayBatDau | ngayKetThuc |
|---|---|---|---|---|
| 1 | 1 (LEC) | 1 (Ferrari) | 01/01/2019 | (trống) |
| 2 | 2 (HAM) | 4 (Mercedes) | 01/01/2013 | 31/12/2024 |
| 3 | 2 (HAM) | 1 (Ferrari) | 01/01/2025 | (trống) |
| 4 | 3 (VER) | 2 (Red Bull) | 01/01/2016 | (trống) |
| 5 | 4 (TSU) | 2 (Red Bull) | 01/04/2025 | (trống) |
| 6 | 5 (NOR) | 3 (McLaren) | 01/01/2019 | (trống) |
| 7 | 6 (PIA) | 3 (McLaren) | 01/01/2023 | (trống) |
| 8 | 7 (RUS) | 4 (Mercedes) | 01/01/2022 | (trống) |
| 9 | 8 (ANT) | 4 (Mercedes) | 01/01/2025 | (trống) |
| 10 | 11 (ALB) | 6 (Williams) | 01/01/2022 | (trống) |
| 11 | 12 (SAI) | 6 (Williams) | 01/01/2025 | (trống) |

> Đội `Aston Martin` (id 5) chưa có hợp đồng nào trong hệ thống (hai tay đua `Fernando Alonso` và `Lance Stroll` mới chỉ được nhập vào danh mục tay đua) — dữ liệu này dùng cho các ca DKC_16 và DKC_20.

`tblDangKyChang`

| id | tblChangDuaid | tblTayDuaid | tblDoiDuaid |
|---|---|---|---|
| *(bảng rỗng)* | | | |

Ngày hệ thống mặc định khi chạy test: **20/05/2025** (ca nào dùng ngày khác sẽ ghi rõ trong cột Các bước thực hiện).

**Data test bổ sung — giả định chuyển nhượng giữa mùa (dùng cho DKC_18, DKC_19):** ngày `02/07/2025`, `Carlos Sainz` ký hợp đồng mới với `Ferrari` hiệu lực từ `02/07/2025`; theo luồng của Module 1, hệ thống **tự đóng** hợp đồng cũ của Sainz với `Williams` (dòng id 11 nhận `ngayKetThuc = 01/07/2025`), nên tại mọi thời điểm Sainz vẫn chỉ thuộc một đội — không phá ràng buộc "một tay đua tại một thời điểm chỉ thuộc một đội". Kết quả: tại chặng `R10 - British Grand Prix - Silverstone - 06/07/2025`, đội `Ferrari` có **3 tay đua hợp đồng hiệu lực**: `Charles Leclerc`, `Lewis Hamilton`, `Carlos Sainz`; đội `Williams` chỉ còn `Alexander Albon`. Riêng `DKC_19` thêm tiền đề: ngày `01/07/2025` — **trước khi** Sainz chuyển đội — nhân viên đã đăng ký đội `Williams` cho chặng `R10` gồm `Alexander Albon` và `Carlos Sainz`, nên `tblDangKyChang` đã có 2 dòng `(4 - R10, 11 - ALB, 6 - Williams)` và `(4 - R10, 12 - SAI, 6 - Williams)`; ở màn đăng ký của Ferrari, Sainz vừa có hợp đồng hiệu lực tại thời điểm chặng, vừa **đã bị đội cũ đăng ký** cho chính chặng đó.

> Giả định chuyển nhượng này **chỉ áp dụng cho DKC_18 và DKC_19**; các ca còn lại và các module khác vẫn dùng đội hình gốc (Sainz thuộc Williams cả mùa).

#### 5.9.2. Bảng test case

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|
| | **Giao diện — màn Chọn chặng và đội** | | |
| DKC_1 | Kiểm tra tổng thể giao diện màn Chọn chặng và đội | 1. Mở màn Chọn chặng và đội.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| DKC_2 | Kiểm tra bố cục màn Chọn chặng và đội | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Đăng ký tay đua tham gia chặng đua — Bước 1: Chọn chặng và đội`.<br>2. Focus được đặt vào ô chọn "Chặng đua".<br>3. Hiển thị đầy đủ các trường: Chặng đua (danh sách thả xuống) · Đội đua (danh sách thả xuống).<br>4. Button: [Tiếp tục], [Về trang chủ]. |
| DKC_3 | Kiểm tra màn Chọn chặng và đội khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| DKC_4 | Kiểm tra thứ tự phím Tab màn Chọn chặng và đội | 1. Focus vào màn Chọn chặng và đội.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| DKC_5 | Kiểm tra thứ tự phím Shift-Tab màn Chọn chặng và đội | 1. Focus vào màn Chọn chặng và đội.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| DKC_6 | Kiểm tra phím Enter màn Chọn chặng và đội | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| | **Giao diện — màn Đăng ký tay đua** | | |
| DKC_7 | Kiểm tra tổng thể giao diện màn Đăng ký tay đua | 1. Mở màn Đăng ký tay đua.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| DKC_8 | Kiểm tra bố cục màn Đăng ký tay đua | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Đăng ký tay đua tham gia chặng đua — Bước 2: Đăng ký tay đua`.<br>2. Focus được đặt vào ô tick của dòng đầu tiên trong bảng tay đua.<br>3. Hiển thị đầy đủ các trường: Tiêu đề chặng và đội (vùng chỉ đọc) · Bảng tay đua (bảng: Chọn, Mã, Tên, Ngày sinh, Quốc tịch, Trạng thái đăng ký) · Bảng danh sách xuất phát (bảng: Đội, Tay đua 1, Tay đua 2 — ban đầu chưa hiện).<br>4. Button: [Quay lại], [Sửa], [Lưu], [OK] (chỉ hiện cùng thông báo lưu thành công).<br>5. Liên kết click được: ô tick chọn trên từng dòng bảng tay đua. |
| DKC_9 | Kiểm tra màn Đăng ký tay đua khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| DKC_10 | Kiểm tra thứ tự phím Tab màn Đăng ký tay đua | 1. Focus vào màn Đăng ký tay đua.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| DKC_11 | Kiểm tra thứ tự phím Shift-Tab màn Đăng ký tay đua | 1. Focus vào màn Đăng ký tay đua.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| DKC_12 | Kiểm tra phím Enter màn Đăng ký tay đua | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| DKC_13 | Màn Chọn chặng và đội hiển thị đúng dữ liệu | 1. Mở màn Chọn chặng và đội.<br>2. Mở lần lượt hai danh sách thả xuống. | Danh sách "Chặng đua" có 6 dòng **khớp các bản ghi trong `tblChangDua`** thuộc mùa 2025, sắp xếp tăng dần theo `thoiGian` (R01 → R24); danh sách "Đội đua" có 6 dòng **khớp các bản ghi trong `tblDoiDua`** (hiển thị dạng `Tên đội (Hãng)`) |
| DKC_14 | Màn Chọn chặng và đội khi không có dữ liệu | 1. Data test riêng: xóa/chuyển các dòng `tblChangDua` sao cho mùa giải đang diễn ra không còn chặng nào.<br>2. Mở màn Chọn chặng và đội. | Danh sách "Chặng đua" rỗng, kèm thông báo "Chưa có chặng đua của mùa giải"; nút [Tiếp tục] không thể chuyển sang active |
| DKC_15 | Màn Đăng ký tay đua hiển thị đúng dữ liệu | 1. Chọn chặng `R06`, đội `Red Bull (Honda RBPT)`, click [Tiếp tục]. | Bảng tay đua có đúng 2 dòng VER, TSU — **khớp các bản ghi `tblHopDong` còn hiệu lực tại 25/05/2025** của đội id 2, thông tin từng dòng đối chiếu đúng `tblTayDua`; cột Trạng thái đăng ký khớp `tblDangKyChang` (đang rỗng → tất cả `Chưa đăng ký`) |
| DKC_16 | Màn Đăng ký tay đua khi không có dữ liệu | 1. Chọn chặng `R06`, đội `Aston Martin (Mercedes)` — đội chưa có bản ghi nào trong `tblHopDong`, click [Tiếp tục]. | Bảng tay đua rỗng (chỉ còn dòng tiêu đề); thông báo "Đội Aston Martin không có tay đua nào có hợp đồng hiệu lực tại thời điểm chặng R06"; [Lưu], [Sửa] chưa active |
| | **Precond:** nhân viên đã đăng nhập; CSDL đúng trạng thái Data test mục 5.9.1; ngày hệ thống 20/05/2025 (ca nào dùng ngày/data khác sẽ ghi rõ ở bước 1). | | |
| DKC_17 | Đăng ký 2 tay đua hợp lệ cho chặng chưa có đăng ký (ca chuẩn) | 1. Tại trang chính click "Đăng ký thi đấu".<br>2. Chọn chặng `R06 - Monaco Grand Prix - Monte Carlo - 25/05/2025`, chọn đội `Red Bull (Honda RBPT)`, click [Tiếp tục].<br>3. Tick dòng `VER - Max Verstappen`, tick dòng `TSU - Yuki Tsunoda`.<br>4. Click [Lưu].<br>5. Đối soát danh sách xuất phát, click [OK]. | Bước 4: hệ thống kiểm tra 3 ràng buộc đều hợp lệ (2 ≤ 2 tay đua; VER, TSU chưa đăng ký R06 cho đội khác; 20/05/2025 trước 25/05/2025), thông báo "Đã lưu đăng ký cho đội Red Bull ở chặng R06"; cột Trạng thái đăng ký của VER, TSU đổi thành `Đã đăng ký (Red Bull)`; danh sách xuất phát hiện 1 dòng `Red Bull \| Max Verstappen \| Yuki Tsunoda`; nút [Sửa] chuyển sang active. **CSDL:** `tblDangKyChang` thêm 2 bản ghi `(3 - R06, 3 - VER, 2 - Red Bull)`, `(3 - R06, 4 - TSU, 2 - Red Bull)`; các bảng khác không đổi. Bước 5: hệ thống quay về trang chính |
| DKC_18 | Tick chọn quá 2 tay đua cho một đội trong một chặng → báo lỗi | 1. Áp data test chuyển nhượng giữa mùa (mục 5.9.1); ngày hệ thống 04/07/2025.<br>2. Chọn chặng `R10 - British Grand Prix - Silverstone - 06/07/2025`, đội `Ferrari (Ferrari)`, click [Tiếp tục].<br>3. Tick cả 3 dòng SAI, LEC, HAM.<br>4. Click [Lưu].<br>5. Bỏ tick dòng `SAI - Carlos Sainz`, click [Lưu]. | Bước 2: bảng hiện 3 dòng theo alphabet của Tên: `Carlos Sainz`, `Charles Leclerc`, `Lewis Hamilton`. Bước 4: báo lỗi "Mỗi đội chỉ được đăng ký tối đa 2 tay đua trong một chặng"; **CSDL:** không dòng nào được ghi vào `tblDangKyChang`; màn hình giữ nguyên 3 ô tick. Bước 5: lưu thành công; danh sách xuất phát hiện `Ferrari \| Charles Leclerc \| Lewis Hamilton`. **CSDL:** `tblDangKyChang` thêm 2 bản ghi `(4 - R10, 1 - LEC, 1 - Ferrari)`, `(4 - R10, 2 - HAM, 1 - Ferrari)` |
| DKC_19 | Tick chọn tay đua đã được đội khác đăng ký ở chính chặng đó → báo lỗi | 1. Áp data test chuyển nhượng + 2 dòng đăng ký Williams tại R10 (mục 5.9.1); ngày hệ thống 04/07/2025.<br>2. Chọn chặng `R10`, đội `Ferrari (Ferrari)`, click [Tiếp tục].<br>3. Tick dòng `LEC - Charles Leclerc` và dòng `SAI - Carlos Sainz`, click [Lưu].<br>4. Bỏ tick SAI, tick dòng `HAM - Lewis Hamilton`, click [Lưu]. | Bước 2: dòng SAI hiện Trạng thái đăng ký `Đã đăng ký (Williams)` — cảnh báo trực quan ràng buộc trùng. Bước 3: báo lỗi "Tay đua Carlos Sainz đã được đăng ký cho đội Williams ở chặng R10"; **CSDL:** không dòng nào được ghi vào `tblDangKyChang` (kể cả dòng của Leclerc). Bước 4: lưu thành công. **CSDL:** `tblDangKyChang` giữ nguyên 2 dòng Williams (ALB, SAI) và thêm 2 dòng `(4 - R10, 1 - LEC, 1 - Ferrari)`, `(4 - R10, 2 - HAM, 1 - Ferrari)` |
| DKC_20 | Chọn đội không có tay đua hợp đồng hiệu lực tại thời điểm chặng → thông báo | 1. Chọn chặng `R06 - Monaco Grand Prix - Monte Carlo - 25/05/2025`, đội `Aston Martin (Mercedes)` — chưa có dòng nào trong `tblHopDong`, click [Tiếp tục].<br>2. Click [Quay lại]. | Bước 1: bảng tay đua rỗng, thông báo "Đội Aston Martin không có tay đua nào có hợp đồng hiệu lực tại thời điểm chặng R06"; [Lưu], [Sửa] chưa active. Bước 2: hệ thống trở về màn Chọn chặng và đội, giữ nguyên chặng R06 để nhân viên chọn đội khác. **CSDL:** không bảng nào thay đổi |
| DKC_21 | Thay tay đua trước ngày đua (sửa danh sách đã đăng ký) | 1. Tiền đề: CSDL sau khi chạy DKC_17 — `tblDangKyChang` có 2 dòng VER, TSU của Red Bull tại R06; ngày hệ thống 22/05/2025.<br>2. Chọn chặng `R06`, đội `Red Bull (Honda RBPT)`, click [Tiếp tục].<br>3. Click [Sửa], bỏ tick dòng `TSU - Yuki Tsunoda` (tay đua chấn thương).<br>4. Click [Lưu].<br>5. Đặt ngày hệ thống 26/05/2025 (sau ngày đua), lặp lại bước 2–4. | Bước 2: 2 dòng được **tick sẵn**, Trạng thái `Đã đăng ký (Red Bull)`; [Sửa] đang active, [Lưu] chưa active. Bước 3: các ô tick được mở khóa, [Lưu] chuyển sang active. Bước 4: kiểm tra hợp lệ (1 ≤ 2; 22/05/2025 trước 25/05/2025), thông báo "Đã cập nhật đăng ký cho đội Red Bull ở chặng R06"; danh sách xuất phát đổi thành `Red Bull \| Max Verstappen \| (trống)`; Trạng thái của dòng TSU đổi lại `Chưa đăng ký`. **CSDL:** `tblDangKyChang` chỉ còn dòng `(3 - R06, 3 - VER, 2 - Red Bull)`, dòng của TSU bị xóa. Bước 5: báo lỗi "Chặng đã diễn ra, không được thay đổi danh sách đăng ký"; **CSDL:** `tblDangKyChang` không đổi |
| DKC_22 | Danh sách tay đua sắp xếp đúng thứ tự alphabet của Tên | 1. Chọn chặng `R06`, đội `Mercedes (Mercedes)`, click [Tiếp tục].<br>2. Click [Quay lại], đổi đội sang `Williams (Mercedes)`, click [Tiếp tục]. | Bước 1: bảng hiện đúng 2 dòng — dòng đầu `ANT - Andrea Kimi Antonelli`, dòng thứ hai `RUS - George Russell` — theo alphabet của Tên (`Andrea` trước `George`), **không** theo thứ tự id trong `tblTayDua` (RUS id 7 nhập trước, ANT id 8 nhập sau). Bước 2: dòng đầu `ALB - Alexander Albon`, dòng thứ hai `SAI - Carlos Sainz` (`Alexander` trước `Carlos`). **CSDL:** không bảng nào thay đổi (ca chỉ xem) |

---

## CHƯƠNG 6: MODULE 3 — CẬP NHẬT KẾT QUẢ CHẶNG ĐUA

**Thành viên thực hiện:** Nguyễn Minh Kiệt — **Use case:** Cập nhật kết quả chặng đua

### 6.1. Biểu đồ Use Case chi tiết

Use case chính của module là **`Cập nhật kết quả chặng đua`**, do actor **Nhân viên 1** (`NhanVien1`) trực tiếp thực hiện thuộc Hệ thống quản lý giải đua F1.

Module bao gồm các use case thành phần và quan hệ mở rộng/bao hàm như sau:
- **`Cập nhật kết quả chặng đua`** bao hàm (<<Include>>) 4 use case con:
  1. `Đăng nhập`
  2. `Chọn chặng`
  3. `Nhập kết quả và tính điểm`
  4. `Lưu kết quả`
- Use case `Lưu kết quả` có các **Extension Points** (điểm mở rộng):
  - *Xử lý kháng nghị kết quả*
  - *Áp dụng án phạt sau chặng*
  - *Phê duyệt kết quả chặng*
- Các use case mở rộng (<<Extend>>) kết nối tới điểm mở rộng của `Lưu kết quả`:
  - `Xử lý kháng nghị kết quả` (do **Nhân viên 1** thực hiện)
  - `Phê duyệt kết quả chặng` (do **Nhân viên 2** thực hiện)
  - `Áp dụng án phạt sau chặng` (do **Nhân viên 2** thực hiện)

| Use case con / Use case mở rộng | Quan hệ với UC chính / UC Lưu kết quả | Actor thực hiện | Màn hình liên quan (theo luồng mục 6.2) |
|---|---|---|---|
| `Đăng nhập` | include | Nhân viên 1 | (màn dùng chung toàn hệ thống, không thuộc luồng màn của module) |
| `Chọn chặng` | include | Nhân viên 1 | Danh sách chặng `Chang.jsp` |
| `Nhập kết quả và tính điểm` | include | Nhân viên 1 | Chi tiết chặng `ChangChiTiet.jsp` |
| `Lưu kết quả` | include | Nhân viên 1 | Chi tiết chặng `ChangChiTiet.jsp` |
| `Xử lý kháng nghị kết quả` | extend (qua extension point) | Nhân viên 1 | Quản lý kháng nghị `KhangNghi.jsp` |
| `Phê duyệt kết quả chặng` | extend (qua extension point) | Nhân viên 2 | Chi tiết chặng `ChangChiTiet.jsp` (thao tác qua nút [Phê duyệt kết quả], không có màn riêng) |
| `Áp dụng án phạt sau chặng` | extend (qua extension point) | Nhân viên 2 | Chi tiết chặng `ChangChiTiet.jsp` (không có màn riêng) |

![Biểu đồ Use Case chi tiết Module 3](<../Module 3 - Kiet/hinh/m3-uc-chitiet.png>)

*Hình 6.1 — Biểu đồ Use Case chi tiết Module 3*

### 6.2. Đặc tả Use Case

Luồng màn hình: **Trang chính `NhanVien.jsp` → Danh sách mùa giải `MuaGiai.jsp` → Danh sách chặng `Chang.jsp` → Chi tiết chặng `ChangChiTiet.jsp` → (Kháng nghị `KhangNghi.jsp`) → Trang chính `NhanVien.jsp`**. Phác thảo của mỗi màn đặt ngay dưới bước hệ thống hiển thị màn đó.

| Mục | Nội dung |
|---|---|
| **Use case** | Cập nhật kết quả chặng đua |
| **Actor** | `NhanVien1` (Nhân viên cập nhật kết quả & xử lý kháng nghị), `NhanVien2` (Nhân viên giám sát, phê duyệt kết quả & áp dụng án phạt) |
| **Tiền điều kiện** | Nhân viên đã đăng nhập thành công vào hệ thống. Mùa giải và danh sách chặng đua đã có dữ liệu. Chặng đua cần cập nhật đã có danh sách tay đua, đội đua đăng ký thi đấu. |
| **Hậu điều kiện** | Kết quả thi đấu (thời gian về đích, số vòng hoàn thành, trạng thái, hạng, điểm) được xếp hạng, tính điểm và lưu vào CSDL. Nếu có đơn kháng nghị từ đội đua, thông tin được tiếp nhận, đối chiếu camera và phê duyệt/cập nhật lại kết quả. |

**Kịch bản chính**

1. `NhanVien1` (sau khi đăng nhập) truy cập giao diện chính `NhanVien.jsp`, click nút [Mùa giải] (`btnMuaGiai`).
2. Hệ thống hiển thị màn hình **Danh sách mùa giải** (`MuaGiai.jsp`): gọi `MuaGiaiDAO.getAllMuaGiai()`, hiển thị bảng `tblMuaGiai` liệt kê các mùa giải (Mùa giải, Năm, Trạng thái); các nút [Xem chi tiết], [Thêm mùa giải], [Lưu], [Quay lại].

   **Màn hình *Danh sách mùa giải* (`MuaGiai.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Bảng mùa giải (`tblMuaGiai`) | bảng | hiển thị danh sách mùa giải (Mùa giải, Năm, Trạng thái) |
   | [Xem chi tiết] (`btnViewDetailMuaGiai`) | nút | active khi chọn 1 mùa giải |
   | [Thêm mùa giải] (`btnCreateMuaGiai`) | nút | active |
   | [Lưu] (`btnSave`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

3. `NhanVien1` chọn mùa giải 2025 trong bảng `tblMuaGiai` (hệ thống gọi `MuaGiaiDAO.getMuaGiaiById()`) và click [Xem chi tiết] (`btnViewDetailMuaGiai`).
4. Hệ thống hiển thị màn hình **Danh sách chặng đua** (`Chang.jsp`): gọi `ChangDuaDAO.getAllChangDuaByMuaGiaiID()`, hiển thị bảng `tblChang` gồm các chặng của mùa giải (Mã, Tên chặng, Địa điểm, Thời gian); các nút [Xem chi tiết chặng], [Thêm chặng], [Lưu], [Quay lại].

   **Màn hình *Danh sách chặng đua* (`Chang.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Bảng chặng đua (`tblChang`) | bảng | hiển thị danh sách chặng đua (Mã, Tên, Địa điểm, Thời gian) |
   | [Xem chi tiết chặng] (`btnViewDetailChang`) | nút | active khi chọn 1 chặng |
   | [Thêm chặng] (`btnCreateChang`) | nút | active |
   | [Lưu] (`btnSave`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

5. `NhanVien1` chọn chặng R16 - Monza và click [Xem chi tiết chặng] (`btnViewDetailChang`).
6. Hệ thống hiển thị màn hình **Chi tiết chặng & Nhập kết quả** (`ChangChiTiet.jsp`): gọi `ChangDuaDAO.getById()` lấy thông tin chặng và `DangKyChangDAO.getAllTayDuaAndDoiDuaByChangID()` lấy danh sách tay đua; dropdown `cmbChang` chọn chặng; bảng `tblTayDua` chứa danh sách tay đua đã đăng ký (Thời gian, Số vòng, Trạng thái - các ô nhập đang rỗng hoặc có dữ liệu cũ); các nút [Tính kết quả] (`btnCalculateResult`), [Lưu] (`btnSave`), [Tiếp tục] (`btnContinue`), [Quay lại] (`btnBack`); bảng đối soát kết quả `tblKetQua` ban đầu chưa hiển thị.

   **Màn hình *Chi tiết chặng & Nhập kết quả* (`ChangChiTiet.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Chặng đua (`cmbChang`) | danh sách thả xuống | hiển thị chặng R16 |
   | Bảng tay đua (`tblTayDua`) | bảng có ô nhập | chứa 12 tay đua đăng ký chặng; các ô nhập Thời gian, Số vòng, Trạng thái rỗng |
   | [Tính kết quả] (`btnCalculateResult`) | nút | active |
   | Bảng đối soát kết quả (`tblKetQua`) | bảng | chưa hiện, chỉ hiện sau khi click [Tính kết quả] |
   | [Lưu] (`btnSave`) | nút | chưa active, chỉ active sau khi bảng đối soát hiển thị |
   | [Tiếp tục] (`btnContinue`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

   Ô chọn ở cột **Trạng thái** là danh sách thả xuống dùng chung cho mọi dòng, gồm đúng ba giá trị:

   | Giá trị hiển thị trong ô chọn | Thời gian về đích | Vị trí khi xếp hạng | Điểm |
   |---|---|---|---|
   | `Hoàn thành` | bắt buộc nhập, định dạng `hh:mm:ss.xxx` | xếp trước, theo thời gian về đích tăng dần | theo thang 25/18/15/12/10/8/6/4/2/1 cho hạng 1–10 |
   | `DNF (bỏ cuộc, tai nạn)` | không bắt buộc, thường để trống | xếp xuống cuối bảng | 0 |
   | `DSQ (bị loại)` | không bắt buộc, có thể vẫn có thời gian | xếp xuống cuối bảng | 0 |

7. `NhanVien1` nhập số vòng hoàn thành, thời gian về đích và chọn trạng thái (`Hoàn thành`, `DNF`, `DSQ`) cho từng tay đua trong `tblTayDua`.
8. Hệ thống kiểm tra định dạng dữ liệu:
   - Nếu nhập sai định dạng → hệ thống hiển thị thông báo lỗi nhập liệu và yêu cầu `NhanVien1` nhập lại.
   - Nếu nhập đúng định dạng → hệ thống tự động xếp hạng và tính điểm toàn chặng, gọi `KetQuaDAO.createKetQua()` để tạo kết quả chặng đua và hiển thị lên bảng đối soát `tblKetQua`; nút [Lưu] (`btnSave`) chuyển sang active.
9. `NhanVien1` đối soát dữ liệu trên `tblKetQua` và click nút [Lưu] (`btnSave`).
10. Hệ thống gọi `KetQuaDAO.kiemTraKetQuaCu()` kiểm tra kết quả cũ:
    - Nếu chặng đua đã có kết quả cũ: hệ thống hiển thị hộp thoại cảnh báo: "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Nếu `NhanVien1` chọn [Hủy] → giữ nguyên kết quả cũ, không lưu. Nếu chọn [Xác nhận] → hệ thống xóa kết quả cũ và gọi `KetQuaDAO.luuKetQua()` để cập nhật kết quả mới.
    - Nếu chặng đua chưa có kết quả cũ: hệ thống gọi `KetQuaDAO.luuKetQua()`, lưu kết quả mới vào CSDL.
11. Hệ thống kiểm tra đơn kháng nghị từ các đội đua / tay đua:
    - **Trường hợp 1 (Không có kháng nghị):** Luồng chuyển trực tiếp đến bước phê duyệt; `NhanVien2` click [Phê duyệt kết quả], hệ thống hiển thị thông báo "Phê duyệt kết quả chặng thành công" và kết thúc luồng.
    - **Trường hợp 2 (Có kháng nghị):** Hệ thống ghi nhận nội dung kháng nghị từ đội đua và gửi chuyển luồng xử lý sang swimlane `NhanVien2` tại màn hình **Quản lý kháng nghị** (`KhangNghi.jsp`).
12. Tại màn hình `KhangNghi.jsp`, hệ thống hiển thị danh sách đơn kháng nghị. `NhanVien2` xem xét từng đơn kháng nghị:
    - Nếu từ chối kháng nghị → ghi nhận kháng nghị bị từ chối.
    - Nếu chấp nhận kháng nghị → `NhanVien2` đối chiếu kết quả qua video camera với nội dung kháng nghị:
      - Nếu đối chiếu không thành công → ghi nhận kết quả đối chiếu không thành công.
      - Nếu đối chiếu thành công → hệ thống tự động cập nhật lại điểm xếp hạng chặng đua; `NhanVien2` click [Lưu] để ghi nhận kết quả cập nhật mới.
13. `NhanVien2` lặp lại bước 12 cho đến khi xử lý hết tất cả các đơn kháng nghị. Sau khi hết kháng nghị, luồng quay trở lại bước phê duyệt kết quả ở swimlane `NhanVien1`; `NhanVien2` click [Phê duyệt kết quả], hệ thống thông báo "Phê duyệt kết quả chặng thành công" và hoàn tất luồng.

**Ngoại lệ**

- **8a.** Còn tay đua chưa chọn Trạng thái hoặc nhập sai định dạng thời gian → hệ thống hiển thị thông báo lỗi nhập liệu và yêu cầu nhập lại, nút [Lưu] giữ nguyên chưa active.
- **8b.** Số vòng hoàn thành vượt quá số vòng tối đa của chặng đua → hệ thống thông báo lỗi "Số vòng hoàn thành không hợp lệ", giữ nguyên dữ liệu đã nhập.
- **10a.** `NhanVien1` chọn [Hủy] tại hộp thoại cảnh báo ghi đè kết quả cũ → hệ thống giữ nguyên kết quả cũ trong CSDL, không ghi đè.

> Luồng chuyển màn: **Trang chính `NhanVien.jsp` → Danh sách mùa giải `MuaGiai.jsp` → Danh sách chặng `Chang.jsp` → Chi tiết chặng `ChangChiTiet.jsp` → (Kháng nghị `KhangNghi.jsp`) → Trang chính `NhanVien.jsp`**.

---

### 6.3. Biểu đồ trạng thái (phân tích hoạt động)

Biểu đồ bắt đầu từ trạng thái hiển thị **giao diện chính của nhân viên** và kết thúc khi lưu kết quả hoặc xử lý xong kháng nghị:

- `Hiển thị giao diện chính của nhân viên` —`[click mùa giải]`→ `Hiển thị danh sách mùa giải` (cung `[click quay lại]` trở về giao diện chính)
- `Hiển thị danh sách mùa giải` —`[click chi tiết mùa giải]`→ `Hiển thị danh sách các chặng đua` (cung `[click quay lại]` trở về danh sách mùa giải)
- `Hiển thị danh sách các chặng đua` —`[click chi tiết chặng đua]`→ `Hiển thị danh sách các tay đua, đội đua, thông tin chặng` (cung tự lặp `[Nhập số vòng, thời gian, trạng thái hợp lệ]`, cung `[click quay lại]` trở về danh sách các chặng đua)
- `Hiển thị danh sách các tay đua, đội đua, thông tin chặng` —`[click tính toán kết quả]`→ `Hiển thị kết quả chặng đua` (cung tự lặp `[click lưu]`)
- `Hiển thị kết quả chặng đua` —`[ko có đội đua, tay đua nộp đơn kháng nghị]`→ Kết thúc; hoặc —`[có đội đua, tay đua nộp đơn kháng nghị]`→ `Hiện thị danh sách kháng nghị` (các cung tự lặp `[Từ chối kháng nghị]`, `[kháng nghị không thành công]`, `[cập nhật lại kết quả chặng đua khi kháng nghị thành công]`, `[ghi nhận còn kháng nghị từ các đội đua, tay đua]`) —`[hết kháng nghị]`→ Kết thúc

![Biểu đồ trạng thái Module 3](<../Module 3 - Kiet/hinh/m3-trangthai.png>)

*Hình 6.2 — Biểu đồ trạng thái Module 3 (phân tích hoạt động)*

---

### 6.4. Biểu đồ lớp phân tích

Biểu đồ chỉ gồm **hai tầng**: lớp biên và lớp thực thể, không có lớp điều khiển. Ở pha phân tích, cả lớp biên và lớp thực thể mới chỉ mô tả **thuộc tính**, chưa gán phương thức; các phương thức nghiệp vụ tương ứng được trình bày ở biểu đồ lớp thiết kế (mục 6.5).

**Lớp biên** (mỗi màn hình một lớp, chỉ có thuộc tính, đặt tên theo chức năng dữ liệu):

| Lớp biên | Màn hình | Thuộc tính |
|---|---|---|
| `GDNhanVien` | Trang chính của nhân viên | `-subKhangNghi`, `-subChang`, `-subCaidat` |
| `GDMuaGiai` | Danh sách mùa giải | `-outMuaGiai`, `-subCreateMuaGiai`, `-subViewDetailMuaGiai`, `-subBack`, `-subSave` |
| `GDChang` | Danh sách các chặng đua | `-outChang`, `-subCreateChang`, `-subViewDetailChang`, `-subBack`, `-subSave` |
| `GDChangChiTiet` | Chi tiết chặng & Nhập kết quả | `-cmbChang`, `-outTayDua`, `-subSave`, `-subBack`, `-subCalculateResult`, `-outKetQua`, `-subContinue` |

**Lớp thực thể** (ở pha phân tích chỉ mô tả thuộc tính, chưa gán phương thức):

| Lớp thực thể | Thuộc tính |
|---|---|
| `MuaGiai` | `-ten`, `-nam`, `-trangThai` |
| `ChangDua` | `-ma`, `-ten`, `-soVong`, `-diaDiem`, `-thoiGian`, `-moTa` |
| `DoiDua` | `-ma`, `-ten`, `-hang`, `-moTa` |
| `TayDua` | `-ma`, `-ten`, `-quocTich`, `-ngaySinh`, `-tieuSu` |
| `KetQua` | `-thoiGian`, `-soVongHoanThanh`, `-trangThai`, `-hang`, `-diem` |
| `DangkyChang` | (lớp liên kết trung gian, thân rỗng — không có thuộc tính riêng) |

**Quan hệ giữa các lớp thực thể:** `MuaGiai` 1 ◆—— 1..* `ChangDua` (thành phần); `ChangDua` 1 ◇—— 1..* `DangkyChang`, `DoiDua` 1 ◇—— 1..* `DangkyChang`, `TayDua` 1 ◇—— 1..* `DangkyChang` (kết tập); `DangkyChang` 1 ◆—— 1 `KetQua` (thành phần).

Các chức năng nghiệp vụ dưới tầng giao diện (`getAllMuaGiai()`, `getMuaGiaiById(id)`, `getAllChangDuaByMuaGiaiID(id)`, `getAllTayDuaAndDoiDuaByChangID(id)`, `createKetQua()`, `kiemTraKetQuaCu()`, `luuKetQua()`) được gán cho các lớp DAO tương ứng ở biểu đồ lớp thiết kế — mục 6.5.

![Biểu đồ lớp phân tích Module 3](<../Module 3 - Kiet/hinh/m3-lop-phantich.png>)

*Hình 6.3 — Biểu đồ lớp phân tích Module 3*

---

### 6.5. Biểu đồ lớp thiết kế (view `.jsp` / `DAO` / `model`)

Biểu đồ lớp thiết kế xây dựng theo mô hình Swing/JSP với Interface `ActionListener`:

**Interface:**
- `<<Interface>> ActionListener`: `+actionPerformed(e : EventAction) : void`

**Tầng View (màn hình hiển thị thực thi Interface `ActionListener`):**
- `NhanVien.jsp`: `-btnKhangNghi: JButton`, `-btnMuaGiai: JButton`, `-btnCaidat: JButton`, `+NhanVien()`, `+actionPerformed(e: EventAction): void`
- `MuaGiai.jsp`: `-tblMuaGiai: JTable`, `-btnCreateMuaGiai: JButton`, `-btnViewDetailMuaGiai: JButton`, `-btnSave: JButton`, `-btnBack: JButton`, `-mg: MuaGiai`, `+getAllMuaGiai()`, `+getMuaGiaiById(id: int)`, `+MuaGiai()`, `+actionPerformed(e: EventAction): void`, `+createMuaGiai(mg: MuaGiai)`
- `Chang.jsp`: `-tblChang: JTable`, `-btnCreateChang: JButton`, `-btnViewDetailChang: JButton`, `-btnBack: JButton`, `-btnSave: JButton`, `-c: ChangDua`, `-n: NhanVien`, `-dkc: DangKyChang`, `-mg: MuaGiai`, `+actionPerformed(e: EventAction): void`, `+Chang()`, `+createChang(dkc: DangKyChang)`, `+getAllChangDuaByMuaGiaiID(id: int)`
- `ChangChiTiet.jsp`: `-cmbChang: JCombobox`, `-tblTayDua: JTable`, `-btnSave: JButton`, `-btnBack: JButton`, `-btnCalculateResult: JButton`, `-btnContinue: JButton`, `-tblKetQua: JTable`, `-n: NhanVien`, `-kq: KetQua`, `-c: ChangDua`, `+actionPerformed(e: EventAction): void`, `+ChangChiTiet()`, `+createKetQua(kq: KetQua)`, `+kiemTraKetQuaCu(kq: KetQua)`, `+luuKetQua(kq: KetQua)`, `+getById(id: int)`, `+getAllTayDuaAndDoiDuaByChangID(id: int)`

**Tầng DAO (kế thừa lớp `DAO` có `-conn: Connection`, `+DAO()`):**
- `MuaGiaiDAO`: `+MuaGiaiDAO()`, `+getAllMuaGiai()`, `+getMuaGiaiById(id: int)`
- `ChangDuaDAO`: `+ChangDuaDAO()`, `+getAllChangDuaByMuaGiaiID(id: int)`, `+getById(id: int)`
- `DangKyChangDAO`: `+DangKyChangDAO()`, `+createChang(dkc: DangKyChang)`, `+getAllTayDuaAndDoiDuaByChangID(id: int)`
- `KetQuaDAO`: `+KetQuaDAO()`, `+createKetQua(kq: KetQua)`, `+kiemTraKetQuaCu(kq: KetQua)`, `+luuKetQua(kq: KetQua)`

**Tầng Model (thực thể dữ liệu):**
- `MuaGiai`: `-id: int`, `-ten: String`, `-nam: integer`, `-trangThai: String`, `-dsChangDua: ChangDua[]`
- `ChangDua`: `-id: int`, `-soVong: int`, `-ma: String`, `-ten: String`, `-diaDiem: String`, `-thoiGian: date`, `-moTa: String`, `-muaGiai: MuaGiai`, `-dsDangKy: DangKyChang[]`
- `DoiDua`: `-id: int`, `-ma: String`, `-ten: String`, `-hang: String`, `-moTa: String`
- `TayDua`: `-id: int`, `-ma: String`, `-ten: String`, `-quocTich: String`, `-ngaySinh: String`, `-tieuSu: String`
- `DangKyChang`: `-id: int`, `-changDua: ChangDua`, `-tayDua: TayDua`, `-dolDua: DoiDua`, `-ketQua: KetQua`
- `KetQua`: `-id: int`, `-thoiGian: float`, `-soVongHoanThanh: int`, `-dangKyChang: DangKyChang`, `-trangThai: String`, `-hang: int`, `-diem: int`

![Biểu đồ lớp thiết kế Module 3](<../Module 3 - Kiet/hinh/m3-lop-mvc.png>)

*Hình 6.4 — Biểu đồ lớp thiết kế Module 3 (view `.jsp` / `DAO` / `model`)*

---

### 6.6. Biểu đồ hoạt động (pha thiết kế)

Biểu đồ hoạt động phân chia theo 2 swimlanes tương ứng với 2 actor (`Nhân viên 1` và `Nhân viên 2`):

**Luồng swimlane `Nhân viên 1`:**
1. **`NhanVien.jsp`**: Hiển thị giao diện chính của nhân viên → click `click MuaGiai`.
2. **`MuaGiai.jsp`**: 
   - Lấy danh sách mùa giải thông qua `MuaGiaiDAO: getAllMuaGiai()`.
   - Hiển thị danh sách mùa giải.
   - Nhân viên chọn mùa giải (gọi `MuaGiaiDAO: getMuaGiaiByID(id: int)`), click `Click xem chi tiết`.
3. **`Chang.jsp`**: 
   - Lấy danh sách chặng của mùa giải qua `ChangDuaDAO: getAllChangDuaByMuaGiaiID()`.
   - Hiển thị danh sách các chặng đua.
   - Nhân viên click `Click chi tiết chặng`.
4. **`ChangChiTiet.jsp`**: 
   - Lấy thông tin chi tiết chặng via `ChangDuaDAO: getById()`.
   - Lấy thông tin tay đua, đội đua via `DangKyChangDAO: getAllTayDuaAndDoiDuaByChangID()`.
   - Hiển thị thông tin danh sách tay đua, đội đua và thông tin chặng.
   - Nhân viên nhập số vòng, thời gian, trạng thái.
   - Kiểm tra định dạng dữ liệu: Nếu nhập sai định dạng → Hệ thống thông báo lỗi nhập liệu và yêu cầu nhập lại; Nếu đúng định dạng → Hệ thống xếp hạng và tính điểm toàn chặng.
   - Tạo kết quả chặng đua qua `KetQuaDAO: createKetQua()`.
   - Nhân viên click `Click lưu`.
   - Kiểm tra kết quả cũ via `KetQuaDAO: kiemTraKetQuaCu()`.
   - Nếu chặng đã có kết quả cũ: Hiển thị cảnh báo ghi đè ("Chặng đua này đã có kết quả, bạn có muốn ghi đè?"). Nếu hủy → Giữ nguyên kết quả cũ, không lưu. Nếu xác nhận → Xóa kết quả cũ và cập nhật kết quả mới qua `KetQuaDAO: luuKetQua()`.
   - Kiểm tra đơn kháng nghị:
     - Nếu **Không có kháng nghị**: Chuyển đến node `Phê duyệt kết quả` → Click phê duyệt → Thông báo phê duyệt thành công → Kết thúc.
     - Nếu **Có kháng nghị**: Tiếp nhận kháng nghị từ đội đua, hệ thống ghi nhận và chuyển luồng xử lý sang swimlane `Nhân viên 2`.

**Luồng swimlane `Nhân viên 2` (`KhangNghi.jsp`):**
1. Hệ thống hiển thị danh sách kháng nghị.
2. `Nhân viên 2` thực hiện node `Xem xét kháng nghị`:
   - Nhánh **Từ chối kháng nghị**: luồng đi thẳng tới node hội tụ `Hệ thống ghi nhận có kháng nghị từ các đội đua?` (trên biểu đồ chỉ có nhãn rẽ nhánh, không có node ghi nhận riêng), kết quả chặng giữ nguyên.
   - Nhánh **Chấp nhận kháng nghị**: chuyển sang node `Đối chiếu kết quả qua camera với kháng nghị`:
     - Nhánh **Kháng nghị ko thành công**: luồng đi thẳng tới node `Hệ thống ghi nhận có kháng nghị từ các đội đua?`, hệ thống không cập nhật lại điểm xếp hạng.
     - Nhánh **Kháng nghị thành công**: chuyển sang node `Hệ thống cập nhập lại điểm xếp hạng`, nhân viên `click lưu`, luồng về node `Hệ thống ghi nhận có kháng nghị từ các đội đua?`.
3. Tại node `Hệ thống ghi nhận có kháng nghị từ các đội đua?`: nếu còn đơn (nhánh `Có kháng nghị`) thì quay lại node `Hệ thống hiển thị danh sách kháng nghị` để xử lý đơn tiếp theo; nếu hết thì luồng quay trở lại node `Phê duyệt kết quả` ở swimlane `Nhân viên 1` để kết thúc.

![Biểu đồ hoạt động Module 3](<../Module 3 - Kiet/hinh/m3-hoatdong.png>)

*Hình 6.5 — Biểu đồ hoạt động Module 3 (pha thiết kế)*

---

### 6.7. Thuyết minh (kịch bản phiên bản 3)

Kịch bản tuần tự mô tả chi tiết luồng tương tác giữa Actor **Nhân viên**, các trang View (`NhanVien.jsp`, `MuaGiai.jsp`, `Chang.jsp`, `ChangChiTiet.jsp`), các lớp DAO (`MuaGiaiDAO`, `ChangDuaDAO`, `DangKyChangDAO`, `KetQuaDAO`) và các lớp Model (`MuaGiai`, `ChangDua`, `DangKyChang`, `KetQua`). Luồng mở đầu từ trang chính `NhanVien.jsp` và kết thúc khi hiển thị thông báo lưu thành công trên `ChangChiTiet.jsp`:

1. Nhân viên (sau khi đăng nhập) click chức năng "Mùa giải" trên trang `NhanVien.jsp`.
2. Trang `NhanVien.jsp` gọi trang `MuaGiai.jsp`.
3. Trang `MuaGiai.jsp` gọi lớp `MuaGiaiDAO` yêu cầu lấy danh sách các mùa giải.
4. Lớp `MuaGiaiDAO` gọi hàm `getAllMuaGiai()`.
5. Hàm `getAllMuaGiai()` gọi lớp `MuaGiai` để đóng gói thông tin thực thể.
6. Lớp `MuaGiai` đóng gói thông tin thực thể và trả kết quả về cho hàm `getAllMuaGiai()`.
7. Hàm `getAllMuaGiai()` trả kết quả về cho trang `MuaGiai.jsp`.
8. Trang `MuaGiai.jsp` hiển thị danh sách các mùa giải cho nhân viên.
9. Nhân viên chọn một mùa giải và click xem chi tiết trên trang `MuaGiai.jsp`.
10. Trang `MuaGiai.jsp` gọi lớp `MuaGiaiDAO` yêu cầu lấy thông tin chi tiết mùa giải.
11. Lớp `MuaGiaiDAO` gọi hàm `getById()`.
12. Hàm `getById()` gọi lớp `MuaGiai` để đóng gói thông tin thực thể.
13. Lớp `MuaGiai` đóng gói thông tin và trả kết quả về cho hàm `getById()`.
14. Hàm `getById()` trả kết quả cho trang `MuaGiai.jsp`.
15. Trang `MuaGiai.jsp` chuyển tiếp yêu cầu sang trang `Chang.jsp`.
16. Trang `Chang.jsp` gọi lớp `ChangDuaDAO` yêu cầu lấy danh sách các chặng đua của mùa giải.
17. Lớp `ChangDuaDAO` gọi hàm `getAllChangDuaByMuaGiaiID()`.
18. Hàm `getAllChangDuaByMuaGiaiID()` gọi lớp `ChangDua` để đóng gói thông tin thực thể.
19. Lớp `ChangDua` đóng gói thông tin và trả kết quả về cho hàm `getAllChangDuaByMuaGiaiID()`.
20. Hàm `getAllChangDuaByMuaGiaiID()` trả kết quả về cho trang `Chang.jsp`.
21. Trang `Chang.jsp` hiển thị danh sách các chặng đua cho nhân viên.
22. Nhân viên chọn một chặng đua và click "Xem chi tiết chặng" trên trang `Chang.jsp`.
23. Trang `Chang.jsp` gọi trang `ChangChiTiet.jsp`.
24. Trang `ChangChiTiet.jsp` gọi lớp `ChangDuaDAO` yêu cầu lấy thông tin chi tiết của chặng.
25. Lớp `ChangDuaDAO` gọi hàm `getById()`.
26. Hàm `getById()` gọi lớp `ChangDua` để đóng gói thông tin thực thể và trả về cho trang `ChangChiTiet.jsp`.
27. Trang `ChangChiTiet.jsp` gọi lớp `DangKyChangDAO` yêu cầu lấy danh sách các tay đua và đội đua đã đăng ký tham gia chặng.
28. Lớp `DangKyChangDAO` gọi hàm `getAllTayDuaAndDoiDuaByChangID()`.
29. Hàm `getAllTayDuaAndDoiDuaByChangID()` gọi lớp `DangKyChang` để đóng gói thông tin và trả kết quả về cho trang `ChangChiTiet.jsp`.
30. Trang `ChangChiTiet.jsp` hiển thị thông tin chặng đua và bảng danh sách các tay đua cho nhân viên.
31. *(Vòng lặp)* Nhân viên nhập thời gian hoàn thành, số vòng hoàn thành và trạng thái cho từng tay đua.
32. Nhân viên click nút [Tính kết quả] (`Calculate Result`) trên trang `ChangChiTiet.jsp`.
33. Trang `ChangChiTiet.jsp` gọi lớp `KetQuaDAO` yêu cầu xếp hạng và tính điểm.
34. Lớp `KetQuaDAO` gọi hàm `createKetQua()` tới lớp thực thể `KetQua` để khởi tạo các bản ghi kết quả và trả về cho trang `ChangChiTiet.jsp`.
35. Trang `ChangChiTiet.jsp` hiển thị bảng xếp hạng kết quả tính toán cho nhân viên kiểm tra.
36. Nhân viên click nút [Lưu] trên trang `ChangChiTiet.jsp`.
37. Trang `ChangChiTiet.jsp` gọi lớp `KetQuaDAO` yêu cầu kiểm tra xem chặng đua đã có kết quả cũ hay chưa.
38. Lớp `KetQuaDAO` gọi hàm `kiemTraKetQuaCu()` tới lớp `KetQua` và trả kết quả kiểm tra cho trang `ChangChiTiet.jsp`.
39. Trang `ChangChiTiet.jsp` gọi lớp `KetQua` thực thi hàm `setter()` tự đóng gói dữ liệu kết quả từng tay đua.
40. *(Vòng lặp)* Trang `ChangChiTiet.jsp` gọi lớp `KetQuaDAO` thực thi hàm `luuKetQua()` để lưu các bản ghi kết quả vào CSDL cho đến khi hoàn tất tất cả tay đua.
41. Trang `ChangChiTiet.jsp` hiển thị thông báo "Lưu thành công" cho nhân viên.

---

### 6.8. Biểu đồ tuần tự

Biểu đồ tuần tự chi tiết biểu diễn luồng tương tác giữa Actor `NhanVien`, các View (`NhanVien.jsp`, `MuaGiai.jsp`, `Chang.jsp`, `ChangChiTiet.jsp`), các DAO (`MuaGiaiDAO`, `ChangDuaDAO`, `DangKyChangDAO`, `KetQuaDAO`) và các Model (`MuaGiai`, `ChangDua`, `DangKyChang`, `KetQua`):

![Biểu đồ tuần tự Module 3](<../Module 3 - Kiet/hinh/m3-tuantu.png>)

*Hình 6.6 — Biểu đồ tuần tự Module 3*

---

### 6.9. Test case

#### 6.9.1. Data test (bước 3 quy trình test)

`tblMuaGiai`

| id | ten | nam | trangThai |
|---|---|---|---|
| 1 | Formula 1 World Championship | 2025 | Đang diễn ra |

`tblChangDua` (mùa giải 2025, `tblMuaGiaiid = 1`)

| id | ma | ten | soVong | diaDiem | thoiGian | tblMuaGiaiid |
|---|---|---|---|---|---|---|
| 1 | R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | 1 |
| 2 | R02 | Chinese Grand Prix | 56 | Thượng Hải | 23/03/2025 | 1 |
| 3 | R06 | Monaco Grand Prix | 78 | Monte Carlo | 25/05/2025 | 1 |
| 4 | R10 | British Grand Prix | 52 | Silverstone | 06/07/2025 | 1 |
| 5 | R16 | Italian Grand Prix | 53 | Monza | 07/09/2025 | 1 |
| 6 | R24 | Abu Dhabi Grand Prix | 58 | Yas Marina | 07/12/2025 | 1 |

`tblDangKyChang` (chặng R16 — Monza)

| id | tblChangDuaid | tblTayDuaid | tblDoiDuaid |
|---|---|---|---|
| 41 | 5 | 1 (LEC) | 1 (Ferrari) |
| 42 | 5 | 2 (HAM) | 1 (Ferrari) |
| 43 | 5 | 3 (VER) | 2 (Red Bull) |
| 44 | 5 | 4 (TSU) | 2 (Red Bull) |
| 45 | 5 | 5 (NOR) | 3 (McLaren) |
| 46 | 5 | 6 (PIA) | 3 (McLaren) |
| 47 | 5 | 7 (RUS) | 4 (Mercedes) |
| 48 | 5 | 8 (ANT) | 4 (Mercedes) |
| 49 | 5 | 9 (ALO) | 5 (Aston Martin) |
| 50 | 5 | 10 (STR) | 5 (Aston Martin) |
| 51 | 5 | 11 (ALB) | 6 (Williams) |
| 52 | 5 | 12 (SAI) | 6 (Williams) |

`tblKetQua` (kết quả cũ chặng R16 — nếu có)

| id | thoiGian | soVongHoanThanh | trangThai | hang | diem | tblDangKyChangid |
|---|---|---|---|---|---|---|
| 101 | 4411.482 | 53 | HoanThanh | 1 | 25 | 41 (LEC) |
| 102 | 4421.663 | 53 | HoanThanh | 2 | 18 | 42 (HAM) |

#### 6.9.2. Bảng test case

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|
| | **Giao diện — màn Mùa giải (`MuaGiai.jsp`)** | | |
| CNKQ_1 | Kiểm tra tổng thể giao diện màn Mùa giải | 1. Đăng nhập với quyền `NhanVien1`.<br>2. Click nút [Mùa giải].<br>3. Kiểm tra các nút bấm, chính tả và bảng dữ liệu. | Hiển thị bảng `tblMuaGiai` gồm các cột Mùa giải, Năm, Trạng thái; có các nút [Xem chi tiết], [Thêm mùa giải], [Lưu], [Quay lại]. Giao diện chuẩn font, không vỡ layout. |
| CNKQ_2 | Kiểm tra thứ tự Tab và Shift-Tab màn Mùa giải | 1. Focus màn `MuaGiai.jsp`.<br>2. Bấm Tab và Shift-Tab liên tục. | Con trỏ di chuyển lần lượt qua các dòng bảng và nút bấm theo đúng thứ tự. |
| | **Giao diện — màn Danh sách chặng (`Chang.jsp`)** | | |
| CNKQ_3 | Kiểm tra tổng thể giao diện màn Danh sách chặng | 1. Tại `MuaGiai.jsp`, chọn mùa 2025 và click [Xem chi tiết].<br>2. Kiểm tra bảng `tblChang` và các nút bấm. | Hiển thị bảng `tblChang` gồm Mã, Tên chặng, Địa điểm, Thời gian; có nút [Xem chi tiết chặng], [Thêm chặng], [Lưu], [Quay lại]. |
| | **Giao diện — màn Chi tiết chặng & Nhập kết quả (`ChangChiTiet.jsp`)** | | |
| CNKQ_4 | Kiểm tra bố cục màn Chi tiết chặng | 1. Tại `Chang.jsp`, chọn chặng R16 và click [Xem chi tiết chặng].<br>2. Kiểm tra dropdown `cmbChang`, bảng `tblTayDua` và các nút bấm. | Hiển thị dropdown `cmbChang`, bảng `tblTayDua` chứa 12 tay đua đăng ký kèm các ô nhập Thời gian, Số vòng, Trạng thái. Các nút [Tính kết quả], [Lưu] (chưa active), [Tiếp tục], [Quay lại] hiển thị đầy đủ. |
| | **Luồng nghiệp vụ** | | |
| CNKQ_5 | Cập nhật kết quả chặng thành công (ca chuẩn) | 1. Mở `ChangChiTiet.jsp` chặng R16.<br>2. Nhập thời gian, số vòng 53, trạng thái `Hoàn thành` cho 12 tay đua.<br>3. Click [Tính kết quả].<br>4. Click [Lưu]. | Bước 3: `KetQuaDAO.createKetQua()` xếp hạng tăng dần theo thời gian, hiển thị bảng đối soát `tblKetQua`. Bước 4: `KetQuaDAO.kiemTraKetQuaCu()` kiểm tra và lưu thành công 12 bản ghi vào CSDL `tblKetQua`, thông báo "Lưu thành công". |
| CNKQ_6 | Xử lý tay đua DNF / DSQ | 1. Nhập kết quả R16, chọn Max Verstappen trạng thái `DNF`, Lewis Hamilton trạng thái `DSQ`.<br>2. Click [Tính kết quả] và [Lưu]. | Verstappen và Hamilton xếp cuối bảng đối soát với 0 điểm; các tay đua hoàn thành được xếp hạng phía trên theo đúng thang điểm 25, 18, 15... |
| CNKQ_7 | Nhập thiếu trạng thái hoặc sai định dạng thời gian — báo lỗi | 1. Nhập thời gian cho 11 tay đua, bỏ trống 1 tay đua.<br>2. Click [Tính kết quả]. | Hệ thống hiển thị thông báo lỗi "Vui lòng nhập thời gian hợp lệ cho tay đua đã hoàn thành", không tính kết quả, nút [Lưu] giữ nguyên chưa active. |
| CNKQ_8 | Ghi đè kết quả khi chặng đã có kết quả cũ | 1. Mở chặng R16 đã nhập kết quả từ trước.<br>2. Nhập lại thời gian mới, click [Tính kết quả], click [Lưu]. | Hệ thống hiển thị hộp thoại cảnh báo "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Chọn Xác nhận → hệ thống xóa kết quả cũ trong `tblKetQua` và lưu kết quả mới thành công. |
| CNKQ_9 | Xử lý kháng nghị thành công (`KhangNghi.jsp`) | 1. Đăng nhập quyền `NhanVien2`, mở màn hình `KhangNghi.jsp`.<br>2. Chọn đơn kháng nghị của đội McLaren, đối chiếu video camera.<br>3. Chấp nhận kháng nghị, nhập lại kết quả đúng và click [Lưu]. | Hệ thống cập nhật lại bảng điểm xếp hạng của chặng, lưu dữ liệu mới và ghi nhận trạng thái kháng nghị thành công. |
| CNKQ_10 | Phê duyệt kết quả chặng đua | 1. `NhanVien2` kiểm tra kết quả chặng R16 sau khi hết kháng nghị.<br>2. Click [Phê duyệt]. | Hệ thống khóa kết quả chặng R16, đổi trạng thái sang đã phê duyệt và hiển thị thông báo "Phê duyệt kết quả chặng thành công". |


---

## CHƯƠNG 7: MODULE 4 — QUYẾT TOÁN VÀ TRAO GIẢI CUỐI MÙA

**Thành viên thực hiện:** Phùng Tuấn Thành — **Use case:** Quyết toán và trao giải cuối mùa

### 7.1. Biểu đồ Use Case chi tiết

Use case chính: **`Quyết toán và trao giải cuối mùa`**, actor **Quản lý**. Use case chi tiết được phân rã theo 2 nguồn: (1) **mỗi giao diện tương tác với người dùng → 1 use case con** (quan hệ include/extend); (2) use case `QL đăng nhập` **kế thừa** use case dùng chung `Đăng nhập` (gắn với actor cha **Thành viên**), và use case chính **include** `QL đăng nhập`; đăng nhập dùng chung toàn hệ thống nên **không** sinh lớp biên hay trang `.jsp` riêng trong module.

Module có 3 màn hình hiển thị nghiệp vụ:

| Màn hình | UC con | Quan hệ với UC chính | Lớp biên | Trang JSP |
|---|---|---|---|---|
| Trang chính quản lý (trang chủ chung) | — | — | `GDChinhQL` | `gdChinhQL.jsp` |
| Bảng tổng sắp (chọn chặng từ danh sách) | `Xem bảng tổng sắp` | include | `GDXepHang` | `gdXepHang.jsp` |
| Chi tiết theo chặng (drill-down 1 dòng) | `Xem chi tiết theo chặng` | **extend từ `Xem bảng tổng sắp`** | `GDChiTietXepHang` | `gdChiTietXepHang.jsp` |
| Trao giải | `Nhập thưởng và lưu` | include | `GDTraoGiai` | `gdTraoGiai.jsp` |
| — (dùng chung toàn hệ thống) | `QL đăng nhập` — kế thừa `Đăng nhập` | include | — | — |
| — (trang xử lý, không hiển thị tương tác) | — | — | — | `doLuuTraoGiai.jsp` |

`Xem chi tiết theo chặng` chỉ xảy ra khi quản lý click vào một dòng tay đua hoặc đội trên bảng tổng sắp, nên là use case mở rộng (**extend**).

![Biểu đồ Use Case chi tiết Module 4](<../Module 4 - Thanh/hinh/m4-uc-chitiet.png>)

*Hình 7.1 — Biểu đồ Use Case chi tiết Module 4*

### 7.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| **Use case** | Quyết toán và trao giải cuối mùa |
| **Actor** | Quản lý |
| **Tiền điều kiện** | Quản lý đã đăng nhập vào hệ thống; mùa giải `FIA Formula One World Championship 2025` đang ở trạng thái `Đã kết thúc` |
| **Hậu điều kiện** | Quyết định trao giải của mùa giải (giải cá nhân hạng 1–3, giải đồng đội hạng 1–3 kèm tiền thưởng) được lưu vào CSDL; danh sách trao giải được in ra |

**Kịch bản chính**

1. Quản lý (đã đăng nhập) click chức năng **Quyết toán mùa giải** trên trang chính `gdChinhQL.jsp`.
2. Hệ thống lấy mùa giải hiện tại `FIA Formula One World Championship 2025` và hiển thị màn **Bảng tổng sắp** (`gdXepHang.jsp`): danh sách thả xuống **Chặng** gồm 6 chặng của mùa giải, vùng chỉ đọc hiện tình trạng mùa giải (`6/6 chặng đã có kết quả`), hai vùng bảng *Xếp hạng cá nhân* và *Xếp hạng đội* (mỗi dòng là một liên kết click được), nút [Tiếp tục] **chưa được active**.

   **Màn hình *Bảng tổng sắp* (`gdXepHang.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Mùa giải | vùng chỉ đọc | `FIA Formula One World Championship 2025` |
   | Chặng | danh sách thả xuống | 6 chặng của mùa giải; nội dung ở bảng ngay dưới |
   | Tình trạng mùa giải | vùng chỉ đọc | `6/6 chặng đã có kết quả` |
   | Xếp hạng cá nhân | bảng, mỗi dòng là liên kết | nội dung ở bảng 1 của bước 4 |
   | Xếp hạng đội | bảng, mỗi dòng là liên kết | nội dung ở bảng 2 của bước 4 |
   | [Tiếp tục] | nút | chưa active, chỉ active khi chặng đang chọn là chặng cuối và đủ 6/6 chặng có kết quả |
   | [Về trang chủ] | nút | active |

   Nội dung danh sách thả xuống **Chặng** — 6 chặng của mùa giải 2025 sắp xếp tăng dần theo thời gian, mỗi mục hiển thị dạng `Mã - Tên chặng (Địa điểm)` (đúng các cột `ma`, `ten`, `diaDiem` của `tblChangDua` ở mục 7.9.1):

   | TT | Mã | Tên chặng | Địa điểm | Ngày đua | Hiển thị trong ô chọn |
   |---|---|---|---|---|---|
   | 1 | R01 | Australian Grand Prix | Melbourne | 16/03/2025 | R01 - Australian Grand Prix (Melbourne) |
   | 2 | R02 | Chinese Grand Prix | Thượng Hải | 23/03/2025 | R02 - Chinese Grand Prix (Thượng Hải) |
   | 3 | R06 | Monaco Grand Prix | Monte Carlo | 25/05/2025 | R06 - Monaco Grand Prix (Monte Carlo) |
   | 4 | R10 | British Grand Prix | Silverstone | 06/07/2025 | R10 - British Grand Prix (Silverstone) |
   | 5 | R16 | Italian Grand Prix | Monza | 07/09/2025 | R16 - Italian Grand Prix (Monza) |
   | 6 | R24 | Abu Dhabi Grand Prix | Yas Marina | 07/12/2025 | R24 - Abu Dhabi Grand Prix (Yas Marina) |

3. Quản lý chọn chặng `R24 - Abu Dhabi Grand Prix (Yas Marina)` — **chặng cuối** — trong danh sách.
4. Hệ thống kiểm tra cả 6/6 chặng đều đã có kết quả; cộng dồn điểm, tổng thời gian và số lần đạt từng thứ hạng của mỗi tay đua và mỗi đội **tính đến chặng đã chọn**, rồi sắp xếp theo **3 tầng**: (1) tổng điểm giảm dần; (2) bằng điểm → **countback** (so số lần về nhất, rồi về nhì, về ba…); (3) countback vẫn bằng → **tổng thời gian tăng dần**. Hệ thống hiển thị bảng *Xếp hạng cá nhân* đủ 12 dòng, trích 3 dòng đầu:

   | Hạng | Tên tay đua | Quốc tịch | Tên đội | Tổng điểm | Tổng thời gian |
   |---|---|---|---|---|---|
   | 1 | Lando Norris | Anh | McLaren | 119 | 9:03:19.885 |
   | 2 | Max Verstappen | Hà Lan | Red Bull | 119 | 9:03:12.418 |
   | 3 | Oscar Piastri | Úc | McLaren | 95 | 9:04:01.207 |

   và bảng *Xếp hạng đội* đủ 6 dòng, trích 3 dòng đầu:

   | Hạng | Tên đội | Hãng | Tổng điểm | Tổng thời gian |
   |---|---|---|---|---|
   | 1 | McLaren | Mercedes | 214 | 18:07:21.092 |
   | 2 | Ferrari | Ferrari | 132 | 18:10:03.757 |
   | 3 | Red Bull | Honda RBPT | 121 | 18:12:45.433 |

   Mỗi dòng của hai bảng là một liên kết click được. Hai dòng đầu bảng cá nhân bằng 119 điểm nên được tô nền nhạt kèm chú thích `Phân định bằng countback (số lần về nhất)`. Bảng xếp hạng luôn được tính **đến chặng đang chọn**, nên nếu quản lý đổi chặng trong danh sách thì hai bảng được tính lại. Nút [Tiếp tục] **chuyển sang active** vì chặng được chọn là chặng cuối và cả 6/6 chặng đều đã có kết quả.

5. Quản lý xem bảng tổng sắp và click [Tiếp tục].
6. Hệ thống hiển thị màn **Trao giải** (`gdTraoGiai.jsp`): 6 ô nhập mức thưởng (cá nhân hạng 1/2/3, đội hạng 1/2/3) **đang rỗng**; bảng *Danh sách trao giải* có 6 dòng (cá nhân hạng 1–3, đội hạng 1–3), 4 cột đầu đã có sẵn dữ liệu top 3 cá nhân và top 3 đội, **cột Tiền thưởng đang rỗng**; nút [Tính thưởng] đang active, nút [Lưu] **chưa được active**.

   **Màn hình *Trao giải* (`gdTraoGiai.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Mức thưởng giải cá nhân hạng 1, 2, 3 | ô nhập | rỗng |
   | Mức thưởng giải đồng đội hạng 1, 2, 3 | ô nhập | rỗng |
   | [Tính thưởng] | nút | active |
   | Danh sách trao giải | bảng | 6 dòng (cá nhân hạng 1–3, đội hạng 1–3); 4 cột đầu đã có dữ liệu, cột Tiền thưởng đang rỗng |
   | [Lưu] | nút | chưa active, chỉ active sau khi cột Tiền thưởng đã được điền |
   | [Quay lại] | nút | active |

7. Quản lý nhập mức thưởng vào 6 ô: cá nhân hạng 1 = `5.000.000.000`, hạng 2 = `3.000.000.000`, hạng 3 = `2.000.000.000`; đội hạng 1 = `20.000.000.000`, hạng 2 = `12.000.000.000`, hạng 3 = `8.000.000.000` rồi click [Tính thưởng].
8. Hệ thống điền cột Tiền thưởng cho đủ 6 dòng của bảng *Danh sách trao giải*:

   | Loại giải | Hạng | Tay đua/Đội | Tổng điểm | Tiền thưởng |
   |---|---|---|---|---|
   | Cá nhân | 1 | Lando Norris | 119 | 5.000.000.000 |
   | Cá nhân | 2 | Max Verstappen | 119 | 3.000.000.000 |
   | Cá nhân | 3 | Oscar Piastri | 95 | 2.000.000.000 |
   | Đội | 1 | McLaren | 214 | 20.000.000.000 |
   | Đội | 2 | Ferrari | 132 | 12.000.000.000 |
   | Đội | 3 | Red Bull | 121 | 8.000.000.000 |

   Nút [Lưu] **chuyển sang active**.

   *(Lặp lại các bước 7–8 cho đến khi quản lý ưng ý với mức thưởng.)*

9. Quản lý kiểm tra danh sách trao giải và click [Lưu]; màn hình gửi dữ liệu sang **trang xử lý** `doLuuTraoGiai.jsp`.
10. Hệ thống lưu 6 bản ghi trao giải, in danh sách trao giải mùa giải 2025 và hiển thị thông báo `Đã lưu quyết định trao giải mùa giải FIA Formula One World Championship 2025`.
11. Quản lý click OK; hệ thống quay về trang chính của quản lý `gdChinhQL.jsp`.

**Ngoại lệ**

**2a.** Không có mùa giải nào ở trạng thái `Đã kết thúc` → hệ thống báo `Không có mùa giải nào đủ điều kiện quyết toán`, quay về trang chính, dừng.

**4a.** Quản lý click vào một dòng của bảng xếp hạng (ví dụ dòng `Max Verstappen` trên bảng xếp hạng cá nhân) → UC con **Xem chi tiết theo chặng** (quan hệ *extend*) được kích hoạt: hệ thống hiển thị màn **Chi tiết theo chặng** (`gdChiTietXepHang.jsp`) với tiêu đề `Max Verstappen — Red Bull`; đây là màn **chỉ đọc**, không có ô nhập nên nút [Quay lại] **luôn active** ngay khi vào màn:

   **Màn hình *Chi tiết theo chặng* (`gdChiTietXepHang.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Tên đối tượng được click | vùng chỉ đọc | `Max Verstappen — Red Bull` |
   | Phạm vi dữ liệu | vùng chỉ đọc | `tính đến chặng R24 - Abu Dhabi Grand Prix (Yas Marina)` |
   | Kết quả từng chặng | bảng | nội dung ở bảng ngay dưới; màn chỉ đọc, không có ô nhập |
   | [Quay lại] | nút | active ngay khi vào màn |

   Bảng chi tiết khi click 1 dòng **tay đua** — 6 dòng, trích dòng đầu:

   | Tên chặng | Hạng về đích | Điểm | Thời gian về đích |
   |---|---|---|---|
   | Australian Grand Prix | 2 | 18 | 1:28:06.334 |

   Bảng chi tiết khi click 1 dòng **đội** (ví dụ `McLaren — Mercedes`) — 6 dòng, trích dòng đầu:

   | Tên chặng | Tổng điểm | Tổng thời gian của 2 tay đua |
   |---|---|---|
   | Australian Grand Prix | 35 | 2:56:36.414 |

   Số cột của bảng chi tiết đổi theo loại đối tượng được click: 4 cột với tay đua, 3 cột với đội. Phạm vi dữ liệu vẫn là "tính đến chặng đang chọn" ở màn Bảng tổng sắp, nên nếu chặng đang chọn là `R01 - Australian Grand Prix (Melbourne)` thì bảng chỉ còn 1 dòng. Quản lý click [Quay lại] → trở về màn **Bảng tổng sắp** ở bước 4, giữ nguyên chặng đang chọn.

**4b.** Quản lý chọn chặng **giữa mùa** (ví dụ `R10 - British Grand Prix (Silverstone)`) → hệ thống hiển thị 2 bảng xếp hạng **tính đến chặng đó**; nút [Tiếp tục] **chưa active** vì chưa phải chặng cuối.

**4c.** Mùa giải còn chặng chưa có kết quả (ví dụ `R24 - Abu Dhabi Grand Prix (Yas Marina)` chưa nhập) → hệ thống vẫn cho xem bảng xếp hạng tính đến chặng gần nhất đã có kết quả, nhưng vùng chỉ đọc tình trạng mùa giải chuyển thành `5/6 chặng đã có kết quả` kèm thông báo `Mùa giải 2025 còn 1 chặng chưa có kết quả (R24 - Abu Dhabi Grand Prix), chưa thể quyết toán`, nút [Tiếp tục] **chưa active**.

**4d.** Hai tay đua (hoặc hai đội) bằng tổng điểm → phân định bằng **countback**: `Lando Norris` và `Max Verstappen` cùng 119 điểm, Norris có 3 lần về nhất so với 2 của Verstappen nên Norris xếp trên (dù tổng thời gian của Verstappen nhỏ hơn).

**4e.** Countback vẫn không phân định được sau khi so hết các thứ hạng → hệ thống so **tổng thời gian tăng dần**: bên có tổng thời gian nhỏ hơn xếp trên (đúng mô tả bài toán).

**7a.** Ô mức thưởng bỏ trống, nhập chữ hoặc nhập số âm → hệ thống báo `Mức thưởng phải là số không âm`, giữ nguyên màn Trao giải, cột Tiền thưởng vẫn rỗng, nút [Lưu] vẫn chưa active.

**9a.** Mùa giải đã có quyết định trao giải trước đó → hệ thống cảnh báo `Mùa giải 2025 đã có quyết định trao giải, xác nhận ghi đè?`; chọn Có → xoá quyết định cũ rồi lưu bản mới; chọn Không → huỷ thao tác lưu, giữ nguyên màn Trao giải.

> Luồng chuyển màn: **Trang chính → Bảng tổng sắp → (click 1 dòng) Chi tiết theo chặng → (Quay lại) Bảng tổng sắp → (Tiếp tục) Trao giải → (Lưu) → Trang chính**.

### 7.3. Biểu đồ trạng thái (phân tích hoạt động)

Biểu đồ bắt đầu từ trạng thái hiển thị **giao diện chính** của quản lý: `Hiển thị GD chính QL` —`[click Quyết toán mùa giải]`→ `Hiển thị GD bảng tổng sắp` (cung tự quay `[chọn chặng từ danh sách]` — xem bảng xếp hạng tính đến chặng bất kỳ; cung `[click 1 dòng tay đua hoặc đội]` sang `Hiển thị GD chi tiết theo chặng`, từ đó `[click Quay lại]` trở về) —`[click Tiếp tục, đã chọn chặng cuối và đủ kết quả]`→ `Hiển thị GD trao giải` (cung tự quay `[nhập mức thưởng, click Tính thưởng]` — tính lại tiền thưởng nhiều lần trước khi lưu) —`[click Lưu, mức thưởng hợp lệ]`→ `Hiển thị thông báo và in danh sách trao giải` —`[click OK]`→ Kết thúc.

![Biểu đồ trạng thái Module 4](<../Module 4 - Thanh/hinh/m4-trangthai.png>)

*Hình 7.2 — Biểu đồ trạng thái Module 4 (phân tích hoạt động)*

### 7.4. Biểu đồ lớp phân tích

**Lớp biên:**

| Lớp biên | Màn hình | Thuộc tính |
|---|---|---|
| `GDChinhQL` | Trang chính của quản lý (trang chủ chung hệ thống) | `-subQuyetToan` |
| `GDXepHang` | Bảng tổng sắp (có chọn chặng; 2 bảng xếp hạng click được từng dòng) | `-inChangDua`, `-outTinhTrangChang`, `-outsubXHCaNhan`, `-outsubXHDoi`, `-subTiepTuc`, `-subVeTrangChu` |
| `GDChiTietXepHang` | Chi tiết theo chặng (drill-down) | `-outTenDoiTuong`, `-outBangChiTiet`, `-subQuayLai` |
| `GDTraoGiai` | Trao giải | `-inMucThuongCaNhan1`, `-inMucThuongCaNhan2`, `-inMucThuongCaNhan3`, `-inMucThuongDoi1`, `-inMucThuongDoi2`, `-inMucThuongDoi3`, `-subTinhThuong`, `-outDSTraoGiai`, `-subLuu`, `-subQuayLai` |

**Phương thức nghiệp vụ gán cho lớp thực thể:**

| Chức năng cần thực hiện dưới tầng giao diện | Gán cho lớp | Phương thức |
|---|---|---|
| Lấy mùa giải hiện tại và danh sách chặng | `MuaGiai` | `getMuaGiaiHienTai()` |
| Kiểm tra một chặng đã có kết quả hay chưa | `KetQua` | `kiemTraKetQuaCu(changDuaId)` |
| Tổng hợp xếp hạng cá nhân tính đến chặng được chọn | `KetQua` | `tongHopCaNhan(muaGiaiId, changDuaId)` |
| Tổng hợp xếp hạng đội tính đến chặng được chọn | `KetQua` | `tongHopDoi(muaGiaiId, changDuaId)` |
| Sắp xếp bảng xếp hạng theo quy tắc 3 tầng | `KetQua` | `sapXepBangXepHang(ds)` |
| Lấy chi tiết kết quả từng chặng của một tay đua | `KetQua` | `getChiTietTheoTayDua(muaGiaiId, tayDuaId, changDuaId)` |
| Lấy chi tiết kết quả từng chặng của một đội | `KetQua` | `getChiTietTheoDoi(muaGiaiId, doiDuaId, changDuaId)` |
| Tính tiền thưởng theo hạng | `TraoGiai` | `tinhTienThuong(hang, mucThuong)` |
| Lưu một bản ghi trao giải | `TraoGiai` | `luuTraoGiai()` |

![Biểu đồ lớp phân tích Module 4](<../Module 4 - Thanh/hinh/m4-lop-phantich.png>)

*Hình 7.3 — Biểu đồ lớp phân tích Module 4*

### 7.5. Biểu đồ lớp thiết kế (view `.jsp` / `DAO` / `model`)

- **View (jsp):** `gdChinhQL` (trang chính của quản lý), `gdXepHang`, `gdChiTietXepHang`, `gdTraoGiai`, `doLuuTraoGiai` (trang xử lý)
- **DAO:** `MuaGiaiDAO` — `+getMuaGiaiHienTai() : MuaGiai`; `KetQuaDAO` — `+kiemTraKetQuaCu(changDuaId : int) : boolean`, `+tongHopCaNhan(muaGiaiId : int, changDuaId : int) : KetQua[]`, `+tongHopDoi(muaGiaiId : int, changDuaId : int) : KetQua[]`, `+sapXepBangXepHang(ds : KetQua[]) : KetQua[]`, `+getChiTietTheoTayDua(muaGiaiId : int, tayDuaId : int, changDuaId : int) : KetQua[]`, `+getChiTietTheoDoi(muaGiaiId : int, doiDuaId : int, changDuaId : int) : KetQua[]`; `TraoGiaiDAO` — `+tinhTienThuong(hang : int, mucThuong : float) : float`, `+luuTraoGiai(listTG : TraoGiai[]) : boolean` (tất cả kế thừa `DAO`)
- **Model:** `MuaGiai`, `ChangDua`, `KetQua`, `TayDua`, `DoiDua`, `TraoGiai`, `ThanhVien`, `QuanLy`

![Biểu đồ lớp thiết kế Module 4](<../Module 4 - Thanh/hinh/m4-lop-mvc.png>)

*Hình 7.4 — Biểu đồ lớp thiết kế Module 4 (view `.jsp` / `DAO` / `model`)*

### 7.6. Biểu đồ hoạt động (pha thiết kế)

![Biểu đồ hoạt động Module 4](<../Module 4 - Thanh/hinh/m4-hoatdong.png>)

*Hình 7.5 — Biểu đồ hoạt động Module 4 (pha thiết kế)*

### 7.7. Thuyết minh (kịch bản phiên bản 3)

1. Quản lý click chức năng "Quyết toán mùa giải" trên trang chính gdChinhQL.jsp.
2. Trang gdChinhQL.jsp gọi trang gdXepHang.jsp.
3. Trang gdXepHang.jsp gọi lớp MuaGiaiDAO yêu cầu lấy mùa giải hiện tại.
4. Lớp MuaGiaiDAO gọi hàm getMuaGiaiHienTai().
5. Hàm getMuaGiaiHienTai() gọi lớp MuaGiai để đóng gói thông tin.
6. Lớp MuaGiai đóng gói thông tin thực thể.
7. Lớp MuaGiai gọi lớp ChangDua để đóng gói danh sách chặng của mùa giải.
8. Lớp ChangDua đóng gói thông tin thực thể.
9. Lớp ChangDua trả kết quả về cho lớp MuaGiai.
10. Lớp MuaGiai trả kết quả về cho hàm getMuaGiaiHienTai().
11. Hàm getMuaGiaiHienTai() trả kết quả cho trang gdXepHang.jsp.
12. Trang gdXepHang.jsp hiển thị màn Bảng tổng sắp kèm danh sách chọn chặng cho quản lý.
13. Quản lý chọn chặng Abu Dhabi (chặng cuối) từ danh sách.
14. Trang gdXepHang.jsp gọi lớp KetQuaDAO yêu cầu kiểm tra một chặng đã có kết quả hay chưa.
15. Lớp KetQuaDAO gọi hàm kiemTraKetQuaCu().
16. Hàm kiemTraKetQuaCu() gọi lớp KetQua để đóng gói thông tin.
17. Lớp KetQua đóng gói thông tin thực thể.
18. Lớp KetQua trả kết quả về cho hàm kiemTraKetQuaCu().
19. Hàm kiemTraKetQuaCu() trả kết quả cho trang gdXepHang.jsp. *(Lặp lại các bước 14–19 cho từng chặng tính đến chặng được chọn.)*
20. Trang gdXepHang.jsp gọi lớp KetQuaDAO yêu cầu tổng hợp xếp hạng cá nhân của mùa giải.
21. Lớp KetQuaDAO gọi hàm tongHopCaNhan().
22. Hàm tongHopCaNhan() gọi lớp KetQua để đóng gói thông tin.
23. Lớp KetQua đóng gói thông tin thực thể.
24. Lớp KetQua gọi lớp TayDua để đóng gói thông tin tay đua cho từng dòng xếp hạng.
25. Lớp TayDua đóng gói thông tin thực thể.
26. Lớp TayDua trả kết quả về cho lớp KetQua.
27. Lớp KetQua trả kết quả về cho hàm tongHopCaNhan().
28. Lớp KetQuaDAO gọi hàm sapXepBangXepHang() sắp xếp bảng xếp hạng cá nhân theo 3 tầng: tổng điểm giảm dần, countback, tổng thời gian tăng dần.
29. Hàm tongHopCaNhan() trả kết quả cho trang gdXepHang.jsp.
30. Trang gdXepHang.jsp gọi lớp KetQuaDAO yêu cầu tổng hợp xếp hạng đội của mùa giải.
31. Lớp KetQuaDAO gọi hàm tongHopDoi().
32. Hàm tongHopDoi() gọi lớp KetQua để đóng gói thông tin.
33. Lớp KetQua đóng gói thông tin thực thể.
34. Lớp KetQua gọi lớp DoiDua để đóng gói thông tin đội đua cho từng dòng xếp hạng.
35. Lớp DoiDua đóng gói thông tin thực thể.
36. Lớp DoiDua trả kết quả về cho lớp KetQua.
37. Lớp KetQua trả kết quả về cho hàm tongHopDoi().
38. Lớp KetQuaDAO gọi hàm sapXepBangXepHang() sắp xếp bảng xếp hạng đội theo 3 tầng.
39. Hàm tongHopDoi() trả kết quả cho trang gdXepHang.jsp.
40. Trang gdXepHang.jsp hiển thị hai bảng xếp hạng cho quản lý.
41. Quản lý click vào dòng Max Verstappen trên bảng xếp hạng cá nhân.
42. Trang gdXepHang.jsp gọi trang gdChiTietXepHang.jsp.
43. Trang gdChiTietXepHang.jsp gọi lớp KetQuaDAO yêu cầu lấy chi tiết kết quả từng chặng của tay đua.
44. Lớp KetQuaDAO gọi hàm getChiTietTheoTayDua().
45. Hàm getChiTietTheoTayDua() gọi lớp KetQua để đóng gói thông tin.
46. Lớp KetQua đóng gói thông tin thực thể.
47. Lớp KetQua gọi lớp ChangDua để đóng gói tên chặng cho từng dòng chi tiết.
48. Lớp ChangDua đóng gói thông tin thực thể.
49. Lớp ChangDua trả kết quả về cho lớp KetQua.
50. Lớp KetQua trả kết quả về cho hàm getChiTietTheoTayDua().
51. Hàm getChiTietTheoTayDua() trả kết quả cho trang gdChiTietXepHang.jsp.
52. Trang gdChiTietXepHang.jsp hiển thị bảng chi tiết từng chặng cho quản lý. *(Khi quản lý click 1 dòng đội, luồng tương tự với hàm getChiTietTheoDoi().)*
53. Quản lý click nút Quay lại.
54. Trang gdChiTietXepHang.jsp gọi lại trang gdXepHang.jsp.
55. Trang gdXepHang.jsp hiển thị lại hai bảng xếp hạng cho quản lý.
56. Quản lý click nút Tiếp tục.
57. Trang gdXepHang.jsp gọi trang gdTraoGiai.jsp.
58. Trang gdTraoGiai.jsp hiển thị màn trao giải cho quản lý.
59. Quản lý nhập mức thưởng cho 6 hạng và click nút Tính thưởng.
60. Trang gdTraoGiai.jsp gọi lớp TraoGiaiDAO yêu cầu tính tiền thưởng cho một hạng.
61. Lớp TraoGiaiDAO gọi hàm tinhTienThuong().
62. Hàm tinhTienThuong() gọi lớp TraoGiai để đóng gói thông tin.
63. Lớp TraoGiai đóng gói thông tin thực thể.
64. Lớp TraoGiai trả kết quả về cho hàm tinhTienThuong().
65. Hàm tinhTienThuong() trả kết quả cho trang gdTraoGiai.jsp. *(Lặp lại các bước 60–65 cho từng hạng được thưởng.)*
66. Trang gdTraoGiai.jsp hiển thị danh sách trao giải kèm cột Tiền thưởng cho quản lý.
67. Quản lý click nút Lưu.
68. Trang gdTraoGiai.jsp gọi trang doLuuTraoGiai.jsp.
69. Trang doLuuTraoGiai.jsp gọi lớp TraoGiai yêu cầu đóng gói danh sách trao giải vừa nhập.
70. Lớp TraoGiai gọi hàm setter() để đóng gói dữ liệu.
71. Lớp TraoGiai trả về cho trang doLuuTraoGiai.jsp.
72. Trang doLuuTraoGiai.jsp gọi lớp TraoGiaiDAO yêu cầu lưu danh sách trao giải.
73. Lớp TraoGiaiDAO gọi hàm luuTraoGiai().
74. Hàm luuTraoGiai() trả kết quả cho trang doLuuTraoGiai.jsp.
75. Trang doLuuTraoGiai.jsp thông báo lưu thành công và in danh sách trao giải cho quản lý.
76. Quản lý click nút OK.
77. Trang doLuuTraoGiai.jsp gọi lại trang chính gdChinhQL.jsp.
78. Trang gdChinhQL.jsp hiển thị cho quản lý.

### 7.8. Biểu đồ tuần tự

![Biểu đồ tuần tự Module 4](<../Module 4 - Thanh/hinh/m4-tuantu.png>)

*Hình 7.6 — Biểu đồ tuần tự Module 4*

### 7.9. Test case

#### 7.9.1. Data test (bước 3 quy trình test)

Bộ dữ liệu nền dùng chung cho nhóm **Luồng nghiệp vụ** (và các ca Chức năng), lấy từ bộ dữ liệu mẫu mùa 2025 thống nhất của nhóm. Hai ca `QTTG_27` (countback bằng → tổng thời gian) và `QTTG_30` (đổi đội giữa mùa) dùng **biến thể rút gọn** của bộ dữ liệu này — phần sửa đổi được mô tả ngay trong cột "Các bước thực hiện" của ca đó.

`tblMuaGiai`

| id | ten | nam | trangThai |
|---|---|---|---|
| 1 | FIA Formula One World Championship | 2025 | Đã kết thúc |

`tblChangDua`

| id | ma | ten | soVong | diaDiem | thoiGian | moTa | tblMuaGiaiid |
|---|---|---|---|---|---|---|---|
| 1 | R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | Chặng mở màn | 1 |
| 2 | R02 | Chinese Grand Prix | 56 | Thượng Hải | 23/03/2025 | | 1 |
| 3 | R06 | Monaco Grand Prix | 78 | Monte Carlo | 25/05/2025 | Đường phố | 1 |
| 4 | R10 | British Grand Prix | 52 | Silverstone | 06/07/2025 | | 1 |
| 5 | R16 | Italian Grand Prix | 53 | Monza | 07/09/2025 | | 1 |
| 6 | R24 | Abu Dhabi Grand Prix | 58 | Yas Marina | 07/12/2025 | Chặng kết mùa | 1 |

`tblDoiDua`

| id | ma | ten | hang | moTa |
|---|---|---|---|---|
| 1 | FER | Ferrari | Ferrari | |
| 2 | RBR | Red Bull | Honda RBPT | |
| 3 | MCL | McLaren | Mercedes | |
| 4 | MER | Mercedes | Mercedes | |
| 5 | AST | Aston Martin | Mercedes | |
| 6 | WIL | Williams | Mercedes | |

`tblTayDua`

| id | ma | ten | ngaySinh | quocTich | tieuSu |
|---|---|---|---|---|---|
| 1 | LEC | Charles Leclerc | 16/10/1997 | Monaco | |
| 2 | HAM | Lewis Hamilton | 07/01/1985 | Anh | |
| 3 | VER | Max Verstappen | 30/09/1997 | Hà Lan | |
| 4 | TSU | Yuki Tsunoda | 11/05/2000 | Nhật Bản | |
| 5 | NOR | Lando Norris | 13/11/1999 | Anh | |
| 6 | PIA | Oscar Piastri | 06/04/2001 | Úc | |
| 7 | RUS | George Russell | 15/02/1998 | Anh | |
| 8 | ANT | Andrea Kimi Antonelli | 25/08/2006 | Ý | |
| 9 | ALO | Fernando Alonso | 29/07/1981 | Tây Ban Nha | |
| 10 | STR | Lance Stroll | 29/10/1998 | Canada | |
| 11 | ALB | Alexander Albon | 23/03/1996 | Thái Lan | |
| 12 | SAI | Carlos Sainz | 01/09/1994 | Tây Ban Nha | |

`tblDangKyChang` — 72 dòng (6 chặng × 12 tay đua). Mỗi tay đua đăng ký cho đúng đội đang có hợp đồng hiệu lực ở cả 6 chặng: LEC, HAM → Ferrari; VER, TSU → Red Bull; NOR, PIA → McLaren; RUS, ANT → Mercedes; ALO, STR → Aston Martin; ALB, SAI → Williams. Trích 12 dòng của chặng R01:

| id | tblChangDuaid | tblTayDuaid | tblDoiDuaid |
|---|---|---|---|
| 1 | 1 | 1 (LEC) | 1 (Ferrari) |
| 2 | 1 | 2 (HAM) | 1 (Ferrari) |
| 3 | 1 | 3 (VER) | 2 (Red Bull) |
| 4 | 1 | 4 (TSU) | 2 (Red Bull) |
| 5 | 1 | 5 (NOR) | 3 (McLaren) |
| 6 | 1 | 6 (PIA) | 3 (McLaren) |
| 7 | 1 | 7 (RUS) | 4 (Mercedes) |
| 8 | 1 | 8 (ANT) | 4 (Mercedes) |
| 9 | 1 | 9 (ALO) | 5 (Aston Martin) |
| 10 | 1 | 10 (STR) | 5 (Aston Martin) |
| 11 | 1 | 11 (ALB) | 6 (Williams) |
| 12 | 1 | 12 (SAI) | 6 (Williams) |

`tblKetQua` — 72 dòng, tất cả `trangThai = HoanThanh`. Trích đầy đủ 12 dòng của chặng R01:

| id | tblDangKyChangid | thoiGian | soVongHoanThanh | trangThai | hang | diem |
|---|---|---|---|---|---|---|
| 1 | 5 (NOR) | 5284.512 | 58 | HoanThanh | 1 | 25 |
| 2 | 3 (VER) | 5286.334 | 58 | HoanThanh | 2 | 18 |
| 3 | 7 (RUS) | 5299.870 | 58 | HoanThanh | 3 | 15 |
| 4 | 1 (LEC) | 5304.115 | 58 | HoanThanh | 4 | 12 |
| 5 | 6 (PIA) | 5311.902 | 58 | HoanThanh | 5 | 10 |
| 6 | 2 (HAM) | 5327.663 | 58 | HoanThanh | 6 | 8 |
| 7 | 8 (ANT) | 5342.238 | 58 | HoanThanh | 7 | 6 |
| 8 | 11 (ALB) | 5355.407 | 58 | HoanThanh | 8 | 4 |
| 9 | 9 (ALO) | 5368.991 | 58 | HoanThanh | 9 | 2 |
| 10 | 12 (SAI) | 5384.126 | 58 | HoanThanh | 10 | 1 |
| 11 | 10 (STR) | 5398.775 | 58 | HoanThanh | 11 | 0 |
| 12 | 4 (TSU) | 5412.043 | 58 | HoanThanh | 12 | 0 |

> Cột `thoiGian` lưu **tổng số giây** (kiểu `float(10)`, xem mục 3.6.4); giao diện hiển thị dạng `hh:mm:ss.xxx`. Ví dụ `5284.512` giây hiển thị là `1:28:04.512`. Cột `Tổng thời gian` trên hai bảng xếp hạng ở mục 7.2 cũng là giá trị cộng dồn từ cột này rồi định dạng lại khi hiển thị.

Nội dung **đầy đủ** hai cột `hang` / `diem` của cả 72 dòng `tblKetQua`, trình bày dạng ma trận `hạng (điểm)` cho gọn:

| Tay đua | R01 | R02 | R06 | R10 | R16 | R24 | Tổng điểm |
|---|---|---|---|---|---|---|---|
| NOR | 1 (25) | 2 (18) | 2 (18) | 1 (25) | 1 (25) | 6 (8) | **119** |
| VER | 2 (18) | 3 (15) | 1 (25) | 2 (18) | 2 (18) | 1 (25) | **119** |
| PIA | 5 (10) | 1 (25) | 4 (12) | 3 (15) | 3 (15) | 2 (18) | 95 |
| LEC | 4 (12) | 4 (12) | 3 (15) | 5 (10) | 4 (12) | 3 (15) | 76 |
| RUS | 3 (15) | 5 (10) | 6 (8) | 6 (8) | 5 (10) | 4 (12) | 63 |
| HAM | 6 (8) | 6 (8) | 5 (10) | 4 (12) | 6 (8) | 5 (10) | 56 |
| ANT | 7 (6) | 7 (6) | 9 (2) | 7 (6) | 8 (4) | 7 (6) | 30 |
| ALB | 8 (4) | 8 (4) | 8 (4) | 10 (1) | 7 (6) | 9 (2) | 21 |
| ALO | 9 (2) | 9 (2) | 7 (6) | 8 (4) | 9 (2) | 8 (4) | 20 |
| SAI | 10 (1) | 11 (0) | 10 (1) | 11 (0) | 10 (1) | 10 (1) | 4 |
| TSU | 12 (0) | 12 (0) | 12 (0) | 9 (2) | 11 (0) | 12 (0) | 2 |
| STR | 11 (0) | 10 (1) | 11 (0) | 12 (0) | 12 (0) | 11 (0) | 1 |

`tblTraoGiai` — **rỗng** (chưa có dòng nào).

#### 7.9.2. Bảng test case

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|
| | **Giao diện — màn Bảng tổng sắp** | | |
| | **Nhóm 1 — Giao diện** | | |
| QTTG_1 | Kiểm tra tổng thể giao diện màn Bảng tổng sắp | 1. Mở màn Bảng tổng sắp.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| QTTG_2 | Kiểm tra bố cục màn Bảng tổng sắp | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Bảng tổng sắp — FIA Formula One World Championship 2025`.<br>2. Focus được đặt vào ô chọn "Chặng".<br>3. Hiển thị đầy đủ các trường: Mùa giải (vùng chỉ đọc) · Chặng (danh sách thả xuống) · Tình trạng mùa giải (vùng chỉ đọc) · Bảng Xếp hạng cá nhân (bảng: Hạng, Tên tay đua, Quốc tịch, Tên đội, Tổng điểm, Tổng thời gian) · Bảng Xếp hạng đội (bảng: Hạng, Tên đội, Hãng, Tổng điểm, Tổng thời gian).<br>4. Button: [Tiếp tục], [Về trang chủ].<br>5. Liên kết click được: từng dòng của hai bảng xếp hạng (mở màn Chi tiết theo chặng). |
| QTTG_3 | Kiểm tra màn Bảng tổng sắp khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| QTTG_4 | Kiểm tra thứ tự phím Tab màn Bảng tổng sắp | 1. Focus vào màn Bảng tổng sắp.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| QTTG_5 | Kiểm tra thứ tự phím Shift-Tab màn Bảng tổng sắp | 1. Focus vào màn Bảng tổng sắp.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| QTTG_6 | Kiểm tra phím Enter màn Bảng tổng sắp | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| | **Giao diện — màn Chi tiết theo chặng** | | |
| QTTG_7 | Kiểm tra tổng thể giao diện màn Chi tiết theo chặng | 1. Mở màn Chi tiết theo chặng.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| QTTG_8 | Kiểm tra bố cục màn Chi tiết theo chặng | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Chi tiết theo chặng — <tên tay đua hoặc tên đội>`.<br>2. Focus được đặt vào button [Quay lại] (màn chỉ đọc, không có ô nhập).<br>3. Hiển thị đầy đủ các trường: Tên đối tượng (vùng chỉ đọc) · Phạm vi dữ liệu (vùng chỉ đọc) · Bảng chi tiết từng chặng (4 cột với tay đua, 3 cột với đội).<br>4. Button: [Quay lại]. |
| QTTG_9 | Kiểm tra màn Chi tiết theo chặng khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| QTTG_10 | Kiểm tra thứ tự phím Tab màn Chi tiết theo chặng | 1. Focus vào màn Chi tiết theo chặng.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| QTTG_11 | Kiểm tra thứ tự phím Shift-Tab màn Chi tiết theo chặng | 1. Focus vào màn Chi tiết theo chặng.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| QTTG_12 | Kiểm tra phím Enter màn Chi tiết theo chặng | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| | **Giao diện — màn Trao giải** | | |
| QTTG_13 | Kiểm tra tổng thể giao diện màn Trao giải | 1. Mở màn Trao giải.<br>2. Kiểm tra bố cục, font chữ, cỡ chữ, màu chữ và chính tả. | Các label và ô nhập cùng font chữ, cỡ chữ; căn lề, độ rộng, khoảng cách đồng đều, không xô lệch; không có lỗi chính tả, cấu trúc câu, ngữ pháp trên màn hình; form được bố trí hợp lý và dễ sử dụng |
| QTTG_14 | Kiểm tra bố cục màn Trao giải | 1. Kiểm tra title của màn hình.<br>2. Kiểm tra focus của con trỏ.<br>3. Kiểm tra hiển thị các trường, button và liên kết trên màn hình. | 1. Hiển thị title `Trao giải mùa giải — FIA Formula One World Championship 2025`.<br>2. Focus được đặt vào ô "Giải cá nhân — Hạng 1".<br>3. Hiển thị đầy đủ các trường: Sáu ô nhập mức thưởng: cá nhân hạng 1/2/3 và đội hạng 1/2/3 (ô nhập) · Bảng Danh sách trao giải (bảng: Loại giải, Hạng, Tay đua/Đội, Tổng điểm, Tiền thưởng).<br>4. Button: [Tính thưởng], [Lưu], [Quay lại]. |
| QTTG_15 | Kiểm tra màn Trao giải khi thu nhỏ, phóng to | 1. Nhấn Ctrl -.<br>2. Nhấn Ctrl +. | Màn hình thu nhỏ, phóng to tương ứng và không bị vỡ giao diện; các bảng vẫn hiển thị đủ cột, không tràn ngang |
| QTTG_16 | Kiểm tra thứ tự phím Tab màn Trao giải | 1. Focus vào màn Trao giải.<br>2. Nhấn Tab liên tục. | Con trỏ di chuyển lần lượt theo thứ tự từ trái qua phải, từ trên xuống dưới, đi hết các trường nhập rồi tới các button |
| QTTG_17 | Kiểm tra thứ tự phím Shift-Tab màn Trao giải | 1. Focus vào màn Trao giải.<br>2. Nhấn Shift-Tab liên tục. | Con trỏ di chuyển ngược lại theo thứ tự từ dưới lên trên, từ phải qua trái |
| QTTG_18 | Kiểm tra phím Enter màn Trao giải | 1. Không focus vào button nào, nhấn Enter.<br>2. Focus vào một button, nhấn Enter. | 1. Thực hiện đúng chức năng của button chính của màn hình.<br>2. Thực hiện đúng chức năng của button đang được focus |
| | **Nhóm 2 — Chức năng** | | |
| QTTG_19 | Màn Bảng tổng sắp hiển thị đúng dữ liệu khi CSDL có dữ liệu | 1. CSDL như mục 7.9.1.<br>2. Mở màn Bảng tổng sắp, chọn chặng `Abu Dhabi`. | Bảng cá nhân đủ 12 dòng — danh sách **khớp** kết quả tổng hợp từ 72 bản ghi trong `tblKetQua` và 12 bản ghi trong `tblTayDua`; bảng đội đủ 6 dòng khớp 6 bản ghi trong `tblDoiDua`; tổng điểm 2 bảng đều bằng 606 = 101 điểm × 6 chặng |
| QTTG_20 | Màn Bảng tổng sắp — ca không có dữ liệu | 1. Sửa data test: `tblKetQua` rỗng (mùa chưa đua chặng nào).<br>2. Mở màn Bảng tổng sắp. | Hai bảng xếp hạng không có dòng nào, hiển thị thông báo `Mùa giải chưa có kết quả chặng nào`; nút [Tiếp tục] **không active**; `tblTraoGiai` không phát sinh bản ghi |
| QTTG_21 | Màn Chi tiết theo chặng hiển thị đúng dữ liệu tay đua | 1. CSDL như mục 7.9.1.<br>2. Chọn chặng `Abu Dhabi`, click dòng `Max Verstappen`. | Bảng chi tiết đủ 6 dòng — **khớp** 6 bản ghi của Verstappen trong `tblKetQua`; dòng đầu `Australian Grand Prix \| 2 \| 18 \| 1:28:06.334` (= 5286.334 giây); tổng cột Điểm của 6 dòng = 119 đúng bằng Tổng điểm trên bảng tổng sắp |
| QTTG_22 | Màn Chi tiết theo chặng hiển thị đúng dữ liệu đội và phạm vi chặng | 1. CSDL như mục 7.9.1.<br>2. Chọn chặng `Abu Dhabi`, click dòng đội `McLaren`.<br>3. Quay lại, chọn chặng `R01 Melbourne`, click lại dòng `McLaren`. | Bước 2: bảng chi tiết đội đủ 6 dòng cột `Tên chặng \| Tổng điểm \| Tổng thời gian của 2 tay đua`, dòng đầu `Australian Grand Prix \| 35 \| 2:56:36.414` (NOR 25 + PIA 10; 5284.512 + 5311.902 giây), tổng điểm 6 dòng = 214. Bước 3: bảng chỉ còn **1 dòng** (phạm vi tính đến chặng R01); đối tượng không có kết quả trong phạm vi lọc hiển thị `Không có dữ liệu` |
| QTTG_23 | Màn Trao giải hiển thị đúng danh sách top 3 | 1. CSDL như mục 7.9.1.<br>2. Chọn chặng cuối, click [Tiếp tục]. | Bảng Danh sách trao giải đúng 6 dòng khớp kết quả tổng hợp từ `tblKetQua`: `Cá nhân \| 1 \| Lando Norris \| 119`, `Cá nhân \| 2 \| Max Verstappen \| 119`, `Cá nhân \| 3 \| Oscar Piastri \| 95`, `Đội \| 1 \| McLaren \| 214`, `Đội \| 2 \| Ferrari \| 132`, `Đội \| 3 \| Red Bull \| 121`; từ hạng 4 trở xuống (`Charles Leclerc`, đội `Mercedes`) **không** xuất hiện |
| QTTG_24 | Màn Trao giải — ca chưa có dữ liệu trao giải | 1. CSDL như mục 7.9.1 (`tblTraoGiai` rỗng).<br>2. Mở màn Trao giải. | Cột Tiền thưởng của cả 6 dòng **rỗng**, 6 ô nhập mức thưởng rỗng, nút [Lưu] **chưa active** (khớp `tblTraoGiai` chưa có bản ghi nào của mùa giải) |
| | **Nhóm 3 — Luồng nghiệp vụ** | | |
| QTTG_25 | Quyết toán mùa giải đủ kết quả — luồng chuẩn end-to-end | 1. Click "Quyết toán mùa giải" trên trang chính.<br>2. Chọn chặng `Abu Dhabi` (chặng cuối) từ danh sách.<br>3. Đối chiếu bảng cá nhân: `1 \| Lando Norris \| Anh \| McLaren \| 119 \| 9:03:19.885`; `2 \| Max Verstappen \| Hà Lan \| Red Bull \| 119 \| 9:03:12.418`; `3 \| Oscar Piastri \| 95`; `4 \| Charles Leclerc \| 76`; `5 \| George Russell \| 63`; `6 \| Lewis Hamilton \| 56`; `7 \| Antonelli \| 30`; `8 \| Albon \| 21`; `9 \| Alonso \| 20`; `10 \| Sainz \| 4`; `11 \| Tsunoda \| 2`; `12 \| Stroll \| 1`.<br>4. Đối chiếu bảng đội: `McLaren 214, Ferrari 132, Red Bull 121, Mercedes 93, Williams 25, Aston Martin 21`.<br>5. Click [Tiếp tục]; nhập mức thưởng cá nhân `5.000.000.000 / 3.000.000.000 / 2.000.000.000`, đội `20.000.000.000 / 12.000.000.000 / 8.000.000.000`; click [Tính thưởng].<br>6. Click [Lưu], click OK ở thông báo. | Hai bảng xếp hạng đúng thứ tự như bước 3–4; cột Tiền thưởng điền đúng 6 dòng, [Lưu] chuyển active; thông báo `Đã lưu quyết định trao giải mùa giải FIA Formula One World Championship 2025` rồi quay về trang chính. **Hiệu ứng CSDL:** `tblTraoGiai` thêm đúng 6 bản ghi mới `(CaNhan, NOR, hang 1, 5.000.000.000)`, `(CaNhan, VER, 2, 3.000.000.000)`, `(CaNhan, PIA, 3, 2.000.000.000)`, `(Doi, MCL, 1, 20.000.000.000)`, `(Doi, FER, 2, 12.000.000.000)`, `(Doi, RBR, 3, 8.000.000.000)`; các bảng khác giữ nguyên |
| QTTG_26 | Bằng tổng điểm → phân định bằng countback (tầng 2) | 1. Mở màn Bảng tổng sắp, chọn chặng `Abu Dhabi`.<br>2. Đối chiếu 2 dòng đầu bảng cá nhân: Norris và Verstappen cùng **119** điểm; theo `tblKetQua`, Norris có 3 lần hạng 1 (R01, R10, R16), Verstappen có 2 lần (R06, R24). | `1 \| Lando Norris \| 119 \| 9:03:19.885`; `2 \| Max Verstappen \| 119 \| 9:03:12.418` — Norris xếp trên nhờ countback (3 lần về nhất so với 2) **dù tổng thời gian của Norris lớn hơn** ⇒ tầng 3 tổng thời gian chưa được dùng khi countback đã phân định; kèm chú thích `Phân định bằng countback (số lần về nhất)`. CSDL không thay đổi |
| QTTG_27 | Countback vẫn bằng → phân định bằng tổng thời gian tăng dần (tầng 3) | 1. Sửa data test: mùa rút gọn còn 2 chặng `R01 Melbourne`, `R02 Thượng Hải`; `tblKetQua` sửa chặng R02: Verstappen hạng 1 (`thoiGian = 5430.000` giây), Norris hạng 2 (`5433.906` giây); chặng R01 giữ nguyên: Norris hạng 1 (`5284.512`), Verstappen hạng 2 (`5286.334`).<br>2. Mở màn Bảng tổng sắp, chọn chặng `R02` (chặng cuối của mùa rút gọn).<br>3. Đối chiếu 2 dòng đầu bảng cá nhân. | Norris và Verstappen cùng **43** điểm (25 + 18), cùng 1 lần hạng 1 và 1 lần hạng 2 ⇒ countback không phân định ⇒ so **tổng thời gian tăng dần**: Verstappen 10716.334 giây (`2:58:36.334`) nhỏ hơn Norris 10718.418 giây (`2:58:38.418`) ⇒ `1 \| Max Verstappen \| 43 \| 2:58:36.334`; `2 \| Lando Norris \| 43 \| 2:58:38.418`. CSDL không thay đổi |
| QTTG_28 | Drill-down xem chi tiết theo chặng của tay đua và đội | 1. Mở màn Bảng tổng sắp, chọn chặng `Abu Dhabi`.<br>2. Click dòng `Max Verstappen`.<br>3. Click [Quay lại].<br>4. Click dòng đội `McLaren`.<br>5. Click [Quay lại]. | Bước 2: màn Chi tiết `Max Verstappen — Red Bull`, 6 dòng khớp `tblKetQua` (dòng đầu `Australian Grand Prix \| 2 \| 18 \| 1:28:06.334`, cột Điểm cộng lại = 119). Bước 3: về màn Bảng tổng sắp, chặng đang chọn giữ nguyên. Bước 4: màn Chi tiết `McLaren — Mercedes` với cột `Tên chặng \| Tổng điểm \| Tổng thời gian của 2 tay đua`, 6 dòng (dòng đầu `Australian Grand Prix \| 35 \| 2:56:36.414`), tổng điểm = 214. Bước 5: về màn Bảng tổng sắp. CSDL không thay đổi |
| QTTG_29 | Tính tiền thưởng: kiểm tra ràng buộc và tính lại nhiều lần | 1. Vào màn Trao giải (qua QTTG_25 bước 1–5, chưa nhập mức thưởng).<br>2. Bỏ trống cả 6 ô, click [Tính thưởng].<br>3. Nhập mức thưởng cá nhân hạng 1 = `-5.000.000`, click [Tính thưởng].<br>4. Nhập đủ 6 mức như QTTG_25 bước 5, click [Tính thưởng].<br>5. Sửa cá nhân hạng 1 thành `6.000.000.000`, click [Tính thưởng] lần 2.<br>6. Click [Lưu], click OK. | Bước 2, 3: báo `Mức thưởng phải là số không âm`, cột Tiền thưởng rỗng, [Lưu] **chưa active**. Bước 4: 6 dòng điền đúng tiền thưởng theo hạng và loại giải, [Lưu] active; hạng 4 trở xuống không được tính. Bước 5: dòng Norris cập nhật `6.000.000.000`, 5 dòng còn lại giữ nguyên. **Hiệu ứng CSDL:** `tblTraoGiai` có 6 bản ghi mới theo lần tính **cuối cùng** — dòng `(CaNhan, NOR, 1)` có `tienThuong = 6.000.000.000` |
| QTTG_30 | Tay đua đổi đội giữa mùa → điểm đội cộng theo đội tại thời điểm chặng | 1. Sửa data test: mùa rút gọn còn 2 chặng `R01 Melbourne`, `R06 Monaco`; `tblDangKyChang` sửa: Hamilton đăng ký cho **Mercedes** ở R01 (`tblDoiDuaid = 4`) và cho **Ferrari** ở R06 (`tblDoiDuaid = 1`); kết quả 2 chặng giữ nguyên cột R01, R06 của ma trận điểm (Hamilton hạng 6 = 8 điểm ở R01, hạng 5 = 10 điểm ở R06); hợp đồng hiệu lực hiện tại của Hamilton là Ferrari.<br>2. Mở màn Bảng tổng sắp, chọn chặng `R06` (chặng cuối của mùa rút gọn).<br>3. Kiểm tra dòng Hamilton ở bảng cá nhân.<br>4. Kiểm tra điểm đội Mercedes và Ferrari ở bảng đội.<br>5. Click [Tiếp tục], nhập mức thưởng như QTTG_25, click [Tính thưởng], click [Lưu]. | Bước 3: `Lewis Hamilton \| Anh \| Ferrari \| 18` (8 + 10; cột Tên đội hiển thị đội hiện tại). Bước 4: **Mercedes = 39** = RUS (15 + 8) + ANT (6 + 2) + Hamilton tại R01 (8); **Ferrari = 37** = LEC (12 + 15) + Hamilton tại R06 (10) — điểm cộng theo `tblDangKyChang.tblDoiDuaid` (đội tại thời điểm chặng), không cộng cả 18 điểm cho Ferrari; tổng 6 đội = 202 = 101 × 2 chặng (không mất, không nhân đôi). **Hiệu ứng CSDL:** `tblTraoGiai` thêm 6 bản ghi mới theo bảng xếp hạng của mùa rút gọn |

> Nhóm Giao diện 6 ca (2 ca/màn × 3 màn), nhóm Chức năng 6 ca (2 ca/màn), nhóm Luồng nghiệp vụ 6 ca — tổng 18 ca, mã `QTTG_1`–`QTTG_30`. Bộ test case kiểm chứng đủ: luồng chuẩn, tie-break 3 tầng (countback tầng 2 — `QTTG_26`, tổng thời gian tầng 3 — `QTTG_27`), drill-down (`QTTG_28`), tính thưởng (`QTTG_29`) và ràng buộc quan trọng nhất của module — điểm đội cộng dồn theo đội tại thời điểm chặng (`QTTG_30`).

---

## CHƯƠNG 8: KẾT LUẬN

Nhóm đã phân tích và thiết kế hệ thống Quản lý giải đua xe F1 với 4 module nghiệp vụ, mỗi module có ràng buộc và xử lý riêng: kiểm tra chồng lấn hợp đồng và tự động đóng hợp đồng cũ (Module 1), giới hạn 2 tay đua/đội/chặng (Module 2), xếp hạng và tính điểm theo luật F1 với ba trạng thái Hoàn thành / DNF / DSQ (Module 3), và quyết toán trao giải với điều kiện đủ kết quả, xem bảng xếp hạng tính đến chặng bất kỳ kèm drill-down chi tiết theo chặng, cùng quy tắc xếp hạng ba tầng: tổng điểm giảm dần → countback → tổng thời gian tăng dần (Module 4).

Các sản phẩm đã hoàn thành gồm: mô tả yêu cầu bài toán theo ngôn ngữ tự nhiên (phạm vi hệ thống, nghiệp vụ 11 chức năng, đối tượng và thuộc tính, quan hệ số lượng, ràng buộc nghiệp vụ); mô tả yêu cầu phần mềm (actor, bảng use case, yêu cầu chức năng, yêu cầu phi chức năng, biểu đồ use case tổng quát); biểu đồ lớp thực thể ở cả hai pha phân tích và thiết kế kèm bảng trích danh từ, thiết kế cơ sở dữ liệu 12 bảng và biểu đồ package triển khai; và với mỗi thành viên là bộ tài liệu đầy đủ cho một use case (biểu đồ use case chi tiết, đặc tả use case kèm giao diện phác thảo, biểu đồ trạng thái phân tích hoạt động, biểu đồ lớp phân tích, biểu đồ lớp thiết kế, biểu đồ hoạt động pha thiết kế, thuyết minh kịch bản kèm biểu đồ tuần tự, và test case\).

**Hướng phát triển:** bổ sung chức năng quản lý danh mục đầy đủ, thống kê theo mùa giải, và triển khai mã nguồn theo kiến trúc phân tầng view (`.jsp`) / dao / model đã thiết kế.
