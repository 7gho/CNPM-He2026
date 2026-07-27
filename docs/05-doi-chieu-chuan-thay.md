# Đối chiếu project với chuẩn của thầy — danh sách cần sửa

> Nguồn đối chiếu: `Lectures/B1.Thu thap yeu cau.docx`, `Lectures/B2. Phan tich (final).docx`, `Lectures/B3.Thiet ke (final).docx` (đọc cả text + 10 hình mẫu), `Lectures/BG CNPM 2020.doc` (giáo trình cũ, mục 11.11 — đề F1 gốc), **`Lectures/BG HP TTTN 2 CNPM 2020 final.pdf` (giáo trình PDF chính thức — NGUỒN ƯU TIÊN CAO NHẤT khi có xung đột)**, `SE-list-of-project.pdf` (đề bài gốc, project 10), `Yeu cau bai tap nhom SE.docx`.
>
> Sắp theo thứ tự nên làm. P0 phải xong **trước khi vẽ tiếp** trong Visual Paradigm.
>
> **Cập nhật lần 2:** sau khi đọc PDF `BG HP TTTN 2 CNPM 2020 final.pdf` (235 trang, bản "final") và đề bài gốc `SE-list-of-project.pdf`, bổ sung **mục P4 (đối chiếu đề bài gốc)** và **mục P5 (đối chiếu giáo trình PDF — có 2 điểm LẬT lại kết luận cũ)** ở cuối file. Đọc P5 trước khi vẽ bất kỳ hình nào.
>
> **Cập nhật lần 3:** bổ sung **mục P6 — quyết định bỏ ảnh giao diện**, chuyển giao diện thành phác thảo đặt trong mục Đặc tả UC. P6 sửa đè phần giao diện của P0-7 và P5-D; số ảnh phải vẽ giảm từ 33 xuống 28.

---

## P0 — Sai kiến trúc, phải sửa trước khi vẽ

### P0-1. Bỏ lớp Control khỏi biểu đồ lớp phân tích (cả 4 module)

Slide B2 (hình mẫu modul đăng kí học) chỉ có **2 tầng**: lớp biên `GDxxx` + lớp thực thể. Không có Control.

| Module | Lớp phải bỏ | Vị trí |
|---|---|---|
| M1 | `HopDongControl` | `Module 1 - Quan/noi-dung.md:118-123` |
| M2 | `DangKyChangControl` | `Module 2 - Kin/noi-dung.md:94-98` |
| M3 | `KetQuaControl` | `Module 3 - Kiet/noi-dung.md:118-124` |
| M4 | `QuyetToanControl` | `Module 4 - Thanh/noi-dung.md:97-101` |

Phương thức của Control **chuyển xuống lớp thực thể** (B2 bước 3: *"đề xuất gán hành động tương ứng với chức năng này cho lớp thực thể nào"*). Ví dụ thầy: `Dangkihoc{+getDangKiCuaSV(), +luuDangKi()}`.

Đặc biệt: `KetQuaControl.xepHangVaTinhDiem()` (M3) và `QuyetToanControl.sapXep()` (M4) là **nghiệp vụ lõi** — phải nằm ở `KetQua`.

Sửa kèm: `docs/03-lop-thuc-the-va-csdl.md:46` ("kiểm ở tầng Control"), `docs/00-ke-hoach-va-phan-cong.md:37` (chỉ đạo cả nhóm vẽ boundary/control/entity).

### P0-2. Bỏ stereotype `<<boundary>>` / `<<control>>` / `<<entity>>`

Hình mẫu của thầy dùng **hộp class trơn**, phân biệt tầng bằng tiền tố tên (`GD…`). Có ở M1:97,101,108,118,124,132,139 · M2:85,94,99,106,112,119,124 · M3:105,118,126,136,144,152,159 · M4:86,97,102,107,111,118,123,128.

*(Việc VP không vẽ được `<<>>` hoá ra lại đúng chuẩn.)*

### P0-3. Đổi mũi tên `-->` thành đường kẻ trơn `--` trong mọi biểu đồ lớp

Thầy chỉ dùng: đường kẻ trơn (association) + hình thoi rỗng ◇ (aggregation) + hình thoi đặc ♦ (composition) + tam giác rỗng ▷ (kế thừa). **Không có mũi tên định hướng.**

Vị trí: M1:148-153, 192-200 · M2:130-135, 174-183 · M3:172-179, 256-268 · M4:138-144, 191-203 · `docs/02-usecase-tong-quat.md:62-72` (liên kết actor–UC).

### P0-4. Lớp biên: bỏ hết phương thức, đổi tên thuộc tính theo convention của thầy

Thầy: **lớp biên chỉ có thuộc tính**, đặt tên theo *chức năng dữ liệu* chứ không theo loại control UI:

- `sub…` = submit (nút bấm)
- `in…` = ô nhập vào
- `out…` = vùng hiện ra
- `inout…` = vừa nhập vừa hiện
- `outsub…` = vừa hiện vừa cho chọn/submit

Mẫu thật của thầy: `GDChonnganh{-inoutDSNganh, -inoutDSKihoc, -subTieptuc}`, `GDMonhoc{-outsubDSMonhoc}`.

Đề xuất chuyển đổi:

| Module | Hiện tại | Sửa thành |
|---|---|---|
| M1 | `GDTimTayDua{txtTen, btnTim, lstTayDua, hienDanhSach(), chonTayDua()}` | `GDTimTayDua{-inTenTayDua, -subTim, -outsubDSTayDua}` |
| M1 | `GDNhapHopDong{lblTayDua, lstHopDongCu, cboDoi, dtpBatDau, btnLuu, hienHopDongCu(), baoLoi(), inHopDong()}` | `GDNhapHopDong{-outTayDua, -outDSHopDongCu, -inDoiDua, -inNgayBatDau, -subLuu}` |
| M2 | `GDDangKyChang{cboChang, cboDoi, lstTayDua, btnLuu, hienDanhSachTayDua(), inPhieuDangKy(), baoLoi()}` | `GDDangKyChang{-inChangDua, -inDoiDua, -outsubDSTayDua, -subLuu, -subSua}` |
| M3 | `GDNhapKetQua{cboChang, tblKetQua, btnTinh, btnLuu, hienDanhSachChang(), …}` | `GDNhapKetQua{-inChangDua, -subTiepTuc, -inoutBangKetQua, -subTinhKetQua, -outBangDoiSoat, -subLuu}` |
| M4 | `GDQuyetToan{btnQuyetToan, tblCaNhan, tblDoi, txtThuong, btnLuu, hienXepHang(), …}` | `GDQuyetToan{-subQuyetToan, -outXHCaNhan, -outXHDoi, -inMucThuong, -subTinhThuong, -subLuu}` |

### P0-5. Bỏ lifeline Controller và lifeline CSDL khỏi biểu đồ tuần tự

Sequence mẫu của thầy (B3 + giáo trình chương 8): lifeline = **actor + các trang .jsp + các DAO + các Entity**. Không có Controller, **không có lifeline CSDL, không có SQL trong message**.

Thay vào đó, mỗi thao tác là **chuỗi 7 message cố định**:

