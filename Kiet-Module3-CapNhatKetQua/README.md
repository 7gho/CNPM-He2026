# Module 3 — Cập nhật kết quả và tính điểm chặng đua (Kiet)

> Đề bài: mục 3 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Actor:** Nhân viên
- **Nghiệp vụ chính:** nhập thời gian/số vòng/DNF cho tay đua đã đăng ký → xếp hạng theo thời gian → gán điểm top 10 (25/18/15/12/10/8/6/4/2/1), DNF = 0 điểm.
- **Lớp thực thể liên quan:** `ChangDua`, `DangKyChang`, `TayDua`, `DoiDua`, `KetQua` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

## Checklist sản phẩm (nộp cho module này)
- [ ] Biểu đồ UC chi tiết
- [ ] Đặc tả UC (kịch bản chuẩn + ngoại lệ)
- [ ] Biểu đồ hoạt động (activity)
- [ ] Biểu đồ lớp phân tích (boundary/control/entity) — *khuyến nghị*
- [ ] Thiết kế giao diện
- [ ] Biểu đồ lớp thiết kế MVC — *khuyến nghị*
- [ ] Biểu đồ tuần tự (sequence)
- [ ] Test case

## Nơi để file
- `hinh/` — ảnh biểu đồ export từ Visual Paradigm (PNG).
- `noi-dung.md` — Claude sẽ dựng nội dung chữ (đặc tả UC, kịch bản, test case, danh sách phần tử biểu đồ + PlantUML) tại đây.

> Claude sẽ sinh `noi-dung.md` đầy đủ cho module này. Bạn chỉ cần: mở VP → vẽ theo blueprint → export ảnh vào `hinh/`.
