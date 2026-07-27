# Module 3 — BẢN MỞ RỘNG CỦA KIET (chưa chuẩn hoá) — LƯU TRỮ, KHÔNG DÙNG TRỰC TIẾP

> **File này là gì:** bản `noi-dung.md` Kiet viết trên nhánh remote (commit `bf8866b`, `20a0238`, `b80b6d4`),
> được giữ lại nguyên vẹn khi merge với bản chuẩn hoá theo giáo trình.
> Bản đang dùng chính thức là `Module 3 - Kiet/noi-dung.md`.
>
> **Phần NGHIỆP VỤ Kiet thêm (đáng giá, chưa có trong bản chính):**
> - Actor thứ hai: **Trọng tài**
> - 3 use case mở rộng: `Xử lý kháng nghị`, `Áp dụng án phạt sau chặng`, `Phê duyệt kết quả chặng`
> - 2 thực thể mới: `KhangNghi`, `AnPhat`; `KetQua` thêm `trangThai` (chờ phê duyệt / chính thức)
> - Sequence 7B cho luồng trọng tài; 5 test case TC5–TC9
>
> **Vì sao chưa gộp thẳng vào bản chính:** phần này viết theo mẫu cũ (có lớp `Control`,
> `Controller`, stereotype `<<boundary>>`, lifeline CSDL + SQL trong sequence, test case bảng 6 cột)
> — đều là những thứ giáo trình của thầy KHÔNG dùng (xem `docs/05-doi-chieu-chuan-thay.md`).
> Ngoài ra kháng nghị / án phạt không có trong đề bài gốc (`SE-list-of-project.pdf` project 10).
>
> **Nhóm cần quyết:** (a) bỏ phần mở rộng, giữ M3 đúng đề — hoặc (b) giữ phần mở rộng
> nhưng viết lại theo chuẩn thầy (bỏ Control, lớp biên chỉ thuộc tính, sequence jsp→DAO→entity,
> test case Bảng 6.7) và bổ sung `KhangNghi`/`AnPhat` vào `docs/03` + UC tổng quát + báo cáo.

---

# Module 3 — Cập nhật kết quả và tính điểm chặng đua — Nội dung chi tiết

> Nội dung chữ do Claude dựng. Việc của bạn: mở Visual Paradigm, vẽ theo các blueprint/PlantUML bên dưới, export ảnh vào `hinh/`, rồi ghép vào báo cáo.

## 0. Danh sách ảnh cần export (đặt vào `hinh/`)

| Tên file | Biểu đồ (mục) |
|---|---|
| `m3-uc-chitiet.png` | UC chi tiết (mục 1) |
| `m3-hoatdong.png` | Biểu đồ hoạt động (mục 3) |
| `m3-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) |
| `m3-giaodien-nhapketqua.png` | Giao diện nhập kết quả + đối soát (mục 5) |
| `m3-lop-mvc.png` | Biểu đồ lớp thiết kế MVC (mục 6) |
| `m3-tuantu.png` | Biểu đồ tuần tự (mục 7) |

> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`.

---

## 1. Biểu đồ UC chi tiết

Module 3 có **hai actor**: Nhân viên (nhập kết quả, xử lý kháng nghị) và Trọng tài (áp dụng án phạt, phê duyệt kết quả chính thức).

- **Nhân viên** thực hiện UC chính `Cập nhật kết quả chặng đua`, include {Đăng nhập, Chọn chặng, Nhập kết quả và tính điểm, Lưu kết quả}.
- `Lưu kết quả` có extension points:
  - **extend** bởi `Xử lý kháng nghị` (Nhân viên) — khi đội đua nộp kháng nghị sau khi kết quả được lưu.
  - **extend** bởi `Áp dụng án phạt sau chặng` (Trọng tài) — khi trọng tài xác nhận vi phạm.
  - **extend** bởi `Phê duyệt kết quả chặng` (Trọng tài) — khi trọng tài xác nhận kết quả chính thức.

```plantuml
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Nhân viên" as NV
actor "Trọng tài" as TT

rectangle "Hệ thống quản lý giải đua F1" {
  usecase "Đăng nhập" as UC_DangNhap
  usecase "Cập nhật kết quả\nchặng đua" as UC1
  usecase "Chọn chặng" as UC2
  usecase "Nhập kết quả\nvà tính điểm" as UC3
  usecase UC4 as "Lưu kết quả
  --
  ..extension points..
  Xử lý kháng nghị
  Áp dụng án phạt
  Phê duyệt"

  usecase "Xử lý kháng nghị" as UC5
  usecase "Áp dụng án phạt\nsau chặng" as UC6
  usecase "Phê duyệt\nkết quả chặng" as UC7
}

' Actor chính
NV --> UC1

' Include từ UC chính
UC1 ..> UC2 : <<include>>
UC1 ..> UC3 : <<include>>
UC1 ..> UC4 : <<include>>
UC1 ..> UC_DangNhap : <<include>>

' Các ngoại lệ extend từ Lưu
UC5 ..> UC4 : <<extend>>
UC6 ..> UC4 : <<extend>>
UC7 ..> UC4 : <<extend>>

' Actor tham gia ngoại lệ
NV --> UC5
TT --> UC6
TT --> UC7
@enduml
```

