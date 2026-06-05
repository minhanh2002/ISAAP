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

![Đánh giá đơn vị lần 1.png](file:///Users/whis/Anh/ISAAP/UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20đơn%20vị%20lần%201.png)
![Đánh giá đơn vị lần 2.png](file:///Users/whis/Anh/ISAAP/UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20đơn%20vị%20lần%202.png)
![Đánh giá từng UC.png](file:///Users/whis/Anh/ISAAP/UI/images/Danh_Gia_Don_Vi/Đánh%20giá%20từng%20UC.png)

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Danh sách Usecase** | Table/List | OUTPUT | Dữ liệu DB | Hiển thị các usecase của đơn vị cần đánh giá |
| 2 | **Nội dung sở cứ** | Link/Preview | OUTPUT | File từ Đơn vị | Xem trước hoặc tải về file sở cứ đơn vị đã nộp |
| 3 | **Trạng thái Đạt/Không đạt** | Radio/Switch | INPUT | Chưa chọn | Chọn kết quả đánh giá cho Usecase |
| 4 | **Lý do (Nếu Không đạt)** | Text Area | INPUT | Trống | Nhập lý do hoặc yêu cầu bổ sung sở cứ nếu đánh giá Không đạt |
| 5 | **Nút Lưu kết quả** | Button | INPUT | Enable | Lưu trạng thái đánh giá vào CSDL |
