# Module 2 — Đăng ký tay đua tham gia chặng đua — Nội dung chi tiết

> Nội dung chữ do Claude dựng. Việc của bạn: mở Visual Paradigm, vẽ theo các blueprint/PlantUML bên dưới, export ảnh vào `hinh/`, rồi ghép vào báo cáo.

## 0. Danh sách ảnh cần export (đặt vào `hinh/`)

| Tên file | Biểu đồ (mục) |
|---|---|
| `m2-uc-chitiet.png` | UC chi tiết (mục 1) |
| `m2-hoatdong.png` | Biểu đồ hoạt động (mục 3) |
| `m2-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) |
| `m2-giaodien-dangky.png` | Giao diện đăng ký (mục 5) |
| `m2-lop-mvc.png` | Biểu đồ lớp thiết kế MVC (mục 6) |
| `m2-tuantu.png` | Biểu đồ tuần tự (mục 7) |

> **Quy tắc tên:** `m<số module>-<tên biểu đồ>.png` — chữ thường, không dấu, ngăn cách bằng `-`.

---

## 1. Biểu đồ UC chi tiết

Chức năng "Đăng ký thi đấu" có các giao diện tương tác với nhân viên ⇒ tách use case con:
- Đăng nhập → UC `Đăng nhập`
- Chọn chặng và đội → UC `Chọn chặng và đội`
- Chọn tay đua + lưu → UC `Chọn tay đua đăng ký`

Quan hệ: `Đăng ký thi đấu` **include** {Đăng nhập, Chọn chặng và đội, Chọn tay đua đăng ký}.

```plantuml
@startuml
left to right direction
actor NhanVien
usecase "Đăng ký thi đấu" as UC
usecase "Đăng nhập" as DN
usecase "Chọn chặng và đội" as CD
usecase "Chọn tay đua đăng ký" as CT
NhanVien --> UC
UC ..> DN : include
UC ..> CD : include
UC ..> CT : include
@enduml
```

## 2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| **Use case** | Đăng ký tay đua tham gia chặng đua |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập; chặng đua và đội đua đã tồn tại |
| **Hậu điều kiện** | Danh sách đăng ký (tối đa 2 tay đua) của đội cho chặng được lưu và in phiếu |
| **Kịch bản chính** | 1. Nhân viên chọn menu "Đăng ký thi đấu".<br>2. Hệ thống hiển thị giao diện đăng ký (danh sách thả xuống chặng đua và đội đua).<br>3. Nhân viên chọn chặng đua và đội đua.<br>4. Hệ thống hiển thị danh sách tay đua đang có hợp đồng hiệu lực với đội tại thời điểm chặng.<br>5. Nhân viên tick chọn các tay đua theo yêu cầu của đội, click Lưu.<br>6. Hệ thống kiểm tra ràng buộc; nếu hợp lệ thì lưu đăng ký và in phiếu đăng ký (danh sách xuất phát). |
| **Ngoại lệ** | 4a. Đội không có tay đua nào có hợp đồng hiệu lực tại thời điểm chặng → thông báo, không đăng ký được.<br>5a. Chọn quá 2 tay đua → báo lỗi "Mỗi đội tối đa 2 tay đua trong một chặng", yêu cầu chọn lại.<br>5b. Tay đua đã được đăng ký chặng này (cho đội khác) → báo lỗi trùng đăng ký. |

## 3. Biểu đồ hoạt động (Activity)

```plantuml
@startuml
start
:Chọn menu Đăng ký thi đấu;
:Chọn chặng đua và đội đua;
:Hiển thị tay đua có hợp đồng hiệu lực;
:Tick chọn tay đua;
:Click Lưu;
if (Số tay đua <= 2 và không trùng?) then (không)
  :Báo lỗi;
  stop
else (có)
  :Lưu đăng ký;
  :In phiếu đăng ký (danh sách xuất phát);
  stop
