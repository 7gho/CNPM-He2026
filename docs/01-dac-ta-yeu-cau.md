# Đặc tả yêu cầu phần mềm — Quản lý giải đua xe F1

> Sản phẩm chung của nhóm (mục 2 trong kế hoạch). Nguồn: đề bài [../de-bai-f1.md](../de-bai-f1.md).
>
> Bố cục theo **5 bước mô tả hệ thống bằng ngôn ngữ tự nhiên**: (1) giới thiệu mục đích — (2) phạm vi hệ thống — (3) mô tả chi tiết hoạt động nghiệp vụ của từng chức năng — (4) các đối tượng được quản lý và thuộc tính — (5) quan hệ số lượng giữa các đối tượng. Mục 6–8 là phần mô hình hóa yêu cầu (danh sách use case, yêu cầu chức năng, yêu cầu phi chức năng).

## 1. Giới thiệu — mục đích hệ thống

Hệ thống quản lý một giải vô địch đua xe F1 diễn ra hằng năm. Mục đích của hệ thống là hỗ trợ ban tổ chức giải quản lý toàn bộ vòng đời một mùa giải: khai báo danh mục nền (mùa giải, chặng đua, đội đua, tay đua), ghi nhận việc các đội đăng ký tham gia mùa giải, quản lý hợp đồng giữa tay đua và đội đua, đăng ký tay đua tham gia từng chặng đua, cập nhật kết quả và tính điểm sau mỗi chặng, và cuối cùng là quyết toán, xếp hạng, trao giải cá nhân và đồng đội khi mùa giải kết thúc.

Trước khi có phần mềm, các công việc trên được làm thủ công trên giấy tờ và bảng tính, dẫn tới ba khó khăn chính: (a) khó kiểm soát ràng buộc "tại một thời điểm một tay đua chỉ thuộc một đội" khi tay đua chuyển đội giữa mùa; (b) dễ sai sót khi cộng dồn điểm của hàng chục tay đua qua hàng chục chặng; (c) khó phân định thứ hạng khi hai tay đua hoặc hai đội bằng điểm. Hệ thống được xây dựng để tự động hóa và kiểm soát chặt ba điểm này.

## 2. Phạm vi hệ thống

Hệ thống có hai nhóm người dùng, đều là thành viên có tài khoản đăng nhập: **Nhân viên** (ban tổ chức) và **Quản lý**. Mỗi vai trò được thực hiện các chức năng sau:

| Người dùng (actor) | Được thực hiện các chức năng |
|---|---|
| **Thành viên** (vai trò trừu tượng, cha của hai vai trò dưới) | 1. Đăng nhập<br>2. Đổi mật khẩu |
| **Nhân viên** (kế thừa Thành viên) | 3. Quản lý mùa giải<br>4. Quản lý tay đua<br>5. Quản lý đội đua<br>6. Quản lý chặng đua<br>7. Đăng ký đội tham gia mùa giải<br>8. Ký hợp đồng tay đua với đội đua *(Module 1)*<br>9. Đăng ký tay đua tham gia chặng đua *(Module 2)*<br>10. Cập nhật kết quả chặng đua *(Module 3)* |
| **Quản lý** (kế thừa Thành viên) | 11. Quyết toán và trao giải cuối mùa *(Module 4)* |

Bốn chức năng 3–6 đều có cùng dạng thao tác (tìm / thêm / sửa / xóa trên một danh mục) nên khi mô hình hóa được gộp lại bằng một use case trừu tượng **Quản lý danh mục** làm cha.

Ngoài hai vai trò trên, hệ thống không phục vụ trực tiếp đối tượng nào khác. Đội đua và tay đua chỉ **tham gia gián tiếp**: họ gửi yêu cầu (yêu cầu ký hợp đồng, yêu cầu đăng ký thi đấu) cho nhân viên, còn thao tác trên phần mềm do nhân viên thực hiện. Khán giả và báo chí không có tài khoản, không xem được dữ liệu qua hệ thống này.

> **Những chức năng không đề cập đến thì mặc định là không thuộc phạm vi của hệ thống.**

Cụ thể, các nội dung sau **không** thuộc phạm vi: bán vé và quản lý khán giả; quản lý hãng sản xuất xe và thông số kỹ thuật xe; quản lý nhân sự kỹ thuật của đội đua; tính toán thời gian vòng chạy trực tuyến trong lúc đua; xử phạt và khiếu nại của ban trọng tài; thanh toán tiền thưởng thực tế qua ngân hàng (hệ thống chỉ lưu quyết định trao giải và số tiền thưởng).

## 3. Mô tả chi tiết hoạt động nghiệp vụ của từng chức năng

### 3.1. Đăng nhập

Thành viên mở phần mềm → hệ thống hiển thị màn hình đăng nhập gồm ô nhập **Tên đăng nhập**, ô nhập **Mật khẩu** (hiển thị dạng dấu chấm) và nút **Đăng nhập**; các ô đang rỗng → thành viên nhập tên đăng nhập (ví dụ `nv01`) và mật khẩu, click **Đăng nhập** → hệ thống **kiểm tra tên đăng nhập có tồn tại không và mật khẩu có khớp không** → nếu sai, hệ thống báo lỗi "Tên đăng nhập hoặc mật khẩu không đúng", giữ nguyên màn hình đăng nhập và xóa ô mật khẩu, yêu cầu nhập lại → nếu đúng, hệ thống tạo phiên đăng nhập, đọc vai trò của tài khoản → nếu vai trò là **Nhân viên**, hệ thống hiển thị màn hình chính với các menu: Quản lý mùa giải, Quản lý tay đua, Quản lý đội đua, Quản lý chặng đua, Đăng ký đội tham gia mùa giải, Ký hợp đồng, Đăng ký chặng, Nhập kết quả chặng, Đổi mật khẩu, Đăng xuất → nếu vai trò là **Quản lý**, hệ thống hiển thị màn hình chính với các menu: Quyết toán và trao giải, Đổi mật khẩu, Đăng xuất.