## 2. Đặc tả Use Case

### 2.1 UC chính — Cập nhật kết quả chặng đua

| Mục | Nội dung |
|---|---|
| **Use case** | Cập nhật kết quả và tính điểm chặng đua |
| **Actor chính** | Nhân viên |
| **Actor phụ** | Trọng tài |
| **Tiền điều kiện** | Nhân viên đã đăng nhập thành công; chặng đua đã có danh sách tay đua đăng ký từ Module 2 |
| **Hậu điều kiện** | Kết quả (hạng, thời gian, số vòng, điểm) của từng tay đua trong chặng được lưu vào CSDL và được trọng tài phê duyệt chính thức |
| **Kịch bản chính** | 1. Nhân viên chọn menu "Nhập kết quả chặng".<br>2. Hệ thống hiển thị giao diện nhập kết quả: danh sách thả xuống chọn chặng đua.<br>3. Nhân viên chọn chặng đua từ dropdown và bấm **Tiếp tục**.<br>4. Hệ thống hiển thị bảng danh sách các tay đua đã đăng ký chặng đó (lấy từ Module 2), mỗi dòng gồm: STT, Tên tay đua, Tên đội, và ba ô nhập: **Thời gian hoàn thành (hh:mm:ss.xxx)**, **Số vòng chạy được**, **DNF ☑ (bỏ cuộc/tai nạn)**.<br>5. Nhân viên nhập đủ kết quả cho tất cả tay đua và click **Tính kết quả**.<br>6. Hệ thống kiểm tra tính hợp lệ: tay đua không tick DNF bắt buộc phải có thời gian hợp lệ. Nếu hợp lệ, hệ thống tự động xếp hạng tăng dần theo thời gian về đích (tay đua DNF xếp cuối cùng); gán điểm cho top 10 theo thứ tự 25, 18, 15, 12, 10, 8, 6, 4, 2, 1; tay đua nằm trong top 10 nhưng DNF nhận 0 điểm; sau đó hiển thị bảng kết quả đối soát gồm: Hạng, Tên tay đua, Tên đội, Thời gian, Số vòng, Điểm.<br>7. Nhân viên kiểm tra bảng đối soát và click **Lưu**.<br>8. Hệ thống lưu kết quả sơ bộ vào CSDL (trạng thái: *chờ phê duyệt*). |
| **Ngoại lệ** | **5a.** Tay đua không tick DNF nhưng để trống hoặc nhập sai định dạng Thời gian → hệ thống báo lỗi "Vui lòng nhập thời gian hợp lệ cho tay đua chưa DNF", không cho tính kết quả.<br>**8a.** Chặng đã có kết quả từ trước → hiển thị hộp thoại cảnh báo "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Nếu nhân viên chọn **Hủy** → không lưu, giữ nguyên kết quả cũ. Nếu chọn **Đồng ý** → xóa kết quả cũ, lưu kết quả mới, tính lại điểm toàn bộ chặng. |

### 2.2 UC5 — Xử lý kháng nghị *(extend UC4)*

| Mục | Nội dung |
|---|---|
| **Use case** | Xử lý kháng nghị |
| **Actor** | Nhân viên |
| **Điểm mở rộng** | Sau khi Lưu kết quả (UC4) — khi có đội đua nộp kháng nghị |
| **Tiền điều kiện** | Kết quả chặng đã được lưu (trạng thái *chờ phê duyệt*) |
| **Hậu điều kiện** | Kháng nghị được ghi nhận vào CSDL với trạng thái (chờ xử lý / chấp nhận / từ chối) |
| **Kịch bản** | 1. Nhân viên chọn chức năng "Ghi nhận kháng nghị".<br>2. Hệ thống hiển thị form: chọn chặng, chọn đội đua nộp kháng nghị, nhập nội dung kháng nghị.<br>3. Nhân viên điền đầy đủ và click **Gửi kháng nghị**.<br>4. Hệ thống lưu kháng nghị (trạng thái: *chờ xử lý*) và chuyển cho trọng tài xem xét. |
| **Ngoại lệ** | Đội đua không được nộp kháng nghị quá 30 phút sau khi kết quả được công bố → báo lỗi "Hết thời hạn nộp kháng nghị". |

