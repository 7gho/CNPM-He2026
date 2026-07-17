# Module 4 — Quyết toán và trao giải cuối mùa — Nội dung chi tiết

> Nội dung chữ do Claude dựng. Việc của bạn: mở Visual Paradigm, vẽ theo các blueprint/PlantUML bên dưới, export ảnh vào `hinh/`, rồi ghép vào báo cáo.

---

## 1. Biểu đồ UC chi tiết

Chức năng "Quyết toán và trao giải" có các giao diện tương tác với quản lý ⇒ tách use case con:
- Đăng nhập → UC `Đăng nhập`
- Tổng hợp xếp hạng cuối mùa → UC `Tổng hợp xếp hạng`
- Nhập thưởng và lưu → UC `Nhập thưởng và lưu`

Quan hệ: `Quyết toán và trao giải` **include** {Đăng nhập, Tổng hợp xếp hạng, Nhập thưởng và lưu}.

```plantuml
@startuml
left to right direction
actor QuanLy
usecase "Quyết toán và trao giải" as UC
usecase "Đăng nhập" as DN
usecase "Tổng hợp xếp hạng" as TH
usecase "Nhập thưởng và lưu" as NT
QuanLy --> UC
UC ..> DN : include
UC ..> TH : include
UC ..> NT : include
@enduml
```

## 2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| **Use case** | Quyết toán và trao giải cuối mùa |
| **Actor** | Quản lý |
| **Tiền điều kiện** | Quản lý đã đăng nhập; mùa giải đã kết thúc |
| **Hậu điều kiện** | Bảng xếp hạng cuối mùa và tiền thưởng được lưu và in danh sách trao giải |
| **Kịch bản chính** | 1. Quản lý chọn menu "Quyết toán mùa giải".<br>2. Hệ thống kiểm tra tất cả chặng trong mùa đã có kết quả.<br>3. Hệ thống cộng dồn điểm và thời gian từng tay đua và từng đội, xếp hạng cá nhân và đội (giảm dần tổng điểm, bằng điểm thì tăng dần tổng thời gian), hiển thị 2 bảng.<br>4. Quản lý nhập mức thưởng cho từng hạng (1, 2, 3 cá nhân và đội), click Tính thưởng.<br>5. Hệ thống tính tiền thưởng tương ứng cho từng tay đua/đội.<br>6. Quản lý kiểm tra, click Lưu → hệ thống lưu quyết định trao giải và in danh sách trao giải. |
| **Ngoại lệ** | 2a. Còn chặng chưa có kết quả → báo lỗi "Chưa đủ kết quả để quyết toán", dừng. |

## 3. Biểu đồ hoạt động (Activity)

```plantuml
@startuml
start
:Chọn menu Quyết toán mùa giải;
:Kiểm tra tất cả chặng đã có kết quả;
if (Đủ kết quả tất cả chặng?) then (không)
  :Báo lỗi "chưa đủ kết quả";
  stop
else (có)
  :Cộng dồn điểm và thời gian toàn mùa;
  :Xếp hạng cá nhân và đội;
  :Nhập mức thưởng theo hạng;
  :Tính tiền thưởng;
  :Click Lưu;
  :Lưu quyết định trao giải;
  :In danh sách trao giải;
  stop
endif
@enduml
```

## 4. Biểu đồ lớp phân tích (Boundary / Control / Entity)

- **Boundary:** `GDQuyetToan` (btnQuyetToan, tblXHCaNhan, tblXHDoi, txtThuongHang1..3, btnTinhThuong, btnLuu)
- **Control:** `QuyetToanControl` điều phối luồng, kiểm tra ràng buộc, cộng dồn và tính thưởng
- **Entity (kèm phương thức nghiệp vụ):** `MuaGiai`, `ChangDua`, `KetQua`, `TayDua`, `DoiDua`, `TraoGiai`

```plantuml
@startuml
class GDQuyetToan <<boundary>> {
  btnQuyetToan
  tblXHCaNhan
  tblXHDoi
  txtThuong
  btnTinhThuong
  btnLuu
  hienXepHang(dsCaNhan, dsDoi)
  inDanhSachTraoGiai(ds)
  baoLoi(tb)
}
class QuyetToanControl <<control>> {
  quyetToan(muaId)
  tinhThuong(mucThuong)
  luuTraoGiai(muaId, dsTraoGiai)
}
class MuaGiai <<entity>> {
  id
  nam
  tenGiai
}
class ChangDua <<entity>> {
  id
  demChangChuaCoKetQua(muaId)
}
class KetQua <<entity>> {
  id
  diem
  thoiGian
  tongHopCaNhan(muaId)
  tongHopDoi(muaId)
}
class TayDua <<entity>> {
  id
  ten
  quocTich
}
class DoiDua <<entity>> {
  id
  ten
  hang
}
class TraoGiai <<entity>> {
  id
  loai
  hang
  tongDiem
  tongThoiGian
  tienThuong
  tinhThuong(hang, mucThuong)
  them()
}
GDQuyetToan --> QuyetToanControl
QuyetToanControl --> MuaGiai
QuyetToanControl --> ChangDua
QuyetToanControl --> KetQua
QuyetToanControl --> TayDua
QuyetToanControl --> DoiDua
QuyetToanControl --> TraoGiai
@enduml
```

> Quy tắc xếp hạng (cài trong `tongHopCaNhan`/`tongHopDoi` + sắp xếp): cộng dồn tổng điểm và tổng thời gian qua tất cả chặng; sắp xếp giảm dần theo tổng điểm, nếu bằng điểm thì tăng dần theo tổng thời gian.

## 5. Thiết kế giao diện

