# Kế hoạch & phân công — Đồ án CNPM (Nhóm 3)

> Đề tài: **Quản lý giải đua xe F1** (project 10). Đề bài gốc: [../project10-F1-4modules.md](../project10-F1-4modules.md) — **không đổi nghiệp vụ của file này**, chỉ bổ sung thuộc tính cho khớp đề gốc trong giáo trình.
> Tài liệu này là bản kế hoạch tổng. Ghi chú/hướng dẫn khác đặt trong thư mục `docs/` hoặc thư mục của từng thành viên.

## 1. Thành viên & phân công

| Thành viên | Module phụ trách | Thư mục |
|---|---|---|
| Quan (trưởng nhóm) | Module 1 — Ký hợp đồng tay đua với đội đua | `Module 1 - Quan/` |
| Kin | Module 2 — Đăng ký tay đua tham gia chặng đua | `Module 2 - Kin/` |
| Kiet | Module 3 — Cập nhật kết quả chặng đua | `Module 3 - Kiet/` |
| Thanh | Module 4 — Quyết toán và trao giải cuối mùa | `Module 4 - Thanh/` |

## 2. Sản phẩm phải nộp (theo yêu cầu giảng viên)

### 2.1. Phần làm chung của cả nhóm
| # | Sản phẩm | File | Trạng thái |
|---|---|---|---|
| 1 | Mô tả bài toán (yêu cầu người dùng) | `project10-F1-4modules.md` | ✅ xong |
| 2 | Đặc tả yêu cầu (chức năng + phi chức năng) | `docs/01-dac-ta-yeu-cau.md` | ✅ nội dung, ⬜ chốt |
| 3 | Biểu đồ UC tổng quát | `docs/02-usecase-tong-quat.md` | ✅ blueprint, ⬜ vẽ VP |
| 4 | Biểu đồ lớp thực thể (**pha phân tích** + **pha thiết kế**) + Thiết kế CSDL + Thiết kế triển khai (package) | `docs/03-lop-thuc-the-va-csdl.md` | ✅ blueprint, ⬜ vẽ VP |
| 5 | Đặc tả UC gọn — danh mục & xác thực | `docs/04-dac-ta-danh-muc-va-auth.md` | ✅ xong |

> **Tài liệu nội bộ (không nộp):** `docs/05-doi-chieu-chuan-thay.md` — bảng đối chiếu toàn bộ tài liệu với chuẩn của thầy (slide B1/B2/B3 + giáo trình), dùng để rà soát trước khi ghép báo cáo.

> **Ghi chú phạm vi:** các UC danh mục (quản lý mùa giải, tay đua, đội, chặng, đăng ký đội tham gia mùa) và Đăng nhập/Đổi mật khẩu là **chức năng hỗ trợ** — chỉ cần đặc tả UC gọn ở `docs/04`, **không** thuộc 4 module được phân công (mỗi module vẫn làm đủ 6 mục). Không phát sinh module thứ 5.

### 2.2. Phần mỗi thành viên tự làm (cho 1 module = 1 Use Case)
Mỗi người làm đủ 7 mục sau cho module của mình (chi tiết trong README thư mục riêng):
1. Biểu đồ UC chi tiết
2. Đặc tả UC (kịch bản chuẩn — theo mẫu bảng ở mục 4)
3. **Biểu đồ trạng thái** (phân tích hoạt động — theo mẫu **Hình 3.9/3.11 giáo trình PDF**: mỗi trạng thái = một lần hệ thống hiển thị một giao diện chờ tương tác, nhãn cung là hành động người dùng `[…]`)
4. Thiết kế giao diện
5. Biểu đồ hoạt động (**pha thiết kế** — theo mẫu **Hình 4.9 giáo trình PDF**: khung `Xử lí tại gdXxx.jsp` cho từng trang, mỗi hành động ứng với một phương thức đã thiết kế, node DAO tách riêng; đặt **sau** biểu đồ lớp thiết kế, ngay trước thuyết minh)
6. **Thuyết minh (kịch bản phiên bản 3) + biểu đồ tuần tự (sequence)**
7. Test case

