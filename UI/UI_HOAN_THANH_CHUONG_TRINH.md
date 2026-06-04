# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Hoàn thành chương trình đánh giá

---

## 1. Giao diện trực quan (Figma Export)

![Giao diện Hoàn thành chương trình đánh giá](file:///Users/whis/Anh/ISAAP/UI/images/Popup_Hoan_Thanh.png)

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Hoàn thành chương trình** | Button | INPUT | Enable/Disable | Chỉ hiển thị khi chương trình đang đánh giá. Chỉ Enable khi thỏa mãn điều kiện tất cả Usecase có kết quả |
| 2 | **Popup Xác nhận hoàn thành** | Popup | OUTPUT | Ẩn | Tiêu đề: Xác nhận hoàn thành chương trình. Nội dung: Bạn có chắc chắn muốn hoàn thành chương trình đánh giá này? Dữ liệu sẽ bị khóa và không thể chỉnh sửa. |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Click để hoàn thành chương trình |
| 4 | **Nút Hủy** | Button | INPUT | Enable | Click để đóng popup |