### 3.2. Đổi mật khẩu

Thành viên đã đăng nhập chọn menu **Đổi mật khẩu** → hệ thống hiển thị màn hình đổi mật khẩu gồm dòng chữ hiển thị họ tên và tên đăng nhập của người đang đăng nhập, ba ô nhập **Mật khẩu cũ**, **Mật khẩu mới**, **Nhập lại mật khẩu mới** và nút **Lưu**; ba ô đang rỗng → thành viên nhập mật khẩu cũ, nhập mật khẩu mới, nhập lại mật khẩu mới rồi click **Lưu** → hệ thống **kiểm tra mật khẩu cũ có khớp với mật khẩu đang lưu không** → nếu không khớp, báo lỗi "Mật khẩu cũ không đúng", xóa ba ô và yêu cầu nhập lại → hệ thống **kiểm tra hai ô mật khẩu mới có giống nhau không** → nếu khác nhau, báo lỗi "Nhập lại mật khẩu mới không khớp" → nếu hợp lệ, hệ thống lưu mật khẩu mới cho tài khoản, hiển thị thông báo "Đổi mật khẩu thành công" và quay về màn hình chính; lần đăng nhập sau thành viên phải dùng mật khẩu mới.

### 3.3. Quản lý mùa giải

Nhân viên chọn menu **Quản lý mùa giải** → hệ thống hiển thị màn hình danh mục mùa giải gồm ô nhập **Năm** hoặc **Tên giải** để tìm, nút **Tìm**, nút **Thêm mới**, và bảng danh sách mùa giải với các cột: Năm, Tên giải, Trạng thái, Số chặng, kèm hai nút **Sửa** và **Xóa** trên mỗi dòng; ban đầu bảng hiển thị toàn bộ mùa giải đang có, ví dụ một dòng `2025 | FIA Formula One World Championship | Đang diễn ra | 24` → nhân viên nhập từ khóa và click **Tìm** → hệ thống hiển thị các mùa giải có năm hoặc tên chứa từ khóa.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu nhập gồm các ô: Tên giải, Năm, Trạng thái và nút **Lưu**; các ô đang rỗng → nhân viên nhập `FIA Formula One World Championship`, `2026`, `Đang diễn ra` rồi click **Lưu** → hệ thống **kiểm tra năm đã tồn tại chưa và các ô bắt buộc đã nhập chưa** → nếu năm đã có, báo lỗi "Mùa giải năm 2026 đã tồn tại" → nếu hợp lệ, hệ thống lưu mùa giải mới và hiển thị lại bảng danh sách có thêm dòng vừa nhập.
- **Sửa:** nhân viên click **Sửa** trên một dòng → hệ thống hiển thị biểu mẫu đã điền sẵn dữ liệu của dòng đó → nhân viên sửa và click **Lưu** → hệ thống kiểm tra như khi thêm mới rồi cập nhật, hiển thị lại bảng danh sách.
- **Xóa:** nhân viên click **Xóa** trên một dòng → hệ thống hiển thị hộp xác nhận "Bạn có chắc muốn xóa mùa giải 2026?" với nút **Đồng ý** và **Hủy** → nhân viên click **Đồng ý** → hệ thống **kiểm tra mùa giải có chặng đua, có đội tham gia hoặc đã có bản ghi trao giải hay không** → nếu có, hệ thống từ chối và báo lỗi "Không thể xóa: mùa giải đang có 24 chặng đua" → nếu không, hệ thống xóa và hiển thị lại bảng danh sách.

### 3.4. Quản lý tay đua

Nhân viên chọn menu **Quản lý tay đua** → hệ thống hiển thị màn hình danh mục tay đua gồm ô nhập **Tên tay đua**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử, kèm nút **Sửa** và **Xóa** trên mỗi dòng → nhân viên nhập `Hamilton` và click **Tìm** → hệ thống hiển thị các tay đua có tên chứa từ khóa, ví dụ một dòng `HAM | Lewis Hamilton | 07/01/1985 | Anh | Bảy lần vô địch thế giới`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm các ô: Mã, Tên, Ngày sinh, Quốc tịch, Tiểu sử và nút **Lưu** → nhân viên nhập `ANT`, `Andrea Kimi Antonelli`, `25/08/2006`, `Ý`, tiểu sử rồi click **Lưu** → hệ thống **kiểm tra mã tay đua đã tồn tại chưa và các ô bắt buộc (mã, tên) đã nhập chưa** → nếu mã trùng, báo lỗi "Mã tay đua ANT đã tồn tại" → nếu hợp lệ, hệ thống lưu và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa** trên một dòng → hệ thống hiển thị biểu mẫu điền sẵn dữ liệu → nhân viên sửa (ví dụ bổ sung tiểu sử) và click **Lưu** → hệ thống cập nhật và hiển thị lại bảng.
- **Xóa:** nhân viên click **Xóa** → hệ thống hỏi xác nhận → nhân viên đồng ý → hệ thống **kiểm tra tay đua đã có hợp đồng, đã đăng ký chặng hoặc đã được trao giải hay chưa** → nếu có, từ chối và báo lỗi "Không thể xóa: tay đua đang có hợp đồng với Ferrari" → nếu không, hệ thống xóa và hiển thị lại bảng.

