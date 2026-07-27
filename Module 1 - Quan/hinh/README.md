# Thư mục ảnh — Module 1

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 1 cần đúng **6 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m1-uc-chitiet.png` | UC chi tiết (mục 1) | đã có — **phải vẽ lại**: thêm UC con `Đăng nhập` (include), system boundary, `Thêm tay đua ..> Tìm tay đua : extend`, actor nối UC bằng đường kẻ trơn |
| `m1-trangthai.png` | Biểu đồ trạng thái (mục 3) | chưa có — vẽ theo mẫu Hình 3.9/3.11 giáo trình PDF (nhãn cung `[hành động]`) |
| `m1-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) | chưa có — có lớp biên trang chính `GDChinhNV` |
| `m1-lop-mvc.png` | Biểu đồ lớp thiết kế view / DAO / model (mục 5) | chưa có — vẽ theo mẫu Hình 4.4 (view có kiểu control + thuộc tính ẩn, DAO có constructor + chữ ký đầy đủ) |
| `m1-hoatdong.png` | Biểu đồ hoạt động pha thiết kế (mục 6) | đã có — **phải vẽ lại** theo mẫu Hình 4.9 (khung "Xử lí tại gdXxx.jsp", node DAO ghi rõ tên hàm; khung `gdChinhNV.jsp` xuất hiện ở đầu và cuối — quay về trang chính sau khi click OK) |
| `m1-tuantu.png` | Biểu đồ tuần tự (mục 7) | chưa có — vẽ theo mẫu Hình 4.10/4.12 (đánh số message, trang chính mở đầu + kết thúc, luồng lưu có `setter()`) |

> Giao diện **không cần vẽ và không cần xuất ảnh** — Module 1 có 2 màn hình hiển thị riêng, đã trình bày dạng phác thảo (khung bố cục + bảng dữ liệu mẫu) trong mục 2.2 của `../noi-dung.md`. Trang `doLuuHopDong.jsp` là trang xử lý, không phải màn hình hiển thị. Trang chính `gdChinhNV.jsp` là trang chủ chung của hệ thống; giao diện đăng nhập (UC con `Đăng nhập`) dùng chung toàn hệ thống, không phác thảo trong module.
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.
