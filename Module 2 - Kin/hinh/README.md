# Thư mục ảnh — Module 2

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 2 cần đúng **8 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m2-uc-chitiet.png` | Biểu đồ UC chi tiết (mục 1) | đã có — **phải vẽ lại**: thêm UC con `Đăng nhập` (include) + 2 UC con `Chọn chặng và đội`, `Chọn tay đua đăng ký`, system boundary, actor nối UC bằng đường kẻ trơn |
| `m2-trangthai.png` | Biểu đồ trạng thái (mục 3) | chưa có — vẽ theo mẫu **Hình 3.9/3.11** giáo trình PDF (nhãn cung `[hành động]`) |
| `m2-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) | chưa có — có thêm lớp biên trang chính `GDChinhNV` |
| `m2-giaodien-chonchangdoi.png` | Giao diện màn hình Chọn chặng và đội (mục 5) | chưa có |
| `m2-giaodien-dangkytaydua.png` | Giao diện màn hình Đăng ký tay đua (mục 5) | chưa có |
| `m2-lop-mvc.png` | Biểu đồ lớp thiết kế (jsp / DAO / model) (mục 6) | chưa có — vẽ theo mẫu **Hình 4.4** (view có kiểu control + thuộc tính ẩn, DAO có constructor + chữ ký đầy đủ) |
| `m2-hoatdong.png` | Biểu đồ hoạt động pha thiết kế (mục 7) | chưa có — vẽ theo mẫu **Hình 4.9** (khung "Xử lí tại gdXxx.jsp" cho từng trang) |
| `m2-tuantu.png` | Biểu đồ tuần tự (mục 8) | chưa có — vẽ theo mẫu **Hình 4.10/4.12** (trang chính mở đầu + kết thúc, luồng lưu có `setter()`, đánh số message) |

> Module 2 có 2 màn hình hiển thị nên có 2 ảnh giao diện. Tên cũ `m2-giaodien-dangky.png` không dùng nữa. Trang chính `gdChinhNV.jsp` là trang chủ chung của hệ thống, không cần mockup riêng.
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.
