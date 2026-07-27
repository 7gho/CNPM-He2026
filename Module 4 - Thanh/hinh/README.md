# Thư mục ảnh — Module 4

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 4 cần đúng **9 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m4-uc-chitiet.png` | UC chi tiết (mục 1) | đã có — **phải vẽ lại**: thêm UC con `Đăng nhập` (include) và `Xem chi tiết theo chặng` (extend từ `Xem bảng tổng sắp`) |
| `m4-trangthai.png` | Biểu đồ trạng thái (mục 3) | chưa có — **mới**, vẽ theo mẫu Hình 3.9/3.11 giáo trình PDF, bắt đầu từ trạng thái "Hiển thị GD chính QL" |
| `m4-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) | chưa có — có thêm `GDChinhQL`, `GDChiTietXepHang`; `KetQua` thêm `sapXepBangXepHang`, `getChiTietTheoTayDua`, `getChiTietTheoDoi` |
| `m4-giaodien-xephang.png` | Giao diện Bảng tổng sắp (mục 5) | chưa có — có danh sách chọn chặng, cột bảng đúng đề gốc, từng dòng click được |
| `m4-giaodien-chitietxephang.png` | Giao diện Chi tiết theo chặng (mục 5) | chưa có — **mới** (màn drill-down theo đề gốc) |
| `m4-giaodien-traogiai.png` | Giao diện Trao giải (mục 5) | chưa có |
| `m4-lop-mvc.png` | Biểu đồ lớp thiết kế view / DAO / model (mục 6) | đã có — **phải vẽ lại** theo mẫu Hình 4.4: view có thuộc tính kèm kiểu control + thuộc tính ẩn, DAO có constructor + chữ ký đầy đủ, thêm `gdChinhQL.jsp`, `gdChiTietXepHang.jsp` |
| `m4-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mục 7) | đã có — **phải vẽ lại** theo mẫu Hình 4.9: khung "Xử lí tại gdXxx.jsp" cho từng trang, node gọi DAO ghi `XxxDAO: tenHam()` |
| `m4-tuantu.png` | Biểu đồ tuần tự (mục 8) | đã có — **phải vẽ lại** theo mẫu Hình 4.10/4.12: trang chính mở đầu + kết thúc, nhánh drill-down, luồng lưu dùng `setter()`, đánh số message |

> Ảnh `m4-giaodien-quyettoan.png` cũ (một màn duy nhất) bị thay bằng **3 ảnh giao diện** `m4-giaodien-xephang.png`, `m4-giaodien-chitietxephang.png`, `m4-giaodien-traogiai.png`, khớp 1-1 với 3 màn hình hiển thị và 3 lớp biên nghiệp vụ (trang chính `gdChinhQL.jsp` là trang chủ chung, không cần mockup riêng).
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.
