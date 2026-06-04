# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: Xử lý lỗi hệ thống (Chạy lại Usecase tự động)

---

## 1. Thông tin chức năng

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Xử lý lỗi hệ thống (Chạy lại Usecase tự động) |
| **Mô tả** | Cho phép Đầu mối điều phối kích hoạt chạy lại các usecase tự động (Auto Usecase) bị lỗi hệ thống trong quá trình thực thi chương trình. |
| **Tác nhân** | Admin, Đầu mối điều phối |
| **Tiền điều kiện** | Chương trình đang chạy. Có ít nhất một usecase tự động có trạng thái phiên chạy gần nhất bị lỗi (status = 3 trong program_department_mapping hoặc error trong rule_run khác null). |
| **Hậu điều kiện** | Hệ thống tái khởi động phiên chạy tự động cho usecase lỗi. Trạng thái được cập nhật theo tiến trình chạy mới. |
| **Ngoại lệ** | Không có usecase nào bị lỗi hoặc hệ thống mất kết nối dịch vụ worker thực thi. |
| **Yêu cầu nghiệp vụ** | - Hiển thị danh sách các usecase tự động bị lỗi và chi tiết log lỗi.<br>- Cung cấp nút Chạy lại (Rerun) đối với từng usecase lỗi hoặc chạy lại tất cả usecase lỗi của đơn vị.<br>- Cập nhật trạng thái rule_run thành Khởi tạo/Đang chạy và gọi worker thực thi lại. |

### Luồng sự kiện chính

```mermaid
graph TD
    Start([Bắt đầu]) --> ViewErrors[Xem danh sách Usecase tự động bị lỗi & log lỗi]
    ViewErrors --> ClickRerun[Nhấp nút Chạy lại]
    ClickRerun --> CallWorker[Gọi dịch vụ Worker chạy lại Luật]
    CallWorker --> CheckResponse{Worker phản hồi thành công?}
    CheckResponse -- Thành công --> UpdateStatus[Cập nhật trạng thái rule_run = Khởi tạo & Đang chạy]
    UpdateStatus --> Success[Thông báo: Đang chạy lại usecase tự động]
    CheckResponse -- Thất bại --> Error[Thông báo: Lỗi kết nối máy chủ thực thi!]
    Success --> End([Kết thúc])
    Error --> End
```

---

## 2. Mô tả chi tiết màn hình (Sườn khung giao diện)

### Giao diện thiết kế (Figma UI Export)
*Chưa có hình ảnh giao diện Figma được kết xuất cho màn hình này.*

### Đặc tả các thành phần giao diện
*Ghi chú: Mô tả chi tiết các trường thông tin và thuộc tính điều khiển trên giao diện màn hình chức năng.*

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| 1 | **Bảng danh sách Usecase tự động lỗi** | Table | OUTPUT | Danh sách UC lỗi | Hiển thị danh sách usecase loại Auto bị lỗi, tên lỗi, thời gian xảy ra |
| 2 | **Log lỗi chi tiết** | Label / Textarea (Read-only) | OUTPUT | Lấy từ DB | Hiển thị chi tiết lỗi kỹ thuật của hệ thống. Mapping DB: `rule_run.error` |
| 3 | **Nút Chạy lại** | Button | INPUT | Enable | Kích hoạt gửi tín hiệu cho worker chạy lại Usecase tự động được chọn |
| 4 | **Nút Chạy lại tất cả lỗi của đơn vị** | Button | INPUT | Enable | Kích hoạt chạy lại toàn bộ Usecase tự động lỗi của đơn vị được chọn |