```
1. gdXxx.jsp  →  XxxDAO        : goi
2. XxxDAO     →  XxxDAO        : getYyy()        ← self-call, tên hàm nghiệp vụ
3. XxxDAO     →  Xxx (entity)  : goi
4. Xxx        →  Xxx           : Xxx()           ← self-call constructor, "đóng gói thông tin"
5. Xxx        ⇢  XxxDAO        : tra ve
6. XxxDAO     ⇢  gdXxx.jsp     : tra ve
7. gdXxx.jsp  ⇢  actor         : hien thi
```

Vị trí phải sửa — lifeline CSDL: M1:217 · M2:200 · M3:284 · M4:219. Lifeline Controller: M1:213 · M2:195 · M3:280 · M4:215. Message SQL: M1:225,242,250,267,275,283 · M2:208,216,233,250,259 · M3:292,309,345,355 · M4:227,235,243,272.

**Lifeline Entity phải bổ sung:** M1 `TayDua, DoiDua, HopDong` · M2 `ChangDua, DoiDua, TayDua, DangKyChang` · M3 `ChangDua, DangKyChang, KetQua` · M4 `MuaGiai, ChangDua, KetQua, TraoGiai`.

**Đánh số message** 1,2,3… (bật *Show sequence number* trong VP). Nhãn ngắn: `goi` / `tra ve` / `hien thi` / `click Luu` / `chon chang` — chỉ self-call mới ghi tên hàm.

### P0-6. Bỏ tầng Controller khỏi biểu đồ lớp thiết kế

Giáo trình chương 8 gọi **DAO chính là "tầng điều khiển" của MVC**:

> *"Các lớp tầng điều khiển: UserDAO là lớp truy cập dữ liệu xử lí thông tin liên quan đến thành viên hệ thống. RoomDAO là lớp truy cập dữ liệu xử lí thông tin liên quan đến phòng. Hai lớp này đều **kế thừa lớp DAO** để xử lí cơ chế dùng chung truy cập vào cơ sở dữ liệu."*

⇒ Vẫn gọi là "mô hình MVC" được (đề bài giáo trình có ghi *"trích các lớp theo mô hình MVC"*), nhưng **M** = entity/model, **V** = trang .jsp, **C** = các DAO. **Không có lớp `XxxController` riêng.**

Phải bỏ: `HopDongController` (M1:168,179-181,192-197) · `DangKyChangController` (M2:148,161-163,174-179) · `KetQuaController` (M3:224,238-240,256-261) · `QuyetToanController` (M4:163,173-175,191-196) · `docs/BAO-CAO.md:142,398` · `docs/01-dac-ta-yeu-cau.md:67`.

**Nên thêm:** lớp cha `DAO` (cơ chế kết nối CSDL dùng chung), các `XxxDAO` kế thừa nó — đúng như thầy làm.

**Nên thêm:** biểu đồ package thiết kế triển khai `view` → `dao` → `model` (B3 có hình mẫu).

### P0-7. Số UC con = số giao diện = số lớp biên = số trang .jsp

B1 (UC chi tiết bước 2): *"Phân rã UC chính thành UC con: **mỗi giao diện** tương tác với người dùng có thể đề xuất thành một use case con."* B2 (bước 1): *"Mỗi giao diện xuất hiện có thể đề xuất thành một lớp biên."*

Hiện đang lệch:

| Module | UC con | Mockup giao diện | Lớp biên | .jsp |
|---|---|---|---|---|
| M1 | 4 | 2 | 3 | 3 |
| M2 | 3 | 1 | 1 | 2 |
| M3 | 3 | 1 ("màn hình duy nhất") | 1 | 2 |
| M4 | 3 | 1 | 1 | 2 |

⇒ Với mỗi module: **chốt danh sách màn hình trước**, rồi suy ra UC con / lớp biên / mockup / jsp cho khớp 1-1.

### P0-8. Bỏ UC `Đăng nhập` khỏi UC chi tiết của 4 module

Có ở M1:24,41 · M2:23,38 · M3:23,42 · M4:23,38 — nhưng không có giao diện, không có lớp biên, không có jsp, không có trong sequence ⇒ vi phạm "mỗi giao diện → 1 UC con". Ngoài ra thầy ghi rõ UC đăng nhập *"sẽ không đạt hoặc đánh giá kết quả thấp"*.

"Đã đăng nhập" đã nằm ở **Tiền điều kiện** (M1:54, M2:50, M3:54, M4:50) — thế là đủ.

---

## P1 — Thiếu hẳn mục bắt buộc

### P1-1. Thiếu THUYẾT MINH biểu đồ tuần tự (cả 4 module)

Yêu cầu bài tập ghi rõ: *"**Thuyết minh và** vẽ biểu đồ tuần tự cho UC"*. Hiện `docs/BAO-CAO.md:225-227, 276-278, 328-330, 379-381` chỉ có caption `(Hình …)`, **không một chữ giải thích**. Grep "thuyết minh" toàn repo = 0 kết quả.

Thuyết minh = **kịch bản phiên bản 3** (B3 bước 1), mẫu của thầy:

```
1. Trang gdChonnganh.jsp gọi lớp KhoaDAO yêu cầu tìm danh sách ngành học của sinh viên.
2. Lớp KhoaDAO gọi hàm getNganhhoccuaSV()
3. Hàm getNganhhoccuaSV() gọi lớp Khoa để đóng gói thông tin
4. Lớp Khoa đóng gói thông tin thực thể
5. Lớp Khoa trả kết quả về cho hàm getNganhhoccuaSV()
6. Hàm getNganhhoccuaSV() trả kết quả cho trang gdChonnganh.jsp
7. Trang gdChonnganh.jsp hiển thị cho sinh viên
```

### P1-2. Thiếu "Mô tả thực thể (thuộc tính, phương thức)" — Chương 4 báo cáo

`docs/BAO-CAO.md:159-165` chỉ liệt kê **tên** 10 lớp rồi nhảy sang hình. Yêu cầu bài tập đòi 3 phần con: phân tích xác định thực thể / **mô tả thực thể (thuộc tính, phương thức)** / vẽ biểu đồ.

⇒ Bê bảng `docs/03-lop-thuc-the-va-csdl.md:7-18` vào, bổ sung cột phương thức nghiệp vụ.

### P1-3. Thiếu bảng trích danh từ (B2 bước 2-3)

`docs/03:3` và `BAO-CAO.md:161` chỉ nói suông *"rút ra bằng phương pháp trích danh từ"* rồi đưa kết quả. Thiếu bước 2 (liệt kê danh từ, nhóm người / vật / thông tin) và bước 3 (đánh giá: thành lớp / thành thuộc tính của lớp X / loại vì trừu tượng–ngoài phạm vi).

⇒ Thêm bảng 3 cột: `Danh từ | Nhóm | Kết luận`.

### P1-4. Thiếu biểu đồ lớp thực thể PHA PHÂN TÍCH

`docs/03` chỉ có **một** bản, và đã là pha thiết kế (có `id`, có kiểu dữ liệu). Thầy tách rõ 2 bản:

| | Pha phân tích (B2) | Pha thiết kế (B3) |
|---|---|---|
| `id` | **không có** | có |
| Kiểu dữ liệu | **không có** | có (`String`, `int`, `Date`, `float`) |
| Phương thức | **không có** | không có |
| Thuộc tính kiểu đối tượng | không | **có** (`-dsChangDua : ChangDua[]`) |
| Quan hệ | association + ◇ ♦ ▷ | đã chuyển hết sang ◇ / ♦ |

