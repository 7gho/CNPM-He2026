# Kế hoạch & phân công — Đồ án CNPM (Nhóm 3)

> Đề tài: **Quản lý giải đua xe F1**. Mô tả bài toán: [../de-bai-f1.md](../de-bai-f1.md) — **không đổi nghiệp vụ của file này**.
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
| 1 | Mô tả bài toán (yêu cầu người dùng) | `de-bai-f1.md` | ✅ xong |
| 2 | Đặc tả yêu cầu (chức năng + phi chức năng) | `docs/01-dac-ta-yeu-cau.md` | ✅ nội dung, ⬜ chốt |
| 3 | Biểu đồ UC tổng quát | `docs/02-usecase-tong-quat.md` | ✅ blueprint, ⬜ vẽ VP |
| 4 | Biểu đồ lớp thực thể (**pha phân tích** + **pha thiết kế**) + Thiết kế CSDL + Thiết kế triển khai (package) | `docs/03-lop-thuc-the-va-csdl.md` | ✅ blueprint, ⬜ vẽ VP |
| 5 | Đặc tả UC gọn — danh mục & xác thực | `docs/04-dac-ta-danh-muc-va-auth.md` | ✅ xong |

> **Tài liệu nội bộ (không nộp):** `docs/05-doi-chieu-chuan-thay.md` — bảng đối chiếu toàn bộ tài liệu với slide bài giảng B1/B2/B3 và giáo trình, dùng để rà soát trước khi ghép báo cáo.

> **Ghi chú phạm vi:** các UC danh mục (quản lý mùa giải, tay đua, đội, chặng, đăng ký đội tham gia mùa) và Đăng nhập/Đổi mật khẩu là **chức năng hỗ trợ** — chỉ cần đặc tả UC gọn ở `docs/04`, **không** thuộc 4 module được phân công (mỗi module vẫn làm đủ 8 mục ở phần 2.2 bên dưới). Không phát sinh module thứ 5.

### 2.2. Phần mỗi thành viên tự làm (cho 1 module = 1 Use Case)
Mỗi người làm đủ 8 mục sau cho module của mình, **đánh số đúng theo bố cục chương module ở mục 5** (chi tiết trong README thư mục riêng):
1. Biểu đồ UC chi tiết
2. Đặc tả UC (kịch bản chuẩn — theo mẫu ở mục 4) — **phác thảo giao diện nhúng ngay giữa các bước của Kịch bản chính**, không có mục "Thiết kế giao diện" riêng
3. **Biểu đồ trạng thái** (phân tích hoạt động — theo mẫu **Hình 3.9/3.11 giáo trình PDF**: mỗi trạng thái = một lần hệ thống hiển thị một giao diện chờ tương tác, nhãn cung là hành động người dùng `[…]`)
4. **Biểu đồ lớp phân tích** của module (lớp biên `GDxxx` + lớp thực thể — chi tiết ở ghi chú mục 4 và 5 bên dưới)
5. **Biểu đồ lớp thiết kế** của module (trang `.jsp` / lớp `XxxDAO` / lớp `model` — chi tiết ở ghi chú mục 4 và 5 bên dưới)
6. Biểu đồ hoạt động (**pha thiết kế** — theo mẫu **Hình 4.9 giáo trình PDF**: khung `Xử lí tại gdXxx.jsp` cho từng trang, mỗi hành động ứng với một phương thức đã thiết kế, node DAO tách riêng; đặt **sau** biểu đồ lớp thiết kế, ngay trước thuyết minh)
7. **Thuyết minh (kịch bản phiên bản 3) + biểu đồ tuần tự (sequence)**
8. Test case

> **Ghi chú mục 2:** nhóm chốt **không vẽ mockup giao diện và không xuất ảnh giao diện**. Giao diện chỉ trình bày ở mức **phác thảo bằng bảng markdown** (bảng thành phần màn hình + bảng dữ liệu mẫu, **không dùng khung ký tự `+---+`**) và đặt **xen giữa các bước của Kịch bản chính**: mỗi khi hệ thống hiển thị một màn hình thì chèn bảng phác thảo **ngay dưới bước đó**, rồi viết tiếp bước kế. **Không có mục "Thiết kế giao diện" riêng ở bất kỳ cấp nào** (kể cả mục con). Căn cứ: giáo trình PDF mục 3.2.1 — kịch bản mẫu của thầy nhúng thẳng bảng dữ liệu vào từng bước, không có mục giao diện riêng và không có ảnh mockup rời.

