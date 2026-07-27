# Module 3 — Cập nhật kết quả chặng đua (Kiet)

> Đề bài: mục 3 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Actor:** Nhân viên
- **Tên UC chính:** `Cập nhật kết quả chặng đua`
- **Nghiệp vụ chính:** nhập thời gian/số vòng/trạng thái (Hoàn thành, DNF, DSQ) cho tay đua đã đăng ký → xếp hạng theo thời gian → gán điểm top 10 (25/18/15/12/10/8/6/4/2/1), DNF và DSQ = 0 điểm và xếp cuối.
- **Lớp thực thể liên quan:** `ChangDua`, `DangKyChang`, `TayDua`, `DoiDua`, `KetQua` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

## Checklist sản phẩm (nộp cho module này)
- [ ] Biểu đồ UC chi tiết
- [ ] Đặc tả UC (kịch bản chuẩn + ngoại lệ)
- [ ] Biểu đồ trạng thái (phân tích hoạt động) + biểu đồ hoạt động pha thiết kế (khung "Xử lí tại gdXxx.jsp")
- [ ] Biểu đồ lớp phân tích (lớp biên `GDxxx` chỉ có thuộc tính + lớp thực thể mang phương thức nghiệp vụ; **không có lớp Control**)
- [x] Giao diện phác thảo (trong mục 2.2 Đặc tả UC — không vẽ, không xuất ảnh)
- [ ] Biểu đồ lớp thiết kế view (.jsp) / DAO / model — **không có Controller**, các `XxxDAO` kế thừa lớp cha `DAO`
- [ ] Thuyết minh (kịch bản phiên bản 3) + biểu đồ tuần tự
- [ ] Test case (kế hoạch kiểm thử + từng test case có CSDL trước/sau)

## Nơi để file
- `hinh/` — ảnh biểu đồ export từ Visual Paradigm (PNG).
- `noi-dung.md` — Claude sẽ dựng nội dung chữ (đặc tả UC, kịch bản, test case, danh sách phần tử biểu đồ + PlantUML) tại đây.

> Claude sẽ sinh `noi-dung.md` đầy đủ cho module này. Bạn chỉ cần: mở VP → vẽ theo blueprint → export ảnh vào `hinh/`.