⇒ Thêm mục "lớp thực thể pha phân tích" + PlantUML riêng. Đồng thời bỏ `id` khỏi mục 4 (lớp phân tích module) của cả 4 file: M1:125,133,140 · M2:100,107,113,120,125 · M3:127,137,145,153,160 · M4:103,108,112,119,124,129. Riêng M3:105-170 còn ghi cả kiểu dữ liệu (`cboChang : Combobox`, `id : int`) — bỏ hết.

### P1-5. Thiếu quan hệ đối tượng (aggregation / composition / kế thừa)

`docs/03:119-130` — cả 12 quan hệ đều là association trơn `--`. B2 bước 5 + B3 bước 3 đòi chuyển sang ◇ / ♦, và hình mẫu của thầy có đủ ◇ ♦ ▷.

Đề xuất: `MuaGiai *-- ChangDua` · `ChangDua *-- DangKyChang` · `DangKyChang *-- KetQua` · `MuaGiai *-- TraoGiai` · `MuaGiai o-- ThamGia` · `DoiDua o-- HopDong`.

### P1-6. Thiếu thuộc tính kiểu đối tượng ở lớp thực thể pha thiết kế (B3 bước 4)

Mẫu thầy: `Monhoc{-dsdaudiem : MonhocDaudiem[], -dsMontienquyet : Monhoc[]}`, `Lichhoc{-lhp : Lophocphan, -gv : Giangvien}`.

Đề xuất: `MuaGiai{-dsChangDua : ChangDua[], -dsThamGia : ThamGia[]}` · `HopDong{-tayDua : TayDua, -doiDua : DoiDua}` · `DangKyChang{-changDua : ChangDua, -tayDua : TayDua, -doiDua : DoiDua, -ketQua : KetQua}` · `TraoGiai{-muaGiai : MuaGiai, …}`.

### P1-7. Chương 1 báo cáo thiếu mục "Phạm vi hệ thống"

Grep "phạm vi" trong `BAO-CAO.md` = 0 kết quả. B1 bước 2 đòi liệt kê **ai được dùng + mỗi người làm chức năng nào**, kèm câu chốt:

> *"Những chức năng không đề cập đến thì mặc định là không thuộc phạm vi của hệ thống."*

Cũng thiếu **bước 4** (đối tượng + thuộc tính, nhóm theo chủ đề) và **bước 5** (quan hệ số lượng dạng "Một X có nhiều Y") ở dạng mục riêng.

### P1-8. Chương 1 chỉ mô tả nghiệp vụ 4/11 chức năng

`BAO-CAO.md:40-84` mô tả 4 module. Thiếu luồng `→` chi tiết cho: Đăng nhập, Đổi mật khẩu, Quản lý mùa giải / tay đua / đội đua / chặng đua, Đăng ký đội tham gia mùa giải. B1 bước 3: *"với **mỗi** chức năng ở bước 2, mô tả chi tiết hoạt động nghiệp vụ"*.

### P1-9. Thiếu 19/26 ảnh, và báo cáo chưa nhúng ảnh thật

`grep '!\[' docs/BAO-CAO.md` = **0 kết quả** — 26 vị trí hình đều chỉ là chữ `(Hình 5.7 — …)`. Xuất Word sẽ ra file **không có biểu đồ nào**.

| Thư mục | Có / Cần | Thiếu |
|---|---|---|
| `docs/hinh/` | 2/2 | — (nhưng `lop-thucthe.png` phải vẽ lại: `KetQua.dnf` → `trangThai`) |
| `Module 1 - Quan/hinh/` | 2/7 | `m1-lop-phantich`, `m1-giaodien-timtaydua`, `m1-giaodien-nhaphopdong`, `m1-lop-mvc`, `m1-tuantu` |
| `Module 2 - Kin/hinh/` | 1/6 | `m2-hoatdong`, `m2-lop-phantich`, `m2-giaodien-dangky`, `m2-lop-mvc`, `m2-tuantu` |
| `Module 3 - Kiet/hinh/` | **0/6** | toàn bộ |
| `Module 4 - Thanh/hinh/` | 4/6 | `m4-lop-phantich`, `m4-giaodien-quyettoan` (+ `m4-tuantu`, `m4-lop-mvc` phải vẽ lại) |

---

## P2 — Sai format so với mẫu của thầy

### P2-1. Test case sai hẳn format ⚠️

Giáo trình mục **9.5.3** có mẫu rất cụ thể, gồm **3 phần**:

**(a) Lập kế hoạch test** — bảng liệt kê trường hợp cần kiểm thử:

| TT | Chức năng | Các trường hợp cần kiểm thử |
|---|---|---|
| 1 | Sửa thông tin phòng | Sửa một phòng đã có trong CSDL |
| 2 | | Sửa một phòng chưa có trong CSDL |
| 3 | | Sửa liên tiếp hai lần cùng một phòng |

**(b) Từng test case** — tiêu đề dạng `Test case 1: <trường hợp> (test case chuẩn)`, rồi:

- **CSDL trước khi test:** in nội dung **từng bảng** với dữ liệu thật
- **Bảng 2 cột:**

| Các bước thực hiện | Kết quả mong đợi |
|---|---|
| 1. Khởi tạo phần mềm | Giao diện đăng nhập hiện ra, có ô nhập username, password và nút đăng nhập |
| 2. Nhập username = manager, password = manager, click đăng nhập | Giao diện trang chủ quản lí hiện ra. Có 3 nút: Quản lí khách sạn / Quản lí phòng / Xem thống kê |
| … | … |

- **CSDL sau khi test:** in lại bảng bị thay đổi với dữ liệu mới

**Hiện tại** cả 4 module + báo cáo dùng bảng 6 cột `ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi`, mỗi test case 1 dòng — **không có CSDL trước/sau, không tách từng bước**. Đây là lệch nặng nhất về format vì đề bài ghi rõ *"Viết test case **chuẩn** cho UC"*.

Ngoài ra `BAO-CAO.md:231-236, 282-287, 334-340, 385-390` còn rút xuống **4 cột** (mất "Tiền điều kiện" và "Các bước") — thụt lùi so với bản `noi-dung.md`.

### P2-2. Kịch bản chính chưa đủ chi tiết

Thầy: *"Kịch bản càng chi tiết càng tốt: thông tin hệ thống hiện lên, thông tin người dùng nhập vào…"*. Mẫu của thầy có **dữ liệu thật** + **trạng thái nút**:

> *"Giao diện đăng kí học hiện lên, có ô chọn kì học; bảng danh sách các môn học/lớp học phần đã đăng kí **đang rỗng**; nút tiếp tục và nút lưu **chưa được active**."*
> *"Giảng viên nhập đầu điểm thi: A: 5, C:6, D:7, S:8, V:9 và click lưu"*

Hiện M1:56, M2:52, M3:56, M4:52 (và `BAO-CAO.md:204,256,307,360`) đều không có dữ liệu thật, không có trạng thái nút. M4:52 sơ sài nhất (không nêu tên cột của 2 bảng xếp hạng).