### 2.3 UC6 — Áp dụng án phạt sau chặng *(extend UC4)*

| Mục | Nội dung |
|---|---|
| **Use case** | Áp dụng án phạt sau chặng |
| **Actor** | Trọng tài |
| **Điểm mở rộng** | Sau khi Lưu kết quả (UC4) — khi trọng tài xác nhận vi phạm (từ kháng nghị hoặc quan sát trực tiếp) |
| **Tiền điều kiện** | Kết quả chặng đã được lưu (trạng thái *chờ phê duyệt*) |
| **Hậu điều kiện** | Án phạt được ghi nhận; xếp hạng và điểm của tay đua bị phạt được tính lại |
| **Kịch bản** | 1. Trọng tài đăng nhập và chọn chức năng "Áp dụng án phạt".<br>2. Hệ thống hiển thị danh sách chặng đang ở trạng thái *chờ phê duyệt*.<br>3. Trọng tài chọn chặng, chọn tay đua bị phạt, nhập loại án phạt (phạt giây: cộng thêm X giây vào thời gian; hoặc phạt vị trí: lùi Y vị trí), nhập mô tả lý do.<br>4. Trọng tài click **Xác nhận án phạt**.<br>5. Hệ thống lưu án phạt vào CSDL, tính lại xếp hạng và điểm cho toàn bộ chặng sau khi áp dụng án phạt, hiển thị bảng kết quả đã cập nhật. |
| **Ngoại lệ** | Trọng tài nhập số giây âm hoặc số vị trí âm → báo lỗi "Giá trị án phạt không hợp lệ". |

### 2.4 UC7 — Phê duyệt kết quả chặng *(extend UC4)*

| Mục | Nội dung |
|---|---|
| **Use case** | Phê duyệt kết quả chặng |
| **Actor** | Trọng tài |
| **Điểm mở rộng** | Sau khi Lưu kết quả (UC4) — khi trọng tài xác nhận kết quả là chính thức |
| **Tiền điều kiện** | Kết quả chặng đã được lưu; tất cả kháng nghị và án phạt đã được xử lý xong |
| **Hậu điều kiện** | Kết quả chặng chuyển trạng thái sang *chính thức*; điểm được ghi nhận vào bảng xếp hạng mùa giải |
| **Kịch bản** | 1. Trọng tài chọn chức năng "Phê duyệt kết quả".<br>2. Hệ thống hiển thị bảng kết quả chặng (sau khi đã áp dụng tất cả án phạt nếu có).<br>3. Trọng tài kiểm tra và click **Phê duyệt**.<br>4. Hệ thống cập nhật trạng thái kết quả chặng thành *chính thức* và thông báo phê duyệt thành công. |
| **Ngoại lệ** | Còn kháng nghị chưa xử lý → hệ thống báo lỗi "Còn kháng nghị chưa xử lý, không thể phê duyệt", từ chối phê duyệt. |

## 3. Biểu đồ hoạt động (Activity)

```plantuml
@startuml
|Nhân viên|
start
:Chọn menu Nhập kết quả chặng;
:Hệ thống hiển thị dropdown chọn chặng menu;
:Chọn chặng đua;

while (Kết quả nhập đã hợp lệ?) is (không hợp lệ)
  :Hệ thống hiển thị bảng danh sách\ntay đua đã đăng ký chặng;
  :Nhập thời gian hoàn thành, số vòng chạy,\ntick DNF (nếu có) cho từng tay đua;
  :Báo lỗi "Vui lòng nhập thời gian\nhợp lệ cho tay đua chưa DNF";
endwhile (hợp lệ)

:Hệ thống sắp xếp tay đua tăng dần\ntheo thời gian (tay đua DNF xếp cuối);
:Hệ thống gán điểm top 10: 25, 18, 15, 12, 10, 8, 6, 4, 2, 1\n(tay đua DNF trong top 10 nhận 0 điểm);
:Hệ thống hiển thị bảng đối soát:\nHạng | Tên tay đua | Tên đội | Thời gian | Số vòng | Điểm;
:Click lưu;

if (Chặng đua đã có kết quả cũ?) then (có)
  :Hệ thống hiển thị cảnh báo:\n"Chặng đua này đã có kết quả,\nbạn có muốn ghi đè?";
  if (Nhân viên xác nhận ghi đè?) then (hủy)
    :Giữ nguyên kết quả cũ, không lưu;
  else (xác nhận)
    :Xóa kết quả cũ và cập nhật\nkết quả mới của chặng;
    :Hệ thống lưu kết quả;
  endif
else (không)
  :Hệ thống lưu kết quả;
endif

if (Đội đua nộp đơn kháng nghị?) then (có)
  :Tiếp nhận kháng nghị từ đội đua;
  :Hệ thống ghi nhận nội dung kháng nghị\nvà gửi cho bên xử lý;

  |Trọng tài|
  repeat :Xem xét kháng nghị;
  if (Chấp nhận kháng nghị?) then (có)
    :Đối chiếu kết quả qua camera\nvới kháng nghị;
    if (Kháng nghị thành công?) then (có)
      :Hệ thống cập nhật lại điểm xếp hạng;
    else (không)
    endif
  else (từ chối)
  endif
  repeat while (Còn kháng nghị từ đội đua khác?) is (còn) not (hết)

else (không)
  |Trọng tài|
endif

:Phê duyệt kết quả;
:Click phê duyệt;
:Hệ thống thông báo phê duyệt thành công;
stop
@enduml
```

