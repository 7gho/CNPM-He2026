# BÁO CÁO ĐỒ ÁN MÔN NHẬP MÔN CÔNG NGHỆ PHẦN MỀM

## Đề tài: Quản lý giải đua xe F1

> Bản thảo báo cáo do Claude dựng để nhóm xem qua. Chỗ có **[Hình …]** là nơi chèn ảnh biểu đồ đã export từ Visual Paradigm (đường dẫn ảnh ghi kèm). Sau khi chèn đủ ảnh, xuất file này ra Word để nộp.

**Nhóm:** Nhóm 3 — Học viện Công nghệ Bưu chính Viễn thông
**Giảng viên hướng dẫn:** (điền tên GV)

| Thành viên | Vai trò | Phần phụ trách |
|---|---|---|
| Quan | Trưởng nhóm | Module 1 — Ký hợp đồng tay đua với đội đua |
| Kin | Thành viên | Module 2 — Đăng ký tay đua tham gia chặng đua |
| Kiet | Thành viên | Module 3 — Cập nhật kết quả và tính điểm chặng đua |
| Thanh | Thành viên | Module 4 — Quyết toán và trao giải cuối mùa |

---

## Mục lục

- Chương 1. Mô tả bài toán
- Chương 2. Đặc tả yêu cầu phần mềm
- Chương 3. Biểu đồ Use Case tổng quát
- Chương 4. Biểu đồ lớp thực thể và thiết kế cơ sở dữ liệu
- Chương 5. Module 1 — Ký hợp đồng tay đua với đội đua (Quan)
- Chương 6. Module 2 — Đăng ký tay đua tham gia chặng đua (Kin)
- Chương 7. Module 3 — Cập nhật kết quả và tính điểm chặng đua (Kiet)
- Chương 8. Module 4 — Quyết toán và trao giải cuối mùa (Thanh)
- Chương 9. Kết luận

---

## Chương 1. Mô tả bài toán

Hệ thống quản lý một giải vô địch đua xe F1 diễn ra hằng năm. Các quy tắc nghiệp vụ:

- Mỗi năm có một giải vô địch. Một giải đấu gồm nhiều chặng đua diễn ra khắp thế giới (mã chặng đua, tên, số vòng đua, địa điểm, thời gian, mô tả).
- Mỗi giải đấu có nhiều đội đua tham gia (mã, tên, hãng, mô tả).
- Mỗi đội đua có nhiều tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử). Nhưng trong mỗi chặng đua, mỗi đội chỉ được phép cho tối đa 2 tay đua tham gia.
- Mỗi tay đua có thể thi đấu cho nhiều đội đua ở các thời điểm khác nhau, nhưng tại một thời điểm chỉ thi đấu cho 1 đội.
- Với mỗi chặng đua, kết quả được xếp hạng theo thứ tự về đích (thời gian); điểm chỉ tính cho top 10 lần lượt là 25, 18, 15, 12, 10, 8, 6, 4, 2, 1. Tay đua trong top 10 nhưng không hoàn thành (DNF) nhận 0 điểm.
- Điểm và thời gian của mỗi tay đua được cộng dồn qua các chặng để quyết định giải cá nhân và giải đồng đội của mùa giải.

Hệ thống gồm 4 chức năng nghiệp vụ chính, mỗi thành viên phụ trách một module: (1) Ký hợp đồng tay đua với đội đua, (2) Đăng ký tay đua tham gia chặng đua, (3) Cập nhật kết quả và tính điểm chặng đua, (4) Quyết toán và trao giải cuối mùa.

---

## Chương 2. Đặc tả yêu cầu phần mềm

### 2.1. Người dùng

| Người dùng (actor) | Được thực hiện |
|---|---|
| Thành viên (chung) | Đăng nhập, đổi mật khẩu |
| Nhân viên | Ký hợp đồng (M1), đăng ký tay đua vào chặng (M2), cập nhật kết quả chặng (M3); quản lý danh mục (mùa giải, tay đua, đội, chặng); đăng ký đội tham gia mùa giải |
| Quản lý | Quyết toán và trao giải cuối mùa (M4) |

### 2.2. Yêu cầu chức năng

