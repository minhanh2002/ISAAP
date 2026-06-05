# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Thêm mới chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Thêm mới chương trình đánh giá |
| **Mô tả** | Cho phép Admin tạo mới một chương trình đánh giá, chọn đơn vị tham gia và thiết lập các usecase tự động/thủ công. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Thêm mới_ màn hình khi mới vào.png](../UI/images/Them_Moi/Thêm%20mới_%20màn%20hình%20khi%20mới%20vào.png)
![Thêm mới_ màn hình mặc định_đã chọn đơn vị.png](../UI/images/Them_Moi/Thêm%20mới_%20màn%20hình%20mặc%20định_đã%20chọn%20đơn%20vị.png)
![Thêm đơn vị.png](../UI/images/Them_Moi/Thêm%20đơn%20vị.png)
![Thiết lập usecase tự động.png](../UI/images/Them_Moi/Thiết%20lập%20usecase%20tự%20động.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Tên chương trình** | Text Input | INPUT | Trống | Tên hiển thị của chương trình. Rule: Bắt buộc (Required), Max 255 chars. Mapping lưu: `evaluation_program.name`. |
| 2 | **Mô tả** | Text Area | INPUT | Trống | Mô tả chi tiết. Rule: Tùy chọn, Max 1000 chars. Mapping lưu: `evaluation_program.description`. |
| 3 | **Ngày bắt đầu** | Date Picker | INPUT | Ngày hiện tại | Ngày bắt đầu chương trình. Rule: Bắt buộc, Format DD/MM/YYYY, Không được lớn hơn ngày kết thúc. Mapping lưu: `evaluation_program.start_date`. |
| 4 | **Ngày kết thúc** | Date Picker | INPUT | Trống | Ngày kết thúc dự kiến. Rule: Bắt buộc, >= Ngày bắt đầu. Mapping lưu: `evaluation_program.end_date`. |
| 5 | **Danh sách đơn vị đánh giá** | Bảng / Dropdown đa chọn | INPUT | Trống | Chọn các đơn vị tham gia. Mapping lưu: Insert vào `program_department` (program_id, department_id) và `program_department_mapping`. |
| 6 | **Cấu hình Đầu mối đơn vị** | Dropdown | INPUT | Trống | Chọn người đại diện nộp sở cứ. Mapping lưu: `department_representative_mapping` (`representative_id`). |
| 7 | **Cấu hình Người đánh giá** | Dropdown | INPUT | Trống | Chọn chuyên gia đánh giá đơn vị. Mapping lưu: `department_reviewer_mapping` (`reviewer_id`). |
| 8 | **Thiết lập Usecase** | Tree View Checkbox | INPUT | Trống | Chọn các Đối tượng > Tiêu chí > Usecase áp dụng. Mapping lưu: Các bảng `department_object_mapping`, `object_criteria_mapping`, `criteria_usecase_mapping`. |
| 9 | **Nút Lưu lại** | Button | INPUT | Enable | Lưu thông tin. Rule: Validate toàn bộ form trước khi submit. Insert bản ghi mới vào `evaluation_program` (`status` = 0 - Chưa đánh giá). |
