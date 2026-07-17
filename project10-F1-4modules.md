# 10. Quản lý giải đua xe F1 (F1 Formula Championship Management)

## Đề bài

- Mỗi năm có một giải vô địch. Một giải đấu gồm nhiều chặng đua diễn ra khắp thế giới (Mã chặng đua, tên, số vòng đua, địa điểm, thời gian, mô tả).
- Mỗi giải đấu có nhiều đội đua tham gia (Mã, tên, hãng, mô tả).
- Mỗi đội đua có nhiều tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử). Nhưng trong mỗi chặng đua, mỗi đội chỉ được phép cho tối đa 2 tay đua tham gia.
- Mỗi tay đua có thể thi đấu cho nhiều đội đua ở các thời điểm khác nhau. Nhưng tại một thời điểm chỉ thi đấu cho 1 đội.
- Với mỗi chặng đua, kết quả được xếp hạng theo thứ tự về đích (thời gian) và điểm chỉ được tính cho top 10, lần lượt theo thứ tự về đích là 25, 18, 15, 12, 10, 8, 6, 4, 2, 1.
- Nếu tay đua nằm trong top 10 nhưng không hoàn thành chặng đua do bỏ cuộc hoặc tai nạn thì nhận 0 điểm.
- Điểm số và thời gian của mỗi tay đua sẽ được cộng dồn qua các chặng để quyết định giải cá nhân và giải đồng đội của mùa giải.

## 4 module

**1. Module "Ký hợp đồng tay đua với đội đua"** (Thành viên 1)

1. Nhân viên chọn menu ký hợp đồng → nhập tên tay đua và tìm kiếm.
2. Hệ thống hiển thị tay đua tìm được + danh sách hợp đồng cũ (tên đội, ngày bắt đầu, ngày kết thúc).
3. Nhân viên chọn đội đua từ danh sách thả xuống + nhập ngày bắt đầu, ngày kết thúc rồi click Lưu.
4. Hệ thống **kiểm tra ràng buộc: tại một thời điểm tay đua chỉ thuộc 1 đội — thời gian hợp đồng mới không được chồng lấn hợp đồng cũ**; nếu chồng lấn thì báo lỗi, yêu cầu nhập lại.
5. Nếu hợp lệ, hệ thống lưu và in hợp đồng (mã hợp đồng, thông tin tay đua, tên đội, ngày bắt đầu, ngày kết thúc).

**2. Module "Đăng ký tay đua tham gia chặng đua"** (Thành viên 2)

1. Nhân viên chọn menu đăng ký thi đấu → chọn chặng đua và đội đua từ danh sách thả xuống.
2. Hệ thống hiển thị danh sách tay đua đang có hợp đồng hiệu lực với đội (mã, tên, quốc tịch).
3. Nhân viên tick chọn các tay đua theo yêu cầu của đội rồi click Lưu.
4. Hệ thống **kiểm tra ràng buộc: mỗi đội tối đa 2 tay đua trong một chặng**; nếu vượt quá thì báo lỗi, không cho lưu.
5. Nếu hợp lệ, hệ thống lưu và in phiếu đăng ký (tên chặng, ngày đua, tên đội, danh sách tay đua đã đăng ký).

**3. Module "Cập nhật kết quả và tính điểm chặng đua"** (Thành viên 3)

1. Nhân viên chọn menu cập nhật kết quả → chọn chặng đua từ danh sách thả xuống.
2. Hệ thống hiển thị bảng các tay đua đã đăng ký chặng, mỗi dòng có ô nhập: thời gian về đích, số vòng, ô tick "bỏ cuộc/tai nạn (DNF)".
3. Nhân viên nhập kết quả cho các tay đua rồi click Tính kết quả.
4. Hệ thống **xếp hạng theo thời gian về đích, gán điểm top 10 theo thứ tự 25, 18, 15, 12, 10, 8, 6, 4, 2, 1; tay đua DNF nhận 0 điểm** và hiển thị bảng kết quả (hạng, tên tay đua, tên đội, thời gian, điểm).
5. Nhân viên kiểm tra và click Lưu → hệ thống lưu và in bảng kết quả chặng đua.

**4. Module "Xem bảng xếp hạng mùa giải"** (Thành viên 4)

1. Nhân viên chọn menu xem bảng xếp hạng → chọn loại (Cá nhân / Đội) và "tính đến chặng" từ danh sách thả xuống.
2. Hệ thống **cộng dồn điểm và thời gian qua các chặng tính đến chặng đã chọn**.
3. Hệ thống hiển thị bảng xếp hạng (Cá nhân: hạng, tên tay đua, đội, tổng điểm, tổng thời gian / Đội: hạng, tên đội, tổng điểm, tổng thời gian), **sắp xếp giảm dần theo tổng điểm, nếu bằng điểm thì tăng dần theo tổng thời gian**.
4. Nhân viên click Lưu để in bảng xếp hạng, dùng làm căn cứ trao giải mùa giải.

## Bảng cân bằng khối lượng 4 module

| Module | Luồng màn hình | Ràng buộc / nghiệp vụ riêng | Kết quả |
|---|---|---|---|
| 1. Ký hợp đồng | Tìm tay đua → DS hợp đồng cũ → form ký mới | 1 đội/thời điểm — chặn chồng lấn thời gian | In hợp đồng |
| 2. Đăng ký chặng | Chọn chặng + đội → DS tay đua → tick chọn | ≤ 2 tay đua/đội/chặng, không trùng | In phiếu đăng ký |
| 3. Kết quả chặng | Chọn chặng → bảng nhập kết quả | Xếp hạng theo thời gian, gán điểm 25→1, DNF = 0 | In bảng kết quả |
| 4. Xếp hạng mùa giải | Chọn chặng + tab → bảng xếp hạng → drill-down | Cộng dồn điểm/thời gian, tie-break 2 tiêu chí | In bảng xếp hạng |

Cả 4 module cùng một khuôn (chọn/tìm → hiển thị danh sách → thao tác lặp → 1 ràng buộc nghiệp vụ → lưu và in), độ khó tương đương module mẫu "Quản lí việc mượn sách" của thầy — mỗi module đủ lớn, có nghiệp vụ và có ràng buộc, không phải CRUD đơn giản.

## Phần làm chung của cả nhóm (theo yêu cầu bài tập)

- Mô tả bài toán (yêu cầu người sử dụng).
- Đặc tả yêu cầu phần mềm: yêu cầu chức năng, phi chức năng.
- Biểu đồ Use Case tổng quát.
- Biểu đồ lớp thực thể.

## Phần mỗi thành viên tự làm cho module của mình

Với 1 module (Use Case) đã nhận: biểu đồ UC chi tiết, đặc tả UC, biểu đồ hoạt động, thiết kế giao diện, biểu đồ tuần tự, test case.
