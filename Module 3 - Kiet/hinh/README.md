# Thư mục ảnh — Module 3

Để ảnh biểu đồ export từ Visual Paradigm vào đây (PNG). Tên file theo bảng "Danh sách ảnh cần export" ở đầu [../noi-dung.md](../noi-dung.md).

Module 3 cần đúng **6 ảnh**:

| Tên file | Biểu đồ | Trạng thái |
|---|---|---|
| `m3-uc-chitiet.png` | Biểu đồ UC chi tiết (mục 1) | có ảnh — **vẽ lại** |
| `m3-trangthai.png` | Biểu đồ trạng thái — phân tích hoạt động (mục 3, mẫu Hình 3.9/3.11) | chưa có |
| `m3-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4, mẫu Hình 3.6) | có ảnh — **sửa lại** |
| `m3-lop-mvc.png` | Biểu đồ lớp thiết kế (jsp / DAO / model) (mục 5, mẫu Hình 4.4) | có ảnh — **vẽ lại** |
| `m3-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mục 6, mẫu Hình 4.9) | có ảnh — **vẽ lại** |
| `m3-tuantu.png` | Biểu đồ tuần tự (mục 7, mẫu Hình 4.10/4.12) | chưa có |

> Giao diện **không cần vẽ và không cần xuất ảnh** — đã trình bày dạng bảng phác thảo xen giữa các bước Kịch bản chính ở mục 2 của `../noi-dung.md`. Vì vậy `m3-giaodien-nhapketqua.png` không dùng đến.
>
> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`. Bảng trạng thái này phải khớp với `docs/00-ke-hoach-va-phan-cong.md` mục 7.

## Việc cần sửa ở các ảnh đã vẽ

Bản render tham chiếu của từng biểu đồ theo blueprint hiện tại nằm ở `ref/` — mở ra đối chiếu khi vẽ.

**Điểm chung của cả bộ:** hệ thống nhóm chốt là **ứng dụng web chạy trên nền JSP**, không phải ứng dụng desktop. Vì vậy trong mọi biểu đồ không dùng `ActionListener`, `JButton`, `JTable`, `JTextField`, `JCombobox`; lớp giao diện là **trang `.jsp` chỉ có thuộc tính**, kiểu thuộc tính là `Text` / `Select` / `Table` / `link` / `submit`.

### `m3-lop-phantich.png` — sửa, giữ được phần lớn bố cục

| Cần sửa | Hiện tại | Đúng phải là |
|---|---|---|
| Tên lớp biên | `gdChang`, `gdChangChiTiet`, `gdNhanVien`, `gdLogin` | `GDChinhNV`, `GDChonChang`, `GDNhapKetQua` — viết hoa `GD`, một lớp cho mỗi màn hình của module; bỏ `gdLogin` (đăng nhập dùng chung, không sinh lớp biên) |
| Thuộc tính `-id` ở lớp thực thể | có | **bỏ** — pha phân tích không có `id`, không có kiểu dữ liệu |
| Lớp `KetQua` | `-dnf`, `-dnq` (hai cờ boolean) | một thuộc tính `-trangThai` nhận `Hoàn thành` / `DNF` / `DSQ` |
| Lớp `NhanVien` | có `-vaiTro`, `+checkLogin()` | `NhanVien` kế thừa lớp trừu tượng `ThanhVien` (đủ 3 thuộc tính `tenDangNhap`, `matKhau`, `hoTen`), không có `-vaiTro` |
| Phương thức nghiệp vụ | chưa có | gán cho lớp thực thể: `MuaGiai.getMuaGiaiHienTai()`, `ChangDua.getDSChangDua()`, `DangKyChang.getDangKyCuaChang()`, `KetQua.kiemTraKetQuaCu()` / `xoaKetQuaCu()` / `xepHangVaTinhDiem()` / `luuKetQua()` |
| Số lớp thực thể | 6 | đủ 12 lớp kèm quan hệ như biểu đồ lớp thực thể chung ở `docs/03` |

Phần **giữ nguyên được**: kiểu hộp lớp để trơn không stereotype, tiền tố thuộc tính `in/out/sub`, đường kẻ trơn, hình thoi rỗng/đặc, bố cục lớp biên hàng trên — lớp thực thể hàng dưới.

### `m3-lop-mvc.png` — vẽ lại

Bản hiện tại đang là biểu đồ của một ứng dụng desktop: có `<<Interface>> ActionListener`, các lớp giao diện mang phương thức `actionPerformed()`, thuộc tính kiểu `JButton` / `JTable`. Biểu đồ đúng gồm ba tầng xếp theo hàng (**không có khung package**):

- **jsp:** `gdChinhNV.jsp`, `gdChonChang.jsp`, `gdNhapKetQua.jsp`, `doLuuKetQua.jsp` — **chỉ có thuộc tính**, không có phương thức
- **DAO:** `DAO` (chỉ `-con : Connection` và `+DAO()`), `MuaGiaiDAO`, `ChangDuaDAO`, `DangKyChangDAO`, `KetQuaDAO` — mỗi lớp có constructor và phương thức ghi đầy đủ chữ ký
- **model:** `MuaGiai`, `ChangDua`, `DangKyChang`, `KetQua`, `ThanhVien`, `NhanVien`

Tên phương thức lấy đúng theo mục 5 của `../noi-dung.md` (`getDSChangDua(muaGiaiId : int) : ChangDua[]`…), không dùng `createChang` / `getAllChang` / `getAllTayDua`.

### `m3-uc-chitiet.png` — vẽ lại

- Actor đang là `NhanVien1`, `NhanVien2` → đúng phải là phân cấp `Thành viên` ▷ `Nhân viên`, và module chỉ có **một** actor `Nhân viên`.
- Bỏ khung hệ thống (khung chỉ dùng ở biểu đồ UC tổng quan).
- Các UC `Xử lý kháng nghị kết quả`, `Áp dụng án phạt sau chặng`, `Phê duyệt kết quả chặng` **không thuộc phạm vi đề bài** đã chốt → bỏ.
- UC chính `Cập nhật kết quả chặng đua` include đúng ba UC con: `NV đăng nhập` (kế thừa `Đăng nhập`), `Chọn chặng`, `Nhập kết quả chặng`.

### `m3-hoatdong.png` — vẽ lại

Bản hiện tại là biểu đồ hoạt động **nghiệp vụ** (swimlane theo người thực hiện). Mục 6 cần biểu đồ hoạt động **pha thiết kế**: khung `Xử lí tại gdXxx.jsp` cho từng trang, mỗi hành động ứng với một phương thức đã thiết kế ở mục 5, lời gọi tầng dữ liệu ghi rõ `XxxDAO: tenHam()`.
