# Cách import PlantUML vào Visual Paradigm

## Plugin đã cài sẵn trên máy

Kiểm tra: `C:\Users\K\AppData\Roaming\VisualParadigm\plugins\plugin-plantuml-vp-v1.0.0`

Nếu máy khác chưa có thì tải [plugin-plantuml-vp-v1.0.0.zip](https://github.com/nbourdi/PlantUML-VP-Plugin/releases/download/v1.0.0/plugin-plantuml-vp-v1.0.0.zip)
rồi trong Visual Paradigm vào **Help → Install Plugin → Install from a zip of plugin**, chọn file zip, khởi động lại VP.

## Import — 4 bước

1. Mở Visual Paradigm, mở project `.vpp` muốn nhập vào.
   Nên tạo project rỗng mới để thử trước, đừng nhập thẳng vào project đang làm.
2. Vào tab **Project** trên ribbon.
3. Chọn **Import → PlantUML...**
4. Trỏ tới thư mục này (`test import plantuml to vp`) hoặc tới một file `.puml` cụ thể.

Xong. Biểu đồ hiện trong Project Browser bên trái.

> Đường dẫn menu lấy từ `plugin.xml` của plugin: `ribbonPath="Project/Import/XML"`.

## Export ngược lại (nếu cần)

- **Project → Export → PlantUML...** — xuất toàn bộ project ra `.puml`
- **Project → Export → Active Diagram as PlantUML...** — chỉ xuất biểu đồ đang mở

## Nếu menu không hiện

Plugin cài rồi mà không thấy **Project → Import → PlantUML...** thì khởi động lại VP một lần nữa.
Vẫn không có thì dùng dòng lệnh — `Plugin.bat` đã có sẵn ở `bin`:

```bat
cd /d "C:\Program Files\Visual Paradigm CE 17.2\bin"
Plugin.bat -project "C:\Users\K\Documents\VPProjects\thu-plantuml.vpp" -pluginid "plugins.plantUML" -pluginargs -action "import" -path "e:\HK3-N4\cnpm\test import plantuml to vp"
```

Đổi `thu-plantuml.vpp` thành tên project của bạn. Lệnh này nhập **cả thư mục** (29 biểu đồ) một lượt.

## Nên thử file nào trước

Đừng nhập cả 29 file ngay. Thử 2 file nhẹ nhất để biết plugin có chạy không:

| File | Dòng | Loại |
|---|---|---|
| `m1-trangthai.puml` | 12 | State Machine |
| `m1-uc-chitiet.puml` | 23 | Use Case |

Chạy được thì thử file nặng nhất: `m4-tuantu.puml` (157 dòng, Sequence).

## Danh sách 29 file

Tên file trùng tên ảnh cần export ở `docs/00-ke-hoach-va-phan-cong.md` mục 7 — import xong export ra là dùng luôn.

| File | Loại | Nguồn |
|---|---|---|
| `m1-uc-chitiet` · `m2-` · `m3-` · `m4-` | Use Case | `Module N/noi-dung.md` mục 1 |
| `m1-trangthai` · `m2-` · `m3-` · `m4-` | State Machine | mục 3 |
| `m1-lop-phantich` · `m2-` · `m3-` · `m4-` | Class | mục 4 |
| `m1-lop-mvc` · `m2-` · `m3-` · `m4-` | Class | mục 5 |
| `m1-hoatdong` · `m2-` · `m3-` · `m4-` | Activity | mục 6 |
| `m1-tuantu` · `m2-` · `m3-` · `m4-` | Sequence | mục 7 |
| `chung-uc-tongquat` | Use Case | `docs/02` mục 4 |
| `chung-lop-thucthe-phantich` | Class | `docs/03` mục 3.1 |
| `chung-lop-thucthe-thietke` | Class | `docs/03` mục 3.2 |
| `chung-package-trienkhai` | Package | `docs/03` mục 6 |
| `chung-dao-kethua` | Class | `docs/03` mục 4 |

Cả 29 file đã qua `plantuml -checkonly`: 0 lỗi cú pháp. Import hỏng là do plugin, không phải do file.

## Sau khi import vẫn phải chỉnh tay

Plugin dựng phần tử và quan hệ, không dựng được cách trình bày:

- **Tuần tự:** bật *Show sequence number* để có số message chạy suốt.
- **Lớp thiết kế:** xếp lại ba tầng theo hàng — `gdXxx.jsp` trên, `XxxDAO` giữa, lớp thực thể dưới.
- **Hoạt động:** tách node `XxxDAO: tenHam()` ra ngoài khung `Xử lí tại gdXxx.jsp`.

---

Đây là thư mục nháp. Sửa blueprint thì sửa trong `Module N/noi-dung.md`, không sửa ở đây.