### 3.5. Quản lý đội đua

Nhân viên chọn menu **Quản lý đội đua** → hệ thống hiển thị màn hình danh mục đội đua gồm ô nhập **Tên đội**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên, Hãng, Mô tả, kèm nút **Sửa** và **Xóa** trên mỗi dòng → nhân viên nhập `Ferrari` và click **Tìm** → hệ thống hiển thị dòng `FER | Ferrari | Ferrari | Đội đua lâu đời nhất F1`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm các ô: Mã, Tên, Hãng, Mô tả và nút **Lưu** → nhân viên nhập `MCL`, `McLaren`, `Mercedes`, mô tả rồi click **Lưu** → hệ thống **kiểm tra mã đội đã tồn tại chưa và các ô bắt buộc đã nhập chưa** → nếu hợp lệ, hệ thống lưu và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa**, hệ thống hiển thị biểu mẫu điền sẵn → nhân viên sửa hãng hoặc mô tả rồi click **Lưu** → hệ thống cập nhật.
- **Xóa:** nhân viên click **Xóa**, xác nhận → hệ thống **kiểm tra đội đã tham gia mùa giải nào, đã có hợp đồng với tay đua nào hoặc đã đăng ký chặng nào chưa** → nếu có, từ chối và báo lỗi cụ thể → nếu không, hệ thống xóa.

### 3.6. Quản lý chặng đua

Nhân viên chọn menu **Quản lý chặng đua** → hệ thống hiển thị màn hình danh mục chặng đua gồm ô chọn **Mùa giải** (danh sách thả xuống, mặc định chọn mùa giải hiện tại `2025`), ô nhập **Tên chặng**, nút **Tìm**, nút **Thêm mới**, và bảng danh sách với các cột: Mã, Tên chặng, Số vòng, Địa điểm, Thời gian, Mô tả, kèm nút **Sửa** và **Xóa** trên mỗi dòng → hệ thống hiển thị các chặng của mùa giải đang chọn, sắp xếp tăng dần theo thời gian, ví dụ `R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | ...`.

- **Thêm mới:** nhân viên click **Thêm mới** → hệ thống hiển thị biểu mẫu gồm ô chọn Mùa giải và các ô: Mã, Tên chặng, Số vòng, Địa điểm, Thời gian, Mô tả và nút **Lưu** → nhân viên nhập `R02`, `Chinese Grand Prix`, `56`, `Thượng Hải`, `23/03/2025`, mô tả rồi click **Lưu** → hệ thống **kiểm tra mã chặng đã tồn tại chưa, số vòng có phải số nguyên dương không, thời gian chặng có nằm trong mùa giải đã chọn không** → nếu vi phạm, báo lỗi tương ứng và yêu cầu nhập lại → nếu hợp lệ, hệ thống lưu chặng đua thuộc mùa giải đã chọn và hiển thị lại bảng danh sách.
- **Sửa:** nhân viên click **Sửa** → hệ thống hiển thị biểu mẫu điền sẵn → nhân viên sửa (ví dụ đổi thời gian chặng) rồi click **Lưu** → hệ thống kiểm tra như trên rồi cập nhật.
- **Xóa:** nhân viên click **Xóa**, xác nhận → hệ thống **kiểm tra chặng đã có tay đua đăng ký hoặc đã có kết quả hay chưa** → nếu có, từ chối và báo lỗi "Không thể xóa: chặng đã có kết quả thi đấu" → nếu không, hệ thống xóa.

### 3.7. Đăng ký đội tham gia mùa giải

Nhân viên chọn menu **Đăng ký đội tham gia mùa giải** → hệ thống hiển thị màn hình đăng ký gồm ô chọn **Mùa giải** (danh sách thả xuống) và một bảng rỗng, nút **Lưu** chưa được active → nhân viên chọn mùa giải `2025` → hệ thống hiển thị bảng danh sách toàn bộ đội đua trong danh mục, mỗi dòng gồm ô tick, Mã, Tên đội, Hãng và cột **Trạng thái** ghi "đã tham gia" hoặc "chưa tham gia" mùa giải đang chọn; các đội đã tham gia được tick sẵn và không cho bỏ tick; nút **Lưu** được active → nhân viên tick chọn các đội đăng ký tham gia mùa giải (ví dụ tick `Ferrari`, `Red Bull`, `Mercedes`, `McLaren`, `Aston Martin`, `Williams`) → nhân viên click **Lưu** → hệ thống **kiểm tra ràng buộc: một đội chỉ được tham gia một mùa giải một lần** (bỏ qua các đội đã có bản ghi tham gia, không tạo bản ghi trùng) → hệ thống sinh bản ghi tham gia cho từng đội mới được tick, lưu vào cơ sở dữ liệu → hệ thống hiển thị lại bảng danh sách với cột Trạng thái đã cập nhật và thông báo "Đã đăng ký 6 đội tham gia mùa giải 2025"; danh sách này là nguồn dữ liệu cho ô chọn đội đua ở các chức năng ký hợp đồng và đăng ký chặng.