- **FR0 — Xác thực & tài khoản:** đăng nhập, đổi mật khẩu, phân quyền theo vai trò.
- **FR1 — Quản lý danh mục:** thêm/sửa/xóa tay đua, đội đua, chặng đua; quản lý mùa giải; đăng ký đội tham gia mùa giải (sinh ThamGia).
- **FR2 — Ký hợp đồng (M1):** ký hợp đồng: CHỈ nhập ngày bắt đầu; nếu tay đua còn HĐ hiệu lực thì hệ thống TỰ ĐỘNG ĐÓNG hợp đồng cũ (ngày kết thúc = ngày liền trước ngày bắt đầu mới); nếu chồng lấn khoảng đã đóng thì báo lỗi; lưu và in hợp đồng.
- **FR3 — Đăng ký chặng (M2):** chọn chặng và đội, hiển thị tay đua có hợp đồng hiệu lực, tick chọn; ràng buộc: mỗi đội tối đa 2 tay đua/chặng, không trùng; lưu và in phiếu đăng ký.
- **FR4 — Cập nhật kết quả (M3):** nhập thời gian/số vòng/DNF; tính điểm top 10 (25→1), DNF = 0; lưu và in bảng kết quả.
- **FR5 — Quyết toán (M4):** kiểm tra đủ kết quả tất cả chặng, cộng dồn điểm/thời gian, xếp hạng cá nhân và đội, nhập mức thưởng và tính tiền thưởng; lưu và in danh sách trao giải.

### 2.3. Yêu cầu phi chức năng

| # | Loại | Yêu cầu |
|---|---|---|
| NFR1 | Bảo mật | Đăng nhập; phân quyền theo vai trò (Nhân viên/Quản lý). |
| NFR2 | Tính đúng đắn | Phép tính điểm, xếp hạng, tiền thưởng chính xác theo luật F1. |
| NFR3 | Toàn vẹn dữ liệu | Kiểm tra ràng buộc trước khi lưu (chồng lấn hợp đồng, ≤2 tay đua/chặng, đủ kết quả trước quyết toán). |
| NFR4 | Khả dụng | Giao diện tiếng Việt; thông báo lỗi rõ ràng khi vi phạm ràng buộc. |
| NFR5 | Hiệu năng | Danh sách hiển thị < 2 giây với quy mô một mùa giải. |
| NFR6 | Khả bảo trì | Kiến trúc phân tầng MVC. |
| NFR7 | Khả chuyển | Chạy trên trình duyệt web thông dụng. |

---

## Chương 3. Biểu đồ Use Case tổng quát

**Actor:** `ThanhVien` (trừu tượng), `NhanVien` và `QuanLy` kế thừa `ThanhVien`.

**Use case:** Đăng nhập, Đổi mật khẩu, Quản lý tay đua/đội/chặng, Quản lý mùa giải, Đăng ký đội tham gia mùa giải (actor NhanVien, danh mục), Ký hợp đồng (M1), Đăng ký tay đua vào chặng (M2), Cập nhật kết quả chặng (M3), Quyết toán và trao giải (M4). Các use case nghiệp vụ đều **include** "Đăng nhập".

Đặc tả gọn cho các UC danh mục và Đăng nhập/Đổi mật khẩu xem docs/04-dac-ta-danh-muc-va-auth.md.

**[Hình 3.1 — Biểu đồ Use Case tổng quát]** — chèn ảnh `docs/hinh/uc-tongquat.png`

![Biểu đồ Use Case tổng quát](<hinh/uc-tongquat.png>)

---

## Chương 4. Biểu đồ lớp thực thể và thiết kế cơ sở dữ liệu

### 4.1. Các lớp thực thể

`MuaGiai`, `ChangDua`, `DoiDua`, `TayDua`, `HopDong` (trung gian TayDua–DoiDua), `DangKyChang` (trung gian ChangDua–TayDua–DoiDua), `KetQua`, `TraoGiai`, `ThamGia` (trung gian MuaGiai–DoiDua), `ThanhVien` (tài khoản người dùng).

Các quan hệ n-n được tách bằng lớp trung gian: `HopDong`, `DangKyChang`, `ThamGia`.

**[Hình 4.1 — Biểu đồ lớp thực thể (pha thiết kế)]** — chèn ảnh `docs/hinh/lop-thucthe.png`

![Biểu đồ lớp thực thể](<hinh/lop-thucthe.png>)

### 4.2. Thiết kế cơ sở dữ liệu