## 4. Biểu đồ lớp phân tích (Boundary / Control / Entity)

- **Boundary:**
  - `GDNhapKetQua` — màn hình Nhân viên: chọn chặng → nhập kết quả → đối soát → lưu
  - `GDKhangNghi` — màn hình Nhân viên: ghi nhận kháng nghị từ đội đua
  - `GDTrongTai` — màn hình Trọng tài: xem xét kháng nghị, áp dụng án phạt, phê duyệt kết quả
- **Control:**
  - `KetQuaControl` — điều phối luồng nhập kết quả, xếp hạng, tính điểm
  - `TrongTaiControl` — điều phối luồng xử lý kháng nghị, án phạt, phê duyệt
- **Entity:** `ChangDua`, `DangKyChang`, `TayDua`, `DoiDua`, `KetQua`, `KhangNghi`, `AnPhat`

```plantuml
@startuml
class GDNhapKetQua <<boundary>> {
  cboChang : Combobox
  btnTiepTuc : Button
  tblNhapKetQua : Table
  btnTinhKetQua : Button
  btnLuu : Button
  hienDanhSachChang(dsChang)
  hienBangNhapLieu(dsDangKy)
  hienBangDoiSoat(dsKetQua)
  hienCanhBaoGhiDe() : boolean
  baoLoi(message)
}

class GDKhangNghi <<boundary>> {
  cboChang : Combobox
  cboDoi : Combobox
  txtNoiDung : TextArea
  btnGuiKhangNghi : Button
  hienDanhSachKhangNghi(dsKN)
  baoLoi(message)
}

class GDTrongTai <<boundary>> {
  lstKhangNghi : List
  tblKetQua : Table
  cboLoaiAnPhat : Combobox
  txtGiaTriAnPhat : TextField
  btnXacNhanAnPhat : Button
  btnPheDuyet : Button
  hienKhangNghi(dsKN)
  hienKetQuaSauAnPhat(dsKQ)
  baoLoi(message)
}

class KetQuaControl <<control>> {
  layDanhSachChang() : List<ChangDua>
  layDanhSachDangKy(changId : int) : List<DangKyChang>
  xepHangVaTinhDiem(dsNhap : List<KetQua>) : List<KetQua>
  kiemTraKetQuaCu(changId : int) : boolean
  luuKetQua(changId : int, dsKetQua : List<KetQua>) : boolean
}

class TrongTaiControl <<control>> {
  layDanhSachKhangNghi(changId : int) : List<KhangNghi>
  xetKhangNghi(khangNghiId : int, ketQua : String) : boolean
  apDungAnPhat(ketQuaId : int, anPhat : AnPhat) : boolean
  tinhLaiXepHang(changId : int) : List<KetQua>
  pheDuyetKetQua(changId : int) : boolean
}

class ChangDua <<entity>> {
  id : int
  ma : String
  ten : String
  soVong : int
  diaDiem : String
  thoiGian : Date
  getAll() : List<ChangDua>
}

class DangKyChang <<entity>> {
  id : int
  changId : int
  tayDuaId : int
  doiDuaId : int
  getByChang(changId : int) : List<DangKyChang>
}

class TayDua <<entity>> {
  id : int
  ma : String
  ten : String
  ngaySinh : Date
  quocTich : String
}

class DoiDua <<entity>> {
  id : int
  ma : String
  ten : String
  hang : String
}

class KetQua <<entity>> {
  id : int
  dangKyChangId : int
  thoiGian : double
  soVong : int
  dnf : boolean
  dnq : boolean
  hang : int
  diem : int
  trangThai : String
  getByChang(changId : int) : List<KetQua>
  xoaTheoChang(changId : int)
  them() : boolean
  capNhatTrangThai(changId, trangThai)
}

class KhangNghi <<entity>> {
  id : int
  changId : int
  doiDuaId : int
  noiDung : String
  trangThai : String
  thoiGianNop : DateTime
  getByChang(changId : int) : List<KhangNghi>
  them() : boolean
  capNhatTrangThai(id, trangThai)
}

class AnPhat <<entity>> {
  id : int
  ketQuaId : int
  loaiAnPhat : String
  giayPhat : int
  viTriTru : int
  moTa : String
  getByKetQua(ketQuaId : int) : List<AnPhat>
  them() : boolean
}

GDNhapKetQua --> KetQuaControl
GDKhangNghi --> KetQuaControl
GDTrongTai --> TrongTaiControl

KetQuaControl --> ChangDua
KetQuaControl --> DangKyChang
KetQuaControl --> TayDua
KetQuaControl --> DoiDua
KetQuaControl --> KetQua
KetQuaControl --> KhangNghi

TrongTaiControl --> KhangNghi
TrongTaiControl --> AnPhat
TrongTaiControl --> KetQua
TrongTaiControl --> ChangDua

DangKyChang "1" -- "1" TayDua
DangKyChang "1" -- "1" DoiDua
KetQua "1" -- "0..*" AnPhat
KhangNghi "0..*" -- "1" DoiDua
@enduml
```


