# 10. F1 Formula Championship Management

## Đề bài

- Mỗi năm có một giải vô địch. Một giải đấu gồm nhiều chặng đua diễn ra khắp thế giới (Mã chặng đua, tên, số vòng đua, địa điểm, thời gian, mô tả).
- Mỗi giải đấu có nhiều đội đua tham gia (Mã, tên, hãng, mô tả).
- Mỗi đội đua có nhiều tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử). Nhưng trong mỗi chặng đua, mỗi đội chỉ được phép cho tối đa 2 tay đua tham gia.
- Mỗi tay đua có thể thi đấu cho nhiều đội đua ở các thời điểm khác nhau. Nhưng tại một thời điểm chỉ thi đấu cho 1 đội.
- Với mỗi chặng đua, kết quả được xếp hạng theo thứ tự về đích (thời gian) và điểm chỉ được tính cho top 10, lần lượt theo thứ tự về đích là 25, 18, 15, 12, 10, 8, 6, 4, 2, 1.
- Nếu tay đua nằm trong top 10 nhưng không hoàn thành chặng đua do bỏ cuộc hoặc tai nạn thì nhận 0 điểm.
- Điểm số và thời gian của mỗi tay đua sẽ được cộng dồn qua các chặng để quyết định giải cá nhân và giải đồng đội của mùa giải.

## 4 module mới (chia cân bằng)

1. **Module "Quản lý hợp đồng tay đua (chuyển đội)"**: Nhân viên chọn chức năng quản lý hợp đồng tay đua → giao diện tìm tay đua theo tên hiện ra → nhân viên nhập tên và click tìm kiếm → hệ thống hiển thị danh sách tay đua có tên chứa từ khóa, mỗi dòng: mã, tên, ngày sinh, quốc tịch, đội hiện tại (nếu chưa có trong hệ thống thì thêm mới tay đua) → nhân viên click vào tay đua đúng → hệ thống hiển thị lịch sử thi đấu của tay đua, mỗi dòng một giai đoạn: tên đội, ngày bắt đầu, ngày kết thúc (dòng có ngày kết thúc trống là hợp đồng đang hiệu lực) → nhân viên click "chuyển đội / ký mới" → giao diện chọn đội từ danh sách thả xuống + nhập ngày bắt đầu hiệu lực → hệ thống **kiểm tra ràng buộc: tại một thời điểm tay đua chỉ thuộc 1 đội** (nếu còn hợp đồng đang hiệu lực thì tự động đóng hợp đồng cũ bằng ngày liền trước ngày bắt đầu mới; nếu ngày bắt đầu chồng lấn lịch sử cũ thì báo lỗi và yêu cầu nhập lại) → nhân viên xác nhận → hệ thống lưu vào CSDL và hiển thị lại lịch sử đã cập nhật.

2. **Module "Đăng ký thi đấu theo chặng"**: Nhân viên chọn chức năng đăng ký thi đấu theo yêu cầu của đội đua → giao diện đăng ký hiện ra → nhân viên chọn chặng đua từ danh sách thả xuống + chọn đội đua từ danh sách thả xuống → hệ thống hiển thị danh sách các tay đua **đang có hợp đồng hiệu lực với đội tại thời điểm diễn ra chặng** (lấy từ module 1), sắp xếp theo thứ tự alphabet của tên, kèm cột trạng thái "đã đăng ký chặng này cho đội khác hay chưa" → nhân viên tick chọn tay đua theo yêu cầu của đội → hệ thống **kiểm tra ràng buộc: tối đa 2 tay đua/đội/chặng và mỗi tay đua chỉ được đăng ký 1 lần trong 1 chặng** (vi phạm thì báo lỗi ngay, không cho lưu) → nhân viên click Lưu → hệ thống lưu và hiển thị danh sách xuất phát (start list) của chặng: mỗi dòng gồm tên đội, tên 2 tay đua đăng ký → nhân viên có thể click "In danh sách xuất phát" để in cho ban tổ chức; trước ngày đua nhân viên có thể mở lại chặng + đội để thay tay đua (hệ thống kiểm tra lại ràng buộc như trên).

3. **Module "Cập nhật kết quả và tính điểm chặng"**: Nhân viên chọn chức năng nhập kết quả chặng → giao diện nhập kết quả hiện ra → nhân viên chọn chặng đua từ danh sách thả xuống → hệ thống hiển thị bảng các tay đua đã đăng ký chặng (từ module 2), mỗi dòng có ô nhập: thời gian hoàn thành, số vòng chạy được, tick "bỏ cuộc/tai nạn (DNF)" → nhân viên nhập đủ kết quả cho tất cả tay đua và click Tính kết quả → hệ thống **tự động xếp hạng theo thời gian về đích (tay đua DNF xếp cuối), gán điểm cho top 10 theo thứ tự 25, 18, 15, 12, 10, 8, 6, 4, 2, 1; tay đua trong top 10 nhưng DNF nhận 0 điểm** → hệ thống hiển thị bảng kết quả chặng để đối soát: hạng, tên tay đua, tên đội, thời gian, số vòng, điểm → nhân viên kiểm tra và click Lưu → hệ thống lưu kết quả + điểm của từng tay đua vào CSDL (nếu chặng đã có kết quả cũ thì cảnh báo ghi đè và tính lại điểm toàn bộ chặng).

4. **Module "Bảng xếp hạng mùa giải (cá nhân và đội)"**: Nhân viên chọn chức năng xem bảng xếp hạng mùa giải → giao diện chọn "tính đến chặng" từ danh sách thả xuống + chọn tab Cá nhân hoặc Đội → **Tab Cá nhân**: hệ thống cộng dồn điểm và thời gian của từng tay đua qua các chặng đã chọn, hiển thị bảng mỗi dòng: hạng, tên tay đua, quốc tịch, tên đội, tổng điểm, tổng thời gian (sắp xếp giảm dần theo tổng điểm, nếu bằng điểm thì tăng dần theo tổng thời gian) → click vào 1 tay đua → hiển thị chi tiết từng chặng: tên chặng, hạng về đích, điểm, thời gian → **Tab Đội**: hệ thống cộng dồn điểm và thời gian của 2 tay đua mỗi đội, hiển thị bảng mỗi dòng: hạng, tên đội, hãng, tổng điểm, tổng thời gian (sắp xếp cùng quy tắc), dùng làm căn cứ trao giải cá nhân và đội của mùa giải.

## Ghi chú cân bằng khối lượng

| Module | Luồng giao diện | Logic nghiệp vụ riêng |
|---|---|---|
| 1. Hợp đồng tay đua | Tìm kiếm + lịch sử + form | Ràng buộc 1 đội/thời điểm, đóng hợp đồng cũ, chặn chồng lấn |
| 2. Đăng ký chặng | 2 dropdown + danh sách tick + in | Ràng buộc ≤2 tay đua/đội/chặng, hợp đồng hiệu lực, thay người |
| 3. Kết quả chặng | Bảng nhập liệu + bảng đối soát | Xếp hạng theo thời gian, gán điểm 25→1, xử lý DNF, ghi đè |
| 4. Xếp hạng mùa giải | 2 tab + drill-down cá nhân | Cộng dồn điểm/thời gian, tie-break 2 tiêu chí cho cá nhân và đội |

Mỗi module đều gồm: một luồng màn hình tìm/chọn, một khối logic nghiệp vụ riêng phải cài đặt, và thao tác lưu/in — khối lượng tương đương nhau, không module nào chỉ là nhập liệu thuần.
