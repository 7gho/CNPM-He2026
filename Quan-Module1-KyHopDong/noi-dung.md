# Module 1 — Ký hợp đồng tay đua với đội đua — Nội dung chi tiết

> Nội dung chữ do Claude dựng. Việc của bạn: mở Visual Paradigm, vẽ theo các blueprint/PlantUML bên dưới, export ảnh vào `hinh/`, rồi ghép vào báo cáo.

---

## 1. Biểu đồ UC chi tiết

Chức năng "Ký hợp đồng" có các giao diện tương tác với nhân viên ⇒ tách use case con:
- Đăng nhập → UC `Đăng nhập`
- Tìm tay đua → UC `Tìm tay đua`
- Nhập thông tin hợp đồng (chọn đội, ngày, lưu) → UC `Nhập thông tin hợp đồng`
- (mở rộng) Thêm tay đua mới khi không tìm thấy → UC `Thêm tay đua`

Quan hệ: `Ký hợp đồng` **include** {Đăng nhập, Tìm tay đua, Nhập thông tin hợp đồng}; `Nhập thông tin hợp đồng` **extend** bởi `Thêm tay đua` (chỉ khi tay đua chưa có).

```plantuml
@startuml
left to right direction
actor NhanVien
usecase "Ký hợp đồng" as UC
usecase "Đăng nhập" as DN
usecase "Tìm tay đua" as TIM
usecase "Nhập thông tin hợp đồng" as NHAP
usecase "Thêm tay đua" as THEM
NhanVien --> UC
UC ..> DN : include
UC ..> TIM : include
UC ..> NHAP : include
THEM ..> NHAP : extend
@enduml
```

## 2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| **Use case** | Ký hợp đồng tay đua với đội đua |
| **Actor** | Nhân viên |
| **Tiền điều kiện** | Nhân viên đã đăng nhập thành công |
| **Hậu điều kiện** | Một hợp đồng mới hợp lệ được lưu vào hệ thống và in ra |
| **Kịch bản chính** | 1. Nhân viên chọn menu "Ký hợp đồng".<br>2. Hệ thống hiển thị giao diện tìm tay đua.<br>3. Nhân viên nhập tên tay đua và click Tìm.<br>4. Hệ thống hiển thị danh sách tay đua có tên chứa từ khóa.<br>5. Nhân viên chọn đúng tay đua.<br>6. Hệ thống hiển thị chi tiết tay đua và danh sách hợp đồng cũ (đội, ngày bắt đầu, ngày kết thúc).<br>7. Nhân viên chọn đội đua, nhập ngày bắt đầu và ngày kết thúc, click Lưu.<br>8. Hệ thống kiểm tra ràng buộc chồng lấn; nếu hợp lệ thì lưu hợp đồng và in ra hợp đồng. |
| **Ngoại lệ** | 4a. Không tìm thấy tay đua → hệ thống cho phép nhập tay đua mới (UC Thêm tay đua) rồi quay lại bước 6.<br>7a. Ngày kết thúc ≤ ngày bắt đầu → báo lỗi, yêu cầu nhập lại.<br>8a. Khoảng thời gian hợp đồng mới chồng lấn một hợp đồng cũ (tay đua đã thuộc đội khác trong thời gian đó) → báo lỗi "Tay đua đã có hợp đồng trong khoảng thời gian này", yêu cầu nhập lại. |

## 3. Biểu đồ hoạt động (Activity)

```plantuml
@startuml
start
:Chọn menu Ký hợp đồng;
:Nhập tên tay đua, click Tìm;
if (Tìm thấy tay đua?) then (không)
  :Nhập tay đua mới;
else (có)
endif
:Chọn tay đua;
:Hiển thị hợp đồng cũ;
:Chọn đội, nhập ngày bắt đầu/kết thúc;
:Click Lưu;
if (Ngày hợp lệ và không chồng lấn?) then (không)
  :Báo lỗi;
  stop
else (có)
  :Lưu hợp đồng;
  :In hợp đồng;
  stop
endif
@enduml
```

## 4. Biểu đồ lớp phân tích (Boundary / Control / Entity)

- **Boundary:** `GDTimTayDua` (txtTen, btnTim, lstTayDua), `GDNhapHopDong` (lblTayDua, lstHopDongCu, cboDoi, dtpBatDau, dtpKetThuc, btnLuu)
- **Control:** `KyHopDongControl` (timTayDua(ten), layHopDongCu(tayDua), kiemTraChongLan(tayDua, batDau, ketThuc), luuHopDong(...))
- **Entity:** `TayDua`, `DoiDua`, `HopDong`

```plantuml
@startuml
class GDTimTayDua <<boundary>> {
  txtTen
  btnTim
  lstTayDua
}
class GDNhapHopDong <<boundary>> {
  lstHopDongCu
  cboDoi
  dtpBatDau
  dtpKetThuc
  btnLuu
}
class KyHopDongControl <<control>> {
  timTayDua(ten)
  layHopDongCu(td)
  kiemTraChongLan(td, bd, kt)
  luuHopDong(td, doi, bd, kt)
}
class TayDua <<entity>>
class DoiDua <<entity>>
class HopDong <<entity>>
GDTimTayDua --> KyHopDongControl
GDNhapHopDong --> KyHopDongControl
KyHopDongControl --> TayDua
KyHopDongControl --> DoiDua
KyHopDongControl --> HopDong
@enduml
```