## 5. Thiết kế giao diện

**Màn hình duy nhất — Nhập kết quả chặng (`m3-giaodien-nhapketqua.png`):**

Giao diện gồm hai phần hiển thị tuần tự trên cùng một màn hình:

**Phần A — Chọn chặng (hiển thị ban đầu):**
- Tiêu đề: "CẬP NHẬT KẾT QUẢ VÀ TÍNH ĐIỂM CHẶNG ĐUA"
- Combobox **[Chọn chặng đua]** liệt kê tất cả các chặng trong mùa.
- Nút **[Tiếp tục]**.

**Phần B — Nhập liệu và đối soát (hiện ra sau khi chọn chặng):**
- Thông tin chặng đã chọn: Tên chặng, Địa điểm, Tổng số vòng đua.
- **Bảng nhập liệu** — danh sách tay đua đã đăng ký chặng:

| STT | Tên tay đua | Tên đội | Thời gian (hh:mm:ss.xxx) | Số vòng | DNF ☑ |
|---|---|---|---|---|---|
| 1 | Lewis Hamilton | Mercedes | [_____] | [__] | ☐ |
| 2 | Max Verstappen | Red Bull | [_____] | [__] | ☐ |
| … | … | … | … | … | … |

- Nút **[Tính kết quả]**: hệ thống kiểm tra hợp lệ → xếp hạng + tính điểm, bảng bên dưới chuyển thành bảng đối soát có thêm cột Hạng và Điểm.
- **Bảng đối soát** (hiện sau khi bấm Tính kết quả):

| Hạng | Tên tay đua | Tên đội | Thời gian | Số vòng | Điểm |
|---|---|---|---|---|---|
| 1 | … | … | … | … | 25 |
| 2 | … | … | … | … | 18 |
| … | … | … | … | … | … |

- Nút **[Lưu]**: lưu vào CSDL (cảnh báo ghi đè nếu chặng đã có kết quả cũ).

> Vẽ mockup trong VP và export: `hinh/m3-giaodien-nhapketqua.png`.

## 6. Biểu đồ lớp thiết kế (MVC)

- **View (jsp):** `gdNhapKetQua.jsp`, `doLuuKetQua.jsp`, `gdKhangNghi.jsp`, `doGuiKhangNghi.jsp`, `gdTrongTai.jsp`, `doAnPhat.jsp`, `doPheDuyet.jsp`
- **Controller:** `KetQuaController`, `TrongTaiController`
- **DAO:**
  - `ChangDuaDAO` — `getAll()`
  - `DangKyChangDAO` — `getByChang(changId)` (JOIN `tblTayDua`, `tblDoiDua`)
  - `KetQuaDAO` — `getByChang()`, `deleteByChang()`, `insert()`, `updateTrangThai()`
  - `KhangNghiDAO` — `getByChang()`, `insert()`, `updateTrangThai()`
  - `AnPhatDAO` — `getByKetQua()`, `insert()`
- **Entity:** `ChangDua`, `DangKyChang`, `TayDua`, `DoiDua`, `KetQua`, `KhangNghi`, `AnPhat`