⇒ Viết lại dùng bộ dữ liệu mẫu đã có ở `docs/03` mục 5. Ví dụ M1 bước 3: *"Nhân viên nhập 'Hamilton' và click Tìm"*; bước 6: *"bảng hợp đồng cũ hiện 1 dòng: Mercedes | 01/01/2013 | (trống); nút Lưu chưa active"*.

Cũng thiếu **ghi chú lặp** *"(Lặp lại bước X-Y cho đến khi…)"* ở M2 (chọn nhiều tay đua), M3 (nhập từng tay đua), M4 (nhập thưởng từng hạng).

### P2-3. Tên UC là hành động của HỆ THỐNG (thầy nhấn mạnh)

> *"Tên use case phải là **động từ chỉ hành động của actor**. Không nên là động từ chỉ hành động của hệ thống."*

| Tên hiện tại | Vấn đề | Đề xuất |
|---|---|---|
| `Nhập kết quả và tính điểm` (M3:25,37) | "tính điểm" là việc hệ thống làm — chính kịch bản M3:56 bước 6 ghi *"Hệ thống tự động xếp hạng… gán điểm"* | `Nhập kết quả chặng` |
| `Cập nhật kết quả và tính điểm chặng đua` (`docs/02`, `BAO-CAO:151`) | như trên | `Cập nhật kết quả chặng đua` |
| `Tổng hợp xếp hạng` (M4:24,35) | Quản lý chỉ click menu; "tổng hợp/xếp hạng" là hệ thống | `Xem bảng tổng sắp` |
| `Quản lý mùa giải / tay đua / đội đua / chặng đua` (`docs/02:19-22`) | "Quản lý" gộp 4 hành động CRUD; thầy cảnh báo UC kiểu "thêm sửa xóa đơn giản" | Tách, hoặc gộp bằng **UC trừu tượng cha** "Quản lý danh mục" + generalization (B1 UC tổng quan bước 3) |

### P2-4. Mẫu đặc tả UC phải đúng 6 dòng

`Module 2 - Kin/noi-dung.md:53` và `BAO-CAO.md:257` có dòng thừa **"Luồng phụ — Thay tay đua trước ngày đua"** ⇒ bảng 7 dòng. Mẫu thầy chính xác 6 dòng: `Use case | Actor | Tiền điều kiện | Hậu điều kiện | Kịch bản chính | Ngoại lệ`.

⇒ Chuyển thành ngoại lệ đánh số theo bước (`3a. Chặng+đội đã có đăng ký → …`) hoặc tách thành UC riêng.

`docs/04-dac-ta-danh-muc-va-auth.md` cũng lệch: mục 1 (dòng 7-12) thiếu dòng `Use case` và `Actor`, sai thứ tự; mục 2 (18-25) thêm dòng "Thuộc tính", thiếu "Hậu điều kiện"; mục 3 (29-36) thay "Ngoại lệ" bằng "Ràng buộc". Kịch bản ở `docs/04` cũng chưa đánh số 1,2,3…

### P2-5. Biểu đồ lớp phân tích phải giữ quan hệ giữa các lớp thực thể

B2: *"Quan hệ giữa các lớp thực thể phải thống nhất, đồng bộ với quan hệ giữa chúng trong biểu đồ lớp thực thể đã vẽ ở bước trước."*

Hiện M1:148-153, M2:130-135, M4:138-144 **không có quan hệ nào** giữa các entity (chỉ Control → entity). M3:178-179 có 2 quan hệ nhưng **sai số lượng** (vẽ 1-1, đúng phải 1-n).

⇒ Copy quan hệ tương ứng từ `docs/03:119-130` vào mục 4 của cả 4 file.

### P2-6. Tên khóa ngoại nên theo quy ước `tblAid`

Hình CSDL mẫu của thầy: `tblTruongid`, `tblKhoaid`, `tblThanhvienid`. Hiện `docs/03:37-42` dùng `muaGiaiId`, `doiDuaId`, `changDuaId`… Cũng **thiếu kiểu dữ liệu cho các cột** (`integer(10)`, `varchar(255)`, `float(10)`, `date`).

### P2-7. Thiết kế CSDL thiếu bước 5 "loại bỏ thuộc tính dẫn xuất"

B3 CSDL bước 5, ví dụ thầy *"bỏ điểm TBM/TB chữ, **bỏ hết bảng thống kê**"*.

`tblTraoGiai` đang giữ `hang, tongDiem, tongThoiGian` — đều là **cộng dồn từ `tblKetQua`**, đúng dạng bảng thống kê mà thầy bảo bỏ. `tblKetQua.hang/diem` cũng suy ra được.

⇒ Hoặc bỏ, hoặc **biện luận rõ** là snapshot chốt sổ theo luật (giữ để có bằng chứng trao giải), chứ không được im lặng bỏ qua bước 5.

---

## P3 — Lỗi vặt, sửa nhanh

