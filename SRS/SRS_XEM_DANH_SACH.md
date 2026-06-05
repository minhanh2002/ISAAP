# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Xem danh sách chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Xem danh sách chương trình đánh giá |
| **Mô tả** | Hiển thị danh sách các chương trình đánh giá. Có các tab phân loại: Tất cả, Cần duyệt, Cần xử lý, Chưa hoàn thành, Hoàn thành. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Danh sách chương trình đánh giá_full.png](../UI/images/Xem_Danh_Sach/Danh%20sách%20chương%20trình%20đánh%20giá_full.png)
![danh sách chương trình đánh giá.png](../UI/images/Xem_Danh_Sach/danh%20sách%20chương%20trình%20đánh%20giá.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Thanh điều hướng / Tab** | Tab Menu | INPUT | Tất cả | Chuyển đổi các tab. Rule: Khi click, filter danh sách theo trạng thái (Tất cả, Cần duyệt, Cần xử lý, Chưa hoàn thành, Hoàn thành). |
| 2 | **Thanh tìm kiếm** | Text Input | INPUT | Trống | Tìm kiếm theo tên chương trình. Rule: Max 255 chars, trigger search khi gõ hoặc enter. Mapping: `evaluation_program.name` (LIKE). |
| 3 | **Bộ lọc trạng thái** | Dropdown | INPUT | Tất cả | Lọc theo trạng thái chương trình. Mapping: `evaluation_program.status`. |
| 4 | **Bộ lọc thời gian** | Date Range | INPUT | Trống | Lọc theo khoảng thời gian. Mapping: `evaluation_program.start_date` và `end_date`. |
| 5 | **Bảng danh sách** | Table | OUTPUT | Dữ liệu DB | Hiển thị danh sách chương trình. Các trường hiển thị: Tên chương trình (`evaluation_program.name`), Thời gian (`start_date` - `end_date`), Trạng thái (`status`), Tiến độ (tính toán dựa trên UC hoàn thành). |
| 6 | **Phân trang** | Pagination | INPUT | Trang 1 | Rule: Hiển thị 10/20/50 bản ghi trên 1 trang. |
| 7 | **Nút Thêm mới** | Button | INPUT | Enable | Mở màn hình Thêm mới chương trình (chỉ hiển thị nếu user có quyền `CREATE` trong `action`). |
