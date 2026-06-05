# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Đánh giá đơn vị

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Đánh giá đơn vị |
| **Mô tả** | Giao diện dành cho người đánh giá chấm điểm hoặc chọn Đạt/Không đạt cho từng usecase dựa trên sở cứ được cung cấp. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Đánh giá đơn vị lần 1.png](../UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20đơn%20vị%20lần%201.png)
![Đánh giá đơn vị lần 2.png](../UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20đơn%20vị%20lần%202.png)
![Đánh giá từng UC.png](../UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20từng%20UC.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **File sở cứ (Preview)** | File Viewer | OUTPUT | DB | Hiển thị danh sách file để tải về hoặc xem trước. Mapping lấy: `usecase_review_file.path`. |
| 2 | **Nội dung giải trình** | Label | OUTPUT | DB | Mapping lấy: `usecase_manual_review_mapping.respond_content`. |
| 3 | **Đánh giá Kết quả** | Radio Button | INPUT | Chưa chọn | Chọn Đạt hoặc Không đạt. Rule: Bắt buộc chọn 1. Mapping lưu: `usecase_manual_review_mapping.result` (1: Đạt, 0: Không đạt). |
| 4 | **Lý do không đạt** | Text Area | INPUT | Trống | Nhập lý do. Rule: Bắt buộc nếu chọn Không đạt. Mapping lưu: `usecase_manual_review_mapping.reason_fail`. |
| 5 | **Yêu cầu bổ sung** | Text Area | INPUT | Trống | Nhập yêu cầu nếu bắt đơn vị làm lại. Mapping lưu: `usecase_manual_review_mapping.request_content`. |
| 6 | **Nút Lưu kết quả** | Button | INPUT | Enable | Xử lý DB: Update `usecase_manual_review_mapping.result`, cập nhật trạng thái `status` = 2 (Hoàn thành) hoặc 3 (Yêu cầu bổ sung). Cập nhật `program_department_mapping.evaluation_result`. |
