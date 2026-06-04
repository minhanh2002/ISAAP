# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Xem chi tiết chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Xem chi tiết chương trình đánh giá |
| **Mô tả** | Cho phép người dùng theo dõi tiến độ tổng thể của chương trình đánh giá, xem trạng thái đánh giá thủ công/tự động của từng đơn vị, danh sách đối tượng, tiêu chí, usecase và kết quả chi tiết. |
| **Tác nhân** | Admin, Đầu mối điều phối, Đầu mối đơn vị, Đầu mối đánh giá |
| **Tiền điều kiện** | Chương trình đã ở trạng thái Đang đánh giá, Đã hoàn thành hoặc Đã hủy. |
| **Hậu điều kiện** | Hệ thống hiển thị đầy đủ thông tin chi tiết và tiến trình chạy của chương trình. |
| **Ngoại lệ** | Không tìm thấy chương trình đánh giá hoặc tài khoản không có quyền truy cập. |
| **Yêu cầu nghiệp vụ** | - Hiển thị thông tin chung của chương trình.<br>- Tính toán tiến độ tổng thể của chương trình.<br>- Hiển thị danh sách các đơn vị được phân bổ.<br>- Cho phép chọn đơn vị để xem chi tiết danh sách Đối tượng > Tiêu chí > Usecase.<br>- Hỗ trợ tải xuống file sở cứ. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> RequestView[Yêu cầu xem chi tiết]
    RequestView --> CheckPerm{Kiểm tra quyền}
    CheckPerm -- Có quyền --> LoadData[Truy vấn CSDL & Tính tiến độ]
    LoadData --> Display[Hiển thị màn hình chi tiết]
    Display --> End([Kết thúc])
    CheckPerm -- Không quyền --> Error[Hiển thị lỗi truy cập]
    Error --> End
```

---

## 2. Giao diện người dùng (UI)

*Chi tiết thiết kế và thành phần giao diện màn hình xem tại:*
*   [Tài liệu thiết kế giao diện: UI_VIEW_CHIT_TIET.md](file:///Users/whis/Anh/ISAAP/UI/UI_VIEW_CHIT_TIET.md)