endif
@enduml
```

## 4. Biểu đồ lớp phân tích (Boundary / Control / Entity)

- **Boundary:** `GDDangKyChang` (cboChang, cboDoi, lstTayDua có checkbox, btnLuu)
- **Control:** `DangKyChangControl` điều phối luồng
- **Entity (kèm phương thức nghiệp vụ):** `ChangDua`, `DoiDua`, `TayDua`, `HopDong`, `DangKyChang`

```plantuml
@startuml
class GDDangKyChang <<boundary>> {
  cboChang
  cboDoi
  lstTayDua
  btnLuu
  hienDanhSachTayDua(ds)
  inPhieuDangKy(phieu)
  baoLoi(tb)
}
class DangKyChangControl <<control>> {
  moManDangKy()
  chonChangDoi(changId, doiId)
  luuDangKy(changId, doiId, dsTayDua)
}
class ChangDua <<entity>> {
  id
  ma
  ten
  thoiGian
  getAll()
}
class DoiDua <<entity>> {
  id
  ma
  ten
  getAll()
}
class TayDua <<entity>> {
  id
  ma
  ten
  quocTich
  getTayDuaHieuLuc(doiId, thoiGianChang)
}
class HopDong <<entity>> {
  id
  ngayBatDau
  ngayKetThuc
}
class DangKyChang <<entity>> {
  id
  demSoTayDua(changId, doiId)
  daDangKy(changId, tayDuaId)
  them()
}
GDDangKyChang --> DangKyChangControl
DangKyChangControl --> ChangDua
DangKyChangControl --> DoiDua
DangKyChangControl --> TayDua
DangKyChangControl --> HopDong
DangKyChangControl --> DangKyChang
@enduml
```

## 5. Thiết kế giao diện

**Màn Đăng ký thi đấu:** hàng trên có 2 danh sách thả xuống [Chặng đua] và [Đội đua]; bên dưới là bảng tay đua (cột checkbox chọn, Mã, Tên, Quốc tịch) — chỉ hiện tay đua có hợp đồng hiệu lực với đội đã chọn; dưới cùng nút [Lưu]. Sau khi lưu → in phiếu đăng ký (danh sách xuất phát) gồm: tên chặng, ngày đua, tên đội, danh sách tay đua đã đăng ký (mỗi tay đua một dòng).

> Vẽ mockup màn này trong VP và export → `hinh/m2-giaodien-dangky.png`.

## 6. Biểu đồ lớp thiết kế (MVC)

- **View (jsp):** `gdDangKyChang.jsp`, `doLuuDangKy.jsp`
- **Controller:** `DangKyChangController`
- **DAO:** `ChangDuaDAO` (getAll), `DoiDuaDAO` (getAll), `TayDuaDAO` (getTayDuaHieuLuc), `DangKyChangDAO` (demSoTayDua, daDangKy, insert)
- **Entity:** `ChangDua`, `DoiDua`, `TayDua`, `HopDong`, `DangKyChang`

```plantuml
@startuml
package View {
  class gdDangKyChang
  class doLuuDangKy
}
package Controller {
  class DangKyChangController
}
package DAO {
  class ChangDuaDAO
  class DoiDuaDAO
  class TayDuaDAO
  class DangKyChangDAO
}
package Entity {
  class ChangDua
  class DoiDua
  class TayDua
  class DangKyChang
}
gdDangKyChang --> DangKyChangController
doLuuDangKy --> DangKyChangController
DangKyChangController --> ChangDuaDAO
DangKyChangController --> DoiDuaDAO
DangKyChangController --> TayDuaDAO
DangKyChangController --> DangKyChangDAO
ChangDuaDAO --> ChangDua
DoiDuaDAO --> DoiDua
TayDuaDAO --> TayDua
DangKyChangDAO --> DangKyChang
@enduml
```

## 7. Biểu đồ tuần tự (Sequence) — luồng chính

> Chỉ vẽ luồng chính. Ngoại lệ (không có tay đua hiệu lực, quá 2 tay đua, trùng đăng ký) mô tả trong đặc tả UC mục 2. Có khối `loop` khi lưu từng tay đua được chọn.

```plantuml
@startuml
actor NhanVien as NV
participant "gdDangKyChang" as V
participant "DangKyChangController" as C
participant "ChangDuaDAO" as CDAO
participant "DoiDuaDAO" as DDAO
participant "TayDuaDAO" as TDAO
participant "DangKyChangDAO" as KDAO
database "CSDL" as DB