> **Ghi chú mục 6:** yêu cầu của giảng viên ghi rõ *"**Thuyết minh và** vẽ biểu đồ tuần tự cho UC"*. Thuyết minh chính là **kịch bản phiên bản 3** — danh sách đánh số 1, 2, 3… mô tả từng lượt gọi giữa trang `.jsp`, lớp `DAO` và lớp thực thể; **số dòng thuyết minh phải khớp số message trong biểu đồ tuần tự**. Không được để hình đứng trơ một mình với caption.

> **Tuỳ chọn (chỉ làm nếu dư thời gian):** kịch bản phiên bản 2 + biểu đồ giao tiếp (communication) của pha phân tích (giáo trình PDF mục 3.2.4) — **không bắt buộc** theo yêu cầu bài tập; nhóm đã có thuyết minh v.3 + biểu đồ tuần tự pha thiết kế thay thế.

> **Bổ sung theo pipeline lecture** (nên có để báo cáo đầy đủ, điểm cao hơn) — 2 biểu đồ lớp cho mỗi module:
> - **Biểu đồ lớp phân tích của module** = **lớp biên `GDxxx`** (chỉ có **thuộc tính**, không có phương thức; tên thuộc tính theo prefix `in` / `out` / `inout` / `sub` / `outsub`) + **lớp thực thể** (mang các **phương thức nghiệp vụ**). Chỉ đúng **2 tầng này**, **không có lớp Control/Controller**, **không có stereotype** `<<boundary>>` / `<<control>>` / `<<entity>>` (hộp lớp để trơn, phân biệt tầng bằng tiền tố tên `GD…`).
> - **Biểu đồ lớp thiết kế của module** = **trang `.jsp`** (tầng giao diện) + **lớp `XxxDAO`** (tầng truy xuất dữ liệu, đều kế thừa lớp cha `DAO`) + **lớp `model`** (chính là các lớp thực thể). Vẽ theo mẫu **Hình 4.4 giáo trình PDF**: thuộc tính view kèm kiểu control (`Text`/`Select`/`Table`/`link`/`submit`/`Reset`), DAO có constructor + phương thức đầy đủ chữ ký. Vẫn gọi được là mô hình MVC với **M** = model, **V** = `.jsp`, **C** = các `DAO`, nhưng **tuyệt đối không có lớp `XxxController`**.
> - Quan hệ trong cả hai biểu đồ vẽ bằng **đường kẻ trơn / hình thoi rỗng ◇ / hình thoi đặc ♦ / tam giác rỗng ▷**, **không dùng mũi tên định hướng**.

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

> Bảng đặc tả **đúng 6 dòng, đúng thứ tự trên**. Không thêm dòng "Luồng phụ", "Thuộc tính", "Ràng buộc" — nội dung đó chuyển thành ngoại lệ đánh số theo bước, hoặc ghi chú dưới bảng.
> Kịch bản phải **có dữ liệu thật và trạng thái nút** (dùng bộ dữ liệu mẫu ở `docs/03` mục 5), ví dụ: *"Nhân viên nhập `Hamilton` và click Tìm"*, *"nút [Lưu] chưa được active"*.

### 4.2. Mẫu Test case (theo Bảng 6.7 giáo trình PDF — 4 cột, 3 nhóm)

Đầu mục test case của mỗi module ghi rõ: *"Xây dựng theo quy trình 4 bước và mẫu Bảng 6.7, giáo trình BG HP TTTN 2 CNPM, mục 6.2."*

Mỗi module viết **MỘT bảng 4 cột**:

| Mã | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|

chia thành **3 nhóm** bằng dòng tiêu đề nhóm in đậm chen giữa bảng (đúng như Bảng 6.7):

