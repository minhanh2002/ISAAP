# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Cung cấp sở cứ bổ sung

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Cung cấp sở cứ bổ sung |
| **Mô tả** | Đầu mối đơn vị tải lên thêm các tài liệu minh chứng mới cho các usecase bị đội đánh giá yêu cầu bổ sung sở cứ để gửi đánh giá lại. |
| **Tác nhân** | Admin, Đầu mối đơn vị |
| **Tiền điều kiện** | Chương trình đang ở trạng thái Đang đánh giá. Usecase thủ công có trạng thái Yêu cầu bổ sung sở cứ (status = 3). |
| **Hậu điều kiện** | Sở cứ bổ sung được gửi đi. Trạng thái usecase chuyển sang Chờ đánh giá bổ sung (status = 4). |
| **Ngoại lệ** | Không tải lên file mới nào hoặc file tải lên không hợp lệ. |
| **Yêu cầu nghiệp vụ** | - Cho phép đầu mối đơn vị xem lý do yêu cầu bổ sung của đầu mối đánh giá.<br>- Bắt buộc phải tải lên tối thiểu 1 file sở cứ mới.<br>- Định dạng file hỗ trợ: .xlsx, .doc, .pdf.<br>- Lưu nháp file sở cứ bổ sung trước khi gửi. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> ViewReason[Xem nội dung yêu cầu bổ sung]
    ViewReason --> UploadNewFile[Tải lên file sở cứ mới]
    UploadNewFile --> ValidateFile{File hợp lệ?}
    ValidateFile -- Hợp lệ --> AddList[Thêm vào danh sách file bổ sung]
    ValidateFile -- Không hợp lệ --> ErrorFile[Báo lỗi file] --> UploadNewFile
    AddList --> Action{Chọn hành động}
    Action -- Lưu nháp --> SaveDraft[Lưu nháp thông tin]
    Action -- Gửi bổ sung --> CheckMin{Có ít nhất 1 file mới?}
    CheckMin -- Đúng --> Submit[Lưu CSDL, cập nhật trạng thái = Chờ đánh giá bổ sung]
    CheckMin -- Sai --> ErrorMin[Báo lỗi: Bắt buộc tải lên ít nhất 1 file mới] --> UploadNewFile
    SaveDraft --> End([Kết thúc])
    Submit --> End
```

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nội dung yêu cầu bổ sung** | Label / Textbox | OUTPUT | Lấy từ DB | Hiển thị nội dung yêu cầu từ Kiểm toán viên. Mapping DB: `usecase_manual_review_mapping.request_content` |
| 2 | **Mô tả nộp bổ sung** | Textbox | INPUT | Null | Nhập thông tin mô tả đợt nộp bổ sung. Maxlength 500 ký tự. Mapping DB: `usecase_manual_review_mapping.respond_content` |
| 3 | **Nút Chọn file bổ sung** | Button | INPUT | Enable | Click để chọn file sở cứ bổ sung mới |
| 4 | **Danh sách file đã nộp & file mới** | Table / List | OUTPUT | Danh sách file cũ và file mới | Phân biệt rõ file đã nộp trước đó (chỉ xem/tải) và file mới upload (có nút xóa) |
| 5 | **Nút Gửi bổ sung** | Button | INPUT | Enable | Gửi hồ sơ bổ sung đi, cập thái Usecase sang Chờ đánh giá bổ sung |
| 6 | **Nút Hủy** | Button | INPUT | Enable | Hủy bỏ và quay lại |
