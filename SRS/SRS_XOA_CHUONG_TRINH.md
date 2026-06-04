# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Xóa chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Xóa chương trình đánh giá |
| **Mô tả** | Cho phép Admin xóa vĩnh viễn một chương trình đánh giá khỏi hệ thống khi chương trình đó chưa bắt đầu đánh giá. |
| **Tác nhân** | Admin |
| **Tiền điều kiện** | Chương trình đánh giá ở trạng thái Chưa đánh giá (status = 0). |
| **Hậu điều kiện** | Chương trình và các bản ghi liên quan bị xóa vĩnh viễn khỏi CSDL hoặc cập nhật trạng thái xóa. |
| **Ngoại lệ** | Chương trình đã bắt đầu đánh giá hoặc không tìm thấy chương trình. |
| **Yêu cầu nghiệp vụ** | - Chỉ hiển thị nút Xóa đối với tài khoản Admin.<br>- Chỉ cho phép xóa khi trạng thái chương trình là Chưa đánh giá.<br>- Hiển thị popup xác nhận trước khi thực hiện xóa. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> RequestDelete[Nhấp nút Xóa]
    RequestDelete --> CheckStatus{Trạng thái == Chưa đánh giá?}
    CheckStatus -- Đúng --> ShowPopup[Hiển thị Popup xác nhận]
    ShowPopup --> Confirm{Xác nhận xóa?}
    Confirm -- Đồng ý --> DeleteDB[Xóa dữ liệu trong CSDL]
    DeleteDB --> Success[Hiển thị thông báo thành công & Load lại trang]
    Confirm -- Hủy --> KeepData[Giữ nguyên dữ liệu & Đóng popup]
    CheckStatus -- Sai --> Error[Hiển thị lỗi: Không thể xóa chương trình đã chạy]
    Success --> End([Kết thúc])
    KeepData --> End
    Error --> End
```

---

## 2. Giao diện người dùng (UI)

*Chi tiết thiết kế và thành phần giao diện màn hình xem tại:*
*   [Tài liệu thiết kế giao diện: UI_XOA_CHUONG_TRINH.md](file:///Users/whis/Anh/ISAAP/UI/UI_XOA_CHUONG_TRINH.md)
