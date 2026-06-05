# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Chỉnh sửa chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Chỉnh sửa chương trình đánh giá |
| **Mô tả** | Cho phép Admin cập nhật lại thông tin chương trình đánh giá khi chương trình ở trạng thái cho phép chỉnh sửa. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Chỉnh sửa.png](../UI/images/Chinh_Sua/Chỉnh%20sửa.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Tên chương trình** | Text Input | I/O | Dữ liệu cũ | Tên chương trình. Rule: Bắt buộc, Max 255. Mapping: Update `evaluation_program.name`. |
| 2 | **Mô tả** | Text Area | I/O | Dữ liệu cũ | Mô tả. Rule: Tùy chọn. Mapping: Update `evaluation_program.description`. |
| 3 | **Thời gian thực hiện** | Date Picker | I/O | Dữ liệu cũ | Ngày chạy. Mapping: Update `evaluation_program.start_date`, `end_date`. |
| 4 | **Danh sách đơn vị** | Table | I/O | Dữ liệu cũ | Cập nhật đơn vị. Mapping: Insert/Delete `program_department` và `program_department_mapping`. |
| 5 | **Nút Cập nhật** | Button | INPUT | Enable | Rule: Chỉ cho phép cập nhật khi chương trình ở trạng thái Khởi tạo (Chưa chạy). Lưu thay đổi vào DB. |
