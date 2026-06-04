# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Hủy đánh giá chương trình

---

## 1. Giao diện trực quan (Figma Export)

![Giao diện Hủy đánh giá chương trình](file:///Users/whis/Anh/ISAAP/UI/images/Popup_Huy.png)

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Hủy đánh giá** | Button | INPUT | Enable/Disable | Chỉ hiển thị khi chương trình ở trạng thái Đang đánh giá |
| 2 | **Popup Yêu cầu nhập lý do hủy** | Popup | OUTPUT | Ẩn | Tiêu đề: Hủy đánh giá chương trình. Yêu cầu nhập lý do hủy. |
| 3 | **Lý do hủy** | Textbox | INPUT | Null | Bắt buộc nhập lý do hủy. Maxlength 500 ký tự. Placeholder: Nhập lý do hủy chương trình |
| 4 | **Nút Xác nhận hủy** | Button | INPUT | Enable | Click để tiến hành hủy và đóng popup |
| 5 | **Nút Quay lại** | Button | INPUT | Enable | Click để đóng popup và giữ nguyên trạng thái chương trình |
