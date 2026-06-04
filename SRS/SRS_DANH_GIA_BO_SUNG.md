# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Đánh giá bổ sung

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Đánh giá bổ sung |
| **Mô tả** | Đầu mối đánh giá tiến hành thẩm định các hồ sơ sở cứ bổ sung của đơn vị và đưa ra kết quả kết luận cuối cùng (Đạt hoặc Không đạt) cho usecase. |
| **Tác nhân** | Admin, Đầu mối đánh giá |
| **Tiền điều kiện** | Đơn vị có trạng thái đánh giá thủ công là Chờ đánh giá bổ sung (manual_review_status = 4). Usecase có trạng thái Chờ đánh giá bổ sung (status = 4). |
| **Hậu điều kiện** | Usecase được cập nhật kết quả cuối cùng (Đạt/Không đạt). Trạng thái chuyển sang Hoàn thành (status = 2). |
| **Ngoại lệ** | Chưa chọn kết quả đánh giá cuối cùng hoặc lý do không đạt trống. |
| **Yêu cầu nghiệp vụ** | - Chỉ hiển thị các usecase có trạng thái Chờ đánh giá bổ sung để chấm điểm.<br>- Cho phép xem lý do yêu cầu bổ sung cũ và tài liệu bổ sung mới nộp của đơn vị.<br>- Kết quả đánh giá bổ sung bắt buộc phải là Đạt hoặc Không đạt (không cho phép yêu cầu bổ sung tiếp).<br>- Yêu cầu nhập lý do nếu đánh giá Không đạt. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> ViewSupplement[Xem thông tin bổ sung & file mới của đơn vị]
    ViewSupplement --> ChooseResult[Chọn kết quả cuối cùng: Đạt / Không đạt]
    ChooseResult --> CheckResult{Kết quả?}
    CheckResult -- Đạt --> Submit[Lưu kết quả Đạt]
    CheckResult -- Không đạt --> InputReason[Yêu cầu nhập lý do không đạt]
    InputReason --> Validate{Lý do hợp lệ?}
    Validate -- Hợp lệ --> Submit
    Validate -- Trống --> Error[Báo lỗi: Nhập lý do không đạt!] --> InputReason
    Submit --> UpdateDB[Cập nhật kết quả, trạng thái Usecase = Hoàn thành]
    UpdateDB --> End([Kết thúc])
```

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)
*Chưa có hình ảnh giao diện Figma được kết xuất cho màn hình này.*

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Thông tin sở cứ cũ & mới** | Table / List | OUTPUT | Danh sách file | Hiển thị tất cả file sở cứ đã tải lên qua các đợt. Phân biệt theo round: Round 1, Round 2 |
| 2 | **Ý kiến giải trình của đơn vị** | Label | OUTPUT | Lấy từ DB | Mapping DB: `usecase_manual_review_mapping.respond_content` |
| 3 | **Kết quả đánh giá bổ sung** | Dropdown / Selectbox | INPUT | Null | Chỉ gồm 2 tùy chọn: Đạt, Không đạt. Bắt buộc chọn |
| 4 | **Lý do không đạt bổ sung** | Textbox | INPUT | Null | Chỉ hiển thị và bắt buộc nhập khi chọn Không đạt. Maxlength 500 ký tự |
| 5 | **Nút Gửi kết quả cuối cùng** | Button | INPUT | Enable | Lưu kết quả cuối cùng lên CSDL, chuyển trạng thái usecase thành Hoàn thành (status = 2) |
| 6 | **Nút Hủy** | Button | INPUT | Enable | Quay lại màn hình trước |