**Màn Quyết toán:** nút [Quyết toán mùa giải] ở trên; sau khi bấm hiện 2 bảng — bảng Xếp hạng cá nhân (Hạng, Tay đua, Đội, Tổng điểm, Tổng thời gian) và bảng Xếp hạng đội (Hạng, Đội, Tổng điểm, Tổng thời gian); khu nhập mức thưởng cho hạng 1/2/3; nút [Tính thưởng] → bổ sung cột Tiền thưởng vào 2 bảng; nút [Lưu]. Sau khi lưu → in danh sách trao giải.

> Vẽ mockup màn này trong VP và export vào `hinh/gd-quyettoan.png`.

## 6. Biểu đồ lớp thiết kế (MVC)

- **View (jsp):** `gdQuyetToan.jsp`, `doLuuTraoGiai.jsp`
- **Controller:** `QuyetToanController`
- **DAO:** `ChangDuaDAO` (demChangChuaCoKetQua), `KetQuaDAO` (tongHopCaNhan, tongHopDoi), `TraoGiaiDAO` (insert)
- **Entity:** `MuaGiai`, `ChangDua`, `KetQua`, `TayDua`, `DoiDua`, `TraoGiai`

```plantuml
@startuml
package View {
  class gdQuyetToan
  class doLuuTraoGiai
}
package Controller {
  class QuyetToanController
}
package DAO {
  class ChangDuaDAO
  class KetQuaDAO
  class TraoGiaiDAO
}
package Entity {
  class MuaGiai
  class ChangDua
  class KetQua
  class TayDua
  class DoiDua
  class TraoGiai
}
gdQuyetToan --> QuyetToanController
doLuuTraoGiai --> QuyetToanController
QuyetToanController --> ChangDuaDAO
QuyetToanController --> KetQuaDAO
QuyetToanController --> TraoGiaiDAO
KetQuaDAO --> KetQua
ChangDuaDAO --> ChangDua
TraoGiaiDAO --> TraoGiai
KetQua --> TayDua
KetQua --> DoiDua
@enduml
```

## 7. Biểu đồ tuần tự (Sequence) — luồng chính

> Chỉ vẽ luồng chính (mùa giải đã đủ kết quả). Ngoại lệ (còn chặng chưa có kết quả) mô tả trong đặc tả UC mục 2. Có 2 khối `loop`: một khi tính thưởng theo hạng, một khi lưu từng bản ghi trao giải.

```plantuml
@startuml
actor QuanLy as QL
participant "gdQuyetToan" as V
participant "QuyetToanController" as C
participant "ChangDuaDAO" as CDAO
participant "KetQuaDAO" as KDAO
participant "TraoGiaiDAO" as TDAO
database "CSDL" as DB

QL -> V : click Quyết toán mùa giải
activate V
V -> C : quyetToan(muaId)
activate C
C -> CDAO : demChangChuaCoKetQua(muaId)
activate CDAO
CDAO -> DB : SELECT COUNT(*) chặng chưa có kết quả
activate DB
DB --> CDAO : count
deactivate DB
CDAO --> C : 0 (đủ kết quả)
deactivate CDAO
C -> KDAO : tongHopCaNhan(muaId)
activate KDAO
KDAO -> DB : SELECT SUM(diem), SUM(thoiGian) GROUP BY tayDua
activate DB
DB --> KDAO : rows
deactivate DB
KDAO --> C : List<XH cá nhân>
deactivate KDAO
C -> KDAO : tongHopDoi(muaId)
activate KDAO
KDAO -> DB : SELECT SUM(diem), SUM(thoiGian) GROUP BY doi
activate DB
DB --> KDAO : rows
deactivate DB
KDAO --> C : List<XH đội>
deactivate KDAO
C -> C : sapXep(giảm điểm, tăng thời gian)
C --> V : hiển thị 2 bảng xếp hạng
deactivate C
V --> QL : bảng xếp hạng cá nhân + đội
deactivate V

QL -> V : nhập mức thưởng, click Tính thưởng
activate V
V -> C : tinhThuong(mucThuong)
activate C
loop mỗi hạng được thưởng
  C -> C : ganTienThuong(hang, mucThuong)
end
C --> V : hiển thị cột tiền thưởng
deactivate C
V --> QL : bảng có tiền thưởng

QL -> V : click Lưu
V -> C : luuTraoGiai(muaId, dsTraoGiai)
activate C
loop mỗi bản ghi trao giải
  C -> TDAO : them(traoGiai)
  activate TDAO
  TDAO -> DB : INSERT INTO tblTraoGiai ...
  activate DB
  DB --> TDAO : ok
  deactivate DB
  TDAO --> C : ok
  deactivate TDAO
end
C --> V : in danh sách trao giải
deactivate C
V --> QL : danh sách trao giải đã in
deactivate V
@enduml
```

## 8. Test case

| ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi |
|---|---|---|---|---|---|
| TC1 | Quyết toán hợp lệ | Tất cả chặng đã có kết quả | Mùa giải 2026 | Quyết toán → nhập thưởng → Lưu | Xếp hạng đúng, tính thưởng, lưu + in danh sách trao giải |
| TC2 | Chặn khi thiếu kết quả | Còn 1 chặng chưa có kết quả | Mùa giải 2026 | Click Quyết toán | Báo lỗi "chưa đủ kết quả", không quyết toán |
| TC3 | Tie-break bằng điểm | Tay đua A và B cùng tổng điểm, A có tổng thời gian nhỏ hơn | Mùa giải 2026 | Quyết toán | A xếp trên B |
| TC4 | Tính tiền thưởng theo hạng | Đã quyết toán, xếp hạng xong | Thưởng hạng 1 = 100tr | Nhập mức thưởng → Tính thưởng | Tay đua/đội hạng 1 nhận đúng 100tr |