## 5. Thiết kế giao diện

**Màn 1 — Tìm tay đua:** ô nhập "Tên tay đua" + nút [Tìm]; bảng kết quả (Mã, Tên, Ngày sinh, Quốc tịch) mỗi dòng có nút [Chọn]; nút [+ Thêm tay đua mới].

**Màn 2 — Nhập hợp đồng:** phần trên hiển thị thông tin tay đua đã chọn + bảng "Hợp đồng cũ" (Đội, Ngày bắt đầu, Ngày kết thúc); phần dưới form: combobox [Đội đua], date [Ngày bắt đầu], date [Ngày kết thúc], nút [Lưu]. Khi lưu lỗi → hiện thông báo đỏ dưới form.

> Vẽ mockup 2 màn này trong VP (hoặc Balsamiq) và export vào `hinh/gd-*.png`.

## 6. Biểu đồ lớp thiết kế (MVC)

- **View (jsp):** `gdTimTayDua.jsp`, `gdNhapHopDong.jsp`, `doLuuHopDong.jsp`
- **Controller:** `HopDongController`
- **DAO:** `TayDuaDAO` (timTheoTen), `DoiDuaDAO` (getAll), `HopDongDAO` (getByTayDua, kiemTraChongLan, insert)
- **Entity:** `TayDua`, `DoiDua`, `HopDong`

```plantuml
@startuml
package View {
  class gdTimTayDua
  class gdNhapHopDong
  class doLuuHopDong
}
package Controller {
  class HopDongController
}
package DAO {
  class TayDuaDAO
  class DoiDuaDAO
  class HopDongDAO
}
package Entity {
  class TayDua
  class DoiDua
  class HopDong
}
gdTimTayDua --> HopDongController
gdNhapHopDong --> HopDongController
doLuuHopDong --> HopDongController
HopDongController --> TayDuaDAO
HopDongController --> DoiDuaDAO
HopDongController --> HopDongDAO
TayDuaDAO --> TayDua
DoiDuaDAO --> DoiDua
HopDongDAO --> HopDong
@enduml
```

## 7. Biểu đồ tuần tự (Sequence)

```plantuml
@startuml
actor NhanVien as NV
participant gdTimTayDua as V1
participant gdNhapHopDong as V2
participant HopDongController as C
participant TayDuaDAO as TDAO
participant HopDongDAO as HDAO
NV -> V1 : nhập tên, click Tìm
V1 -> C : timTayDua(ten)
C -> TDAO : timTheoTen(ten)
TDAO --> C : danh sách tay đua
C --> V1 : hiển thị danh sách
NV -> V1 : chọn tay đua
V1 -> C : layHopDongCu(tayDua)
C -> HDAO : getByTayDua(id)
HDAO --> C : hợp đồng cũ
C --> V2 : mở màn nhập + hợp đồng cũ
NV -> V2 : chọn đội, nhập ngày, click Lưu
V2 -> C : luuHopDong(td, doi, bd, kt)
C -> HDAO : kiemTraChongLan(td, bd, kt)
HDAO --> C : ket qua
alt hợp lệ
  C -> HDAO : insert(hopDong)
  HDAO --> C : ok
  C --> V2 : in hợp đồng
else chồng lấn
  C --> V2 : báo lỗi
end
@enduml
```

## 8. Test case

| ID | Mục tiêu | Tiền điều kiện | Dữ liệu vào | Các bước | Kết quả mong đợi |
|---|---|---|---|---|---|
| TC1 | Ký hợp đồng hợp lệ | Đã đăng nhập; tay đua chưa có hợp đồng trùng thời gian | Tay đua A, Đội X, 01/01/2026–31/12/2026 | Tìm A → chọn → chọn X, nhập ngày → Lưu | Lưu thành công, in hợp đồng |
| TC2 | Chặn chồng lấn thời gian | Tay đua A đã có HĐ với Đội Y 01/06/2026–31/12/2026 | Tay đua A, Đội X, 01/01/2026–30/06/2026 | Tìm A → chọn → nhập ngày chồng lấn → Lưu | Báo lỗi "đã có hợp đồng trong khoảng thời gian này", không lưu |
| TC3 | Thêm tay đua khi không tìm thấy | Đã đăng nhập | Tên "Zzz" (chưa có) | Tìm "Zzz" → không có → Thêm mới | Hiện form thêm tay đua, thêm xong quay lại ký HĐ |
| TC4 | Kiểm tra ngày | Đã đăng nhập | Tay đua A, Đội X, 31/12/2026–01/01/2026 | Nhập ngày kết thúc < bắt đầu → Lưu | Báo lỗi ngày không hợp lệ, không lưu |