> **Ghi chú mục 7:** yêu cầu của giảng viên ghi rõ *"**Thuyết minh và** vẽ biểu đồ tuần tự cho UC"*. Thuyết minh chính là **kịch bản phiên bản 3** — danh sách đánh số 1, 2, 3… mô tả từng lượt gọi giữa trang `.jsp`, lớp `DAO` và lớp thực thể; **số dòng thuyết minh phải khớp số message trong biểu đồ tuần tự**. Không được để hình đứng trơ một mình với caption.

> **Tuỳ chọn (chỉ làm nếu dư thời gian):** kịch bản phiên bản 2 + biểu đồ giao tiếp (communication) của pha phân tích (giáo trình PDF mục 3.2.4) — **không bắt buộc** theo yêu cầu bài tập; nhóm đã có thuyết minh v.3 + biểu đồ tuần tự pha thiết kế thay thế.

> **Ghi chú mục 4 và 5** (2 biểu đồ lớp của mỗi module, theo pipeline lecture):
> - **Biểu đồ lớp phân tích của module** = **lớp biên `GDxxx`** (chỉ có **thuộc tính**, không có phương thức; tên thuộc tính theo prefix `in` / `out` / `inout` / `sub` / `outsub`) + **lớp thực thể** (mang các **phương thức nghiệp vụ**). Chỉ đúng **2 tầng này**, **không có lớp Control/Controller**, **không có stereotype** `<<boundary>>` / `<<control>>` / `<<entity>>` (hộp lớp để trơn, phân biệt tầng bằng tiền tố tên `GD…`).
> - **Biểu đồ lớp thiết kế của module** = **trang `.jsp`** (tầng giao diện) + **lớp `XxxDAO`** (tầng truy xuất dữ liệu, đều kế thừa lớp cha `DAO`) + **lớp `model`** (chính là các lớp thực thể). Vẽ theo mẫu **Hình 4.4 giáo trình PDF**: tên lớp view là **tên trang kèm đuôi `.jsp`** (`gdChinhNV.jsp`), thuộc tính view kèm kiểu control (`Text`/`Select`/`Table`/`link`/`submit`/`Reset`), DAO có constructor + phương thức đầy đủ chữ ký, lớp cha `DAO` chỉ gồm `-con : Connection` và `+DAO()`. **Không vẽ khung package `view`/`dao`/`model` trong biểu đồ lớp** — ba tầng chỉ xếp theo hàng; khung package chỉ xuất hiện ở **biểu đồ gói** (Hình 4.15, `docs/03` mục 6). Vẫn gọi được là mô hình MVC với **M** = model, **V** = `.jsp`, **C** = các `DAO`, nhưng **tuyệt đối không có lớp `XxxController`**.
> - Quan hệ trong cả hai biểu đồ vẽ bằng **đường kẻ trơn / hình thoi rỗng ◇ / hình thoi đặc ♦ / tam giác rỗng ▷**, **không dùng mũi tên định hướng**.

## 3. Quy trình làm việc với Visual Paradigm

Claude không vẽ trực tiếp trong Visual Paradigm, nhưng với **mỗi biểu đồ** Claude cung cấp:
- **Bản liệt kê phần tử** (actor / use case / lớp + thuộc tính + phương thức / message tuần tự / bước activity) và **quan hệ** giữa chúng — đủ để vẽ lại một cách cơ học.
- **Mã PlantUML** kèm theo. Nếu bản Visual Paradigm của nhóm hỗ trợ PlantUML (Tools → PlantUML), có thể import thẳng ra hình rồi chỉnh; nếu không, dùng làm bản mẫu để kéo-thả.

Sau khi vẽ xong trong VP → **export PNG/hình** vào thư mục của thành viên (mục `hinh/`), và dán vào báo cáo.

## 4. Mẫu chuẩn dùng chung

### 4.1. Mẫu đặc tả Use Case (kịch bản)

Đặc tả UC gồm **3 khối viết liền nhau** trong file markdown, theo thứ tự dưới đây.

**(a) Bảng 4 dòng — thông tin đầu use case**

