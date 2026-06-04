# THIẾT KẾ GIAO DIỆN (UI) - MÀN HÌNH: Xem chi tiết chương trình đánh giá

---

## 1. Giao diện trực quan (Figma Export)

![Giao diện Xem chi tiết chương trình đánh giá](file:///Users/whis/Anh/ISAAP/UI/images/Xem_Chi_Tiet.png)

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Tiêu đề trang** | Label | OUTPUT | Xem chi tiết chương trình | Hiển thị tiêu đề màn hình |
| 2 | **Tên chương trình** | Label | OUTPUT | Lấy từ DB | Mapping DB: `evaluation_program.name` |
| 3 | **Thời gian hoạt động** | Label | OUTPUT | Lấy từ DB | Format: dd/mm/yyyy - dd/mm/yyyy. Mapping DB: `evaluation_program.start_date` - `evaluation_program.end_date` |
| 4 | **Tiến độ tổng thể** | Label | OUTPUT | Tính toán tự động | Công thức: (Số UC hoàn thành / Tổng số UC) * 100% |
| 5 | **Bảng danh sách đơn vị** | Table | OUTPUT | Danh sách đơn vị | Hiển thị danh sách các đơn vị và trạng thái |
| 6 | **Nút Quay lại** | Button | INPUT | Enable | Click để quay lại màn hình danh sách và giữ nguyên bộ lọc lọc cũ |
