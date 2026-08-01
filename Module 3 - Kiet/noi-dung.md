# Module 3 — Cập nhật kết quả chặng đua — Nội dung chi tiết

## 0. Danh sách ảnh (đặt trong `hinh/`)

| Tên file | Biểu đồ (mục) |
|---|---|
| `m3-uc-chitiet.png` | Biểu đồ UC chi tiết (mục 1) |
| `m3-trangthai.png` | Biểu đồ trạng thái — phân tích hoạt động (mục 3) |
| `m3-lop-phantich.png` | Biểu đồ lớp phân tích (mục 4) |
| `m3-lop-mvc.png` | Biểu đồ lớp thiết kế — view / dao / model (mục 5) |
| `m3-hoatdong.png` | Biểu đồ hoạt động — pha thiết kế (mục 6) |
| `m3-tuantu.png` | Biểu đồ tuần tự (mục 7) |

---

## 1. Biểu đồ UC chi tiết

Use case chính của module là **`Cập nhật kết quả chặng đua`**, do actor **Nhân viên 1** (`NhanVien1`) trực tiếp thực hiện thuộc Hệ thống quản lý giải đua F1.

Module bao gồm các use case thành phần và quan hệ mở rộng/bao hàm như sau:
- **`Cập nhật kết quả chặng đua`** bao hàm (<<Include>>) 4 use case con:
  1. `Đăng nhập`
  2. `Chọn chặng`
  3. `Nhập kết quả và tính điểm`
  4. `Lưu kết quả`
- Use case `Lưu kết quả` có các **Extension Points** (điểm mở rộng):
  - *Xử lý kháng nghị kết quả*
  - *Áp dụng án phạt sau chặng*
  - *Phê duyệt kết quả chặng*
- Các use case mở rộng (<<Extend>>) kết nối tới điểm mở rộng của `Lưu kết quả`:
  - `Xử lý kháng nghị kết quả` (do **Nhân viên 1** thực hiện)
  - `Phê duyệt kết quả chặng` (do **Nhân viên 2** thực hiện)
  - `Áp dụng án phạt sau chặng` (do **Nhân viên 2** thực hiện)

| Màn hình / Vai trò | Use case con / Use case mở rộng | Quan hệ với UC chính / UC Lưu kết quả | Actor thực hiện |
|---|---|---|---|
| Màn đăng nhập | `Đăng nhập` | include | Nhân viên 1 |
| Màn chọn chặng | `Chọn chặng` | include | Nhân viên 1 |
| Màn chi tiết chặng | `Nhập kết quả và tính điểm` | include | Nhân viên 1 |
| Màn chi tiết chặng | `Lưu kết quả` | include | Nhân viên 1 |
| Màn kháng nghị | `Xử lý kháng nghị kết quả` | extend (qua extension point) | Nhân viên 1 |
| Màn phê duyệt/án phạt | `Phê duyệt kết quả chặng` | extend (qua extension point) | Nhân viên 2 |
| Màn phê duyệt/án phạt | `Áp dụng án phạt sau chặng` | extend (qua extension point) | Nhân viên 2 |

---

## 2. Đặc tả Use Case

Luồng màn hình: **Trang chính `NhanVien.jsp` → Danh sách mùa giải `MuaGiai.jsp` → Danh sách chặng `Chang.jsp` → Chi tiết chặng `ChangChiTiet.jsp` → (Kháng nghị `KhangNghi.jsp`) → Trang chính `NhanVien.jsp`**. Phác thảo của mỗi màn đặt ngay dưới bước hệ thống hiển thị màn đó.

| Mục | Nội dung |
|---|---|
| **Use case** | Cập nhật kết quả chặng đua |
| **Actor** | `NhanVien1` (Nhân viên cập nhật kết quả & xử lý kháng nghị), `NhanVien2` (Nhân viên giám sát, phê duyệt kết quả & áp dụng án phạt) |
| **Tiền điều kiện** | Nhân viên đã đăng nhập thành công vào hệ thống. Mùa giải và danh sách chặng đua đã có dữ liệu. Chặng đua cần cập nhật đã có danh sách tay đua, đội đua đăng ký thi đấu. |
| **Hậu điều kiện** | Kết quả thi đấu (thời gian về đích, số vòng hoàn thành, trạng thái, hạng, điểm) được xếp hạng, tính điểm và lưu vào CSDL. Nếu có đơn kháng nghị từ đội đua, thông tin được tiếp nhận, đối chiếu camera và phê duyệt/cập nhật lại kết quả. |

