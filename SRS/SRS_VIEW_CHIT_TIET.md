# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Xem chi tiết chương trình đánh giá

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Xem chi tiết chương trình đánh giá |
| **Mô tả** | Hiển thị thông tin chi tiết của chương trình, bao gồm thông tin chung, danh sách đơn vị, đối tượng, tiêu chí, và usecase. Hỗ trợ tra cứu và xóa thành phần. |
| **Tác nhân** | Admin, Đầu mối đơn vị, Đầu mối điều phối, Đầu mối đánh giá |

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)

![Xem_Chi_Tiet.png](file:///Users/whis/Anh/ISAAP/UI/images/Xem_Chi_Tiet/Xem_Chi_Tiet.png)
![Xem chi tiết_Có mô tả.png](file:///Users/whis/Anh/ISAAP/UI/images/Xem_Chi_Tiet/Xem%20chi%20tiết_Có%20mô%20tả.png)
![Popup Tra cứu usecase_ mặc định.png](file:///Users/whis/Anh/ISAAP/UI/images/Xem_Chi_Tiet/Popup%20Tra%20cứu%20usecase_%20mặc%20định.png)
![Popup Xác nhận xóa usecase.png](file:///Users/whis/Anh/ISAAP/UI/images/Xem_Chi_Tiet/Popup%20Xác%20nhận%20xóa%20usecase.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Thông tin tổng quan** | Group | OUTPUT | Dữ liệu DB | Hiển thị Tên, Trạng thái, Tiến độ, Thời gian |
| 2 | **Cây cấu trúc** | Tree View | OUTPUT | Cấu trúc DB | Hiển thị danh sách Đơn vị -> Đối tượng -> Tiêu chí -> Usecase |
| 3 | **Nút Xóa (Tiêu chí/UC)** | Icon Button | INPUT | Enable | Click để mở popup xác nhận xóa |
| 4 | **Thanh tra cứu** | Search Box | INPUT | Trống | Nhập tên usecase để tra cứu nhanh |
| 5 | **Nút Quay lại** | Button | INPUT | Enable | Trở về màn hình danh sách |
