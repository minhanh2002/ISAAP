# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Bắt đầu đánh giá (Chạy chương trình)

---

## 1. Giao diện trực quan (Figma Export)

![Giao diện Bắt đầu đánh giá (Chạy chương trình)](file:///Users/whis/Anh/ISAAP/UI/images/Popup_Bat_Dau.png)

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Bắt đầu đánh giá** | Button | INPUT | Enable/Disable | Chỉ hiển thị khi chương trình ở trạng thái Chưa đánh giá |
| 2 | **Popup Xác nhận bắt đầu** | Popup | OUTPUT | Ẩn | Tiêu đề: Xác nhận chạy chương trình. Nội dung: Bạn có chắc chắn muốn bắt đầu đánh giá chương trình này? Hệ thống sẽ sinh các bản ghi và kích hoạt đánh giá tự động. |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Click để kích hoạt chương trình và đóng popup |
| 4 | **Nút Hủy** | Button | INPUT | Enable | Click để hủy lệnh và đóng popup |