| Mục | Nội dung |
|---|---|
| **Use case** | Tên use case |
| **Actor** | Ai thực hiện |
| **Tiền điều kiện** | Điều kiện trước khi chạy |
| **Hậu điều kiện** | Kết quả sau khi chạy thành công |

**(b) Khối `**Kịch bản chính**`** — danh sách đánh số 1., 2., 3.… mỗi bước một dòng (người dùng ↔ hệ thống). Khi một bước là *"hệ thống hiển thị màn hình X"* thì **ngay dưới bước đó** chèn phác thảo màn hình, rồi viết tiếp bước kế. Phác thảo **luôn viết bằng bảng markdown** (thụt vào 3 dấu cách để nằm trong item danh sách) — **không dùng khung ký tự `+---+`** vì khung này lệch ngay khi đổi font hoặc đổi độ rộng cột. Dùng hai loại bảng:

- **bảng thành phần màn hình** — ba cột cố định `Thành phần | Kiểu | Trạng thái khi mới mở màn`;
- **bảng dữ liệu mẫu** — nội dung thật của bảng/danh sách mà màn hình hiển thị.

Ví dụ:

```
**Kịch bản chính**

1. Nhân viên (đã đăng nhập) chọn menu **Ký hợp đồng** trên trang chính.
2. Hệ thống hiển thị màn hình **Tìm tay đua** (`gdTimTayDua.jsp`): ô nhập "Tên tay đua" đang rỗng, nút [Tìm], nút [+ Thêm tay đua mới]; bảng kết quả đang rỗng.

   **Màn hình *Tìm tay đua* (`gdTimTayDua.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Tên tay đua | ô nhập | rỗng, con trỏ đặt sẵn |
   | [Tìm] | nút | active |
   | Kết quả tìm kiếm | bảng | rỗng — nội dung hiện ở bước 4 |

3. Nhân viên nhập `Hamilton` và click [Tìm].
4. Hệ thống hiển thị bảng kết quả tìm kiếm:

   | TT | Mã | Tên | Ngày sinh | Quốc tịch | Đội hiện tại | Thao tác |
   |---|---|---|---|---|---|---|
   | 1 | HAM | Lewis Hamilton | 07/01/1985 | Anh | Mercedes | [Chọn] |

5. Nhân viên click [Chọn] ở dòng `HAM`.
```

**(c) Khối `**Ngoại lệ**`** — danh sách đánh số **theo bước bị lỗi** (`4a.`, `7a.`, `9b.`…), ví dụ: *"9a. Ngày bắt đầu vi phạm ràng buộc → báo lỗi, quay lại bước 7"*.

Sau khối Ngoại lệ đặt **một dòng ghi chú ánh xạ lớp biên** (gom một chỗ, không rải rác trong từng bước):

> **Ánh xạ sang lớp biên:** màn *Tìm tay đua* (`GDTimTayDua`) — ô "Tên tay đua" = `-inTenTayDua`, nút [Tìm] = `-subTim`, bảng kết quả = `-outsubDSTayDua`. Màn *Nhập hợp đồng* (`GDNhapHopDong`) — …

**Lý do tách 3 khối.** Markdown **không lồng được bảng vào ô của một bảng khác**, nên không thể viết thẳng bảng dữ liệu bên trong ô "Kịch bản chính" của bảng đặc tả. Khi sinh file Word bằng `docs/build-baocao-docx.py` (mục 4.3), script **tự ghép 3 khối lại thành đúng bảng 6 dòng như mẫu của thầy**, với các bảng phác thảo và bảng dữ liệu **lồng trong ô "Kịch bản chính"**. Vì vậy phải giữ đúng thứ tự và đúng tên hai nhãn `**Kịch bản chính**` / `**Ngoại lệ**` để script nhận diện.

> Bản Word sinh ra phải là bảng **đúng 6 dòng, đúng thứ tự** `Use case | Actor | Tiền điều kiện | Hậu điều kiện | Kịch bản chính | Ngoại lệ`. Không thêm dòng "Luồng phụ", "Thuộc tính", "Ràng buộc" vào bảng 4 dòng — nội dung đó chuyển thành ngoại lệ đánh số theo bước, hoặc ghi chú sau khối Ngoại lệ.
> Kịch bản chính phải **có dữ liệu thật và trạng thái nút** (dùng bộ dữ liệu mẫu ở `docs/03` mục 5), ví dụ: *"Nhân viên nhập `Hamilton` và click Tìm"*, *"nút [Lưu] chưa được active"*; các bảng phác thảo chèn kèm cũng dùng chính bộ dữ liệu đó.

### 4.2. Mẫu Test case (theo Bảng 6.7 giáo trình PDF — 4 cột, 3 nhóm)

Mỗi module viết **MỘT bảng 4 cột**:

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|

chia thành **3 nhóm** bằng dòng tiêu đề nhóm in đậm chen giữa bảng (theo Bảng 6.7):

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

### 4.3. Script sinh bản Word — `docs/build-baocao-docx.py`

Không convert `docs/BAO-CAO.md` bằng tay; nhóm dùng script có sẵn:

```
pip install python-docx
python docs/build-baocao-docx.py
```

Script đọc `docs/BAO-CAO.md` và sinh ra **`docs/BAO-CAO.docx`** với:

- **Times New Roman cỡ 13, giãn dòng 1.5** cho toàn bộ văn bản (đúng quy định trình bày báo cáo).
- **Heading đúng cấp** (`#` → Heading 1, `##` → Heading 2…) để Word **tự sinh mục lục** (References → Table of Contents); mỗi chương cấp 1 tự sang trang mới.
- **Ghép đặc tả Use Case thành bảng 6 dòng**: bảng 4 dòng + khối `**Kịch bản chính**` + khối `**Ngoại lệ**` được gộp lại thành một bảng 6 dòng, **bảng dữ liệu và khung phác thảo nằm lồng trong ô "Kịch bản chính"** (xem mục 4.1).
- **Tự chèn ảnh** từ mọi cú pháp `![…](đường-dẫn)`, căn giữa, kèm caption in nghiêng. Ảnh chưa vẽ **không làm hỏng file**: script in một dòng **chữ đỏ `[ CHƯA CÓ HÌNH: <tên-file> ]`** đúng vị trí đó, và cuối lượt chạy báo số ảnh đã chèn / số ảnh còn thiếu — dùng con số này để biết còn phải export bao nhiêu hình từ Visual Paradigm.

