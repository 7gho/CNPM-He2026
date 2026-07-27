# Thư mục ảnh — Module 1

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 1 cần đúng **8 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m1-uc-chitiet.png` | UC chi tiết (mục 1) | đã có — **phải vẽ lại**: thêm UC con `Đăng nhập` (include), system boundary, `Thêm tay đua ..> Tìm tay đua : extend`, actor nối UC bằng đường kẻ trơn |
| `m1-trangthai.png` | Biểu đồ trạng thái (mục 3) | chưa có — vẽ theo mẫu Hình 3.9/3.11 giáo trình PDF (nhãn cung `[hành động]`) |
| `m1-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) | chưa có — có lớp biên trang chính `GDChinhNV` |
| `m1-giaodien-timtaydua.png` | Giao diện màn 1 — Tìm tay đua (mục 5) | chưa có |
| `m1-giaodien-nhaphopdong.png` | Giao diện màn 2 — Nhập hợp đồng (mục 5) | chưa có |
| `m1-lop-mvc.png` | Biểu đồ lớp thiết kế view / DAO / model (mục 6) | chưa có — vẽ theo mẫu Hình 4.4 (view có kiểu control + thuộc tính ẩn, DAO có constructor + chữ ký đầy đủ) |
| `m1-hoatdong.png` | Biểu đồ hoạt động pha thiết kế (mục 7) | đã có — **phải vẽ lại** theo mẫu Hình 4.9 (khung "Xử lí tại gdXxx.jsp", node DAO ghi rõ tên hàm; khung `gdChinhNV.jsp` xuất hiện ở đầu và cuối — quay về trang chính sau khi click OK) |
| `m1-tuantu.png` | Biểu đồ tuần tự (mục 8) | chưa có — vẽ theo mẫu Hình 4.10/4.12 (đánh số message, trang chính mở đầu + kết thúc, luồng lưu có `setter()`) |

> Module 1 có 2 màn hình hiển thị riêng ⇒ 2 ảnh giao diện. Trang `doLuuHopDong.jsp` là trang xử lý, không có ảnh giao diện. Trang chính `gdChinhNV.jsp` là trang chủ chung của hệ thống, không cần mockup riêng; giao diện đăng nhập (UC con `Đăng nhập`) dùng chung toàn hệ thống, không vẽ trong module.
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.