| # | Vị trí | Lỗi | Sửa |
|---|---|---|---|
| 1 | `BAO-CAO.md:13` | MSSV `B22DCCVT270` thừa 1 chữ C | `B22DCVT270` |
| 2 | M3:305,307,309,345 | cột `changId` — nơi khác dùng `changDuaId` | thống nhất `changDuaId` |
| 3 | M3:22/27/35/52 | tên UC chính có **4 biến thể** trong cùng file | chốt 1 tên |
| 4 | `BAO-CAO.md` vs `docs/02` vs mục 1 các module | mỗi UC có **3 tên** khác nhau | chốt 1 tên/UC dùng ở mọi nơi |
| 5 | M3:168-170 vs M3:228 | `xoaTheoChang` vs `deleteByChang`, `them()` vs `insert()` | thống nhất |
| 6 | M4:135 vs M4:99 vs M4:260 | `tinhThuong` có 3 tên/3 nơi | thống nhất `TraoGiai.tinhTienThuong()` |
| 7 | M1:29,44 | `Thêm tay đua` extend sai UC gốc (`Nhập thông tin hợp đồng`); ngoại lệ 4a thuộc màn *Tìm tay đua* | `THEM ..> TIM : extend` |
| 8 | M1:256-259, M4:256-266 | lệch activate/deactivate trong sequence | cân bằng |
| 9 | M4:111-117 | lớp `KetQua` thiếu thuộc tính `hang` nhưng SQL countback dùng `SUM(hang=1)` | thêm `hang` |
| 10 | M4:164 | `MuaGiaiDAO` không có lifeline trong sequence, `muaGiaiId` xuất hiện từ hư không | thêm lifeline + cặp message |
| 11 | M2:168-173 | package Entity thiếu lớp `HopDong` | thêm |
| 12 | M2:141 vs M2:85-89 | nút [Sửa] và cột "Trạng thái đăng ký" có ở mockup nhưng không có ở lớp biên | thêm `-subSua` |
| 13 | M2:58-75, M4:57-76 | biểu đồ hoạt động quá sơ sài (8 và 11 node, 1 quyết định) | lấy M3:61-93 làm mốc |
| 14 | `docs/01:54` | FR5.2 vẫn ghi tie-break "tăng dần tổng thời gian" — mâu thuẫn countback | sửa sang countback |
| 15 | `docs/01:48-49` | FR4 vẫn chỉ có DNF, thiếu DSQ | thêm DSQ |
| 16 | `docs/01:33-37` | FR2 thiếu chức năng "thêm mới tay đua" trong luồng M1 | thêm FR2.1b |
| 17 | `docs/01:47-50` | thiếu FR cho ràng buộc "cảnh báo ghi đè + tính lại điểm toàn chặng" | thêm FR4.4 |
| 18 | M2:275-280 | test case không phủ luồng thay tay đua + ràng buộc sắp xếp alphabet | thêm TC5, TC6 |
| 19 | M4:288-293 | thiếu test case cho ràng buộc quan trọng nhất M4 (điểm đội cộng theo `DangKyChang.doiDuaId`, không theo đội hiện tại) | thêm TC dùng ca Hamilton đổi đội giữa mùa |
| 20 | M1:130,143-146 | tên phương thức kiểu CRUD (`getByTen`, `insert`) | đổi sang tên nghiệp vụ (`getTayDuaTheoTen`, `luuHopDong`) — thầy dùng `getKhoaCuaSV()`, `luuDangKi()` |
| 21 | M1:91 vs M1:167 | `GDKyHopDong` có ở lớp biên nhưng không có mockup, không có jsp | bỏ hoặc bổ sung |
| 22 | `BAO-CAO.md:320,322` vs M3:12,186 | báo cáo khai 2 màn M3, `noi-dung` ghi "màn hình duy nhất" | chốt 1 phương án |
| 23 | `docs/02:9,42` | actor `ThanhVien` khai trừu tượng ở bảng nhưng PlantUML không đánh dấu | `abstract actor` |
| 24 | `docs/02:5-11` | không xét actor gián tiếp (Đội đua, Ban tổ chức, Tay đua) | bổ sung hoặc ghi rõ lý do loại |
| 25 | `docs/03:26,48` | quan hệ 1-1 `DangKyChang`–`KetQua` để ngỏ *"tùy nhóm"* | chốt (thầy: 1-1 nên gộp) |
| 26 | `docs/00:76-90` | sơ đồ thư mục lỗi thời, thiếu `04`, `BAO-CAO.md`, `hinh/` | cập nhật |
| 27 | `BAO-CAO.md:20-28` | mục lục chỉ 9 dòng cấp chương, không mục con, không số trang | bổ sung khi lên Word |
| 28 | `BAO-CAO.md` | không có heading "Phần 1 — Công việc chung" / "Phần 2 — Kết quả từng thành viên"; UC tổng quát bị tách thành chương riêng thay vì mục con của "Mô tả yêu cầu phần mềm" | thêm 2 heading phân định |
| 29 | M1,M2,M4 mục 1 | thiếu system boundary (chỉ M3:34-39 có `rectangle`) | thống nhất |

---

## Phần riêng: đối chiếu với đề F1 gốc trong giáo trình (mục 11.11)

Giáo trình `BG CNPM 2020.doc` mục **11.11** có nguyên văn đề F1. So với đề bài nhóm đang dùng:

### Khác biệt về dữ liệu — nên bổ sung

| Thực thể | Giáo trình | Nhóm đang có |
|---|---|---|
| `ChangDua` | mã chặng, tên, **số vòng đua**, **địa điểm**, thời gian, **mô tả** | thiếu vài thuộc tính |
| `DoiDua` | mã, tên, **hãng**, **mô tả** | thiếu `hãng` |
| `TayDua` | mã, tên, ngày sinh, quốc tịch, **tiểu sử** | thiếu `tiểu sử` |
| — | có **modul "quản lí hãng đua"** riêng ⇒ `Hang` là thực thể | không có |

### Khác biệt về actor

Giáo trình dùng **"Ban tổ chức (BTC)"** cho đăng ký thi đấu / cập nhật kết quả / xem BXH, và **"Quản lí (QL)"** cho các modul danh mục. Nhóm đang dùng **"Nhân viên"** và **"Quản lý"**.

⇒ Cân nhắc đổi "Nhân viên" → "Ban tổ chức" cho sát đề gốc.

### ⚠️ Hai chỗ nhóm đã CỐ Ý đi khác đề gốc — cần cân nhắc rủi ro

**1. Tie-break.** Giáo trình ghi rõ **hai lần**:

> *"Kết quả sắp xếp theo thứ tự giảm dần của tổng điểm, sau đó là **thứ tự tăng dần tổng thời gian**."*

Nhóm đã đổi sang **countback** (số lần P1 → P2 → P3, đúng luật FIA thật).

**2. Trạng thái kết quả.** Giáo trình chỉ có:

> *"Nếu tay đua nằm trong top 10 nhưng **không về đích do bỏ cuộc hoặc tai nạn** thì 0 điểm."*

Nhóm đã thêm **DSQ** (bị loại vì vi phạm kỹ thuật).

**Đề xuất xử lý:** giữ cả hai (chúng làm hệ thống sát thực tế hơn, và thầy có nói hệ thống F1 "có đặc thù"), **nhưng phải ghi rõ trong báo cáo Chương 1** rằng đây là **tinh chỉnh nghiệp vụ có chủ đích so với mô tả gốc**, kèm lý do (luật FIA thật), và **giữ tổng thời gian hiển thị để tham khảo**. Như vậy thầy đọc sẽ thấy là hiểu sâu chứ không phải làm sai đề.

### Điểm nhóm làm chặt hơn đề gốc (giữ nguyên)

Giáo trình: *"BTC tích chọn **đúng 2** tay đua"* nhưng phần ràng buộc lại ghi *"mỗi đội chỉ được phép cho **tối đa 2** tay đua"*. Nhóm chọn "tối đa 2" — hợp lý hơn (đội có thể chỉ đăng ký 1 nếu tay đua kia chấn thương).

---

## P4 — Đối chiếu với ĐỀ BÀI GỐC `SE-list-of-project.pdf` (project 10, tiếng Anh)

> Đề bài gốc là văn bản giao đề, đứng TRÊN giáo trình về mặt phạm vi công việc. Đã đọc nguyên văn project 10 "F1 formula championship management" (trang 21-22 của PDF).

### P4-1. ⚠️ Tie-break: đề gốc cũng ghi "tăng dần tổng thời gian" — chốt phương án 3 TẦNG

Đề gốc ghi **2 lần** (cả BXH tay đua lẫn BXH đội): *"sorted in descending order of total score, then in **ascending order of total time**"*. Giáo trình cũ mục 11.11 cũng vậy. Nhóm đổi hẳn sang countback là **mâu thuẫn trực tiếp với đề**.

**Chốt: tie-break 3 tầng** — (1) tổng điểm giảm dần → (2) **countback** (số lần về nhất, rồi về nhì, về ba… — bổ sung theo luật FIA thật, có ghi chú giải trình) → (3) nếu vẫn bằng: **tổng thời gian tăng dần** (đúng nguyên văn đề). Tổng thời gian vẫn hiển thị trên BXH. Cách này giữ được realism mà không cãi đề.

Áp vào: đề bài, `docs/01` (FR5.2), `docs/03`, M4 noi-dung (đặc tả + hoạt động + thuyết minh + sequence + test case), `BAO-CAO.md`.

### P4-2. ⚠️ M4 thiếu DRILL-DOWN mà đề gốc BẮT BUỘC

