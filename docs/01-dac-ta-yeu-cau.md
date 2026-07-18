# Đặc tả yêu cầu phần mềm — Quản lý giải đua xe F1

> Sản phẩm chung của nhóm (mục 2 trong kế hoạch). Nguồn: đề bài [../project10-F1-4modules.md](../project10-F1-4modules.md).

## 1. Giới thiệu

Hệ thống quản lý một giải vô địch đua xe F1 diễn ra hằng năm: quản lý các chặng đua, đội đua, tay đua; quản lý hợp đồng tay đua với đội; đăng ký tay đua tham gia từng chặng; nhập kết quả và tính điểm mỗi chặng; và quyết toán trao giải cá nhân/đồng đội cuối mùa.

## 2. Phạm vi & người dùng

| Người dùng (actor) | Được thực hiện |
|---|---|
| **Thành viên** (chung) | Đăng nhập, đổi mật khẩu |
| **Nhân viên** | Ký hợp đồng tay đua (M1), đăng ký tay đua vào chặng (M2), cập nhật kết quả chặng (M3); quản lý danh mục (mùa giải, tay đua, đội, chặng); đăng ký đội tham gia mùa giải |
| **Quản lý** | Quyết toán và trao giải cuối mùa (M4) |

Nhân viên và Quản lý đều kế thừa các chức năng của Thành viên.

## 3. Yêu cầu chức năng

### FR0 — Xác thực & tài khoản (chung)
- FR0.1 Đăng nhập bằng tài khoản (tên đăng nhập, mật khẩu).
- FR0.2 Đổi mật khẩu cá nhân.
- FR0.3 Phân quyền theo vai trò: **Nhân viên** (M1/M2/M3 + danh mục), **Quản lý** (M4).

### FR1 — Quản lý danh mục (chung, hỗ trợ)
- FR1.1 Thêm/sửa/xóa **tay đua** (mã, tên, ngày sinh, quốc tịch, tiểu sử).
- FR1.2 Thêm/sửa/xóa **đội đua** (mã, tên, hãng, mô tả).
- FR1.3 Thêm/sửa/xóa **chặng đua** (mã, tên, số vòng, địa điểm, thời gian, mô tả) thuộc một mùa giải.
- FR1.4 Thêm/sửa/xóa **mùa giải** (năm, tên giải, mô tả).
- FR1.5 **Đăng ký đội tham gia mùa giải**: chọn mùa giải + chọn đội đua tham gia (sinh bản ghi `ThamGia`).

### FR2 — Ký hợp đồng tay đua với đội đua (Module 1)
- FR2.1 Tìm tay đua theo tên; hiển thị danh sách hợp đồng cũ.
- FR2.2 Ký hợp đồng mới: chọn đội, **chỉ nhập ngày bắt đầu hiệu lực** (ngày kết thúc để trống = hợp đồng đang hiệu lực).
- FR2.3 **Ràng buộc (tại một thời điểm tay đua chỉ thuộc 1 đội):** (a) nếu tay đua còn hợp đồng đang hiệu lực → hệ thống **tự động đóng** hợp đồng cũ (đặt ngày kết thúc = ngày liền trước ngày bắt đầu mới), không báo lỗi; (b) nếu ngày bắt đầu mới **chồng lấn khoảng thời gian của hợp đồng đã đóng** (lịch sử) → báo lỗi, yêu cầu nhập lại.
- FR2.4 Lưu và in hợp đồng.

### FR3 — Đăng ký tay đua tham gia chặng đua (Module 2)
- FR3.1 Chọn chặng đua và đội đua.
- FR3.2 Hiển thị danh sách tay đua đang có hợp đồng hiệu lực với đội tại thời điểm chặng, **sắp xếp theo alphabet của tên**, kèm **cột trạng thái** "đã đăng ký chặng này cho đội khác hay chưa".
- FR3.3 Tick chọn tay đua đăng ký.
- FR3.4 **Ràng buộc:** mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ đăng ký 1 lần trong chặng.
- FR3.5 Lưu và in phiếu đăng ký (danh sách xuất phát).
- FR3.6 **Chỉnh sửa đăng ký trước ngày đua**: mở lại chặng + đội, thay tay đua đã đăng ký (bỏ/tick lại), hệ thống kiểm tra lại ràng buộc FR3.4 rồi lưu.

### FR4 — Cập nhật kết quả và tính điểm chặng (Module 3)
- FR4.1 Chọn chặng; hiển thị bảng tay đua đã đăng ký để nhập thời gian về đích, số vòng, cờ DNF.
- FR4.2 **Tính điểm:** xếp hạng theo thời gian về đích; gán điểm top 10 = 25/18/15/12/10/8/6/4/2/1; tay đua DNF nhận 0 điểm.
- FR4.3 Lưu kết quả + điểm và in bảng kết quả chặng.

### FR5 — Quyết toán và trao giải cuối mùa (Module 4)
- FR5.1 **Ràng buộc:** chỉ quyết toán khi tất cả chặng trong mùa đã có kết quả.
- FR5.2 Cộng dồn điểm và thời gian từng tay đua và từng đội qua tất cả chặng; xếp hạng cá nhân và đội (giảm dần tổng điểm, bằng điểm thì tăng dần tổng thời gian).
- FR5.3 Nhập mức thưởng theo hạng; tính tiền thưởng cho từng tay đua/đội.
- FR5.4 Lưu quyết định trao giải và in danh sách trao giải.

## 4. Yêu cầu phi chức năng

| # | Loại | Yêu cầu |
|---|---|---|
| NFR1 | Bảo mật | Đăng nhập bằng tài khoản; phân quyền theo vai trò (Nhân viên/Quản lý). |
| NFR2 | Tính đúng đắn | Các phép tính điểm, xếp hạng, tiền thưởng phải chính xác theo luật F1 trong đề bài. |
| NFR3 | Toàn vẹn dữ liệu | Kiểm tra ràng buộc (chồng lấn hợp đồng, ≤2 tay đua/đội/chặng, đủ kết quả trước khi quyết toán) trước khi lưu. |
| NFR4 | Khả dụng | Giao diện tiếng Việt, thao tác tìm kiếm → chọn → lưu rõ ràng; thông báo lỗi cụ thể khi vi phạm ràng buộc. |
| NFR5 | Hiệu năng | Danh sách (tay đua, kết quả, xếp hạng) hiển thị < 2 giây với quy mô một mùa giải. |
| NFR6 | Khả bảo trì | Kiến trúc phân tầng (giao diện / xử lý / dữ liệu — MVC) để dễ mở rộng. |
| NFR7 | Khả chuyển | Chạy trên trình duyệt web thông dụng. |
