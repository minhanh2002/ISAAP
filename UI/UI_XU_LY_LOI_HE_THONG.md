# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Xử lý lỗi hệ thống (Chạy lại Usecase tự động)

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Bảng danh sách Usecase tự động lỗi** | Table | OUTPUT | Danh sách UC lỗi | Hiển thị danh sách usecase loại Auto bị lỗi, tên lỗi, thời gian xảy ra |
| 2 | **Log lỗi chi tiết** | Label / Textarea (Read-only) | OUTPUT | Lấy từ DB | Hiển thị chi tiết lỗi kỹ thuật của hệ thống. Mapping DB: `rule_run.error` |
| 3 | **Nút Chạy lại** | Button | INPUT | Enable | Kích hoạt gửi tín hiệu cho worker chạy lại Usecase tự động được chọn |
| 4 | **Nút Chạy lại tất cả lỗi của đơn vị** | Button | INPUT | Enable | Kích hoạt chạy lại toàn bộ Usecase tự động lỗi của đơn vị được chọn |
