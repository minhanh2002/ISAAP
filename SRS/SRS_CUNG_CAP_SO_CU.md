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

![Cung cấp sở cứ lần 1.png](../UI/images/Cung_Cap_So_Cu/Cung%20cấp%20sở%20cứ%20lần%201.png)
![Cung cấp sở cứ lần 2.png](../UI/images/Cung_Cap_So_Cu/Cung%20cấp%20sở%20cứ%20lần%202.png)
![Tải file (Up sở cứ).png](../UI/images/Cung_Cap_So_Cu/Tải%20file%20(Up%20sở%20cứ).png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Tên Usecase** | Label | OUTPUT | DB | Tên Usecase cần nộp sở cứ. Lấy từ join `rule.name`. |
| 2 | **Nút Chọn File (Upload)** | File Input | INPUT | Trống | Rule: Hỗ trợ định dạng PDF, DOCX, XLSX, PNG, JPG. Max size 20MB. |
| 3 | **Danh sách File tải lên** | List | OUTPUT | DB/Local | Hiển thị file được chọn. Mapping lưu: Insert vào `usecase_review_file` (`name`, `path`, `size`, `usecase_review_id`, `round`, `draft_status`). |
| 4 | **Trường Ghi chú/Giải trình** | Text Area | INPUT | Trống | Rule: Tùy chọn. Max 1000 chars. Mapping lưu: `usecase_manual_review_mapping.respond_content`. |
| 5 | **Nút Lưu Nháp** | Button | INPUT | Enable | Rule: Lưu file với `usecase_review_file.draft_status` = 1, lưu nội dung vào `usecase_manual_review_mapping.draft_content`. |
| 6 | **Nút Gửi sở cứ** | Button | INPUT | Enable | Xử lý DB: Update `usecase_manual_review_mapping.status` = 1 (Chờ đánh giá). Update `usecase_review_file.draft_status` = 0. Update `program_department_mapping.manual_review_status` = 1. |