Đề gốc (module 3 và 4): *"The staff clicks on a line of a racer → the system displays the **detailed results of each race stage** given by that racer, each stage on one line: **stage name, finish rank, score, time to finish**"* (đội: `race name, total score, total time of the 2 racers`). Và BXH xem theo **chặng bất kỳ chọn từ dropdown** ("The staff selects a stage from the dropdown list"), không chỉ cuối mùa.

⇒ M4 phải thêm màn **Chi tiết theo chặng** (`GDChiTietXepHang` / `gdChiTietXepHang.jsp`, UC con **extend** từ `Xem bảng tổng sắp`), thêm chọn-chặng vào màn BXH, thêm 2 phương thức `KetQua.getChiTietTheoTayDua(muaGiaiId, tayDuaId)` / `getChiTietTheoDoi(muaGiaiId, doiDuaId)` + 2 method tương ứng ở `KetQuaDAO`, thêm ảnh `m4-giaodien-chitietxephang.png`, thêm test case drill-down.

Cột bảng phải đúng đề gốc:
- BXH cá nhân: `Hạng | Tên tay đua | Quốc tịch | Tên đội | Tổng điểm | Tổng thời gian`
- BXH đội: `Hạng | Tên đội | Hãng | Tổng điểm | Tổng thời gian`
- Chi tiết tay đua: `Tên chặng | Hạng về đích | Điểm | Thời gian`
- Chi tiết đội: `Tên chặng | Tổng điểm | Tổng thời gian của 2 tay đua`

### P4-3. M1 không nằm trong 4 module đề gốc — phải GIẢI TRÌNH ánh xạ

Đề gốc có 4 module: *Register to racing* (= M2), *Update results* (= M3), *View racers' standings* + *View team rankings* (= M4 gộp). **Không có "ký hợp đồng"** — M1 xuất phát từ ràng buộc *"Each driver can play for many racing teams at different times. But at a time only play for 1 team"*.

⇒ Viết đoạn giải trình ánh xạ vào Chương 1 `BAO-CAO.md` + đề bài: M1 hiện thực hoá ràng buộc trên (không có nó thì M2/M3/M4 không xác định được tay đua thuộc đội nào tại thời điểm chặng); M4 gộp 2 module BXH vì UC "xem bảng" thuần hiển thị là UC yếu theo tiêu chí chấm ("UC phải đủ lớn, có nghiệp vụ").

### P4-4. Xác nhận thuộc tính + ràng buộc

- Thuộc tính `hang` (brand), `tieuSu` (biography), `diaDiem` (location), `moTa` — **đúng đề gốc**, đã bổ sung. ✓
- "Tối đa 2 tay đua" — đề ghi "maximum of 2" ở ràng buộc. ✓
- **M2: danh sách tay đua phải "sorted by their alphabetic order of name"** — nguyên văn đề; phải có trong đặc tả + giao diện + test case.

---

## P5 — Đối chiếu với GIÁO TRÌNH PDF `BG HP TTTN 2 CNPM 2020 final.pdf` — NGUỒN ƯU TIÊN CAO NHẤT

> 235 trang, 6 chương. Đã đọc trọn chương 3 (Thu thập & phân tích yêu cầu), chương 4 (Thiết kế), mục 6.2 (Test chức năng) + trích 10 hình mẫu (Hình 3.6-3.11, 4.1-4.15). Khi PDF khác slide/doc cũ → **PDF thắng**.

### P5-A. XÁC NHẬN các kết luận cũ (không đổi)

1. **Không có lớp Control** trong biểu đồ lớp phân tích modul — mục 3.2.3 tuy tiêu đề có chữ "và điều khiển" nhưng toàn bộ nội dung + 3 hình mẫu (3.6/3.7/3.8) chỉ có lớp biên `GDxxx` + lớp thực thể; phương thức gán cho lớp thực thể. Không stereotype, không mũi tên.
2. **Không có tầng Controller** ở thiết kế: jsp + DAO + entity (Hình 4.4/4.6/4.8). Package `view / dao / model` (Hình 4.15).
3. Sequence thiết kế (Hình 4.10/4.12): lifeline = actor + jsp + DAO + Entity; **không CSDL, không SQL**; đánh số 1..48; nhãn `goi / tra ve / hien thi / click …`; DAO self-call tên hàm; Entity self-call constructor; có `loop`.
4. Lớp thực thể pha phân tích: không `id`, không kiểu. Pha thiết kế: + `id`, + kiểu, + thuộc tính đối tượng.
5. Đặc tả UC 6 dòng; kịch bản chi tiết **nhúng bảng dữ liệu thật vào từng bước** (mẫu 3.2.1 có bảng `TT|Mã|Tên môn học|số tín chỉ|…` ngay trong kịch bản); ngoại lệ đánh số theo bước.
6. FK đặt tên `tblXxxid` (Hình 4.2). Tên UC = động từ hành động của actor.

### P5-B. ❗ LẬT LẠI 2 kết luận cũ

**P5-B1. UC "Đăng nhập" PHẢI CÓ trong UC chi tiết** *(lật lại P0-8).* Cả PDF (3.1.3) lẫn slide B1 đều phân rã: *"Đăng nhập → đề xuất UC đăng nhập… UC đăng kí **include** các UC này"* — hình mẫu UC chi tiết có UC con `Đăng nhập` (include). Lưu ý cảnh báo "UC đăng nhập không đạt" chỉ áp cho việc **chọn nó làm UC chính** của thành viên. ⇒ Khôi phục UC con `Đăng nhập` (include) ở UC chi tiết cả 4 module; vẫn KHÔNG cần lớp biên/jsp/sequence cho nó (giáo trình cũng không có — kịch bản mở đầu "sau khi đăng nhập").

**P5-B2. Test case theo format Bảng 6.7 PDF, KHÔNG theo 9.5.3 doc cũ** *(lật lại P2-1).* Mục 6.2 PDF: quy trình 4 bước (checklist → viết test case → chuẩn bị data test → chạy & ghi pass/fail). Bảng test case **4 cột**: `Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn`, chia 3 nhóm:
- **Giao diện** (theo từng màn): bố cục/title/focus, hiển thị đủ trường + button, Tab/Shift-Tab, Enter, Ctrl±…
- **Chức năng** (theo từng màn): hiển thị đúng dữ liệu — đối chiếu với bảng CSDL (vd *"Danh sách lớp đăng kí tương ứng với các bản ghi trong tblDangKiHoc"*), ca rỗng/có dữ liệu.
- **Luồng nghiệp vụ**: end-to-end, kết quả mong muốn ghi cả hiệu ứng CSDL (*"tblDangKiHoc bổ sung các bản ghi tương ứng, sĩ số hiện tại tăng 1"*).
Mã dạng `DKH_1…DKH_55` (viết tắt module + số). `Precond` ghi ở dòng đầu nhóm. Data test: PDF ghi *"mô tả các ràng buộc về data test ở cột Các bước thực hiện"* — mình vẫn nhúng dữ liệu F1 2025 cụ thể vào cột bước (điểm cộng, không mâu thuẫn).
Mã đề xuất: M1 = `KHD_n`, M2 = `DKC_n`, M3 = `CNKQ_n`, M4 = `QTTG_n`. Mỗi module tối thiểu: 4-6 ca Giao diện (2-3/màn), 4 ca Chức năng (2/màn), + số ca Luồng nghiệp vụ như đã định (M1:4, M2:6 gồm alphabet, M3:5, M4:6 gồm drill-down & countback & đổi đội giữa mùa).

