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

![Popup_Bat_Dau.png](../UI/images/Bat_Dau/Popup_Bat_Dau.png)
![Popup xác nhận_Bắt đầu đánh giá.png](../UI/images/Bat_Dau/Popup%20xác%20nhận_Bắt%20đầu%20đánh%20giá.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Bắt đầu đánh giá** | Button | INPUT | Enable/Disable | Chỉ Enable khi chương trình ở trạng thái Khởi tạo (`status` = 0). |
| 2 | **Popup Xác nhận** | Modal | OUTPUT | Ẩn | Hiển thị cảnh báo xác nhận chạy chương trình. |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Xử lý DB: 1. Update `evaluation_program.status` = Đang đánh giá. 2. Insert hàng loạt vào `usecase_manual_review_mapping` (status = 0 - Chưa nộp sở cứ). 3. Lập lịch / insert vào `rule_run` cho các auto rules. |
| 4 | **Nút Hủy** | Button | INPUT | Enable | Đóng popup không thực hiện thao tác. |