### 3.8. Ký hợp đồng tay đua với đội đua (Module 1)

Nhân viên chọn chức năng **Ký hợp đồng** → hệ thống hiển thị màn hình tìm tay đua gồm ô nhập **Tên tay đua**, nút **Tìm**, nút **[+ Thêm tay đua mới]** và một bảng kết quả đang rỗng → nhân viên nhập tên (ví dụ `Hamilton`) và click **Tìm** → hệ thống hiển thị danh sách tay đua có tên chứa từ khóa, mỗi dòng gồm Mã, Tên, Ngày sinh, Quốc tịch, Đội hiện tại và nút **[Chọn]** → nếu **không tìm thấy**, hệ thống hiện dòng chữ "Không tìm thấy tay đua nào"; nhân viên click **[+ Thêm tay đua mới]**, nhập mã, tên, ngày sinh, quốc tịch, tiểu sử rồi lưu, hệ thống quay lại bảng kết quả có tay đua vừa thêm → nhân viên click **[Chọn]** ở đúng tay đua → hệ thống hiển thị màn hình nhập hợp đồng: vùng thông tin tay đua, bảng **lịch sử thi đấu** gồm các cột Đội đua, Ngày bắt đầu, Ngày kết thúc (**dòng có ngày kết thúc trống là hợp đồng đang hiệu lực**), ô chọn **Đội đua**, ô nhập **Ngày bắt đầu** và nút **Lưu** chưa được active → nhân viên chọn đội đua từ danh sách thả xuống và **chỉ nhập ngày bắt đầu hiệu lực** (không có ô ngày kết thúc, hợp đồng mới luôn ở trạng thái mở); nút **Lưu** chuyển sang active → nhân viên click **Lưu** → hệ thống **kiểm tra ngày bắt đầu có chồng lấn khoảng thời gian của hợp đồng đã đóng nào không** → nếu chồng lấn, báo lỗi "Tay đua đã có hợp đồng trong khoảng thời gian này" và yêu cầu nhập lại → hệ thống **kiểm tra tay đua còn hợp đồng đang hiệu lực hay không** → nếu còn, **tự động đóng hợp đồng cũ** bằng cách đặt ngày kết thúc = ngày liền trước ngày bắt đầu mới → hệ thống lưu hợp đồng mới với ngày kết thúc để trống, in phiếu xác nhận hợp đồng và nạp lại bảng lịch sử thi đấu đã cập nhật.

### 3.9. Đăng ký tay đua tham gia chặng đua (Module 2)

Nhân viên chọn chức năng **Đăng ký thi đấu** → hệ thống hiển thị màn hình chọn chặng và đội gồm ô chọn **Chặng đua** (danh sách thả xuống các chặng của mùa giải đang diễn ra, sắp xếp tăng dần theo thời gian, mỗi dòng dạng `Mã - Tên chặng - Địa điểm - Thời gian`), ô chọn **Đội đua** và nút **Tiếp tục** chưa được active → nhân viên chọn chặng và chọn đội; nút **Tiếp tục** chuyển sang active → nhân viên click **Tiếp tục** → hệ thống hiển thị màn hình đăng ký tay đua với bảng gồm các cột (ô tick), Mã, Tên, Ngày sinh, Quốc tịch, **Trạng thái đăng ký**; bảng chỉ liệt kê **các tay đua đang có hợp đồng hiệu lực với đội tại thời điểm diễn ra chặng** và **sắp xếp tăng dần theo alphabet của tên** → nếu đội không có tay đua nào hợp đồng hiệu lực, hệ thống hiện bảng rỗng kèm thông báo và không cho lưu → nếu chặng và đội đã có đăng ký từ trước, hệ thống **tick sẵn** các tay đua đang đăng ký và bật nút **Sửa** để nhân viên thay tay đua trước ngày đua → nhân viên tick chọn tay đua theo yêu cầu của đội rồi click **Lưu** → hệ thống **kiểm tra ba ràng buộc**: mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ được đăng ký 1 lần trong một chặng; chỉ được lưu khi ngày hiện tại còn trước thời gian diễn ra chặng → vi phạm bất kỳ ràng buộc nào thì báo lỗi cụ thể và không ghi dòng nào → hợp lệ thì hệ thống lưu danh sách đăng ký, cập nhật cột Trạng thái đăng ký và hiển thị bảng **danh sách xuất phát** của chặng (Đội, Tay đua 1, Tay đua 2) để nhân viên đối soát và in gửi ban tổ chức.

### 3.10. Cập nhật kết quả chặng đua (Module 3)