1. **Nhóm Giao diện** — theo từng màn, mỗi màn 2 ca: (a) bố cục tổng thể (title đúng, hiển thị đầy đủ các trường/nút — liệt kê đúng danh sách control của màn, focus vào trường đầu tiên); (b) một ca hành vi phím (Tab đúng thứ tự hoặc Enter thực hiện nút chính).
2. **Nhóm Chức năng** — theo từng màn, 2 ca: hiển thị đúng dữ liệu khi CSDL có dữ liệu (kết quả mong muốn **đối chiếu bảng CSDL**, ví dụ *"danh sách khớp các bản ghi trong tblTayDua"*) và ca không có dữ liệu.
3. **Nhóm Luồng nghiệp vụ** — end-to-end; cột "Các bước thực hiện" đánh số 1, 2, 3… kèm **dữ liệu thật F1 2025** (bộ dữ liệu mẫu ở `docs/03` mục 5); cột "Kết quả mong muốn" ghi cả hiệu ứng CSDL (ví dụ *"tblHopDong: hợp đồng cũ có ngayKetThuc = 31/12/2024, thêm bản ghi mới Ferrari 01/01/2025"*). Dòng đầu nhóm ghi `Precond:` (điều kiện CSDL + đăng nhập).

**Mã test case + các ca luồng nghiệp vụ bắt buộc:**

| Module | Mã | Luồng nghiệp vụ bắt buộc |
|---|---|---|
| M1 | `KHD_n` | ký mới tay đua tự do (chuẩn) · ký khi đang có HĐ hiệu lực → tự đóng HĐ cũ · ngày bắt đầu chồng lấn → lỗi · không tìm thấy tay đua → thêm mới rồi ký |
| M2 | `DKC_n` | đăng ký 2 tay đua (chuẩn) · chọn >2 → lỗi · trùng đăng ký chặng (đội khác) → lỗi · đội không có tay đua hiệu lực → thông báo · thay tay đua trước ngày đua · danh sách đúng thứ tự alphabet |
| M3 | `CNKQ_n` | nhập đủ kết quả, tính điểm đúng (chuẩn) · DNF → 0 điểm xếp cuối · DSQ → 0 điểm xếp cuối · thiếu thời gian + trạng thái Hoàn thành → lỗi · chặng đã có kết quả → cảnh báo ghi đè + tính lại |
| M4 | `QTTG_n` | xem BXH đến chặng bất kỳ (chuẩn) · bằng điểm → countback · countback bằng → tổng thời gian · drill-down chi tiết tay đua/đội · tính tiền thưởng · tay đua đổi đội giữa mùa → điểm đội cộng theo đội tại thời điểm chặng |

**Số lượng:** nhóm Giao diện + Chức năng mỗi module ~8–10 ca, nhóm Luồng nghiệp vụ 4–6 ca ⇒ **~14–16 ca/module**.

## 5. Cấu trúc báo cáo cuối kỳ

Ghép tất cả thành **01 file Word** theo đúng bố cục yêu cầu của giảng viên (2 phần):

**Trang bìa** — tên đề tài, danh sách thành viên **ghi rõ ai làm Use Case nào**.

**PHẦN 1 — CÔNG VIỆC CHUNG CỦA NHÓM**
1. **Mô tả yêu cầu bài toán, yêu cầu người dùng** (ngôn ngữ tự nhiên, khoảng 2–3 trang, chưa mô hình hóa): mục đích → phạm vi hệ thống (kèm câu chốt *"Những chức năng không đề cập đến thì mặc định là không thuộc phạm vi của hệ thống."*) → mô tả nghiệp vụ chi tiết từng chức năng → các đối tượng được quản lý và thuộc tính → quan hệ số lượng → các ràng buộc nghiệp vụ.
2. **Mô tả yêu cầu phần mềm**: xác định actor → yêu cầu chức năng (bảng Use case) → yêu cầu phi chức năng → **biểu đồ UC tổng quát** (là **mục con cuối** của chương này, không tách thành chương riêng).
3. **Xây dựng biểu đồ lớp thực thể**: phân tích xác định thực thể (bảng trích danh từ) → mô tả thực thể (thuộc tính, phương thức) → biểu đồ lớp thực thể **pha phân tích** → biểu đồ lớp thực thể **pha thiết kế** → thiết kế CSDL → thiết kế triển khai (package `view` → `dao` → `model`).

**PHẦN 2 — KẾT QUẢ TỪNG THÀNH VIÊN** (mỗi thành viên 1 chương, ghi **tên thành viên + tên Use Case** ở ngay trước nội dung)

Cấu trúc mỗi chương module (×4), theo đúng thứ tự:

