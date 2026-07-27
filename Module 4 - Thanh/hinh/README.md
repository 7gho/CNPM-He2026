# Thư mục ảnh — Module 4

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 4 cần đúng **6 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m4-uc-chitiet.png` | UC chi tiết (mục 1) | đã có — **phải vẽ lại**: thêm UC con `Đăng nhập` (include) và `Xem chi tiết theo chặng` (extend từ `Xem bảng tổng sắp`) |
| `m4-trangthai.png` | Biểu đồ trạng thái (mục 3) | chưa có — **mới**, vẽ theo mẫu Hình 3.9/3.11 giáo trình PDF, bắt đầu từ trạng thái "Hiển thị GD chính QL" |
| `m4-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) | chưa có — có thêm `GDChinhQL`, `GDChiTietXepHang`; `KetQua` thêm `sapXepBangXepHang`, `getChiTietTheoTayDua`, `getChiTietTheoDoi` |
| `m4-lop-mvc.png` | Biểu đồ lớp thiết kế view / DAO / model (mục 5) | đã có — **phải vẽ lại** theo mẫu Hình 4.4: view có thuộc tính kèm kiểu control + thuộc tính ẩn, DAO có constructor + chữ ký đầy đủ, thêm `gdChinhQL.jsp`, `gdChiTietXepHang.jsp` |
| `m4-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mục 6) | đã có — **phải vẽ lại** theo mẫu Hình 4.9: khung "Xử lí tại gdXxx.jsp" cho từng trang, node gọi DAO ghi `XxxDAO: tenHam()` |
| `m4-tuantu.png` | Biểu đồ tuần tự (mục 7) | đã có — **phải vẽ lại** theo mẫu Hình 4.10/4.12: trang chính mở đầu + kết thúc, nhánh drill-down, luồng lưu dùng `setter()`, đánh số message |

> Giao diện **không cần vẽ và không cần xuất ảnh**: nhóm chốt trình bày giao diện ở mức phác thảo (khung bố cục + bảng dữ liệu mẫu) ngay trong mục 2.2 của [../noi-dung.md](../noi-dung.md).
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.
