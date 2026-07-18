# Đặc tả UC gọn — Danh mục & Xác thực

> Các use case **hỗ trợ** (không phải 4 module được phân công). Chỉ cần đặc tả UC gọn (không cần đủ 6 biểu đồ như 4 module chính). Truy vết: đề bài (thuộc tính từng thực thể) + docs/03.

## 1. Đăng nhập / Đổi mật khẩu (actor: ThanhVien)

| Mục | Đăng nhập | Đổi mật khẩu |
|---|---|---|
| Tiền điều kiện | Có tài khoản trong `tblThanhVien` | Đã đăng nhập |
| Kịch bản chính | Nhập tên đăng nhập + mật khẩu → hệ thống kiểm tra → đúng thì vào hệ thống theo vai trò (NhanVien/QuanLy) | Nhập mật khẩu cũ + mật khẩu mới → hệ thống kiểm tra mật khẩu cũ → lưu mật khẩu mới |
| Ngoại lệ | Sai tên đăng nhập/mật khẩu → báo lỗi | Mật khẩu cũ sai → báo lỗi |
| Hậu điều kiện | Phiên đăng nhập được tạo, phân quyền theo `vaiTro` | Mật khẩu được cập nhật |

## 2. Quản lý danh mục — CRUD chuẩn (actor: NhanVien)

Áp dụng chung cho 4 danh mục: **Mùa giải**, **Tay đua**, **Đội đua**, **Chặng đua**.

| Mục | Nội dung |
|---|---|
| Use case | Quản lý &lt;đối tượng&gt; (thêm / sửa / xóa / tìm) |
| Actor | Nhân viên |
| Tiền điều kiện | Đã đăng nhập |
| Kịch bản chính | Chọn menu quản lý &lt;đối tượng&gt; → tìm theo tên → hệ thống hiển thị danh sách → chọn **Thêm** (nhập thuộc tính, lưu) / **Sửa** (chọn dòng, sửa, lưu) / **Xóa** (chọn dòng, xác nhận, xóa) |
| Thuộc tính | Mùa giải: năm, tên giải, mô tả · Tay đua: mã, tên, ngày sinh, quốc tịch, tiểu sử · Đội đua: mã, tên, hãng, mô tả · Chặng đua: mã, tên, số vòng, địa điểm, thời gian, mô tả (+ thuộc mùa giải) |
| Ngoại lệ | Xóa đối tượng đang được tham chiếu (vd chặng đã có kết quả) → chặn, báo lỗi |

## 3. Đăng ký đội tham gia mùa giải (actor: NhanVien)

| Mục | Nội dung |
|---|---|
| Use case | Đăng ký đội tham gia mùa giải |
| Actor | Nhân viên |
| Tiền điều kiện | Đã đăng nhập; đã có mùa giải và đội đua trong danh mục |
| Kịch bản chính | Chọn menu đăng ký đội tham gia → chọn mùa giải → hệ thống hiển thị danh sách đội chưa tham gia mùa → tick chọn các đội → Lưu → hệ thống sinh bản ghi `ThamGia` cho từng đội |
| Ràng buộc | Một đội chỉ tham gia một mùa giải một lần (không trùng trong `tblThamGia`) |
| Hậu điều kiện | Các bản ghi `ThamGia` (mùa giải ↔ đội) được lưu — làm nguồn dữ liệu cho đội tham gia ở các module nghiệp vụ |