> **UC chi tiết → đặc tả UC → biểu đồ trạng thái (phân tích hoạt động) → biểu đồ lớp phân tích → thiết kế giao diện → biểu đồ lớp thiết kế (`.jsp` / `DAO` / `model`) → biểu đồ hoạt động (pha thiết kế) → thuyết minh (kịch bản v.3) + biểu đồ tuần tự → test case**

> Biểu đồ hoạt động đặt **sau** biểu đồ lớp thiết kế vì mỗi hành động trong biểu đồ hoạt động ứng với một phương thức đã thiết kế (giáo trình PDF mục 4.3.2 bước 1).

**Kết luận.**

> **Bắt buộc:** mọi vị trí hình trong báo cáo phải **nhúng ảnh thật** bằng cú pháp `![…](đường-dẫn)`, không được chỉ ghi caption `(Hình 5.7 — …)` — nếu không, bản Word xuất ra sẽ trắng hình. Mỗi hình phải có **lời văn mô tả** đi kèm, không để hình đứng trơ.

> Claude sẽ dựng bản thảo báo cáo (`docs/BAO-CAO.md`) tổng hợp từ tất cả nội dung; nhóm chỉ chèn hình VP đã export và xuất ra Word.

## 6. Cấu trúc thư mục repo

```
project10-F1-4modules.md          ← đề bài (chỉ bổ sung thuộc tính cho khớp đề gốc)
docs/                             ← tài liệu chung + kế hoạch
  00-ke-hoach-va-phan-cong.md
  01-dac-ta-yeu-cau.md
  02-usecase-tong-quat.md
  03-lop-thuc-the-va-csdl.md
  04-dac-ta-danh-muc-va-auth.md
  05-doi-chieu-chuan-thay.md      ← nội bộ: đối chiếu với chuẩn của thầy
  BAO-CAO.md                      ← bản thảo báo cáo cuối kỳ (ghép để xuất Word)
  bao-cao-xem-truoc.md            ← bản xem trước
  hinh/                           ← ảnh biểu đồ phần chung
Module 1 - Quan/                  ← mỗi thành viên 1 thư mục
  README.md
  noi-dung.md
  hinh/
Module 2 - Kin/
Module 3 - Kiet/
Module 4 - Thanh/
Lectures/                         ← tài liệu giảng viên (tham khảo)
```

## 7. Danh sách ảnh cần export từ Visual Paradigm

**Quy tắc tên file:** chữ thường, không dấu, ngăn cách bằng `-`, đuôi `.png`. Ảnh của module đặt tên `m<số module>-<tên biểu đồ>.png`. Tên file ở bảng dưới là **tên chốt**, phải trùng với bảng "Danh sách ảnh cần export" ở đầu `noi-dung.md` của từng module và với đường dẫn `![…](…)` trong `docs/BAO-CAO.md`.

### 7.1. `docs/hinh/` — phần chung của nhóm (4 ảnh)

| Tên file | Biểu đồ | Blueprint | Trạng thái |
|---|---|---|---|
| `uc-tongquat.png` | Biểu đồ UC tổng quát | `docs/02` mục 4 | đã vẽ — **VẼ LẠI** (thêm UC trừu tượng `Quản lý danh mục`, actor trừu tượng `ThanhVien`, bỏ 4 quan hệ include, đổi mũi tên thành đường kẻ trơn) |
| `lop-thucthe-phantich.png` | Lớp thực thể **pha phân tích** (không `id`, không kiểu dữ liệu, không phương thức) | `docs/03` | chưa vẽ |
| `lop-thucthe-thietke.png` | Lớp thực thể **pha thiết kế** (có `id`, có kiểu dữ liệu, có thuộc tính kiểu đối tượng) | `docs/03` | chưa vẽ |
| `package-trienkhai.png` | Thiết kế triển khai — package `view` → `dao` → `model` | `docs/03` | chưa vẽ |

> File cũ `docs/hinh/lop-thucthe.png` **bị thay bởi 2 file** `lop-thucthe-phantich.png` và `lop-thucthe-thietke.png` — xóa khỏi repo sau khi có 2 ảnh mới.

### 7.2. Ảnh của từng module (M1–M3: 8 ảnh, M4: 9 ảnh)

