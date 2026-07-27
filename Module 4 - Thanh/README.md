# Module 4 — Quyết toán và trao giải cuối mùa (Thanh)

> Đề bài: mục 4 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Tên UC chính:** `Quyết toán và trao giải cuối mùa`
- **Actor:** Quản lý
- **UC con / màn hình:** `Đăng nhập` (include, dùng chung), `Xem bảng tổng sắp` (`gdXepHang.jsp`, có chọn chặng), `Xem chi tiết theo chặng` (extend, `gdChiTietXepHang.jsp`) và `Nhập thưởng và lưu` (`gdTraoGiai.jsp`); thêm trang chính `gdChinhQL.jsp` và trang xử lý `doLuuTraoGiai.jsp`.
- **Ràng buộc chính:** chỉ quyết toán (sang màn trao giải) khi đã chọn chặng cuối và tất cả chặng trong mùa đã có kết quả.
- **Nghiệp vụ chính:** cộng dồn điểm/thời gian tính đến chặng được chọn → xếp hạng cá nhân & đội theo **3 tầng**: (1) tổng điểm giảm dần; (2) bằng điểm → **countback** (số lần về nhất, rồi về nhì, rồi về ba…); (3) countback vẫn bằng → **tổng thời gian tăng dần**; tổng thời gian luôn hiển thị trên bảng xếp hạng → drill-down chi tiết theo chặng của 1 tay đua/đội → nhập mức thưởng theo hạng → tính tiền thưởng → lưu & in danh sách trao giải.
- **Điểm đội** cộng theo đội đã đăng ký tay đua ở **từng chặng** (`DangKyChang`), không theo đội hiện tại của tay đua.
- **Lớp thực thể liên quan:** `MuaGiai`, `ChangDua`, `KetQua`, `TayDua`, `DoiDua`, `TraoGiai` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

## Checklist sản phẩm (nộp cho module này)
- [ ] Biểu đồ UC chi tiết (có system boundary, actor nối UC bằng đường kẻ trơn)
- [ ] Đặc tả UC (mẫu 6 dòng, kịch bản đánh số có dữ liệu thật + trạng thái nút, ngoại lệ đánh số theo bước)
- [ ] Biểu đồ trạng thái (phân tích hoạt động) + biểu đồ hoạt động pha thiết kế (khung "Xử lí tại gdXxx.jsp")
- [ ] Biểu đồ lớp phân tích (lớp biên `GDxxx` chỉ có thuộc tính + lớp thực thể mang phương thức nghiệp vụ; **không có lớp Control**)
- [x] Giao diện phác thảo (bảng xen giữa các bước Kịch bản chính của mục 2 Đặc tả UC — không vẽ, không xuất ảnh)
- [ ] Biểu đồ lớp thiết kế view (.jsp) / DAO / model — **không có Controller**, các `XxxDAO` kế thừa lớp cha `DAO`
- [ ] Thuyết minh (kịch bản phiên bản 3) + biểu đồ tuần tự
- [ ] Test case (mẫu Bảng 6.7 giáo trình PDF: 1 bảng 4 cột, 3 nhóm Giao diện / Chức năng / Luồng nghiệp vụ, mã `QTTG_n`, kèm mục Data test)

## Nơi để file
- `hinh/` — ảnh biểu đồ export từ Visual Paradigm (PNG).
- `noi-dung.md` — nội dung chữ đầy đủ (đặc tả UC, kịch bản, thuyết minh, test case, blueprint PlantUML).

> Việc cần làm: mở VP → vẽ theo blueprint trong `noi-dung.md` → export ảnh vào `hinh/`.