⇒ Sau mỗi lần sửa `docs/BAO-CAO.md` hoặc thêm ảnh mới, chỉ cần chạy lại script; **không sửa trực tiếp file `.docx`** (sẽ bị ghi đè).

## 5. Cấu trúc báo cáo cuối kỳ

Ghép tất cả thành **01 file Word** theo bố cục yêu cầu của giảng viên (2 phần):

**Trang bìa** — tên đề tài, danh sách thành viên **ghi rõ ai làm Use Case nào**.

**PHẦN 1 — CÔNG VIỆC CHUNG CỦA NHÓM**
1. **Mô tả yêu cầu bài toán, yêu cầu người dùng** (ngôn ngữ tự nhiên, khoảng 2–3 trang, chưa mô hình hóa): mục đích → phạm vi hệ thống (kèm câu chốt *"Những chức năng không đề cập đến thì mặc định là không thuộc phạm vi của hệ thống."*) → mô tả nghiệp vụ chi tiết từng chức năng → các đối tượng được quản lý và thuộc tính → quan hệ số lượng → các ràng buộc nghiệp vụ.
2. **Mô tả yêu cầu phần mềm**: xác định actor → yêu cầu chức năng (bảng Use case) → yêu cầu phi chức năng → **biểu đồ UC tổng quát** (là **mục con cuối** của chương này, không tách thành chương riêng).
3. **Xây dựng biểu đồ lớp thực thể**: phân tích xác định thực thể (bảng trích danh từ) → mô tả thực thể (thuộc tính, phương thức) → biểu đồ lớp thực thể **pha phân tích** → biểu đồ lớp thực thể **pha thiết kế** → thiết kế CSDL → thiết kế triển khai (package `view` → `dao` → `model`).

**PHẦN 2 — KẾT QUẢ TỪNG THÀNH VIÊN** (mỗi thành viên 1 chương, ghi **tên thành viên + tên Use Case** ở ngay trước nội dung)

Cấu trúc mỗi chương module (×4), theo đúng thứ tự:

> **UC chi tiết → đặc tả UC (kịch bản chính có phác thảo giao diện nhúng xen giữa các bước) → biểu đồ trạng thái (phân tích hoạt động) → biểu đồ lớp phân tích → biểu đồ lớp thiết kế (`.jsp` / `DAO` / `model`) → biểu đồ hoạt động (pha thiết kế) → thuyết minh (kịch bản v.3) + biểu đồ tuần tự → test case**