> **Mẫu hình bắt buộc (giáo trình PDF `BG HP TTTN 2 CNPM`):** biểu đồ **trạng thái** vẽ theo mẫu **Hình 3.9/3.11**; biểu đồ **hoạt động** vẽ theo mẫu **Hình 4.9** (khung `Xử lí tại gdXxx.jsp` cho từng trang, node DAO tách riêng); biểu đồ **lớp thiết kế** vẽ theo mẫu **Hình 4.4** (3 tầng jsp/DAO/model, DAO kế thừa `DAO`, chữ ký đầy đủ); biểu đồ **tuần tự** vẽ theo mẫu **Hình 4.10/4.12** (đánh số message, trang chính mở đầu + kết thúc, luồng lưu có `setter()`). Mọi ảnh hoạt động / tuần tự / lớp thiết kế đã vẽ trước đây đều phải **vẽ lại** theo các mẫu này.

| Module | Tên file | Biểu đồ | Trạng thái |
|---|---|---|---|
| M1 | `m1-uc-chitiet.png` | UC chi tiết | đã vẽ — **VẼ LẠI** (giữ UC con `Đăng nhập` include theo giáo trình PDF; màn `GDKyHopDong` đổi thành trang chính `GDChinhNV` — không sinh UC con; `Thêm tay đua` extend từ `Tìm tay đua`) |
| M1 | `m1-trangthai.png` | Biểu đồ trạng thái (mẫu Hình 3.9) | chưa vẽ |
| M1 | `m1-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | đã vẽ — **VẼ LẠI** (theo mẫu Hình 4.9: khung theo từng trang jsp; tách từng ràng buộc thành một node quyết định riêng) |
| M1 | `m1-lop-phantich.png` | Lớp phân tích (lớp biên + lớp thực thể) | chưa vẽ |
| M1 | `m1-giaodien-timtaydua.png` | Giao diện tìm tay đua | chưa vẽ |
| M1 | `m1-giaodien-nhaphopdong.png` | Giao diện nhập hợp đồng | chưa vẽ |
| M1 | `m1-lop-mvc.png` | Lớp thiết kế (`.jsp` / `DAO` / `model`, mẫu Hình 4.4) | chưa vẽ |
| M1 | `m1-tuantu.png` | Biểu đồ tuần tự (mẫu Hình 4.10/4.12) | chưa vẽ |
| M2 | `m2-uc-chitiet.png` | UC chi tiết | đã vẽ — **VẼ LẠI** (giữ UC con `Đăng nhập` include theo giáo trình PDF; tách thành 2 UC con `Chọn chặng và đội` + `Chọn tay đua đăng ký`) |
| M2 | `m2-trangthai.png` | Biểu đồ trạng thái (mẫu Hình 3.9) | chưa vẽ |
| M2 | `m2-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mẫu Hình 4.9) | chưa vẽ |
| M2 | `m2-lop-phantich.png` | Lớp phân tích | chưa vẽ |
| M2 | `m2-giaodien-chonchangdoi.png` | Giao diện chọn chặng và đội | chưa vẽ |
| M2 | `m2-giaodien-dangkytaydua.png` | Giao diện đăng ký tay đua | chưa vẽ |
| M2 | `m2-lop-mvc.png` | Lớp thiết kế (`.jsp` / `DAO` / `model`, mẫu Hình 4.4) | chưa vẽ |
| M2 | `m2-tuantu.png` | Biểu đồ tuần tự (mẫu Hình 4.10/4.12) | chưa vẽ |
| M3 | `m3-uc-chitiet.png` | UC chi tiết | chưa vẽ |
| M3 | `m3-trangthai.png` | Biểu đồ trạng thái (mẫu Hình 3.9) | chưa vẽ |
| M3 | `m3-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mẫu Hình 4.9) | chưa vẽ |
| M3 | `m3-lop-phantich.png` | Lớp phân tích | chưa vẽ |
| M3 | `m3-giaodien-chonchang.png` | Giao diện chọn chặng | chưa vẽ |
| M3 | `m3-giaodien-nhapketqua.png` | Giao diện nhập kết quả + đối soát | chưa vẽ |
| M3 | `m3-lop-mvc.png` | Lớp thiết kế (`.jsp` / `DAO` / `model`, mẫu Hình 4.4) | chưa vẽ |
| M3 | `m3-tuantu.png` | Biểu đồ tuần tự (mẫu Hình 4.10/4.12) | chưa vẽ |
| M4 | `m4-uc-chitiet.png` | UC chi tiết | đã vẽ — **VẼ LẠI** (giữ UC con `Đăng nhập` include theo giáo trình PDF; đổi tên UC con thành `Xem bảng tổng sắp` + `Nhập thưởng và lưu`; thêm UC con `Xem chi tiết theo chặng` extend từ `Xem bảng tổng sắp`) |
| M4 | `m4-trangthai.png` | Biểu đồ trạng thái (mẫu Hình 3.9) | chưa vẽ |
| M4 | `m4-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | đã vẽ — **VẼ LẠI** (theo mẫu Hình 4.9; biểu đồ cũ quá sơ sài: tách từng ràng buộc thành một node quyết định riêng, thêm nhánh countback + tổng thời gian) |
| M4 | `m4-lop-phantich.png` | Lớp phân tích | chưa vẽ |
| M4 | `m4-giaodien-xephang.png` | Giao diện bảng tổng sắp (có chọn chặng) | chưa vẽ |
| M4 | `m4-giaodien-chitietxephang.png` | Giao diện chi tiết theo chặng (drill-down) | chưa vẽ |
| M4 | `m4-giaodien-traogiai.png` | Giao diện trao giải | chưa vẽ |
| M4 | `m4-lop-mvc.png` | Lớp thiết kế (`.jsp` / `DAO` / `model`, mẫu Hình 4.4) | đã vẽ — **VẼ LẠI** (bản cũ có lớp `QuyetToanController` — phải bỏ tầng Controller, thay bằng `.jsp` / `DAO` kế thừa lớp cha `DAO` / `model`) |
| M4 | `m4-tuantu.png` | Biểu đồ tuần tự (mẫu Hình 4.10/4.12) | đã vẽ — **VẼ LẠI** (bản cũ có lifeline Controller và lifeline CSDL với câu lệnh SQL — phải bỏ cả hai, thay bằng lifeline `.jsp` + `DAO` + lớp thực thể, có đánh số message) |

