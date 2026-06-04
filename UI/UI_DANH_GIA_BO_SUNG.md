# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Đánh giá bổ sung

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Thông tin sở cứ cũ & mới** | Table / List | OUTPUT | Danh sách file | Hiển thị tất cả file sở cứ đã tải lên qua các đợt. Phân biệt theo round: Round 1, Round 2 |
| 2 | **Ý kiến giải trình của đơn vị** | Label | OUTPUT | Lấy từ DB | Mapping DB: `usecase_manual_review_mapping.respond_content` |
| 3 | **Kết quả đánh giá bổ sung** | Dropdown / Selectbox | INPUT | Null | Chỉ gồm 2 tùy chọn: Đạt, Không đạt. Bắt buộc chọn |
| 4 | **Lý do không đạt bổ sung** | Textbox | INPUT | Null | Chỉ hiển thị và bắt buộc nhập khi chọn Không đạt. Maxlength 500 ký tự |
| 5 | **Nút Gửi kết quả cuối cùng** | Button | INPUT | Enable | Lưu kết quả cuối cùng lên CSDL, chuyển trạng thái usecase thành Hoàn thành (status = 2) |
| 6 | **Nút Hủy** | Button | INPUT | Enable | Quay lại màn hình trước |
