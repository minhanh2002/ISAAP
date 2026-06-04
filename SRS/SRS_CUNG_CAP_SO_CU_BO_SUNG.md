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

## 2. Giao diện người dùng (UI)

*Chi tiết thiết kế và thành phần giao diện màn hình xem tại:*
*   [Tài liệu thiết kế giao diện: UI_CUNG_CAP_SO_CU_BO_SUNG.md](file:///Users/whis/Anh/ISAAP/UI/UI_CUNG_CAP_SO_CU_BO_SUNG.md)