```plantuml
@startuml
package View {
  class gdNhapKetQua
  class doLuuKetQua
  class gdKhangNghi
  class doGuiKhangNghi
  class gdTrongTai
  class doAnPhat
  class doPheDuyet
}

package Controller {
  class KetQuaController
  class TrongTaiController
}

package DAO {
  class ChangDuaDAO
  class DangKyChangDAO
  class KetQuaDAO
  class KhangNghiDAO
  class AnPhatDAO
}

package Entity {
  class ChangDua
  class DangKyChang
  class TayDua
  class DoiDua
  class KetQua {
    dnq : boolean
  }
  class KhangNghi
  class AnPhat
}

gdNhapKetQua --> KetQuaController
doLuuKetQua --> KetQuaController
gdKhangNghi --> KetQuaController
doGuiKhangNghi --> KetQuaController
gdTrongTai --> TrongTaiController
doAnPhat --> TrongTaiController
doPheDuyet --> TrongTaiController

KetQuaController --> ChangDuaDAO
KetQuaController --> DangKyChangDAO
KetQuaController --> KetQuaDAO
KetQuaController --> KhangNghiDAO

TrongTaiController --> KhangNghiDAO
TrongTaiController --> AnPhatDAO
TrongTaiController --> KetQuaDAO
TrongTaiController --> ChangDuaDAO

ChangDuaDAO --> ChangDua
DangKyChangDAO --> DangKyChang
DangKyChangDAO --> TayDua
DangKyChangDAO --> DoiDua
KetQuaDAO --> KetQua
KhangNghiDAO --> KhangNghi
AnPhatDAO --> AnPhat

DangKyChang --> TayDua
DangKyChang --> DoiDua
KetQua --> AnPhat
@enduml
```

## 7. Biểu đồ tuần tự (Sequence)

> Có **hai sequence riêng**: 7A cho Nhân viên (nhập kết quả → lưu) và 7B cho Trọng tài (xử lý kháng nghị → án phạt → phê duyệt). Ngoại lệ (nhập sai TG, ghi đè) đã mô tả trong mục 2+3.

### 7A — Luồng Nhân viên: Nhập và lưu kết quả (chặng chưa có kết quả cũ)

```plantuml
@startuml
actor NhanVien as NV
participant "gdNhapKetQua" as V
participant "KetQuaController" as C
participant "ChangDuaDAO" as CDAO
participant "DangKyChangDAO" as DDAO
participant "KetQuaDAO" as KDAO
database "CSDL" as DB

NV -> V : chọn menu Nhập kết quả chặng
activate V
V -> C : moManNhap()
activate C
C -> CDAO : getAll()
activate CDAO
CDAO -> DB : SELECT * FROM tblChangDua
activate DB
DB --> CDAO : rows
deactivate DB
CDAO --> C : List<ChangDua>
deactivate CDAO
C --> V : hiển thị dropdown chặng
deactivate C
V --> NV : giao diện chọn chặng
deactivate V

NV -> V : chọn chặng, click Tiếp tục
activate V
V -> C : chonChang(changId)
activate C
C -> DDAO : getByChang(changId)
activate DDAO
DDAO -> DB : SELECT dk.*, td.ten, doi.ten\nFROM tblDangKyChang dk\nJOIN tblTayDua td ON dk.tayDuaId = td.id\nJOIN tblDoiDua doi ON dk.doiDuaId = doi.id\nWHERE dk.changId = ?
activate DB
DB --> DDAO : rows
deactivate DB
DDAO --> C : List<DangKyChang>
deactivate DDAO
C --> V : hiển thị bảng nhập liệu
deactivate C
V --> NV : bảng nhập liệu (tên tay đua, tên đội, ô nhập TG/SV/DNF)
deactivate V

NV -> V : nhập thời gian/số vòng/DNF, click Tính kết quả
activate V
V -> C : tinhKetQua(dsNhap)
activate C
C -> C : xepHangVaTinhDiem(dsNhap)
note right of C
  1. Tách danh sách: nhóm DNF và nhóm hoàn thành.
  2. Sắp xếp nhóm hoàn thành tăng dần theo thời gian.
  3. Ghép: [hoàn thành đã xếp] + [DNF].
  4. Gán hang = vị trí trong danh sách ghép.
  5. Gán điểm: hang 1->25, 2->18, 3->15, 4->12,
     5->10, 6->8, 7->6, 8->4, 9->2, 10->1.
  6. Tay đua DNF -> diem = 0 (dù hang <= 10).
end note
C --> V : List<KetQua> đã có hang và diem
deactivate C
V --> NV : bảng đối soát (Hạng, Tên, Đội, TG, SV, Điểm)
deactivate V

NV -> V : click Lưu
activate V
V -> C : luuKetQua(changId, dsKetQua)
activate C
C -> KDAO : getByChang(changId)
activate KDAO
KDAO -> DB : SELECT COUNT(*) FROM tblKetQua kq\nJOIN tblDangKyChang dk ON kq.dangKyChangId = dk.id\nWHERE dk.changId = ?
activate DB
DB --> KDAO : count = 0
deactivate DB
KDAO --> C : coKetQuaCu = false
deactivate KDAO

loop mỗi ketQua trong dsKetQua
  C -> KDAO : insert(ketQua)
  activate KDAO
  KDAO -> DB : INSERT INTO tblKetQua\n(dangKyChangId, thoiGian, soVong, dnf, hang, diem)\nVALUES (?, ?, ?, ?, ?, ?)
  activate DB
  DB --> KDAO : ok
  deactivate DB
  KDAO --> C : ok
  deactivate KDAO
end

C --> V : lưu thành công
deactivate C
V --> NV : thông báo lưu thành công
deactivate V
@enduml
```