Nhân viên chọn chức năng **Cập nhật kết quả chặng đua** → hệ thống hiển thị màn hình chọn chặng gồm nhãn mùa giải đang hoạt động, ô chọn **Chặng đua** đang rỗng và nút **Tiếp tục** chưa được active → nhân viên chọn chặng; nút **Tiếp tục** chuyển sang active; nhân viên click **Tiếp tục** → hệ thống **kiểm tra chặng đã có tay đua đăng ký hay chưa** → nếu chưa, báo lỗi và giữ nguyên màn hình chọn chặng → nếu có, hệ thống hiển thị màn hình nhập kết quả: dòng thông tin chặng và bảng nhập gồm các cột STT, Mã, Tên tay đua, Đội đua (chỉ đọc, lấy từ đăng ký chặng) và ba cột nhập là **Thời gian về đích**, **Số vòng hoàn thành**, **Trạng thái** (ô chọn ba giá trị Hoàn thành / DNF / DSQ); bảng đối soát chưa hiện và nút **Lưu** chưa được active → nhân viên nhập kết quả cho từng tay đua rồi click **Tính kết quả** → hệ thống kiểm tra dữ liệu: mọi tay đua đã chọn trạng thái, tay đua Hoàn thành phải có thời gian đúng định dạng `hh:mm:ss.xxx`, số vòng hoàn thành nằm trong khoảng từ 0 đến số vòng của chặng, thời gian về đích của các tay đua Hoàn thành đôi một khác nhau → vi phạm thì báo lỗi tương ứng và không tính kết quả → hợp lệ thì hệ thống **tách nhóm Hoàn thành và nhóm DNF/DSQ, sắp xếp nhóm Hoàn thành tăng dần theo thời gian về đích, xếp nhóm DNF/DSQ xuống cuối, gán hạng theo vị trí và gán điểm cho hạng 1 đến 10 theo thang 25, 18, 15, 12, 10, 8, 6, 4, 2, 1**; tay đua DNF hoặc DSQ nhận 0 điểm dù nằm trong top 10 → hệ thống hiển thị **bảng đối soát** (Hạng, Mã, Tên tay đua, Đội đua, Thời gian, Số vòng, Trạng thái, Điểm) và bật nút **Lưu** → nhân viên đối chiếu với biên bản chính thức rồi click **Lưu** → hệ thống **kiểm tra chặng đã có kết quả cũ hay chưa** → nếu có, hiện hộp thoại cảnh báo ghi đè; chọn Hủy thì giữ nguyên kết quả cũ, chọn Đồng ý thì hệ thống xóa toàn bộ kết quả cũ của chặng và tính lại điểm cho toàn chặng → hệ thống lưu kết quả của từng tay đua và hiển thị thông báo lưu thành công.

### 3.11. Quyết toán và trao giải cuối mùa (Module 4)

Quản lý chọn chức năng **Quyết toán mùa giải** → hệ thống lấy mùa giải hiện tại và hiển thị màn hình **Bảng tổng sắp** gồm ô chọn **Chặng đua** (danh sách thả xuống các chặng của mùa, mặc định là chặng gần nhất đã có kết quả), hai bảng xếp hạng và nút **Tiếp tục** chưa được active → quản lý chọn một chặng (ví dụ chọn Abu Dhabi Grand Prix — chặng cuối — để xem bảng cuối mùa) → hệ thống **cộng dồn tổng điểm, tổng thời gian và số lần đạt từng thứ hạng của mỗi tay đua và mỗi đội tính từ chặng đầu mùa đến hết chặng được chọn**, trong đó điểm của tay đua ở mỗi chặng được cộng cho **đội mà tay đua đã đăng ký tại chặng đó** (xử lý đúng trường hợp đổi đội giữa mùa) → hệ thống sắp xếp theo **ba tầng tiêu chí: giảm dần tổng điểm; nếu bằng điểm thì countback — so số lần về nhất, vẫn bằng thì số lần về nhì, rồi về ba…; nếu countback vẫn bằng thì tăng dần tổng thời gian** → hệ thống hiển thị bảng xếp hạng cá nhân (Hạng, Tên tay đua, Quốc tịch, Tên đội, Tổng điểm, Tổng thời gian) và bảng xếp hạng đội (Hạng, Tên đội, Hãng, Tổng điểm, Tổng thời gian) → quản lý có thể **click vào một dòng tay đua hoặc một dòng đội** → hệ thống hiển thị màn hình **Chi tiết theo chặng**: với tay đua là bảng (Tên chặng, Hạng về đích, Điểm, Thời gian về đích), với đội là bảng (Tên chặng, Tổng điểm, Tổng thời gian của 2 tay đua), kèm nút **Quay lại** để trở về bảng tổng sắp → khi mùa giải ở trạng thái "Đã kết thúc", chặng được chọn là chặng cuối và hệ thống **kiểm tra tất cả các chặng đã có kết quả** (còn chặng chưa nhập kết quả thì báo lỗi kèm tên chặng và từ chối quyết toán), nút **Tiếp tục** được active → quản lý click **Tiếp tục** → hệ thống hiển thị màn hình **Trao giải**: sáu ô nhập mức thưởng (cá nhân hạng 1, 2, 3 và đội hạng 1, 2, 3) đang rỗng, bảng Danh sách trao giải 6 dòng với **cột Tiền thưởng rỗng**, nút **Tính thưởng** active và nút **Lưu** chưa active → quản lý nhập mức thưởng cho từng hạng rồi click **Tính thưởng** → hệ thống **kiểm tra mức thưởng là số không âm** → nếu vi phạm, báo lỗi và giữ nguyên màn hình → hợp lệ thì hệ thống **tính tiền thưởng tương ứng cho từng tay đua/đội theo hạng đạt được**, điền cột Tiền thưởng và bật nút **Lưu** (quản lý có thể lặp lại bước nhập – tính thưởng nhiều lần) → quản lý click **Lưu** → nếu mùa giải đã có quyết định trao giải trước đó, hệ thống cảnh báo và hỏi xác nhận ghi đè → hệ thống lưu các bản ghi trao giải vào cơ sở dữ liệu và in danh sách trao giải mùa giải (hạng, tên tay đua/đội, tổng điểm, tiền thưởng).