> **Đánh số mục trong mỗi chương module:** `1.` UC chi tiết · `2.` Đặc tả UC (mục phẳng, **không có mục con**) · `3.` Phân tích hoạt động — biểu đồ trạng thái · `4.` Biểu đồ lớp phân tích · `5.` Biểu đồ lớp thiết kế · `6.` Biểu đồ hoạt động (pha thiết kế) · `7.` Thuyết minh + biểu đồ tuần tự · `8.` Test case. **Không có mục "Thiết kế giao diện" ở bất kỳ cấp nào** — phác thảo giao diện nằm xen giữa các bước của Kịch bản chính trong mục `2`.

> Biểu đồ hoạt động đặt **sau** biểu đồ lớp thiết kế vì mỗi hành động trong biểu đồ hoạt động ứng với một phương thức đã thiết kế (giáo trình PDF mục 4.3.2 bước 1).

**Kết luận.**

> **Bắt buộc:** mọi vị trí hình trong báo cáo phải **nhúng ảnh thật** bằng cú pháp `![…](đường-dẫn)`, không được chỉ ghi caption `(Hình 5.7 — …)` — nếu không, bản Word xuất ra sẽ trắng hình. Mỗi hình phải có **lời văn mô tả** đi kèm, không để hình đứng trơ.

> Claude sẽ dựng bản thảo báo cáo (`docs/BAO-CAO.md`) tổng hợp từ tất cả nội dung; nhóm chỉ chèn hình VP đã export và xuất ra Word.

## 6. Cấu trúc thư mục repo

