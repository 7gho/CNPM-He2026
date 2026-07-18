# Kế hoạch & phân công — Đồ án CNPM (Nhóm 3)

> Đề tài: **Quản lý giải đua xe F1** (project 10). Đề bài gốc: [../project10-F1-4modules.md](../project10-F1-4modules.md) — **không sửa file này**.
> Tài liệu này là bản kế hoạch tổng. Ghi chú/hướng dẫn khác đặt trong thư mục `docs/` hoặc thư mục của từng thành viên.

## 1. Thành viên & phân công

| Thành viên | Module phụ trách | Thư mục |
|---|---|---|
| Quan (trưởng nhóm) | Module 1 — Ký hợp đồng tay đua với đội đua | `Module 1 - Quan/` |
| Kin | Module 2 — Đăng ký tay đua tham gia chặng đua | `Module 2 - Kin/` |
| Kiet | Module 3 — Cập nhật kết quả và tính điểm chặng đua | `Module 3 - Kiet/` |
| Thanh | Module 4 — Quyết toán và trao giải cuối mùa | `Module 4 - Thanh/` |

## 2. Sản phẩm phải nộp (theo yêu cầu giảng viên)

### 2.1. Phần làm chung của cả nhóm
| # | Sản phẩm | File | Trạng thái |
|---|---|---|---|
| 1 | Mô tả bài toán (yêu cầu người dùng) | `project10-F1-4modules.md` | ✅ xong |
| 2 | Đặc tả yêu cầu (chức năng + phi chức năng) | `docs/01-dac-ta-yeu-cau.md` | ✅ nội dung, ⬜ chốt |
| 3 | Biểu đồ UC tổng quát | `docs/02-usecase-tong-quat.md` | ✅ blueprint, ⬜ vẽ VP |
| 4 | Biểu đồ lớp thực thể + Thiết kế CSDL | `docs/03-lop-thuc-the-va-csdl.md` | ✅ blueprint, ⬜ vẽ VP |
| 5 | Đặc tả UC gọn — danh mục & xác thực | `docs/04-dac-ta-danh-muc-va-auth.md` | ✅ xong |

> **Ghi chú phạm vi:** các UC danh mục (quản lý mùa giải, tay đua, đội, chặng, đăng ký đội tham gia mùa) và Đăng nhập/Đổi mật khẩu là **chức năng hỗ trợ** — chỉ cần đặc tả UC gọn ở `docs/04`, **không** thuộc 4 module được phân công (mỗi module vẫn làm đủ 6 mục). Không phát sinh module thứ 5.

### 2.2. Phần mỗi thành viên tự làm (cho 1 module = 1 Use Case)
Mỗi người làm đủ 6 mục sau cho module của mình (chi tiết trong README thư mục riêng):
1. Biểu đồ UC chi tiết
2. Đặc tả UC (kịch bản chuẩn — theo mẫu bảng ở mục 4)
3. Biểu đồ hoạt động (activity)
4. Thiết kế giao diện
5. Biểu đồ tuần tự (sequence)
6. Test case

> Bổ sung theo pipeline lecture (nên có để báo cáo đầy đủ, điểm cao hơn): biểu đồ lớp phân tích (boundary/control/entity) + biểu đồ lớp thiết kế MVC cho module.

## 3. Quy trình làm việc với Visual Paradigm

Claude không vẽ trực tiếp trong Visual Paradigm, nhưng với **mỗi biểu đồ** Claude cung cấp:
- **Bản liệt kê phần tử** (actor / use case / lớp + thuộc tính + phương thức / message tuần tự / bước activity) và **quan hệ** giữa chúng — đủ để vẽ lại một cách cơ học.
- **Mã PlantUML** kèm theo. Nếu bản Visual Paradigm của nhóm hỗ trợ PlantUML (Tools → PlantUML), có thể import thẳng ra hình rồi chỉnh; nếu không, dùng làm bản mẫu để kéo-thả.

Sau khi vẽ xong trong VP → **export PNG/hình** vào thư mục của thành viên (mục `hinh/`), và dán vào báo cáo.

## 4. Mẫu chuẩn dùng chung

### 4.1. Mẫu đặc tả Use Case (kịch bản)
| Mục | Nội dung |
|---|---|
| **Use case** | Tên use case |
| **Actor** | Ai thực hiện |
| **Tiền điều kiện** | Điều kiện trước khi chạy |
| **Hậu điều kiện** | Kết quả sau khi chạy thành công |
| **Kịch bản chính** | Các bước 1,2,3… (người dùng ↔ hệ thống) |
| **Ngoại lệ** | Đánh số theo bước bị lỗi (vd: 4. dữ liệu vi phạm ràng buộc → báo lỗi) |

### 4.2. Mẫu Test case
| ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi | Kết quả thực tế | Pass/Fail |
|---|---|---|---|---|---|---|---|

## 5. Cấu trúc báo cáo cuối kỳ

Ghép tất cả thành **01 file Word** theo thứ tự:
1. Trang bìa, thành viên, phân công
2. Mô tả bài toán (đề bài)
3. Đặc tả yêu cầu (chức năng + phi chức năng)
4. Biểu đồ UC tổng quát
5. Biểu đồ lớp thực thể (phân tích + thiết kế) + Thiết kế CSDL
6. Chương cho từng module (×4): UC chi tiết → đặc tả UC → biểu đồ hoạt động → lớp phân tích → giao diện → lớp thiết kế MVC → biểu đồ tuần tự → test case
7. Kết luận

> Claude sẽ dựng bản thảo báo cáo (`docs/BAO-CAO.md`) tổng hợp từ tất cả nội dung; nhóm chỉ chèn hình VP đã export và xuất ra Word.

## 6. Cấu trúc thư mục repo

```
project10-F1-4modules.md      ← đề bài (KHÔNG sửa)
docs/                          ← tài liệu chung + kế hoạch
  00-ke-hoach-va-phan-cong.md
  01-dac-ta-yeu-cau.md
  02-usecase-tong-quat.md
  03-lop-thuc-the-va-csdl.md
Module 1 - Quan/               ← mỗi thành viên 1 thư mục
Module 2 - Kin/
Module 3 - Kiet/
Module 4 - Thanh/
Lectures/                      ← tài liệu giảng viên (tham khảo)
```
