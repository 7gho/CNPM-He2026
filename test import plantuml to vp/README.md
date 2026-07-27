# Thử import PlantUML vào Visual Paradigm

Thư mục thử nghiệm plugin [nbourdi/PlantUML-VP-Plugin](https://github.com/nbourdi/PlantUML-VP-Plugin).
Nếu import chạy tốt thì nhóm đỡ phải kéo-thả tay 29 biểu đồ.

**Đây là thư mục nháp.** Nội dung trong này được tách ra từ các khối ```plantuml trong
`Module N/noi-dung.md`, `docs/02`, `docs/03` — sửa ở đó mới là sửa thật, sửa ở đây không tính.
Thử xong có thể xoá cả thư mục.

## Cách thử

1. Cài plugin theo hướng dẫn của repo trên (Visual Paradigm → `Help` → `Install Plugin`).
2. Import lần lượt vài file, **bắt đầu bằng 4 file dễ nhất** để biết plugin có chạy không:
   `m1-trangthai.puml` · `m1-uc-chitiet.puml` · `chung-dao-kethua.puml` · `chung-package-trienkhai.puml`
3. Nếu 4 file trên vào được thì thử tiếp file nặng: `m4-tuantu.puml` (157 dòng), `m2-lop-phantich.puml` (120 dòng).
4. Ghi lại file nào lỗi để nhóm biết loại nào phải vẽ tay.

## Danh sách file

Tên file trùng với tên ảnh cần export ở `docs/00-ke-hoach-va-phan-cong.md` mục 7.

| File | Loại biểu đồ | Nguồn |
|---|---|---|
| `m1-uc-chitiet.puml` · `m2-` · `m3-` · `m4-` | Use Case | `Module N/noi-dung.md` mục 1 |
| `m1-trangthai.puml` · `m2-` · `m3-` · `m4-` | State Machine | mục 3 |
| `m1-lop-phantich.puml` · `m2-` · `m3-` · `m4-` | Class | mục 4 |
| `m1-lop-mvc.puml` · `m2-` · `m3-` · `m4-` | Class | mục 5 |
| `m1-hoatdong.puml` · `m2-` · `m3-` · `m4-` | Activity (new syntax) | mục 6 |
| `m1-tuantu.puml` · `m2-` · `m3-` · `m4-` | Sequence | mục 7 |
| `chung-uc-tongquat.puml` | Use Case | `docs/02` mục 4 |
| `chung-lop-thucthe-phantich.puml` | Class | `docs/03` mục 3.1 |
| `chung-lop-thucthe-thietke.puml` | Class | `docs/03` mục 3.2 |
| `chung-package-trienkhai.puml` | Package / Component | `docs/03` mục 6 |
| `chung-dao-kethua.puml` | Class | `docs/03` mục 4 |

Cả 29 file đã qua `plantuml -checkonly`: **0 lỗi cú pháp**. Nếu import hỏng thì là do plugin, không phải do file.

## Bốn chỗ nhiều khả năng plugin nuốt không trôi

Thử xong thì biết ngay — ghi lại ở đây để khỏi mất công đoán:

1. **`class "gdChinhNV.jsp" as gdChinhNV`** (file `*-lop-mvc.puml`). Dạng đặt bí danh này có thể bị plugin
   lấy `gdChinhNV` làm tên lớp và bỏ mất đuôi `.jsp`. Nếu vậy, sửa tay tên lớp sau khi import.
2. **`partition "Xử lí tại gdXxx.jsp"`** (file `*-hoatdong.puml`). Plugin ghi là hỗ trợ activity "new syntax"
   nhưng không nói có nhận `partition` không. Đây là khối dễ hỏng nhất.
   Nhắc lại: khi vẽ, node `XxxDAO: tenHam()` phải nằm **ngoài** khung, nối bằng mũi tên — plugin
   chắc chắn không tự làm được việc đó, phải kéo tay.
3. **Tiếng Việt có dấu.** Toàn bộ file lưu UTF-8 không BOM. Nếu VP hiện ô vuông hoặc dấu hỏi thì là
   lỗi encoding lúc đọc file, thử đổi font trong VP trước khi kết luận plugin lỗi.
4. **`chung-package-trienkhai.puml`** dùng package lồng package. Plugin liệt kê Component và Deployment
   chứ không liệt kê Package diagram, nên file này có thể vào sai loại biểu đồ.

## Sau khi import vẫn phải chỉnh tay

Plugin chỉ dựng phần tử và quan hệ, không dựng được cách trình bày mà thầy yêu cầu:

- **Biểu đồ tuần tự:** bật *Show sequence number* để có số thứ tự message chạy suốt.
- **Biểu đồ lớp thiết kế:** xếp lại ba tầng theo hàng — `gdXxx.jsp` trên, `XxxDAO` giữa, lớp thực thể dưới.
- **Biểu đồ hoạt động:** tách node DAO ra ngoài khung `Xử lí tại gdXxx.jsp`.
- **Biểu đồ UC chi tiết:** kiểm tra `<<include>>` / `<<extend>>` và mũi tên kế thừa `Đăng nhập` ← `NV đăng nhập`.