| Bảng | Cột chính | Khóa |
|---|---|---|
| `tblMuaGiai` | id, nam, tenGiai, moTa | PK: id |
| `tblDoiDua` | id, ma, ten, hang, moTa | PK: id |
| `tblTayDua` | id, ma, ten, ngaySinh, quocTich, tieuSu | PK: id |
| `tblChangDua` | id, ma, ten, soVong, diaDiem, thoiGian, moTa, muaGiaiId | PK: id · FK: muaGiaiId |
| `tblThamGia` | id, muaGiaiId, doiDuaId | PK: id · FK: muaGiaiId, doiDuaId |
| `tblHopDong` | id, tayDuaId, doiDuaId, ngayBatDau, ngayKetThuc | PK: id · FK: tayDuaId, doiDuaId |
| `tblDangKyChang` | id, changDuaId, tayDuaId, doiDuaId | PK: id · FK: changDuaId, tayDuaId, doiDuaId |
| `tblKetQua` | id, dangKyChangId, thoiGian, soVong, dnf, hang, diem | PK: id · FK: dangKyChangId |
| `tblTraoGiai` | id, muaGiaiId, loai, tayDuaId, doiDuaId, hang, tongDiem, tongThoiGian, tienThuong | PK: id · FK: muaGiaiId, tayDuaId, doiDuaId |
| tblThanhVien | id, tenDangNhap, matKhau, hoTen, vaiTro | PK: id |

- tblDangKyChang có UNIQUE(changDuaId, tayDuaId)
- tblHopDong.ngayKetThuc NULL-able (NULL = HĐ đang hiệu lực)

---

## Chương 5. Module 1 — Ký hợp đồng tay đua với đội đua (Quan)

### 5.1. Biểu đồ Use Case chi tiết
UC `Ký hợp đồng` include {Đăng nhập, Tìm tay đua, Nhập thông tin hợp đồng}; `Nhập thông tin hợp đồng` được extend bởi `Thêm tay đua`.

**[Hình 5.1]** — `../Module 1 - Quan/hinh/m1-uc-chitiet.png`
![UC chi tiết M1](<../Module 1 - Quan/hinh/m1-uc-chitiet.png>)

### 5.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| Use case | Ký hợp đồng tay đua với đội đua |
| Actor | Nhân viên |
| Tiền điều kiện | Nhân viên đã đăng nhập |
| Hậu điều kiện | Một hợp đồng mới hợp lệ được lưu và in ra |
| Kịch bản chính | 1. Chọn menu Ký hợp đồng. 2. Hệ thống hiện giao diện tìm tay đua. 3. Nhập tên, click Tìm. 4. Hệ thống hiện danh sách tay đua. 5. Chọn tay đua. 6. Hệ thống hiện chi tiết + hợp đồng cũ. 7. Chọn đội, CHỈ nhập ngày bắt đầu hiệu lực, click Lưu. 8. Hệ thống: nếu tay đua còn HĐ hiệu lực → tự động đóng HĐ cũ (ngày kết thúc = ngày bắt đầu mới − 1); nếu ngày bắt đầu chồng lấn khoảng đã đóng → báo lỗi; hợp lệ → lưu và in hợp đồng. |
| Ngoại lệ | 4a. Không tìm thấy → thêm tay đua mới. 8a. Chồng lấn khoảng thời gian của hợp đồng ĐÃ ĐÓNG (lịch sử) → báo lỗi. |

### 5.3. Biểu đồ hoạt động
**[Hình 5.2]** — `../Module 1 - Quan/hinh/m1-hoatdong.png`
![Hoạt động M1](<../Module 1 - Quan/hinh/m1-hoatdong.png>)

### 5.4. Biểu đồ lớp phân tích
**[Hình 5.3]** — `../Module 1 - Quan/hinh/m1-lop-phantich.png`
![Lớp phân tích M1](<../Module 1 - Quan/hinh/m1-lop-phantich.png>)

### 5.5. Thiết kế giao diện
**[Hình 5.4]** — `../Module 1 - Quan/hinh/m1-giaodien-timtaydua.png`
![Giao diện tìm tay đua](<../Module 1 - Quan/hinh/m1-giaodien-timtaydua.png>)