NV -> V : chọn menu Đăng ký thi đấu
activate V
V -> C : moManDangKy()
activate C
C -> CDAO : getAll()
activate CDAO
CDAO -> DB : SELECT tblChangDua
activate DB
DB --> CDAO : rows
deactivate DB
CDAO --> C : List<ChangDua>
deactivate CDAO
C -> DDAO : getAll()
activate DDAO
DDAO -> DB : SELECT tblDoiDua
activate DB
DB --> DDAO : rows
deactivate DB
DDAO --> C : List<DoiDua>
deactivate DDAO
C --> V : hiển thị dropdown chặng, đội
deactivate C
V --> NV : giao diện đăng ký
deactivate V

NV -> V : chọn chặng, chọn đội
activate V
V -> C : chonChangDoi(changId, doiId)
activate C
C -> TDAO : getTayDuaHieuLuc(doiId, thoiGianChang)
activate TDAO
TDAO -> DB : SELECT tblTayDua JOIN tblHopDong (hiệu lực)
activate DB
DB --> TDAO : rows
deactivate DB
TDAO --> C : List<TayDua>
deactivate TDAO
C --> V : hiển thị danh sách tay đua
deactivate C
V --> NV : danh sách tay đua hợp lệ
deactivate V

NV -> V : tick chọn tay đua, click Lưu
activate V
V -> C : luuDangKy(changId, doiId, dsTayDua)
activate C
C -> KDAO : demSoTayDua(changId, doiId)
activate KDAO
KDAO -> DB : SELECT COUNT(*) tblDangKyChang
activate DB
DB --> KDAO : count
deactivate DB
KDAO --> C : soHienTai
deactivate KDAO
loop mỗi tay đua được chọn
  C -> KDAO : them(changId, doiId, tayDuaId)
  activate KDAO
  KDAO -> DB : INSERT INTO tblDangKyChang ...
  activate DB
  DB --> KDAO : ok
  deactivate DB
  KDAO --> C : ok
  deactivate KDAO
end
C --> V : in phiếu đăng ký
deactivate C
V --> NV : phiếu đăng ký đã in
deactivate V
@enduml
```

## 8. Test case

| ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi |
|---|---|---|---|---|---|
| TC1 | Đăng ký 2 tay đua hợp lệ | Đội X có ≥2 tay đua hợp đồng hiệu lực; chưa đăng ký chặng R | Chặng R, Đội X, tay đua A và B | Chọn R, X → tick A, B → Lưu | Lưu thành công, in phiếu đăng ký 2 tay đua |
| TC2 | Chặn quá 2 tay đua | Đội X có ≥3 tay đua hiệu lực | Chặng R, Đội X, tick A, B, C | Chọn R, X → tick 3 người → Lưu | Báo lỗi "tối đa 2 tay đua", không lưu |
| TC3 | Chặn trùng đăng ký | Tay đua A đã đăng ký chặng R cho đội Y | Chặng R, Đội X, tick A | Chọn R, X → tick A → Lưu | Báo lỗi trùng đăng ký, không lưu |
| TC4 | Đội không có tay đua hiệu lực | Đội Z không có hợp đồng hiệu lực tại thời điểm R | Chặng R, Đội Z | Chọn R, Z | Thông báo không có tay đua, không đăng ký được |