**Kịch bản chính**

1. `NhanVien1` (sau khi đăng nhập) truy cập giao diện chính `NhanVien.jsp`, click nút [Mùa giải] (`btnMuaGiai`).
2. Hệ thống hiển thị màn hình **Danh sách mùa giải** (`MuaGiai.jsp`): hiển thị bảng `tblMuaGiai` liệt kê các mùa giải (Mùa giải, Năm, Trạng thái); các nút [Xem chi tiết], [Thêm mùa giải], [Lưu], [Quay lại].

   **Màn hình *Danh sách mùa giải* (`MuaGiai.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Bảng mùa giải (`tblMuaGiai`) | bảng | hiển thị danh sách mùa giải (Mùa giải, Năm, Trạng thái) |
   | [Xem chi tiết] (`btnViewDetailMuaGiai`) | nút | active khi chọn 1 mùa giải |
   | [Thêm mùa giải] (`btnCreateMuaGiai`) | nút | active |
   | [Lưu] (`btnSave`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

3. `NhanVien1` chọn mùa giải 2025 trong bảng `tblMuaGiai` và click [Xem chi tiết] (`btnViewDetailMuaGiai`).
4. Hệ thống hiển thị màn hình **Danh sách chặng đua** (`Chang.jsp`): hiển thị bảng `tblChang` gồm các chặng của mùa giải (Mã, Tên chặng, Địa điểm, Thời gian); các nút [Xem chi tiết chặng], [Thêm chặng], [Lưu], [Quay lại].

   **Màn hình *Danh sách chặng đua* (`Chang.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Bảng chặng đua (`tblChang`) | bảng | hiển thị danh sách chặng đua (Mã, Tên, Địa điểm, Thời gian) |
   | [Xem chi tiết chặng] (`btnViewDetailChang`) | nút | active khi chọn 1 chặng |
   | [Thêm chặng] (`btnCreateChang`) | nút | active |
   | [Lưu] (`btnSave`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

5. `NhanVien1` chọn chặng R16 - Monza và click [Xem chi tiết chặng] (`btnViewDetailChang`).
6. Hệ thống hiển thị màn hình **Chi tiết chặng & Nhập kết quả** (`ChangChiTiet.jsp`): dropdown `cmbChang` chọn chặng; bảng `tblTayDua` chứa danh sách các tay đua đã đăng ký (Thời gian, Số vòng, Trạng thái - các ô nhập đang rỗng hoặc có dữ liệu cũ); các nút [Tính kết quả] (`btnCalculateResult`), [Lưu] (`btnSave`), [Tiếp tục] (`btnContinue`), [Quay lại] (`btnBack`); bảng đối soát kết quả `tblKetQua` ban đầu chưa hiển thị.

   **Màn hình *Chi tiết chặng & Nhập kết quả* (`ChangChiTiet.jsp`)**

   | Thành phần | Kiểu | Trạng thái khi mới mở màn |
   |---|---|---|
   | Chặng đua (`cmbChang`) | danh sách thả xuống | hiển thị chặng R16 |
   | Bảng tay đua (`tblTayDua`) | bảng có ô nhập | chứa 12 tay đua đăng ký chặng; các ô nhập Thời gian, Số vòng, Trạng thái rỗng |
   | [Tính kết quả] (`btnCalculateResult`) | nút | active |
   | Bảng đối soát kết quả (`tblKetQua`) | bảng | chưa hiện, chỉ hiện sau khi click [Tính kết quả] |
   | [Lưu] (`btnSave`) | nút | chưa active, chỉ active sau khi bảng đối soát hiển thị |
   | [Tiếp tục] (`btnContinue`) | nút | active |
   | [Quay lại] (`btnBack`) | nút | active |

   Ô chọn ở cột **Trạng thái** là danh sách thả xuống dùng chung cho mọi dòng, gồm đúng ba giá trị:

   | Giá trị hiển thị trong ô chọn | Thời gian về đích | Vị trí khi xếp hạng | Điểm |
   |---|---|---|---|
   | `Hoàn thành` | bắt buộc nhập, định dạng `hh:mm:ss.xxx` | xếp trước, theo thời gian về đích tăng dần | theo thang 25/18/15/12/10/8/6/4/2/1 cho hạng 1–10 |
   | `DNF (bỏ cuộc, tai nạn)` | không bắt buộc, thường để trống | xếp xuống cuối bảng | 0 |
   | `DSQ (bị loại)` | không bắt buộc, có thể vẫn có thời gian | xếp xuống cuối bảng | 0 |

7. `NhanVien1` nhập số vòng hoàn thành, thời gian về đích và chọn trạng thái (`Hoàn thành`, `DNF`, `DSQ`) cho từng tay đua trong `tblTayDua`.
8. `NhanVien1` click nút [Tính kết quả] (`btnCalculateResult`). Hệ thống kiểm tra dữ liệu, tự động sắp xếp các tay đua `Hoàn thành` theo thời gian tăng dần, đẩy `DNF`/`DSQ` xuống cuối (0 điểm), tính điểm top 10 và hiển thị lên bảng đối soát `tblKetQua`; nút [Lưu] (`btnSave`) chuyển sang active.
9. `NhanVien1` đối soát dữ liệu trên `tblKetQua` và click nút [Lưu] (`btnSave`).
10. Hệ thống gọi `KetQuaDAO.kiemTraKetQuaCu()`. Nếu chưa có kết quả cũ, hệ thống gọi `KetQuaDAO.luuKetQua()`, lưu dữ liệu vào CSDL và thông báo "Lưu thành công".
11. Nếu có đơn kháng nghị từ đội đua/tay đua: Luồng chuyển sang màn hình **Quản lý kháng nghị** (`KhangNghi.jsp`). `NhanVien2` xem xét danh sách đơn kháng nghị, thực hiện đối chiếu băng ghi hình camera:
    - Nếu từ chối kháng nghị: ghi nhận từ chối, giữ nguyên kết quả.
    - Nếu kháng nghị thành công: hệ thống cập nhật lại điểm xếp hạng và lưu dữ liệu mới.
12. Sau khi xử lý hết đơn kháng nghị, `NhanVien2` click [Phê duyệt kết quả], hệ thống thông báo "Phê duyệt kết quả chặng thành công" và hoàn tất luồng.

**Ngoại lệ**

- **6a.** Còn tay đua chưa chọn Trạng thái → hệ thống thông báo "Vui lòng chọn trạng thái cho tất cả tay đua", không tính kết quả, giữ nguyên dữ liệu đã nhập.
- **6b.** Tay đua có trạng thái `Hoàn thành` nhưng để trống hoặc sai định dạng Thời gian → hệ thống thông báo lỗi nhập liệu "Vui lòng nhập thời gian hợp lệ cho tay đua đã hoàn thành", không tính kết quả.
- **6c.** Số vòng hoàn thành vượt quá số vòng chặng đua → hệ thống thông báo "Số vòng hoàn thành không hợp lệ", giữ nguyên dữ liệu.
- **10a.** Chặng đã có kết quả từ trước → hệ thống hiển thị hộp thoại cảnh báo: "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Chọn [Hủy] → giữ nguyên kết quả cũ. Chọn [Xác nhận] → xóa kết quả cũ và lưu kết quả mới.

> Luồng chuyển màn: **Trang chính `NhanVien.jsp` → Danh sách mùa giải `MuaGiai.jsp` → Danh sách chặng `Chang.jsp` → Chi tiết chặng `ChangChiTiet.jsp` → (Kháng nghị `KhangNghi.jsp`) → Trang chính `NhanVien.jsp`**.

---

## 3. Phân tích hoạt động — biểu đồ trạng thái

Biểu đồ mô tả sự chuyển dịch trạng thái của hệ thống trong toàn bộ quá trình cập nhật kết quả và xử lý kháng nghị:

- `Hiển thị GD chính của nhân viên` —`[click Mùa giải]`→ `Hiển thị danh sách mùa giải` (cung `[click quay lại]` trở về GD chính)
- `Hiển thị danh sách mùa giải` —`[click chi tiết mùa giải]`→ `Hiển thị danh sách các chặng đua` (cung `[click quay lại]` trở về GD mùa giải)
- `Hiển thị danh sách các chặng đua` —`[click chi tiết chặng đua]`→ `Hiển thị danh sách các tay đua, đội đua, thông tin chặng` (cung tự quay `[Nhập số vòng, thời gian, trạng thái hợp lệ]`, cung `[click quay lại]` về GD chặng)
- `Hiển thị danh sách các tay đua, đội đua, thông tin chặng` —`[click tính toán kết quả]`→ `Hiển thị kết quả chặng đua` (cung tự quay `[click lưu]`)
- `Hiển thị kết quả chặng đua`:
  - `[ko có đội đua, tay đua nộp đơn kháng nghị]` → Kết thúc (node kết thúc)
  - `[có đội đua, tay đua nộp đơn kháng nghị]` → `Hiển thị danh sách kháng nghị`
- `Hiển thị danh sách kháng nghị` có các cung tự quay: `[Từ chối kháng nghị]`, `[kháng nghị không thành công]`, `[ghi nhận còn kháng nghị từ các đội đua, tay đua]`, `[cập nhật lại kết quả chặng đua khi kháng nghị thành công]`. Sau khi `[hết kháng nghị]` → Kết thúc.

---

## 4. Biểu đồ lớp phân tích

Biểu đồ chỉ gồm **hai tầng**: lớp biên và lớp thực thể. Không có lớp điều khiển; nghiệp vụ được gán thẳng cho lớp thực thể.

**Lớp biên** (mỗi màn hình một lớp, chỉ có thuộc tính, đặt tên theo chức năng dữ liệu):

| Lớp biên | Màn hình | Thuộc tính |
|---|---|---|
| `GDNhanVien` | Trang chính của nhân viên | `-subKhangNghi`, `-subChang`, `-subCaiDat` |
| `GDMuaGiai` | Danh sách mùa giải | `-outMuaGiai`, `-subCreateMuaGiai`, `-subViewDetailMuaGiai`, `-subBack`, `-subSave` |
| `GDChang` | Danh sách các chặng đua | `-outChang`, `-subCreateChang`, `-subViewDetailChang`, `-subBack`, `-subSave` |
| `GDChangChiTiet` | Chi tiết chặng & Nhập kết quả | `-cmbChang`, `-outTayDua`, `-subSave`, `-subBack`, `-subCalculateResult`, `-outKetQua`, `-subContinue` |

**Phương thức nghiệp vụ gán cho lớp thực thể:**

| Chức năng cần thực hiện dưới tầng giao diện | Gán cho lớp | Phương thức |
|---|---|---|
| Lấy danh sách mùa giải | `MuaGiai` | `getAllMuaGiai()`, `getMuaGiaiById(id)` |
| Lấy danh sách chặng đua theo mùa giải | `ChangDua` | `getAllChangDuaByMuaGiaiID(id)` |
| Lấy danh sách tay đua và đội đua của chặng | `DangKyChang` | `getAllTayDuaAndDoiDuaByChangID(id)` |
| Tạo đối tượng kết quả chặng | `KetQua` | `createKetQua()` |
| Kiểm tra kết quả cũ | `KetQua` | `kiemTraKetQuaCu()` |
| Lưu kết quả mới | `KetQua` | `luuKetQua()` |

---

## 5. Biểu đồ lớp thiết kế (view / dao / model)

Biểu đồ lớp thiết kế xây dựng theo mô hình Swing/JSP với Interface `ActionListener`:

- **Tầng View (JSP):** `NhanVien.jsp`, `MuaGiai.jsp`, `Chang.jsp`, `ChangChiTiet.jsp`. Tất cả các View đều kế thừa `ActionListener` và cài đặt hàm `+actionPerformed(e: EventAction): void`. Các thành phần nút bấm (`JButton`), bảng (`JTable`), dropdown (`JComboBox`) được khai báo thành thuộc tính.
- **Tầng DAO:** Lớp cha `DAO` giữ kết nối CSDL (`-conn: Connection`). Các lớp `MuaGiaiDAO`, `ChangDuaDAO`, `DangKyChangDAO`, `KetQuaDAO` kế thừa lớp `DAO`, chứa các phương thức tương tác CSDL với đầy đủ chữ ký: `getAllMuaGiai()`, `getAllChangDuaByMuaGiaiID(id)`, `getAllTayDuaAndDoiDuaByChangID(id)`, `createKetQua(kq)`, `kiemTraKetQuaCu(kq)`, `luuKetQua(kq)`.
- **Tầng Model:** `MuaGiai`, `ChangDua`, `DoiDua`, `TayDua`, `DangKyChang`, `KetQua` chứa đầy đủ thuộc tính định danh (`id`), thuộc tính dữ liệu và quan hệ đối tượng.

---

## 6. Biểu đồ hoạt động (pha thiết kế)

Biểu đồ hoạt động phân chia theo 2 swimlanes tương ứng với 2 actor (`Nhân viên 1` và `Nhân viên 2`):

**Luồng swimlane `Nhân viên 1`:**
1. **`NhanVien.jsp`**: Hiển thị giao diện chính của nhân viên → click `click MuaGiai`.
2. **`MuaGiai.jsp`**: 
   - Lấy danh sách mùa giải thông qua `MuaGiaiDAO: getAllMuaGiai()`.
   - Hiển thị danh sách mùa giải.
   - Nhân viên chọn mùa giải (gọi `MuaGiaiDAO: getMuaGiaiById(id: int)`), click `Click xem chi tiết`.
3. **`Chang.jsp`**: 
   - Lấy danh sách chặng của mùa giải qua `ChangDuaDAO: getAllChangDuaByMuaGiaiID()`.
   - Hiển thị danh sách các chặng đua.
   - Nhân viên click `Click chi tiết chặng`.
4. **`ChangChiTiet.jsp`**: 
   - Lấy thông tin chi tiết chặng via `ChangDuaDAO: getById()`.
   - Lấy thông tin tay đua, đội đua via `DangKyChangDAO: getAllTayDuaAndDoiDuaByChangID()`.
   - Hiển thị thông tin danh sách tay đua, đội đua và thông tin chặng.
   - Nhân viên nhập số vòng, thời gian, trạng thái.
   - Kiểm tra định dạng dữ liệu: Nếu nhập sai định dạng → Hệ thống thông báo lỗi nhập liệu và yêu cầu nhập lại; Nếu đúng định dạng → Hệ thống xếp hạng và tính điểm toàn chặng.
   - Tạo kết quả chặng đua qua `KetQuaDAO: createKetQua()`.
   - Nhân viên click `Click lưu`.
   - Kiểm tra kết quả cũ via `KetQuaDAO: kiemTraKetQuaCu()`.
   - Nếu chặng đã có kết quả cũ: Hiển thị cảnh báo ghi đè ("Chặng đua này đã có kết quả, bạn có muốn ghi đè?"). Nếu hủy → Giữ nguyên kết quả cũ, không lưu. Nếu xác nhận → Xóa kết quả cũ và cập nhật kết quả mới qua `KetQuaDAO: luuKetQua()`.
   - Kiểm tra đơn kháng nghị:
     - Nếu **Không có kháng nghị**: Chuyển đến node `Phê duyệt kết quả` → Click phê duyệt → Thông báo phê duyệt thành công → Kết thúc.
     - Nếu **Có kháng nghị**: Tiếp nhận kháng nghị từ đội đua, hệ thống ghi nhận và chuyển luồng xử lý sang swimlane `Nhân viên 2`.

**Luồng swimlane `Nhân viên 2` (`KhangNghi.jsp`):**
1. Hệ thống hiển thị danh sách kháng nghị.
2. `Nhân viên 2` xem xét đơn kháng nghị:
   - Nếu **Từ chối kháng nghị**: Ghi nhận kháng nghị bị từ chối.
   - Nếu **Chấp nhận kháng nghị**: Đối chiếu kết quả qua camera:
     - Nếu kháng nghị không thành công: Ghi nhận kết quả đối chiếu không thành công.
     - Nếu kháng nghị thành công: Hệ thống cập nhật lại điểm xếp hạng, nhân viên click lưu → ghi nhận cập nhật thành công.
3. Sau khi hết đơn kháng nghị: Luồng quay trở lại node `Phê duyệt kết quả` ở swimlane `Nhân viên 1` để kết thúc.

---

## 7. Thuyết minh (kịch bản phiên bản 3)

1. `Nhân viên` click `click MuaGiai` trên giao diện `NhanVien.jsp`.
2. Trang `NhanVien.jsp` tự thực thi `1.1: actionPerformed()`, sau đó gửi yêu cầu `1.1.1: call` mở trang `MuaGiai.jsp`.
3. Trang `MuaGiai.jsp` gửi yêu cầu `2: MuaGiai()` tới `MuaGiaiDAO`.
4. `MuaGiaiDAO` tự xử lý `2.1: call` và gọi hàm `2.1.1: getAllMuaGiai()` tới lớp thực thể `MuaGiai`.
5. Lớp `MuaGiai` tự khởi tạo `2.1.1.1: call`, sau đó thực thi `2.1.1.1.2: return` trả dữ liệu về cho `MuaGiaiDAO`.
6. `MuaGiaiDAO` gửi kết quả `2.1.2: return` về cho `MuaGiai.jsp`.
7. Trang `MuaGiai.jsp` phản hồi `3: display` hiển thị danh sách mùa giải cho `Nhân viên`.
8. `Nhân viên` thực hiện `4: click mua giai nao do` trên trang `MuaGiai.jsp`.
9. Trang `MuaGiai.jsp` tự thực thi `4.1: actionPerformed()` và gửi yêu cầu `4.1.1: call` tới `MuaGiaiDAO`.
10. `MuaGiaiDAO` gọi hàm `4.1.1.1: getById()` tới thực thể `MuaGiai`. `MuaGiai` tự thực thi `4.1.1.1.1: call` và gửi phản hồi `4.1.1.1.2: return` về cho `MuaGiaiDAO`.
11. `MuaGiaiDAO` trả kết quả `4.1.2: return` về cho `MuaGiai.jsp`.
12. Trang `MuaGiai.jsp` chuyển tiếp `4.1.2.1: call` tới trang `Chang.jsp`.
13. Trang `Chang.jsp` gửi yêu cầu `4.1.2.1.1: call` tới `ChangDuaDAO`.
14. `ChangDuaDAO` gọi hàm `4.1.2.1.1.1: getAllChangDuaByMuaGiaiID()` tới lớp thực thể `ChangDua`. `ChangDua` tự thực thi `4.1.2.1.1.1.1: call` và phản hồi `4.1.2.1.1.1.2: return` về cho `ChangDuaDAO`.
15. `ChangDuaDAO` gửi kết quả `4.1.2.1.1.2: return` cho `Chang.jsp`.
16. Trang `Chang.jsp` phản hồi `4.1.2.2: display` hiển thị danh sách các chặng đua cho `Nhân viên`.
17. `Nhân viên` thực hiện `5: click chi tiet chang` trên trang `Chang.jsp`.
18. Trang `Chang.jsp` tự thực thi `5.1: actionPerformed()` và gửi yêu cầu `5.1.1: call` tới `ChangChiTiet.jsp`.
19. Trang `ChangChiTiet.jsp` gửi yêu cầu `5.1.1.1: call` tới `ChangDuaDAO`.
20. `ChangDuaDAO` gọi hàm `5.1.1.1.1: getById()` tới `ChangDua`. `ChangDua` tự gọi `5.1.1.1.1.1: call` và trả về `5.1.1.1.2: return` cho `ChangDuaDAO`.
21. Trang `ChangChiTiet.jsp` gửi yêu cầu `5.1.1.2: call` tới `DangKyChangDAO`.
22. `DangKyChangDAO` gọi hàm `5.1.1.2.1: getAllTayDuaAndDoiDuaByChangID()` tới `DangKyChang`. `DangKyChang` tự thực thi `5.1.1.2.1.1: call` và trả về `5.1.1.2.1.2: return` cho `DangKyChangDAO`.
23. `DangKyChangDAO` trả kết quả `5.1.1.2.2: return` về cho `ChangChiTiet.jsp`.
24. Trang `ChangChiTiet.jsp` phản hồi `5.1.1.2: display` hiển thị bảng thông tin chi tiết chặng và danh sách tay đua cho `Nhân viên`.
25. **Vòng lặp (loop):** `Nhân viên` nhập thời gian, số vòng, trạng thái (`6: nhập thời gian, số vòng, trạng thái`) cho tới khi hoàn tất tất cả tay đua.
26. `Nhân viên` thực hiện `7: click calculate result` trên trang `ChangChiTiet.jsp`.
27. Trang `ChangChiTiet.jsp` tự gọi `7.1: actionPerformed()` và gửi yêu cầu `7.1.1: call` tới `KetQuaDAO`.
28. `KetQuaDAO` gọi hàm `7.1.1.1: createKetQua()` tới lớp `KetQua`. `KetQua` tự gọi `7.1.1.1.1: call` và trả về `7.1.1.1.2: return` cho `KetQuaDAO`.
29. `KetQuaDAO` gửi kết quả `7.1.2: return` về cho `ChangChiTiet.jsp`. Trang `ChangChiTiet.jsp` hiển thị `7.1.2: display` bảng xếp hạng và tính điểm cho `Nhân viên`.
30. `Nhân viên` thực hiện `8: click Luu` trên trang `ChangChiTiet.jsp`.
31. Trang `ChangChiTiet.jsp` tự xử lý `8.1: actionPerformed()` và gửi yêu cầu `8.1.1: call` tới `KetQuaDAO`.
32. `KetQuaDAO` gọi hàm `8.1.1.1: kiemTraKetQuaCu()` tới `KetQua`. `KetQua` tự gọi `8.1.1.1.1: call` và trả về `8.1.1.1.2: return` cho `KetQuaDAO`.
33. `KetQuaDAO` gửi phản hồi `8.1.2: return` cho `ChangChiTiet.jsp`.
34. Trang `ChangChiTiet.jsp` gửi yêu cầu `8.1.2: call` sang `KetQua`. `KetQua` tự đóng gói dữ liệu qua `8.1.2.1: setter()` và trả về `8.1.2.2: return` cho `ChangChiTiet.jsp`.
35. **Vòng lặp (loop):** Trang `ChangChiTiet.jsp` gửi yêu cầu `8.1.3: call` tới `KetQuaDAO`, `KetQuaDAO` gọi hàm `8.1.3.1: luuKetQua()` tới `KetQua` và phản hồi `8.1.3.2: return` về cho `ChangChiTiet.jsp` cho đến khi lưu hết tất cả các tay đua.
36. Trang `ChangChiTiet.jsp` phản hồi `8.2: display message Lưu thành công` hiển thị thông báo thành công cho `Nhân viên`.

---

## 8. Test case

#### 8.1. Data test (bước 3 quy trình test)

`tblMuaGiai`

| id | ten | nam | trangThai |
|---|---|---|---|
| 1 | Formula 1 World Championship | 2025 | Đang diễn ra |

`tblChangDua` (mùa giải 2025, `tblMuaGiaiid = 1`)

| id | ma | ten | soVong | diaDiem | thoiGian | tblMuaGiaiid |
|---|---|---|---|---|---|---|
| 1 | R01 | Australian Grand Prix | 58 | Melbourne | 16/03/2025 | 1 |
| 2 | R02 | Chinese Grand Prix | 56 | Thượng Hải | 23/03/2025 | 1 |
| 3 | R06 | Monaco Grand Prix | 78 | Monte Carlo | 25/05/2025 | 1 |
| 4 | R10 | British Grand Prix | 52 | Silverstone | 06/07/2025 | 1 |
| 5 | R16 | Italian Grand Prix | 53 | Monza | 07/09/2025 | 1 |
| 6 | R24 | Abu Dhabi Grand Prix | 58 | Yas Marina | 07/12/2025 | 1 |

`tblDangKyChang` (chặng R16 — Monza)

| id | tblChangDuaid | tblTayDuaid | tblDoiDuaid |
|---|---|---|---|
| 41 | 5 | 1 (LEC) | 1 (Ferrari) |
| 42 | 5 | 2 (HAM) | 1 (Ferrari) |
| 43 | 5 | 3 (VER) | 2 (Red Bull) |
| 44 | 5 | 4 (TSU) | 2 (Red Bull) |
| 45 | 5 | 5 (NOR) | 3 (McLaren) |
| 46 | 5 | 6 (PIA) | 3 (McLaren) |
| 47 | 5 | 7 (RUS) | 4 (Mercedes) |
| 48 | 5 | 8 (ANT) | 4 (Mercedes) |
| 49 | 5 | 9 (ALO) | 5 (Aston Martin) |
| 50 | 5 | 10 (STR) | 5 (Aston Martin) |
| 51 | 5 | 11 (ALB) | 6 (Williams) |
| 52 | 5 | 12 (SAI) | 6 (Williams) |

`tblKetQua` (kết quả cũ chặng R16 — nếu có)

| id | thoiGian | soVongHoanThanh | trangThai | hang | diem | tblDangKyChangid |
|---|---|---|---|---|---|---|
| 101 | 4411.482 | 53 | HoanThanh | 1 | 25 | 41 (LEC) |
| 102 | 4421.663 | 53 | HoanThanh | 2 | 18 | 42 (HAM) |

#### 8.2. Bảng test case

| Mã trường hợp kiểm thử | Mục đích kiểm thử | Các bước thực hiện | Kết quả mong muốn |
|---|---|---|---|
| | **Giao diện — màn Mùa giải (`MuaGiai.jsp`)** | | |
| CNKQ_1 | Kiểm tra tổng thể giao diện màn Mùa giải | 1. Đăng nhập với quyền `NhanVien1`.<br>2. Click nút [Mùa giải].<br>3. Kiểm tra các nút bấm, chính tả và bảng dữ liệu. | Hiển thị bảng `tblMuaGiai` gồm các cột Mùa giải, Năm, Trạng thái; có các nút [Xem chi tiết], [Thêm mùa giải], [Lưu], [Quay lại]. Giao diện chuẩn font, không vỡ layout. |
| CNKQ_2 | Kiểm tra thứ tự Tab và Shift-Tab màn Mùa giải | 1. Focus màn `MuaGiai.jsp`.<br>2. Bấm Tab và Shift-Tab liên tục. | Con trỏ di chuyển lần lượt qua các dòng bảng và nút bấm theo đúng thứ tự. |
| | **Giao diện — màn Danh sách chặng (`Chang.jsp`)** | | |
| CNKQ_3 | Kiểm tra tổng thể giao diện màn Danh sách chặng | 1. Tại `MuaGiai.jsp`, chọn mùa 2025 và click [Xem chi tiết].<br>2. Kiểm tra bảng `tblChang` và các nút bấm. | Hiển thị bảng `tblChang` gồm Mã, Tên chặng, Địa điểm, Thời gian; có nút [Xem chi tiết chặng], [Thêm chặng], [Lưu], [Quay lại]. |
| | **Giao diện — màn Chi tiết chặng & Nhập kết quả (`ChangChiTiet.jsp`)** | | |
| CNKQ_4 | Kiểm tra bố cục màn Chi tiết chặng | 1. Tại `Chang.jsp`, chọn chặng R16 và click [Xem chi tiết chặng].<br>2. Kiểm tra dropdown `cmbChang`, bảng `tblTayDua` và các nút bấm. | Hiển thị dropdown `cmbChang`, bảng `tblTayDua` chứa 12 tay đua đăng ký kèm các ô nhập Thời gian, Số vòng, Trạng thái. Các nút [Tính kết quả], [Lưu] (chưa active), [Tiếp tục], [Quay lại] hiển thị đầy đủ. |
| | **Luồng nghiệp vụ** | | |
| CNKQ_5 | Cập nhật kết quả chặng thành công (ca chuẩn) | 1. Mở `ChangChiTiet.jsp` chặng R16.<br>2. Nhập thời gian, số vòng 53, trạng thái `Hoàn thành` cho 12 tay đua.<br>3. Click [Tính kết quả].<br>4. Click [Lưu]. | Bước 3: `KetQuaDAO.createKetQua()` xếp hạng tăng dần theo thời gian, hiển thị bảng đối soát `tblKetQua`. Bước 4: `KetQuaDAO.kiemTraKetQuaCu()` kiểm tra và lưu thành công 12 bản ghi vào CSDL `tblKetQua`, thông báo "Lưu thành công". |
| CNKQ_6 | Xử lý tay đua DNF / DSQ | 1. Nhập kết quả R16, chọn Max Verstappen trạng thái `DNF`, Lewis Hamilton trạng thái `DSQ`.<br>2. Click [Tính kết quả] và [Lưu]. | Verstappen và Hamilton xếp cuối bảng đối soát với 0 điểm; các tay đua hoàn thành được xếp hạng phía trên theo đúng thang điểm 25, 18, 15... |
| CNKQ_7 | Nhập thiếu trạng thái hoặc sai định dạng thời gian — báo lỗi | 1. Nhập thời gian cho 11 tay đua, bỏ trống 1 tay đua.<br>2. Click [Tính kết quả]. | Hệ thống hiển thị thông báo lỗi "Vui lòng nhập thời gian hợp lệ cho tay đua đã hoàn thành", không tính kết quả, nút [Lưu] giữ nguyên chưa active. |
| CNKQ_8 | Ghi đè kết quả khi chặng đã có kết quả cũ | 1. Mở chặng R16 đã nhập kết quả từ trước.<br>2. Nhập lại thời gian mới, click [Tính kết quả], click [Lưu]. | Hệ thống hiển thị hộp thoại cảnh báo "Chặng đua này đã có kết quả, bạn có muốn ghi đè?". Chọn Xác nhận → hệ thống xóa kết quả cũ trong `tblKetQua` và lưu kết quả mới thành công. |
| CNKQ_9 | Xử lý kháng nghị thành công (`KhangNghi.jsp`) | 1. Đăng nhập quyền `NhanVien2`, mở màn hình `KhangNghi.jsp`.<br>2. Chọn đơn kháng nghị của đội McLaren, đối chiếu video camera.<br>3. Chấp nhận kháng nghị, nhập lại kết quả đúng và click [Lưu]. | Hệ thống cập nhật lại bảng điểm xếp hạng của chặng, lưu dữ liệu mới và ghi nhận trạng thái kháng nghị thành công. |
| CNKQ_10 | Phê duyệt kết quả chặng đua | 1. `NhanVien2` kiểm tra kết quả chặng R16 sau khi hết kháng nghị.<br>2. Click [Phê duyệt]. | Hệ thống khóa kết quả chặng R16, đổi trạng thái sang đã phê duyệt và hiển thị thông báo "Phê duyệt kết quả chặng thành công". |