**[Hình 5.5]** — `../Module 1 - Quan/hinh/m1-giaodien-nhaphopdong.png`
![Giao diện nhập hợp đồng](<../Module 1 - Quan/hinh/m1-giaodien-nhaphopdong.png>)

### 5.6. Biểu đồ lớp thiết kế (MVC)
**[Hình 5.6]** — `../Module 1 - Quan/hinh/m1-lop-mvc.png`
![Lớp MVC M1](<../Module 1 - Quan/hinh/m1-lop-mvc.png>)

### 5.7. Biểu đồ tuần tự
**[Hình 5.7]** — `../Module 1 - Quan/hinh/m1-tuantu.png`
![Tuần tự M1](<../Module 1 - Quan/hinh/m1-tuantu.png>)

### 5.8. Test case

| ID | Mục tiêu | Dữ liệu vào | Kết quả mong đợi |
|---|---|---|---|
| TC1 | Ký hợp đồng hợp lệ | Tay đua A, Đội X, từ 01/01/2026 (ngày kết thúc để trống) | Lưu thành công, in hợp đồng |
| TC2 | Chặn chồng lấn | A đã có HĐ 01/06–31/12; nhập 01/01–30/06 | Báo lỗi, không lưu |
| TC3 | Thêm tay đua khi không tìm thấy | Tên chưa có | Hiện form thêm tay đua |
| TC4 | Ký HĐ mới khi tay đua CÒN HĐ hiệu lực với đội khác | Tay đua A đang có HĐ hiệu lực với đội Y, ký HĐ mới với đội X | Tự động đóng HĐ cũ (ngày kết thúc = ngày bắt đầu mới − 1), lưu HĐ mới |

---

## Chương 6. Module 2 — Đăng ký tay đua tham gia chặng đua (Kin)

### 6.1. Biểu đồ Use Case chi tiết
UC `Đăng ký thi đấu` include {Đăng nhập, Chọn chặng và đội, Chọn tay đua đăng ký}.

**[Hình 6.1]** — `../Module 2 - Kin/hinh/m2-uc-chitiet.png`
![UC chi tiết M2](<../Module 2 - Kin/hinh/m2-uc-chitiet.png>)

### 6.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| Use case | Đăng ký tay đua tham gia chặng đua |
| Actor | Nhân viên |
| Tiền điều kiện | Đã đăng nhập; chặng và đội đã tồn tại |
| Hậu điều kiện | Danh sách đăng ký (≤2 tay đua) được lưu và in phiếu |
| Kịch bản chính | 1. Chọn menu Đăng ký thi đấu. 2. Hệ thống hiện dropdown chặng, đội. 3. Chọn chặng và đội. 4. Hệ thống hiện tay đua có hợp đồng hiệu lực. 5. Tick chọn tay đua, click Lưu. 6. Hệ thống kiểm tra ràng buộc; hợp lệ → lưu và in phiếu đăng ký. |
| Ngoại lệ | 4a. Đội không có tay đua hiệu lực → thông báo. 5a. Quá 2 tay đua → báo lỗi. 5b. Tay đua đã đăng ký chặng → báo lỗi trùng. |

### 6.3. Biểu đồ hoạt động
**[Hình 6.2]** — `../Module 2 - Kin/hinh/m2-hoatdong.png`
![Hoạt động M2](<../Module 2 - Kin/hinh/m2-hoatdong.png>)

### 6.4. Biểu đồ lớp phân tích
**[Hình 6.3]** — `../Module 2 - Kin/hinh/m2-lop-phantich.png`
![Lớp phân tích M2](<../Module 2 - Kin/hinh/m2-lop-phantich.png>)

### 6.5. Thiết kế giao diện
**[Hình 6.4]** — `../Module 2 - Kin/hinh/m2-giaodien-dangky.png`
![Giao diện đăng ký](<../Module 2 - Kin/hinh/m2-giaodien-dangky.png>)

### 6.6. Biểu đồ lớp thiết kế (MVC)
**[Hình 6.5]** — `../Module 2 - Kin/hinh/m2-lop-mvc.png`
![Lớp MVC M2](<../Module 2 - Kin/hinh/m2-lop-mvc.png>)

### 6.7. Biểu đồ tuần tự
**[Hình 6.6]** — `../Module 2 - Kin/hinh/m2-tuantu.png`
![Tuần tự M2](<../Module 2 - Kin/hinh/m2-tuantu.png>)

### 6.8. Test case

