# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Đánh giá đơn vị (Đánh giá lần đầu)

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Bảng danh sách Usecase** | Table | OUTPUT | Danh sách Usecase chờ đánh giá | Hiển thị danh sách usecase và tài liệu sở cứ đính kèm |
| 2 | **Kết quả đánh giá** | Dropdown / Selectbox | INPUT | Null | Các tùy chọn: Đạt, Không đạt, Yêu cầu bổ sung sở cứ. Mặc định trống. Bắt buộc chọn |
| 3 | **Lý do không đạt / yêu cầu bổ sung** | Textbox | INPUT | Null | Chỉ hiển thị và bắt buộc nhập khi chọn Không đạt hoặc Yêu cầu bổ sung. Maxlength 500 ký tự |
| 4 | **Nút Lưu nháp** | Button | INPUT | Enable | Lưu thông tin đánh giá hiện tại vào trường draft_content dưới dạng nháp |
| 5 | **Nút Gửi kết quả** | Button | INPUT | Enable | Lưu chính thức kết quả đánh giá lên CSDL và chuyển trạng thái |
| 6 | **Nút Hủy** | Button | INPUT | Enable | Hủy bỏ các thay đổi chưa lưu và quay lại màn hình trước đó |