```
de-bai-f1.md                      ← mô tả bài toán
docs/                             ← tài liệu chung + kế hoạch
  00-ke-hoach-va-phan-cong.md
  01-dac-ta-yeu-cau.md
  02-usecase-tong-quat.md
  03-lop-thuc-the-va-csdl.md
  04-dac-ta-danh-muc-va-auth.md
  05-doi-chieu-chuan-thay.md      ← nội bộ: đối chiếu với giáo trình
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

## 7. Danh sách ảnh cần export từ Visual Paradigm (tổng **29 ảnh**)

> **Giao diện không có ảnh:** nhóm không vẽ mockup, nên bảng dưới **không có dòng ảnh giao diện nào**. Tổng cộng **6 ảnh mỗi module × 4 module + 5 ảnh chung = 29 ảnh**.

**Quy tắc tên file:** chữ thường, không dấu, ngăn cách bằng `-`, đuôi `.png`. Ảnh của module đặt tên `m<số module>-<tên biểu đồ>.png`. Tên file ở bảng dưới là **tên chốt**, phải trùng với bảng "Danh sách ảnh cần export" ở đầu `noi-dung.md` của từng module và với đường dẫn `![…](…)` trong `docs/BAO-CAO.md`.

### 7.1. `docs/hinh/` — phần chung của nhóm (5 ảnh)

| Tên file | Biểu đồ | Blueprint | Trạng thái |
|---|---|---|---|
| `uc-tongquat.png` | Biểu đồ UC tổng quát | `docs/02` mục 4 | đã vẽ — **VẼ LẠI** (thêm UC trừu tượng `Quản lý danh mục`, actor trừu tượng `ThanhVien`, bỏ 4 quan hệ include, đổi mũi tên thành đường kẻ trơn) |
| `lop-thucthe-phantich.png` | Lớp thực thể **pha phân tích** (không `id`, không kiểu dữ liệu, không phương thức) | `docs/03` | chưa vẽ |
| `lop-thucthe-thietke.png` | Lớp thực thể **pha thiết kế** (có `id`, có kiểu dữ liệu, có thuộc tính kiểu đối tượng) | `docs/03` | chưa vẽ |
| `package-trienkhai.png` | Thiết kế triển khai — package `view` → `dao` → `model` | `docs/03` | chưa vẽ |
| `csdl.png` | Biểu đồ thiết kế cơ sở dữ liệu (ERD, 12 bảng) | `docs/03` mục 4.6 | chưa vẽ — dùng **Entity Relationship Diagram** của VP, không phải Class Diagram |

> File cũ `docs/hinh/lop-thucthe.png` **bị thay bởi 2 file** `lop-thucthe-phantich.png` và `lop-thucthe-thietke.png` — xóa khỏi repo sau khi có 2 ảnh mới.

### 7.2. Ảnh của từng module (mỗi module đúng **6 ảnh**)

> **Mẫu hình bắt buộc (giáo trình PDF `BG HP TTTN 2 CNPM`):** biểu đồ **UC chi tiết** vẽ theo mẫu **Hình 3.2/3.3/3.4** — không có khung hệ thống; có phân cấp actor `Thành viên` → `Nhân viên`/`Quản lý`; UC `Đăng nhập` gắn với actor cha, UC `NV đăng nhập`/`QL đăng nhập` kế thừa nó và được UC chính include. Biểu đồ **trạng thái** theo mẫu **Hình 3.9/3.11**. Biểu đồ **lớp phân tích** theo mẫu **Hình 3.6** — lớp biên `GDXxx` chỉ có thuộc tính, tiền tố `in/out/sub/inout/outsub`; lớp thực thể không `id`, không kiểu dữ liệu. Biểu đồ **lớp thiết kế** theo mẫu **Hình 4.4** — **không dùng khung package**, ba tầng xếp theo hàng `gdXxx.jsp` → `XxxDAO` → lớp thực thể; lớp cha `DAO` chỉ có `-con : Connection` và `+DAO()`. Biểu đồ **hoạt động** theo mẫu **Hình 4.9** — khung `Xử lí tại gdXxx.jsp` cho từng trang, node DAO tách riêng. Biểu đồ **tuần tự** theo mẫu **Hình 4.10/4.12** — đánh số message, trang chính mở đầu và kết thúc, luồng lưu có `setter()`.

Toàn bộ ảnh cũ trong `hinh/` sẽ bị bỏ và vẽ lại từ đầu theo blueprint PlantUML trong `noi-dung.md` của từng module. Bản render tham chiếu của mỗi blueprint có sẵn ở `hinh/ref/` — mở ra xem rồi vẽ lại trong Visual Paradigm.

| Module | Tên file | Biểu đồ | Blueprint |
|---|---|---|---|
| M1 | `m1-uc-chitiet.png` | UC chi tiết | `Module 1 - Quan/noi-dung.md` mục 1 |
| M1 | `m1-trangthai.png` | Biểu đồ trạng thái | mục 3 |
| M1 | `m1-lop-phantich.png` | Lớp phân tích (lớp biên + lớp thực thể) | mục 4 |
| M1 | `m1-lop-mvc.png` | Lớp thiết kế (`.jsp` / `DAO` / `model`) | mục 5 |
| M1 | `m1-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | mục 6 |
| M1 | `m1-tuantu.png` | Biểu đồ tuần tự | mục 7 |
| M2 | `m2-uc-chitiet.png` | UC chi tiết | `Module 2 - Kin/noi-dung.md` mục 1 |
| M2 | `m2-trangthai.png` | Biểu đồ trạng thái | mục 3 |
| M2 | `m2-lop-phantich.png` | Lớp phân tích | mục 4 |
| M2 | `m2-lop-mvc.png` | Lớp thiết kế | mục 5 |
| M2 | `m2-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | mục 6 |
| M2 | `m2-tuantu.png` | Biểu đồ tuần tự | mục 7 |
| M3 | `m3-uc-chitiet.png` | UC chi tiết | `Module 3 - Kiet/noi-dung.md` mục 1 |
| M3 | `m3-trangthai.png` | Biểu đồ trạng thái | mục 3 |
| M3 | `m3-lop-phantich.png` | Lớp phân tích | mục 4 |
| M3 | `m3-lop-mvc.png` | Lớp thiết kế | mục 5 |
| M3 | `m3-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | mục 6 |
| M3 | `m3-tuantu.png` | Biểu đồ tuần tự | mục 7 |
| M4 | `m4-uc-chitiet.png` | UC chi tiết | `Module 4 - Thanh/noi-dung.md` mục 1 |
| M4 | `m4-trangthai.png` | Biểu đồ trạng thái | mục 3 |
| M4 | `m4-lop-phantich.png` | Lớp phân tích | mục 4 |
| M4 | `m4-lop-mvc.png` | Lớp thiết kế | mục 5 |
| M4 | `m4-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế | mục 6 |
| M4 | `m4-tuantu.png` | Biểu đồ tuần tự | mục 7 |