| ID | Mục tiêu | Dữ liệu vào | Kết quả mong đợi |
|---|---|---|---|
| TC1 | Đăng ký 2 tay đua hợp lệ | Chặng R, Đội X, A và B | Lưu, in phiếu đăng ký |
| TC2 | Chặn quá 2 tay đua | Tick A, B, C | Báo lỗi "tối đa 2 tay đua" |
| TC3 | Chặn trùng đăng ký | A đã đăng ký chặng R cho đội Y | Báo lỗi trùng |
| TC4 | Đội không có tay đua hiệu lực | Đội Z | Thông báo, không đăng ký được |

---

## Chương 7. Module 3 — Cập nhật kết quả và tính điểm chặng đua (Kiet)

### 7.1. Biểu đồ Use Case chi tiết
UC `Cập nhật kết quả` include {Đăng nhập, Chọn chặng, Nhập kết quả và tính điểm}.

**[Hình 7.1]** — `../Module 3 - Kiet/hinh/m3-uc-chitiet.png`
![UC chi tiết M3](<../Module 3 - Kiet/hinh/m3-uc-chitiet.png>)

### 7.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| Use case | Cập nhật kết quả và tính điểm chặng đua |
| Actor | Nhân viên |
| Tiền điều kiện | Đã đăng nhập; chặng đã có tay đua đăng ký |
| Hậu điều kiện | Kết quả + điểm được lưu và in bảng kết quả |
| Kịch bản chính | 1. Chọn menu Cập nhật kết quả. 2. Hệ thống hiện chọn chặng. 3. Chọn chặng. 4. Hệ thống hiện bảng tay đua đăng ký. 5. Nhập thời gian/số vòng/DNF, click Tính kết quả. 6. Hệ thống xếp hạng, gán điểm 25→1, DNF = 0. 7. Kiểm tra, click Lưu → lưu và in bảng kết quả. |
| Ngoại lệ | 5a. Thiếu/sai thời gian (chưa DNF) → báo lỗi. 7a. Chặng đã có kết quả → cảnh báo ghi đè. |

### 7.3. Biểu đồ hoạt động
**[Hình 7.2]** — `../Module 3 - Kiet/hinh/m3-hoatdong.png`
![Hoạt động M3](<../Module 3 - Kiet/hinh/m3-hoatdong.png>)

### 7.4. Biểu đồ lớp phân tích
**[Hình 7.3]** — `../Module 3 - Kiet/hinh/m3-lop-phantich.png`
![Lớp phân tích M3](<../Module 3 - Kiet/hinh/m3-lop-phantich.png>)

### 7.5. Thiết kế giao diện
**[Hình 7.4]** — `../Module 3 - Kiet/hinh/m3-giaodien-chonchang.png`
![Giao diện chọn chặng](<../Module 3 - Kiet/hinh/m3-giaodien-chonchang.png>)

**[Hình 7.5]** — `../Module 3 - Kiet/hinh/m3-giaodien-nhapketqua.png`
![Giao diện nhập kết quả](<../Module 3 - Kiet/hinh/m3-giaodien-nhapketqua.png>)

### 7.6. Biểu đồ lớp thiết kế (MVC)
**[Hình 7.6]** — `../Module 3 - Kiet/hinh/m3-lop-mvc.png`
![Lớp MVC M3](<../Module 3 - Kiet/hinh/m3-lop-mvc.png>)

### 7.7. Biểu đồ tuần tự
**[Hình 7.7]** — `../Module 3 - Kiet/hinh/m3-tuantu.png`
![Tuần tự M3](<../Module 3 - Kiet/hinh/m3-tuantu.png>)

### 7.8. Test case

| ID | Mục tiêu | Dữ liệu vào | Kết quả mong đợi |
|---|---|---|---|
| TC1 | Tính điểm top 10 đúng | Thời gian tăng dần | Hạng 1=25đ … hạng 10=1đ |
| TC2 | DNF nhận 0 điểm | A về nhì nhưng DNF | A xuống cuối, 0 điểm |
| TC3 | Chặn thiếu thời gian | B không DNF, bỏ trống thời gian | Báo lỗi, không tính |
| TC4 | Cảnh báo ghi đè | Chặng đã có kết quả | Cảnh báo trước khi lưu |

---