### 7B — Luồng Trọng tài: Xử lý kháng nghị → Áp dụng án phạt → Phê duyệt

```plantuml
@startuml
actor TrongTai as TT
participant "gdTrongTai" as VTT
participant "TrongTaiController" as C
participant "KhangNghiDAO" as KNDAO
participant "AnPhatDAO" as APDAO
participant "KetQuaDAO" as KDAO
database "CSDL" as DB

TT -> VTT : chọn chức năng Xem kháng nghị
activate VTT
VTT -> C : layDanhSachKhangNghi(changId)
activate C
C -> KNDAO : getByChang(changId)
activate KNDAO
KNDAO -> DB : SELECT * FROM tblKhangNghi\nWHERE changId = ? AND trangThai = 'cho_xu_ly'
activate DB
DB --> KNDAO : rows
deactivate DB
KNDAO --> C : List<KhangNghi>
deactivate KNDAO
C --> VTT : hiển thị danh sách kháng nghị
deactivate C
VTT --> TT : danh sách kháng nghị chờ xử lý
deactivate VTT

TT -> VTT : chọn kháng nghị, áp dụng án phạt, click Xác nhận
activate VTT
VTT -> C : apDungAnPhat(ketQuaId, loaiAnPhat, giaTri, moTa)
activate C
C -> APDAO : insert(anPhat)
activate APDAO
APDAO -> DB : INSERT INTO tblAnPhat\n(ketQuaId, loaiAnPhat, giayPhat, viTriTru, moTa)\nVALUES (?, ?, ?, ?, ?)
activate DB
DB --> APDAO : ok
deactivate DB
APDAO --> C : ok
deactivate APDAO
C -> C : tinhLaiXepHang(changId)
note right of C
  1. Lấy toàn bộ KetQua của chặng.
  2. Với từng KetQua có AnPhat:
     - Nếu phạt giây: thoiGian += giayPhat.
     - Nếu phạt vị trí: ghi nhận offset vị trí.
  3. Sắp xếp lại theo thời gian đã điều chỉnh.
  4. Cập nhật lại hang và diem tương ứng.
end note
C -> KDAO : updateTrangThai(changId, 'cho_phe_duyet')
activate KDAO
KDAO -> DB : UPDATE tblKetQua SET hang=?, diem=?\nWHERE dangKyChangId = ?
activate DB
DB --> KDAO : ok
deactivate DB
KDAO --> C : ok
deactivate KDAO
C --> VTT : bảng kết quả sau án phạt
deactivate C
VTT --> TT : kết quả đã cập nhật
deactivate VTT

TT -> VTT : kiểm tra kết quả, click Phê duyệt
activate VTT
VTT -> C : pheDuyetKetQua(changId)
activate C
C -> KNDAO : getByChang(changId)
activate KNDAO
KNDAO -> DB : SELECT COUNT(*) FROM tblKhangNghi\nWHERE changId = ? AND trangThai = 'cho_xu_ly'
activate DB
DB --> KNDAO : count = 0
deactivate DB
KNDAO --> C : conKhangNghi = false
deactivate KNDAO
C -> KDAO : updateTrangThai(changId, 'chinh_thuc')
activate KDAO
KDAO -> DB : UPDATE tblKetQua SET trangThai = 'chinh_thuc'\nWHERE changId = ?
activate DB
DB --> KDAO : ok
deactivate DB
KDAO --> C : ok
deactivate KDAO
C --> VTT : phê duyệt thành công
deactivate C
VTT --> TT : thông báo kết quả chính thức
deactivate VTT
@enduml
```

## 8. Test case

| ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi |
|---|---|---|---|---|---|
| **TC1** | Xếp hạng và tính điểm đúng cho top 10 khi không có DNF | Chặng R có 12 tay đua đăng ký; chưa có kết quả lưu | 12 tay đua có thời gian về đích khác nhau, không ai DNF | 1. Chọn chặng R → Tiếp tục.<br>2. Nhập thời gian cho 12 tay đua.<br>3. Click Tính kết quả.<br>4. Click Lưu. | Bảng đối soát xếp hạng tăng dần theo thời gian. Hạng 1–10 nhận điểm `25, 18, 15, 12, 10, 8, 6, 4, 2, 1`; hạng 11 và 12 nhận `0` điểm. Lưu thành công (trạng thái: chờ phê duyệt). |
| **TC2** | Tay đua DNF xếp cuối và nhận 0 điểm dù thời gian nhanh | Chặng R có 10 tay đua đăng ký | Tay đua A có thời gian nhanh thứ 2 nhưng tick DNF | 1. Chọn chặng R → Tiếp tục.<br>2. Nhập thời gian; tick DNF ở dòng tay đua A.<br>3. Click Tính kết quả. | Tay đua A bị xếp xuống vị trí cuối bảng và nhận `0` điểm, không ảnh hưởng đến xếp hạng 9 tay đua còn lại. |
| **TC3** | Chặn tính kết quả khi thiếu thời gian bắt buộc | Chặng R có tay đua đăng ký | Tay đua B không tick DNF nhưng để trống cột Thời gian | 1. Chọn chặng R → Tiếp tục.<br>2. Nhập đủ kết quả các tay đua khác, riêng tay đua B để trống Thời gian và không tick DNF.<br>3. Click Tính kết quả. | Hệ thống báo lỗi "Vui lòng nhập thời gian hợp lệ cho tay đua chưa DNF". Không thực hiện xếp hạng, không cho phép Lưu. |
| **TC4** | Cảnh báo và ghi đè khi chặng đã có kết quả cũ | Chặng R đã có kết quả lưu trong CSDL | Nhập bộ thời gian mới cho các tay đua của chặng R | 1. Chọn chặng R → Tiếp tục.<br>2. Nhập kết quả mới → Tính kết quả.<br>3. Click Lưu. | Hệ thống hiển thị cảnh báo "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Khi chọn **Đồng ý**: xóa kết quả cũ, lưu kết quả mới, tính lại điểm toàn bộ chặng. Khi chọn **Hủy**: giữ nguyên kết quả cũ, không thay đổi. |
| **TC5** | Ghi nhận kháng nghị hợp lệ từ đội đua | Kết quả chặng R đã được lưu (trạng thái: chờ phê duyệt) | Đội Mercedes kháng nghị về vị trí của tay đua Hamilton | 1. Nhân viên chọn "Ghi nhận kháng nghị".<br>2. Chọn chặng R, chọn đội Mercedes, nhập nội dung.<br>3. Click Gửi kháng nghị. | Kháng nghị được lưu (trạng thái: chờ xử lý). Trọng tài thấy kháng nghị mới trong danh sách. |
| **TC6** | Chặn nộp kháng nghị quá hạn | Chặng R đã kết thúc hơn 30 phút | Đội Red Bull nộp kháng nghị sau 35 phút | 1. Nhân viên chọn "Ghi nhận kháng nghị".<br>2. Điền thông tin → Click Gửi. | Hệ thống báo lỗi "Hết thời hạn nộp kháng nghị". Kháng nghị không được lưu. |
| **TC7** | Trọng tài áp dụng án phạt giây → xếp hạng thay đổi | Chặng R đã có kết quả; tay đua Verstappen hạng 1 | Phạt Verstappen +5 giây → thời gian mới đẩy xuống hạng 2 | 1. Trọng tài chọn chặng R.<br>2. Chọn tay đua Verstappen, chọn loại phạt giây, nhập 5.<br>3. Click Xác nhận án phạt. | Hệ thống tính lại: Verstappen xuống hạng 2 (mất 18đ → 25đ), tay đua hạng 2 cũ lên hạng 1. Bảng xếp hạng cập nhật đúng. |
| **TC8** | Chặn phê duyệt khi còn kháng nghị chưa xử lý | Chặng R có 1 kháng nghị (trạng thái: chờ xử lý) | — | 1. Trọng tài chọn chặng R → Click Phê duyệt. | Hệ thống báo lỗi "Còn kháng nghị chưa xử lý, không thể phê duyệt". Kết quả vẫn ở trạng thái chờ phê duyệt. |
| **TC9** | Phê duyệt thành công sau khi xử lý hết kháng nghị | Chặng R đã lưu kết quả; tất cả kháng nghị đã xử lý xong | — | 1. Trọng tài chọn chặng R → Click Phê duyệt. | Trạng thái kết quả chặng R chuyển thành *chính thức*. Thông báo phê duyệt thành công. |
