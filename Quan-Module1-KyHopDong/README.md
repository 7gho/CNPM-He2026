# Module 1 — Ký hợp đồng tay đua với đội đua (Quan)

> Đề bài: mục 1 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Actor:** Nhân viên
- **Ràng buộc chính:** tại một thời điểm tay đua chỉ thuộc 1 đội — hợp đồng mới không được chồng lấn thời gian hợp đồng cũ.
- **Lớp thực thể liên quan:** `TayDua`, `DoiDua`, `HopDong` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

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