### P5-C. BỔ SUNG MỚI từ PDF (chưa có trong P0–P3)

**P5-C1. Biểu đồ TRẠNG THÁI pha phân tích (mục 3.2.4, Hình 3.9/3.11/3.13)** — MỚI. Mỗi modul có 1 biểu đồ chuyển trạng thái: *mỗi trạng thái = một lần hệ thống hiển thị 1 giao diện chờ tương tác; điều kiện chuyển = hành động người dùng* (nhãn `[chọn 1 kì học]`…). Bắt đầu → các trạng thái "Hiển thị GD …" → Kết thúc. ⇒ Thêm cho cả 4 module (dễ vẽ, 4-6 node), ảnh `m<N>-trangthai.png`, đặt trong mục "Phân tích hoạt động".

**P5-C2. Biểu đồ HOẠT ĐỘNG thuộc pha THIẾT KẾ, phong cách Hình 4.9** — thay thế phong cách flowchart nghiệp vụ hiện tại. Quy tắc (4.3.2 bước 1): *"Mỗi hành động tương ứng một phương thức đã thiết kế trong biểu đồ lớp."* Phong cách hình mẫu:
- Nhóm khung theo trang: `Xử lí tại gdXxx.jsp` (mỗi jsp 1 khung, cả trang `doXxx.jsp`).
- Trong khung: các hành động `Nhận thông tin X`, `Lấy thông tin Y`, `Hiển thị GD`, `Lưu DK`, `Thông báo lưu thành công`…
- Guard trên cung chuyển: `[click đăng kí]`, `[đã chọn kì]`, `[lấy xong dữ liệu]`, `[lưu xong]`…
- Các node DAO tách riêng ở đáy: `KihocDAO: getKihoc()`, `DangkihocDAO: luuDKcuaSV()`… nối với hành động dùng nó.
- `Bắt đầu` (initial) và `Kết thúc` (final).
⇒ Vẽ lại biểu đồ hoạt động cả 4 module theo phong cách này (PlantUML dùng `partition "Xử lí tại gdXxx.jsp"`). Vị trí trong báo cáo giữ nguyên mục "biểu đồ hoạt động" theo yêu cầu bài tập.

**P5-C3. Trang chính `gdChinhNV.jsp` / `gdChinhQL.jsp`** — giáo trình LUÔN có giao diện chính của actor: lớp biên phân tích `GDChinhSV{-subDangki}`, lớp view thiết kế `gdChinhSV.jsp{-dangkihoc : link, -sv : Sinhvien}`, là **lifeline đầu và cuối** sequence (msg 1 `click DK`; áp cuối: `46: click OK` → `47: goi` (doXxx.jsp gọi lại trang chính) → `48: hien thi`). ⇒ Khôi phục cho cả 4 module: M1-M3 dùng `GDChinhNV`/`gdChinhNV.jsp` (thuộc tính `-subKyHopDong` / `-subDangKyChang` / `-subCapNhatKetQua` tuỳ module), M4 dùng `GDChinhQL`/`gdChinhQL.jsp{-subQuyetToan}`. *(Lật lại một phần quyết định bỏ `GDKyHopDong` — bản chất nó là trang chính, đổi tên thành `GDChinhNV`.)* Trang chính KHÔNG sinh UC con (hình mẫu UC chi tiết không có UC "trang chủ").

**P5-C4. Luồng LƯU: đóng gói bằng setter() TRƯỚC rồi mới gọi DAO** (Hình 4.12, msg 37-48): `nhập liệu + click lưu` → jsp gọi trang `doXxx.jsp` → `doXxx.jsp` **gọi Entity, Entity self-call `setter()`** (đóng gói dữ liệu nhập) → trả về → `doXxx.jsp` gọi `XxxDAO`, DAO self-call `luuXxx()` (KHÔNG gọi entity nữa) → trả về → thông báo thành công → `click OK` → gọi lại trang chính → hiển thị. ⇒ Sửa mẫu chuỗi message cho các luồng lưu ở cả 4 module (luồng ĐỌC giữ nguyên chuỗi 7 message có Entity constructor).

**P5-C5. Lớp view pha thiết kế có thuộc tính KÈM KIỂU CONTROL + thuộc tính ẩn** (Hình 4.4/4.6/4.8): `gdChonnganh.jsp{-kihoc : Select, -tblNganhhoc : Table, -chonNganh : link, -sv : Sinhvien}`, `gdDangki.jsp{-listDangki : Dangkihoc[], -btnTieptuc : submit, -btnLuuDK : submit, …}`, `gdDiem.jsp{-btnLuu : submit, -btnReset : Reset}`. Kiểu control: `Select`, `Table`, `link`, `submit`, `Reset`; thuộc tính ẩn kiểu entity (`-sv : Sinhvien`) hoặc mảng (`-listDK : Dangkihoc[]`) để truyền dữ liệu giữa trang. Bước 2 mục 4.3.1 cho phép **tách/gộp lớp giao diện so với pha phân tích**. ⇒ Mục 6 của 4 module: nâng cấp lớp view theo mẫu này.

**P5-C6. DAO có constructor + chữ ký đầy đủ; lớp cha `DAO{-con : Connection, +DAO()}`** (Hình 4.4): `DangkihocDAO{+DangkihocDAO(), +getDKcuaSV(idSinhvienKhoa : int, idKihoc : int) : Dangkihoc[], +luuDKcuaSV(listDK : Dangkihoc[]) : boolean}`. Mục 4.3.1: DAO *"nên thiết kế dạng Interface hoặc kế thừa từ lớp trừu tượng để dùng chung kết nối CSDL"*; quy tắc ánh xạ *"lớp thực thể pha phân tích cần phương thức nào thì đề xuất DAO tương ứng và gán phương thức đó cho DAO"*. ⇒ Mục 6 cả 4 module: ghi đầy đủ chữ ký (tham số : kiểu, kiểu trả về) + constructor.

**P5-C7. Quy tắc GÁN phương thức cho lớp thực thể (mục 3.2.3 bước 3)** — căn cứ biện luận mới: *"Nếu tham số đầu ra liên quan lớp thực thể nào thì gán cho lớp đó; nếu không, xét tham số đầu vào — 1 thực thể thì gán cho nó; nhiều thực thể thì tìm thực thể nhỏ nhất chứa được nhiều tham số nhất."* ⇒ Ghi quy tắc này vào `docs/03` + dùng để biện luận việc gán (`xepHangVaTinhDiem` → `KetQua` vì đầu ra là danh sách KetQua, v.v.).

**P5-C8. Pha phân tích còn có: kịch bản v.2 + biểu đồ giao tiếp + chuyển hóa thành tuần tự phân tích** (3.2.4 bước 1-3). Không bắt buộc theo Yêu cầu bài tập ⇒ TUỲ CHỌN, không đưa vào phạm vi nhóm (đã có thuyết minh v.3 + tuần tự thiết kế). Ghi chú trong docs/00 là "có thể bổ sung nếu dư thời gian".

