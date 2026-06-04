# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Cung cấp sở cứ (Lần đầu)

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Chọn file** | Button | INPUT | Enable | Click để chọn file từ máy tính. Hỗ trợ chọn nhiều file cùng lúc |
| 2 | **Danh sách file đã chọn** | Table / List | OUTPUT | Trống | Hiển thị danh sách file đang chuẩn bị upload gồm: Tên file, dung lượng, nút Xóa file |
| 3 | **Nút Lưu nháp** | Button | INPUT | Enable | Lưu tạm thời danh sách file đã chọn dưới trạng thái draft_status = 1 |
| 4 | **Nút Gửi đánh giá** | Button | INPUT | Enable | Chuyển các file thành chính thức (draft_status = 0) và cập nhật trạng thái usecase thành Chờ đánh giá |
| 5 | **Nút Hủy** | Button | INPUT | Enable | Hủy bỏ toàn bộ file đã chọn và quay lại màn hình danh sách |
