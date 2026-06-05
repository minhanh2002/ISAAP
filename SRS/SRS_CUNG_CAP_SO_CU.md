# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Cung cấp sở cứ (Tải file)

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Cung cấp sở cứ (Tải file) |
| **Mô tả** | Cho phép đầu mối đơn vị nộp sở cứ cho các usecase thủ công lần 1 và lần 2. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Cung cấp sở cứ lần 1.png](file:///Users/whis/Anh/ISAAP/UI/images/Cung_Cap_So_Cu/Cung%20cấp%20sở%20cứ%20lần%201.png)
![Cung cấp sở cứ lần 2.png](file:///Users/whis/Anh/ISAAP/UI/images/Cung_Cap_So_Cu/Cung%20cấp%20sở%20cứ%20lần%202.png)
![Tải file (Up sở cứ).png](file:///Users/whis/Anh/ISAAP/UI/images/Cung_Cap_So_Cu/Tải%20file%20(Up%20sở%20cứ).png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Thông tin Usecase** | Label | OUTPUT | Tên UC | Tên Usecase đang được yêu cầu cung cấp sở cứ |
| 2 | **Nút Tải lên (Upload)** | File Input | INPUT | Trống | Cho phép chọn file tài liệu, hình ảnh để tải lên làm sở cứ |
| 3 | **Khung hiển thị file** | List | OUTPUT | Trống | Danh sách các file đã được chọn để upload, có nút [X] để xóa |
| 4 | **Ghi chú bổ sung** | Text Area | INPUT | Trống | Nhập giải trình hoặc ghi chú gửi kèm sở cứ |
| 5 | **Nút Gửi sở cứ** | Button | INPUT | Enable | Xác nhận lưu file vào hệ thống và chuyển trạng thái Chờ đánh giá |
