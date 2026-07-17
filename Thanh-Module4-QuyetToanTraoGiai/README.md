# Module 4 — Quyết toán và trao giải cuối mùa (Thanh)

> Đề bài: mục 4 trong [../project10-F1-4modules.md](../project10-F1-4modules.md).
> Tài liệu chung: [../docs/](../docs/). Mẫu đặc tả UC & test case: [../docs/00-ke-hoach-va-phan-cong.md](../docs/00-ke-hoach-va-phan-cong.md) mục 4.

## Tóm tắt module
- **Actor:** Quản lý
- **Ràng buộc chính:** chỉ quyết toán khi tất cả chặng trong mùa đã có kết quả.
- **Nghiệp vụ chính:** cộng dồn điểm/thời gian toàn mùa → xếp hạng cá nhân & đội (giảm dần điểm, bằng điểm thì tăng dần thời gian) → nhập mức thưởng theo hạng → tính tiền thưởng → lưu & in danh sách trao giải.
- **Lớp thực thể liên quan:** `MuaGiai`, `ChangDua`, `KetQua`, `TayDua`, `DoiDua`, `TraoGiai` (xem [../docs/03-lop-thuc-the-va-csdl.md](../docs/03-lop-thuc-the-va-csdl.md)).

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
