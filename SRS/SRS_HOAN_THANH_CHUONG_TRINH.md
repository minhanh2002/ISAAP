# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Hoàn thành chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Hoàn thành chương trình đánh giá |
| **Mô tả** | Kết thúc chương trình đánh giá và đóng băng dữ liệu sau khi tất cả các usecase của mọi đơn vị đã hoàn thành chấm điểm và có kết quả cuối cùng. |
| **Tác nhân** | Admin, Đầu mối điều phối |
| **Tiền điều kiện** | Chương trình đang ở trạng thái Đang đánh giá. Tất cả usecase thủ công và tự động của tất cả đơn vị đã có kết quả cuối cùng (Đạt/Không đạt). |
| **Hậu điều kiện** | Chương trình chuyển sang trạng thái Đã hoàn thành (status = Hoàn thành). Khóa toàn bộ dữ liệu. |
| **Ngoại lệ** | Vẫn còn usecase chưa hoàn thành đánh giá hoặc chưa có kết quả. |
| **Yêu cầu nghiệp vụ** | - Kiểm tra điều kiện hoàn thành: Tất cả các bản ghi trong `usecase_manual_review_mapping` có status = 2 (Hoàn thành) và tất cả `rule_run` có kết quả khác null.<br>- Cập nhật trạng thái chương trình thành Đã hoàn thành (completed_at = Hiện tại).<br>- Đóng băng dữ liệu, khóa mọi quyền chỉnh sửa sở cứ hoặc đánh giá. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> RequestComplete[Nhấp nút Hoàn thành chương trình]
    RequestComplete --> CheckAllDone{Tất cả Usecase đã hoàn thành & có KQ?}
    CheckAllDone -- Đúng --> ShowPopup[Hiển thị Popup xác nhận]
    ShowPopup --> Confirm{Xác nhận hoàn thành?}
    Confirm -- Đồng ý --> UpdateStatus[Cập nhật trạng thái = Đã hoàn thành & Đóng băng dữ liệu]
    UpdateStatus --> Success[Hiển thị thông báo thành công]
    Confirm -- Hủy --> ClosePopup[Đóng popup]
    CheckAllDone -- Sai --> Error[Hiển thị lỗi: Vẫn còn usecase chưa hoàn thành đánh giá]
    Success --> End([Kết thúc])
    ClosePopup --> End
    Error --> End
```

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)
![Giao diện Hoàn thành chương trình đánh giá](../UI/images/Popup_Hoan_Thanh.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nút Hoàn thành chương trình** | Button | INPUT | Enable/Disable | Chỉ hiển thị khi chương trình đang đánh giá. Chỉ Enable khi thỏa mãn điều kiện tất cả Usecase có kết quả |
| 2 | **Popup Xác nhận hoàn thành** | Popup | OUTPUT | Ẩn | Tiêu đề: Xác nhận hoàn thành chương trình. Nội dung: Bạn có chắc chắn muốn hoàn thành chương trình đánh giá này? Dữ liệu sẽ bị khóa và không thể chỉnh sửa. |
| 3 | **Nút Xác nhận** | Button | INPUT | Enable | Click để hoàn thành chương trình |
| 4 | **Nút Hủy** | Button | INPUT | Enable | Click để đóng popup |
