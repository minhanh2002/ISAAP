# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Cung cấp sở cứ bổ sung

---

## 1. Giao diện trực quan (Figma Export)

*Chưa có hình ảnh giao diện Figma được kết nối cho màn hình này.*

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Nội dung yêu cầu bổ sung** | Label / Textbox | OUTPUT | Lấy từ DB | Hiển thị nội dung yêu cầu từ Kiểm toán viên. Mapping DB: `usecase_manual_review_mapping.request_content` |
| 2 | **Mô tả nộp bổ sung** | Textbox | INPUT | Null | Nhập thông tin mô tả đợt nộp bổ sung. Maxlength 500 ký tự. Mapping DB: `usecase_manual_review_mapping.respond_content` |
| 3 | **Nút Chọn file bổ sung** | Button | INPUT | Enable | Click để chọn file sở cứ bổ sung mới |
| 4 | **Danh sách file đã nộp & file mới** | Table / List | OUTPUT | Danh sách file cũ và file mới | Phân biệt rõ file đã nộp trước đó (chỉ xem/tải) và file mới upload (có nút xóa) |
| 5 | **Nút Gửi bổ sung** | Button | INPUT | Enable | Gửi hồ sơ bổ sung đi, cập nhật trạng thái Usecase sang Chờ đánh giá bổ sung |
| 6 | **Nút Hủy** | Button | INPUT | Enable | Hủy bỏ và quay lại |