> Bốn chức năng nghiệp vụ chính ở mục 3.8 – 3.11 chính là **4 module được phân công** cho bốn thành viên; nguồn gốc là đề bài [../de-bai-f1.md](../de-bai-f1.md). Yêu cầu chức năng tương ứng được hệ thống hóa ở mục 7 (FR2 – FR5) của tài liệu này.

## 4. Các đối tượng được quản lý và thuộc tính

### 4.1. Nhóm con người

| Đối tượng | Thuộc tính |
|---|---|
| **Tay đua** | mã, tên, ngày sinh, quốc tịch, tiểu sử |
| **Thành viên** (tài khoản người dùng) | tên đăng nhập, mật khẩu, họ tên |
| **Nhân viên** | kế thừa Thành viên |
| **Quản lý** | kế thừa Thành viên |

### 4.2. Nhóm đơn vị tổ chức

| Đối tượng | Thuộc tính |
|---|---|
| **Đội đua** | mã, tên, hãng, mô tả |

> Đề bài có nhắc tới **hãng** xe của đội đua. Vì hệ thống không có chức năng quản lý hãng đua (không thuộc phạm vi ở mục 2), hãng được giữ làm **thuộc tính** của đội đua chứ không tách thành đối tượng riêng.

### 4.3. Nhóm chuyên môn vận hành

| Đối tượng | Thuộc tính |
|---|---|
| **Mùa giải** | tên, năm, trạng thái |
| **Chặng đua** | mã, tên, số vòng, địa điểm, thời gian, mô tả |
| **Hợp đồng** | ngày bắt đầu, ngày kết thúc (để trống = đang hiệu lực) |
| **Tham gia** (đội tham gia mùa giải) | không có thuộc tính riêng, chỉ nối mùa giải với đội đua |
| **Đăng ký chặng** | không có thuộc tính riêng, chỉ nối chặng đua với tay đua và đội đua |

### 4.4. Nhóm kết quả

| Đối tượng | Thuộc tính |
|---|---|
| **Kết quả** | thời gian, số vòng hoàn thành, trạng thái (Hoàn thành / DNF / DSQ), hạng, điểm |
| **Trao giải** | loại (cá nhân / đồng đội), hạng, tiền thưởng |

## 5. Quan hệ số lượng giữa các đối tượng

- Một **mùa giải** có nhiều **chặng đua**; một chặng đua chỉ thuộc về một mùa giải.
- Một **mùa giải** có nhiều bản ghi **tham gia**; một bản ghi tham gia chỉ thuộc về một mùa giải.
- Một **đội đua** có nhiều bản ghi **tham gia** (tham gia nhiều mùa giải khác nhau); một bản ghi tham gia chỉ ứng với một đội đua.
- Một **tay đua** có nhiều **hợp đồng** (qua các thời kỳ khác nhau); một hợp đồng chỉ của một tay đua.
- Một **đội đua** có nhiều **hợp đồng**; một hợp đồng chỉ với một đội đua.
- Một **chặng đua** có nhiều bản ghi **đăng ký chặng**; một bản ghi đăng ký chặng chỉ thuộc về một chặng đua.
- Một **tay đua** có nhiều bản ghi **đăng ký chặng** (đăng ký nhiều chặng trong mùa); một bản ghi đăng ký chặng chỉ ứng với một tay đua.
- Một **đội đua** có nhiều bản ghi **đăng ký chặng**; một bản ghi đăng ký chặng chỉ ứng với một đội đua. Trong cùng một chặng, một đội có **tối đa 2** bản ghi đăng ký.
- Một bản ghi **đăng ký chặng** có **nhiều nhất một** **kết quả** (chưa có kết quả khi chặng chưa diễn ra); một kết quả chỉ thuộc về một bản ghi đăng ký chặng.
- Một **mùa giải** có nhiều bản ghi **trao giải**; một bản ghi trao giải chỉ thuộc về một mùa giải.
- Một **tay đua** có nhiều bản ghi **trao giải** (qua các mùa giải); một bản ghi trao giải cá nhân chỉ ứng với một tay đua.
- Một **đội đua** có nhiều bản ghi **trao giải**; một bản ghi trao giải đồng đội chỉ ứng với một đội đua.
- **Thành viên** là đối tượng cha; **nhân viên** và **quản lý** kế thừa thành viên.

Ba quan hệ nhiều–nhiều được tách bằng đối tượng trung gian: mùa giải – đội đua tách bằng **tham gia**; tay đua – đội đua (theo thời gian) tách bằng **hợp đồng**; chặng đua – tay đua tách bằng **đăng ký chặng**.

## 6. Danh sách use case

