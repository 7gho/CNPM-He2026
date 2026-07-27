# Module 2 — Đăng ký tay đua tham gia chặng đua (Kin)

> Đề bài: mục 2 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Actor:** Nhân viên
- **Ràng buộc chính:** mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ đăng ký 1 lần trong chặng. Chỉ hiện tay đua đang có hợp đồng hiệu lực với đội.
- **Lớp thực thể liên quan:** `ChangDua`, `DoiDua`, `TayDua`, `HopDong`, `DangKyChang` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

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