**P5-C9. jsp submit chính nó**: khi 1 trang xử lý submit của chính nó, kịch bản v.3 ghi *"Trang gdXxx.jsp submit gọi chính nó xử lí"* (Hình 4.12 msg 11) ⇒ dùng cho M3 (`gdNhapKetQua.jsp` nút Tính kết quả) nếu cần.

**P5-C10. Naming (4.1.1)**: tên lớp chữ HOA đầu, thuộc tính chữ thường đầu, tiếng Việt **không dấu, không dấu cách, không ký tự đặc biệt** — rà lại toàn bộ tên trong PlantUML.

### P5-D. Ảnh cần vẽ — cập nhật theo P4+P5

Mỗi module: `m<N>-uc-chitiet` · `m<N>-trangthai` (MỚI) · `m<N>-hoatdong` (vẽ lại theo style Hình 4.9) · `m<N>-lop-phantich` · ảnh giao diện (M1: 2, M2: 2, M3: 2, M4: **3** — thêm chi tiết xếp hạng) · `m<N>-lop-thietke` (style Hình 4.4, đủ chữ ký) · `m<N>-tuantu` (style Hình 4.10, có trang chính + luồng lưu setter) — tức **mọi ảnh hoạt động/tuần tự/lớp đã vẽ đều phải vẽ lại**. Chung: `uc-tongquat`, `lop-thucthe-phantich`, `lop-thucthe-thietke`, `csdl` (ERD kiểu Hình 4.2, tuỳ chọn), `package-trienkhai`.

---

## P6 — Quyết định: bỏ ảnh giao diện, chuyển thành phác thảo trong Đặc tả UC

> Quyết định của nhóm ở lần rà soát thứ 3. Mục này **sửa đè** phần giao diện của P0-7 và P5-D; mọi kết luận khác giữ nguyên.

### P6-1. Nội dung quyết định

Nhóm chốt **không vẽ mockup giao diện và không xuất ảnh giao diện**. Giao diện chỉ trình bày ở mức **phác thảo**, gồm hai phần đi liền nhau cho mỗi màn hình: **khung bố cục** vẽ bằng ký tự trong code fence thường (thể hiện tiêu đề màn, ô nhập, nút bấm, vị trí bảng) và **bảng dữ liệu markdown** có dữ liệu mẫu thật từ bộ dữ liệu F1 2025 đã chốt, kèm một đoạn văn ngắn giải thích thuộc tính lớp biên tương ứng và trạng thái nút.

Phần phác thảo này **đặt bên trong chương Đặc tả Use Case**, làm mục con `2.2. Giao diện phác thảo` ngay sau `2.1. Bảng đặc tả`, chứ không còn là một mục riêng ở giữa tài liệu.

### P6-2. Căn cứ

1. **Giáo trình PDF mục 3.2.1** — kịch bản mẫu của thầy **nhúng thẳng bảng dữ liệu** vào các bước hệ thống hiển thị (bảng `TT | Mã | Tên môn học | số tín chỉ | …` nằm ngay trong kịch bản đặc tả UC). Giáo trình **không có ảnh mockup rời** cho từng màn hình. Đặt phác thảo trong đặc tả UC là bám đúng cách trình bày này.
2. **Yêu cầu bài tập nhóm** chỉ ghi *"Thiết kế giao diện cho UC"* — không quy định phải vẽ mockup bằng công cụ và không bắt buộc xuất ảnh. Khung bố cục + bảng dữ liệu mẫu đã đủ để đọc ra danh sách control của từng màn (phục vụ nhóm test case Giao diện) và đủ để ánh xạ sang lớp biên `GDxxx` cùng trang `.jsp`.
3. Ràng buộc **"số UC con = số giao diện = số lớp biên = số trang `.jsp`"** ở P0-7 **vẫn giữ nguyên** — chỉ khác là "giao diện" nay được đếm theo số màn phác thảo, không đếm theo số file ảnh.

### P6-3. Hệ quả

**Về số ảnh** — giảm từ **33** xuống **28**:

| | Trước | Sau |
|---|---|---|
| `docs/hinh/` (ảnh chung) | 4 | 4 |
| Mỗi module | M1–M3: 8, M4: 9 | **6** (`uc-chitiet`, `trangthai`, `lop-phantich`, `lop-mvc`, `hoatdong`, `tuantu`) |
| **Tổng** | **33** | **28** |

9 ảnh bị bỏ: `m1-giaodien-timtaydua`, `m1-giaodien-nhaphopdong`, `m2-giaodien-chonchangdoi`, `m2-giaodien-dangkytaydua`, `m3-giaodien-chonchang`, `m3-giaodien-nhapketqua`, `m4-giaodien-xephang`, `m4-giaodien-chitietxephang`, `m4-giaodien-traogiai`.

**Về đánh số mục** — mục `5. Thiết kế giao diện` bị xoá khỏi vị trí cũ, các mục sau dồn lên một số:

| Cũ | Mới |
|---|---|
| 5. Thiết kế giao diện | *(bỏ — chuyển thành mục con 2.2)* |
| 6. Biểu đồ lớp thiết kế | **5.** Biểu đồ lớp thiết kế |
| 7. Biểu đồ hoạt động (pha thiết kế) | **6.** Biểu đồ hoạt động (pha thiết kế) |
| 8. Thuyết minh + biểu đồ tuần tự (8.1, 8.2) | **7.** (7.1, 7.2) |
| 9. Test case (9.1, 9.2, 9.3) | **8.** (8.1, 8.2, 8.3) |

Mục 0–4 giữ nguyên số. Trong `docs/BAO-CAO.md`, mỗi chương module đổi tương ứng: `x.2` tách thành `x.2.1` (bảng đặc tả) + `x.2.2` (giao diện phác thảo), `x.5` bỏ, `x.6 → x.5`, `x.7 → x.6`, `x.8 → x.7`, `x.9 → x.8`, `x.10 → x.9`; mục lục cập nhật theo.

**Về nội dung khác:** nghiệp vụ, kịch bản, test case (kể cả nhóm test case Giao diện), biểu đồ PlantUML và bộ dữ liệu mẫu F1 2025 **không đổi**.

---

## Thứ tự làm đề xuất (cập nhật)

0. **P6** — bỏ ảnh giao diện, dời phác thảo vào mục 2.2 của Đặc tả UC, đánh số lại các mục sau.
1. **P0-1 → P0-6** (kiến trúc) — đã áp ở pass 1.
2. **P5-B1, P5-C3** — khôi phục UC Đăng nhập + trang chính `gdChinhNV/QL.jsp` (lật lại P0-8 và một phần M1).
3. **P4-1, P4-2, P4-3** — tie-break 3 tầng, M4 drill-down, giải trình ánh xạ đề gốc.
4. **P5-B2** — viết lại test case theo Bảng 6.7 (4 cột, 3 nhóm, mã `KHD_/DKC_/CNKQ_/QTTG_`).
5. **P5-C1, P5-C2** — thêm biểu đồ trạng thái; vẽ lại biểu đồ hoạt động theo style thiết kế.
6. **P5-C4 → C7** — luồng lưu setter, view class đủ kiểu, DAO đủ chữ ký, quy tắc gán phương thức.
7. **P1** còn lại (thuyết minh, trích danh từ, phạm vi…) — đã áp ở pass 1, rà lại.
8. **P5-D** — vẽ + export ảnh, nhúng vào `BAO-CAO.md`.