| Use case | Actor | Mô tả ngắn |
|---|---|---|
| Đăng nhập | Thành viên | Đăng nhập vào hệ thống bằng tên đăng nhập và mật khẩu, được phân quyền theo vai trò |
| Đổi mật khẩu | Thành viên | Đổi mật khẩu của tài khoản đang đăng nhập |
| **Quản lý danh mục** *(use case trừu tượng)* | Nhân viên | Use case cha, gộp bốn use case danh mục có cùng dạng thao tác tìm / thêm / sửa / xóa |
| Quản lý mùa giải | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho mùa giải |
| Quản lý tay đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho tay đua |
| Quản lý đội đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho đội đua |
| Quản lý chặng đua | Nhân viên | Kế thừa *Quản lý danh mục*, áp cho chặng đua |
| Đăng ký đội tham gia mùa giải | Nhân viên | Chọn mùa giải, tick các đội đua tham gia, lưu bản ghi tham gia |
| **Ký hợp đồng tay đua với đội đua** *(Module 1)* | Nhân viên | Tìm tay đua, xem lịch sử hợp đồng, ký hợp đồng mới với một đội đua |
| **Đăng ký tay đua tham gia chặng đua** *(Module 2)* | Nhân viên | Chọn chặng và đội, tick tay đua đang có hợp đồng hiệu lực để đăng ký thi đấu |
| **Cập nhật kết quả chặng đua** *(Module 3)* | Nhân viên | Nhập thời gian, số vòng, trạng thái của từng tay đua; hệ thống xếp hạng và tính điểm |
| **Quyết toán và trao giải cuối mùa** *(Module 4)* | Quản lý | Xem bảng tổng sắp tính đến chặng bất kỳ, xem chi tiết theo chặng của một tay đua/đội, nhập mức thưởng, lưu quyết định trao giải |

## 7. Yêu cầu chức năng

### FR0 — Xác thực và tài khoản (chung)
- FR0.1 Đăng nhập bằng tài khoản (tên đăng nhập, mật khẩu).
- FR0.2 Đổi mật khẩu cá nhân (kiểm tra mật khẩu cũ, xác nhận mật khẩu mới hai lần).
- FR0.3 Phân quyền theo vai trò: **Nhân viên** (danh mục + Module 1/2/3), **Quản lý** (Module 4).

### FR1 — Quản lý danh mục (chung, hỗ trợ)
- FR1.1 Tìm/thêm/sửa/xóa **tay đua** (mã, tên, ngày sinh, quốc tịch, tiểu sử).
- FR1.2 Tìm/thêm/sửa/xóa **đội đua** (mã, tên, hãng, mô tả).
- FR1.3 Tìm/thêm/sửa/xóa **chặng đua** (mã, tên, số vòng, địa điểm, thời gian, mô tả) thuộc một mùa giải.
- FR1.4 Tìm/thêm/sửa/xóa **mùa giải** (tên, năm, trạng thái).
- FR1.5 **Đăng ký đội tham gia mùa giải**: chọn mùa giải, tick chọn các đội đua tham gia, hệ thống sinh bản ghi tham gia (một đội chỉ tham gia một mùa giải một lần).
- FR1.6 **Ràng buộc xóa:** không cho xóa đối tượng đang được đối tượng khác tham chiếu (mùa giải đã có chặng, tay đua đã có hợp đồng, đội đã tham gia mùa giải, chặng đã có đăng ký hoặc kết quả).

### FR2 — Ký hợp đồng tay đua với đội đua (Module 1)
- FR2.1 Tìm tay đua theo tên; hiển thị danh sách hợp đồng cũ của tay đua được chọn.
- FR2.1b **Thêm mới tay đua ngay trong luồng ký hợp đồng:** nếu tìm không thấy tay đua trong hệ thống, nhân viên được phép thêm mới tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử) ngay tại màn hình tìm kiếm, sau đó tiếp tục ký hợp đồng cho tay đua vừa thêm mà không phải rời khỏi chức năng.
- FR2.2 Ký hợp đồng mới: chọn đội, **chỉ nhập ngày bắt đầu hiệu lực** (ngày kết thúc để trống = hợp đồng đang hiệu lực).
- FR2.3 **Ràng buộc (tại một thời điểm tay đua chỉ thuộc 1 đội):** (a) nếu tay đua còn hợp đồng đang hiệu lực → hệ thống **tự động đóng** hợp đồng cũ (đặt ngày kết thúc = ngày liền trước ngày bắt đầu mới), không báo lỗi; (b) nếu ngày bắt đầu mới **chồng lấn khoảng thời gian của hợp đồng đã đóng** (lịch sử) → báo lỗi, yêu cầu nhập lại.
- FR2.4 Lưu và in hợp đồng; hiển thị lại lịch sử hợp đồng đã cập nhật.

### FR3 — Đăng ký tay đua tham gia chặng đua (Module 2)
- FR3.1 Chọn chặng đua và đội đua.
- FR3.2 Hiển thị danh sách tay đua đang có hợp đồng hiệu lực với đội tại thời điểm chặng, **sắp xếp theo alphabet của tên**, kèm **cột trạng thái** "đã đăng ký chặng này cho đội khác hay chưa".
- FR3.3 Tick chọn tay đua đăng ký.
- FR3.4 **Ràng buộc:** mỗi đội tối đa 2 tay đua trong một chặng; mỗi tay đua chỉ đăng ký 1 lần trong chặng.
- FR3.5 Lưu và in phiếu đăng ký (danh sách xuất phát).
- FR3.6 **Chỉnh sửa đăng ký trước ngày đua**: mở lại chặng + đội, hệ thống hiển thị lại danh sách với các tay đua đang đăng ký được tick sẵn; nhân viên thay tay đua (bỏ tick / tick lại), hệ thống kiểm tra lại ràng buộc FR3.4 rồi lưu.