## Chương 8. Module 4 — Quyết toán và trao giải cuối mùa (Thanh)

### 8.1. Biểu đồ Use Case chi tiết
UC `Quyết toán và trao giải` include {Đăng nhập, Tổng hợp xếp hạng, Nhập thưởng và lưu}.

**[Hình 8.1]** — `../Module 4 - Thanh/hinh/m4-uc-chitiet.png`
![UC chi tiết M4](<../Module 4 - Thanh/hinh/m4-uc-chitiet.png>)

### 8.2. Đặc tả Use Case

| Mục | Nội dung |
|---|---|
| Use case | Quyết toán và trao giải cuối mùa |
| Actor | Quản lý |
| Tiền điều kiện | Đã đăng nhập; mùa giải đã kết thúc |
| Hậu điều kiện | Bảng xếp hạng + tiền thưởng được lưu và in danh sách trao giải |
| Kịch bản chính | 1. Chọn menu Quyết toán. 2. Hệ thống kiểm tra tất cả chặng đã có kết quả. 3. Cộng dồn điểm/thời gian, xếp hạng cá nhân và đội. 4. Nhập mức thưởng theo hạng, click Tính thưởng. 5. Hệ thống tính tiền thưởng. 6. Kiểm tra, click Lưu → lưu và in danh sách trao giải. |
| Ngoại lệ | 2a. Còn chặng chưa có kết quả → báo lỗi, dừng. |

### 8.3. Biểu đồ hoạt động
**[Hình 8.2]** — `../Module 4 - Thanh/hinh/m4-hoatdong.png`
![Hoạt động M4](<../Module 4 - Thanh/hinh/m4-hoatdong.png>)

### 8.4. Biểu đồ lớp phân tích
**[Hình 8.3]** — `../Module 4 - Thanh/hinh/m4-lop-phantich.png`
![Lớp phân tích M4](<../Module 4 - Thanh/hinh/m4-lop-phantich.png>)

### 8.5. Thiết kế giao diện
**[Hình 8.4]** — `../Module 4 - Thanh/hinh/m4-giaodien-quyettoan.png`
![Giao diện quyết toán](<../Module 4 - Thanh/hinh/m4-giaodien-quyettoan.png>)

### 8.6. Biểu đồ lớp thiết kế (MVC)
**[Hình 8.5]** — `../Module 4 - Thanh/hinh/m4-lop-mvc.png`
![Lớp MVC M4](<../Module 4 - Thanh/hinh/m4-lop-mvc.png>)

### 8.7. Biểu đồ tuần tự
**[Hình 8.6]** — `../Module 4 - Thanh/hinh/m4-tuantu.png`
![Tuần tự M4](<../Module 4 - Thanh/hinh/m4-tuantu.png>)

### 8.8. Test case

| ID | Mục tiêu | Dữ liệu vào | Kết quả mong đợi |
|---|---|---|---|
| TC1 | Quyết toán hợp lệ | Tất cả chặng đã có kết quả | Xếp hạng, tính thưởng, lưu + in |
| TC2 | Chặn khi thiếu kết quả | Còn 1 chặng chưa có kết quả | Báo lỗi, không quyết toán |
| TC3 | Tie-break bằng điểm | A và B cùng điểm, A ít thời gian hơn | A xếp trên B |
| TC4 | Tính tiền thưởng | Thưởng hạng 1 = 100tr | Hạng 1 nhận đúng 100tr |

---

## Chương 9. Kết luận

Nhóm đã phân tích và thiết kế hệ thống Quản lý giải đua xe F1 với 4 module nghiệp vụ, mỗi module có ràng buộc và xử lý riêng: kiểm tra chồng lấn hợp đồng (M1), giới hạn 2 tay đua/đội/chặng (M2), tính điểm theo luật F1 (M3), và quyết toán trao giải có điều kiện đủ kết quả (M4). Các sản phẩm gồm: đặc tả yêu cầu, biểu đồ use case tổng quát, biểu đồ lớp thực thể và thiết kế CSDL, cùng bộ biểu đồ chi tiết (UC, hoạt động, lớp phân tích, giao diện, lớp MVC, tuần tự) và test case cho từng module.

**Hướng phát triển:** bổ sung chức năng quản lý danh mục đầy đủ, thống kê theo mùa, và triển khai mã nguồn theo kiến trúc MVC đã thiết kế.
