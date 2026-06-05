# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Bắt đầu đánh giá (Chạy chương trình)

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Bắt đầu đánh giá (Chạy chương trình) |
| **Mô tả** | Popup xác nhận để bắt đầu chạy chương trình đánh giá. Ngoài ra còn có popup hủy và hoàn thành chương trình. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Popup_Bat_Dau.png](file:///Users/whis/Anh/ISAAP/UI/images/Bat_Dau/Popup_Bat_Dau.png)
![Popup xác nhận_Bắt đầu đánh giá.png](file:///Users/whis/Anh/ISAAP/UI/images/Bat_Dau/Popup%20xác%20nhận_Bắt%20đầu%20đánh%20giá.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Tiêu đề Popup** | Label | OUTPUT | Xác nhận bắt đầu | Hiển thị tiêu đề popup |
| 2 | **Nội dung cảnh báo** | Label | OUTPUT | Text mặc định | Hiển thị cảnh báo hệ thống sẽ sinh dữ liệu và gửi thông báo |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Click để chuyển trạng thái sang Đang đánh giá |
| 4 | **Nút Đóng** | Button | INPUT | Enable | Đóng popup |