### FR4 — Cập nhật kết quả chặng đua (Module 3)
- FR4.1 Chọn chặng; hiển thị bảng tay đua đã đăng ký để nhập **thời gian về đích**, **số vòng hoàn thành** và **trạng thái**. Trạng thái nhận một trong ba giá trị: **Hoàn thành**, **DNF** (bỏ cuộc hoặc tai nạn), **DSQ** (bị loại vì vi phạm kỹ thuật).
- FR4.2 **Tính điểm:** xếp hạng các tay đua trạng thái *Hoàn thành* theo thứ tự tăng dần thời gian về đích; tay đua **DNF hoặc DSQ xếp cuối bảng và nhận 0 điểm**. Gán điểm cho top 10 theo thứ tự 25/18/15/12/10/8/6/4/2/1; tay đua nằm trong top 10 nhưng DNF hoặc DSQ vẫn nhận 0 điểm.
- FR4.3 Hiển thị bảng kết quả chặng để đối soát (hạng, tên tay đua, tên đội, thời gian, số vòng, trạng thái, điểm); lưu kết quả + điểm và in bảng kết quả chặng.
- FR4.4 **Ghi đè kết quả cũ:** nếu chặng được chọn **đã có kết quả** từ lần nhập trước, hệ thống phải **cảnh báo ghi đè** trước khi lưu ("Chặng này đã có kết quả, bạn có chắc muốn ghi đè?"); nếu nhân viên xác nhận, hệ thống xóa toàn bộ kết quả cũ của chặng và **tính lại điểm cho toàn bộ chặng** theo dữ liệu mới, không được cập nhật từng phần làm lệch bảng điểm.

### FR5 — Quyết toán và trao giải cuối mùa (Module 4)
- FR5.1 **Ràng buộc:** chỉ quyết toán khi tất cả chặng trong mùa đã có kết quả; nếu còn chặng chưa nhập kết quả thì báo lỗi và từ chối quyết toán.
- FR5.2 Cộng dồn điểm và thời gian của từng tay đua và từng đội qua các chặng; xếp hạng cá nhân và xếp hạng đội theo **ba tầng tiêu chí**: (1) **giảm dần tổng điểm**; (2) nếu **bằng điểm** thì phân định bằng **countback** — so sánh **số lần về nhất**, nếu vẫn bằng thì **số lần về nhì**, rồi **số lần về ba**… cho đến khi phân định được; (3) nếu countback vẫn bằng thì xếp theo **tăng dần tổng thời gian**. Trong đó countback là tầng bổ sung theo luật FIA thật, còn tổng thời gian là quy tắc gốc của đề bài, được giữ làm tiêu chí phân định cuối cùng. **Tổng thời gian luôn được hiển thị trên bảng xếp hạng.**
- FR5.2b **Xem bảng xếp hạng tính đến chặng bất kỳ:** quản lý chọn một chặng từ danh sách thả xuống; hệ thống tổng hợp bảng xếp hạng cá nhân và bảng xếp hạng đội **tính từ chặng đầu mùa đến hết chặng được chọn**, xem được ở bất kỳ thời điểm nào trong mùa. Chức năng trao giải chỉ được kích hoạt khi chặng được chọn là chặng cuối và mọi chặng đã có kết quả (FR5.1).
- FR5.2c **Xem chi tiết theo chặng (drill-down):** quản lý click vào một dòng trên bảng xếp hạng; hệ thống hiển thị bảng chi tiết kết quả từng chặng của tay đua đó (Tên chặng | Hạng về đích | Điểm | Thời gian về đích) hoặc của đội đó (Tên chặng | Tổng điểm | Tổng thời gian của 2 tay đua), kèm nút quay lại bảng xếp hạng.
- FR5.3 Điểm của tay đua được cộng cho **đội mà tay đua đăng ký thi đấu tại chặng đó**, không phải đội hiện tại của tay đua (xử lý đúng trường hợp tay đua đổi đội giữa mùa).
- FR5.4 Nhập mức thưởng theo hạng (hạng 1, 2, 3 cá nhân và hạng 1, 2, 3 đội); hệ thống tính tiền thưởng tương ứng cho từng tay đua/đội theo hạng đạt được.
- FR5.5 Lưu quyết định trao giải và in danh sách trao giải (hạng, tên tay đua/đội, tổng điểm, tiền thưởng).

## 8. Yêu cầu phi chức năng

| # | Loại | Yêu cầu |
|---|---|---|
| NFR1 | Bảo mật | Đăng nhập bằng tài khoản; phân quyền theo vai trò (Nhân viên/Quản lý). |
| NFR2 | Tính đúng đắn | Các phép tính điểm, xếp hạng (kể cả countback), tiền thưởng phải chính xác theo luật F1 trong đề bài. |
| NFR3 | Toàn vẹn dữ liệu | Kiểm tra ràng buộc (chồng lấn hợp đồng, ≤2 tay đua/đội/chặng, cảnh báo ghi đè kết quả, đủ kết quả trước khi quyết toán) trước khi lưu. |
| NFR4 | Khả dụng | Giao diện tiếng Việt, thao tác tìm kiếm → chọn → lưu rõ ràng; thông báo lỗi cụ thể khi vi phạm ràng buộc. |
| NFR5 | Hiệu năng | Danh sách (tay đua, kết quả, xếp hạng) hiển thị < 2 giây với quy mô một mùa giải. |
| NFR6 | Khả bảo trì | **Kiến trúc phân tầng view (.jsp) / dao / model**: tầng `view` là các trang `.jsp` hiển thị và nhận dữ liệu, tầng `dao` là các lớp truy xuất dữ liệu, tầng `model` là các lớp thực thể. Mỗi tầng chỉ gọi tầng ngay dưới nó, giúp dễ sửa và mở rộng. |
| NFR7 | Khả chuyển | Chạy trên trình duyệt web thông dụng. |
