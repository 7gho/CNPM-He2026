# Đề tài: Quản lý giải đua xe F1

> Mô tả bài toán của nhóm. Chi tiết đầu việc của từng module nằm trong `Module N/noi-dung.md`.

## 1. Mô tả bài toán

- Mỗi năm có một giải vô địch. Một giải đấu gồm nhiều chặng đua diễn ra khắp thế giới; mỗi chặng đua có: mã chặng đua, tên, số vòng đua, địa điểm, thời gian, mô tả.
- Mỗi giải đấu có nhiều đội đua tham gia; mỗi đội đua có: mã, tên, hãng, mô tả.
- Mỗi đội đua có nhiều tay đua; mỗi tay đua có: mã, tên, ngày sinh, quốc tịch, tiểu sử.
- Trong mỗi chặng đua, mỗi đội chỉ được phép cho tối đa 2 tay đua tham gia.
- Mỗi tay đua có thể thi đấu cho nhiều đội đua ở các thời điểm khác nhau, nhưng tại một thời điểm chỉ thi đấu cho 1 đội.
- Với mỗi chặng đua, kết quả được xếp hạng theo thứ tự về đích (thời gian); điểm chỉ tính cho top 10, lần lượt là 25, 18, 15, 12, 10, 8, 6, 4, 2, 1. Tay đua không hoàn thành chặng do bỏ cuộc hoặc tai nạn (DNF), hoặc bị loại vì vi phạm kỹ thuật (DSQ), nhận 0 điểm.
- Điểm và thời gian của mỗi tay đua, mỗi đội được cộng dồn qua các chặng để lập bảng xếp hạng và quyết định giải cá nhân, giải đồng đội của mùa giải.

## 2. Bốn module của nhóm

**Module 1 — Ký hợp đồng tay đua với đội đua.** Nhân viên tìm tay đua theo tên (chưa có trong hệ thống thì thêm mới ngay trong luồng), xem lịch sử thi đấu rồi ký hợp đồng mới: chọn đội, nhập ngày bắt đầu. Hệ thống giữ ràng buộc "tại một thời điểm chỉ thuộc 1 đội": tự động đóng hợp đồng đang hiệu lực bằng ngày liền trước ngày bắt đầu mới, báo lỗi nếu chồng lấn lịch sử cũ; lưu xong in phiếu xác nhận hợp đồng.

**Module 2 — Đăng ký tay đua tham gia chặng đua.** Nhân viên chọn chặng và đội; hệ thống liệt kê các tay đua đang có hợp đồng hiệu lực với đội tại thời điểm chặng (từ Module 1), sắp theo alphabet của tên, kèm trạng thái đã đăng ký hay chưa. Nhân viên tick tối đa 2 tay đua; hệ thống chặn trùng đăng ký, lưu và in danh sách xuất phát; trước ngày đua có thể mở lại để thay tay đua.

**Module 3 — Cập nhật kết quả chặng đua.** Nhân viên chọn chặng, nhập thời gian, số vòng và trạng thái (Hoàn thành / DNF / DSQ) cho từng tay đua đã đăng ký. Hệ thống xếp hạng theo thời gian về đích (DNF/DSQ xếp cuối, 0 điểm), gán điểm 25→1 cho top 10, hiển thị bảng đối soát rồi lưu; chặng đã có kết quả thì cảnh báo ghi đè và tính lại điểm toàn chặng.

**Module 4 — Quyết toán và trao giải cuối mùa.** Quản lý chọn chặng bất kỳ từ danh sách thả xuống để xem bảng xếp hạng cá nhân và bảng xếp hạng đội tính đến hết chặng đó; click một dòng để xem chi tiết kết quả từng chặng của tay đua/đội đó (drill-down). Khi mùa giải kết thúc và mọi chặng đã có kết quả, quản lý nhập mức thưởng theo hạng; hệ thống tính tiền thưởng, lưu quyết định trao giải và in danh sách trao giải.

## 3. Ràng buộc nghiệp vụ chính

- Mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ được đăng ký 1 lần trong một chặng.
- Hợp đồng của một tay đua không được chồng lấn thời gian; ký mới khi còn hợp đồng đang hiệu lực thì hệ thống tự động đóng hợp đồng cũ.
- Điểm top 10: 25→1; DNF/DSQ nhận 0 điểm và xếp cuối; điểm của tay đua cộng cho đội mà tay đua đăng ký tại chặng đó (đúng cả khi đổi đội giữa mùa).
- Xếp hạng ba tầng: (1) tổng điểm giảm dần; (2) bằng điểm → countback (so số lần về nhất, rồi về nhì, về ba… cho đến khi phân định được); (3) countback vẫn bằng → tổng thời gian tăng dần. Tổng thời gian luôn hiển thị trên bảng xếp hạng.
- Chỉ quyết toán và trao giải khi tất cả các chặng của mùa đã có kết quả.
