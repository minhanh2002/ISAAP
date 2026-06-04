# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Xóa chương trình đánh giá

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Xóa** | Button | INPUT | Enable/Disable | Hiển thị tại màn hình danh sách chương trình. Chỉ Enable khi status = Chưa đánh giá |
| 2 | **Popup Xác nhận xóa** | Popup | OUTPUT | Ẩn | Tiêu đề: Xác nhận xóa chương trình đánh giá. Nội dung: Bạn có chắc chắn muốn xóa chương trình này? Hành động này không thể hoàn tác. |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Click để thực hiện xóa chương trình và đóng popup |
| 4 | **Nút Hủy** | Button | INPUT | Enable | Click để đóng popup và giữ nguyên chương trình |