### 7.3. Tóm tắt các ảnh đã vẽ nhưng PHẢI VẼ LẠI

| Ảnh | Lý do |
|---|---|
| `Module 4 - Thanh/hinh/m4-lop-mvc.png` | còn lớp `QuyetToanController` — sai kiến trúc, không có tầng Controller |
| `Module 4 - Thanh/hinh/m4-tuantu.png` | còn lifeline Controller và lifeline CSDL kèm SQL trong message |
| `Module 4 - Thanh/hinh/m4-uc-chitiet.png` | tên UC con đã đổi, thiếu UC con `Xem chi tiết theo chặng` (extend); UC con `Đăng nhập` giữ lại (include) theo giáo trình PDF |
| `Module 4 - Thanh/hinh/m4-hoatdong.png` | biểu đồ quá sơ sài, thiếu nhánh countback; vẽ lại theo mẫu Hình 4.9 (khung theo từng trang jsp) |
| `Module 2 - Kin/hinh/m2-uc-chitiet.png` | đã tách thành 2 UC con theo 2 màn hình; UC con `Đăng nhập` giữ lại (include) theo giáo trình PDF |
| `Module 1 - Quan/hinh/m1-uc-chitiet.png` | màn `GDKyHopDong` đổi thành trang chính `GDChinhNV` (không sinh UC con), quan hệ extend gắn sai UC gốc, thiếu system boundary; UC con `Đăng nhập` giữ lại (include) theo giáo trình PDF |
| `Module 1 - Quan/hinh/m1-hoatdong.png` | chưa tách từng ràng buộc thành một node quyết định riêng; vẽ lại theo mẫu Hình 4.9 (khung theo từng trang jsp) |
| `docs/hinh/uc-tongquat.png` | thiếu UC trừu tượng `Quản lý danh mục`, thiếu actor trừu tượng, còn mũi tên và quan hệ include thừa |
| `docs/hinh/lop-thucthe.png` | bị **thay thế** bởi `lop-thucthe-phantich.png` + `lop-thucthe-thietke.png` |
