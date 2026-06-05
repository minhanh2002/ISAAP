# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS) - CHỨC NĂNG: BẮT ĐẦU ĐÁNH GIÁ (CHẠY CHƯƠNG TRÌNH)

**DỰ ÁN: NỀN TẢNG QUẢN LÝ TUÂN THỦ AN TOÀN THÔNG TIN (ISAAP)**
**PHÂN HỆ: QUẢN LÝ & CHẠY CHƯƠNG TRÌNH ĐÁNH GIÁ**

---

### Hà Nội, 06 - 2026

---

## BẢNG GHI NHẬN THAY ĐỔI

| Ngày thay đổi | Vị trí thay đổi | A/M/D (*) | Nguồn gốc | Phiên bản cũ | Mô tả thay đổi | Phiên bản mới |
| :--- | :--- | :---: | :--- | :--- | :--- | :--- |
| 05/06/2026 | Toàn bộ tài liệu | M | Yêu cầu người dùng | V1.0 | Cập nhật định dạng tài liệu, viết lại nội dung bằng ngôn ngữ nghiệp vụ, bổ sung xử lý sinh Usecase thủ công và kích hoạt Usecase tự động. | V2.0 |

*Ghi chú ký hiệu (\*):*
- **A\***: Add (Tạo mới)
- **M**: Modify (Sửa đổi)
- **D**: Delete (Xóa bỏ)

### 3.1.1. Thông tin chung & Phân quyền
- **Tên chức năng cha**: Chương trình đánh giá
- **Mục đích**: Cho phép kích hoạt chạy chương trình đánh giá, phân bổ nhiệm vụ nộp sở cứ và kích hoạt các kịch bản đánh giá tự động.
- **Tác nhân**: Admin nghiệp vụ, nhân sự phụ trách ATTT của các đơn vị trong Tập đoàn. Chú ý, admin hệ thống có quyền thực hiện mọi hành động trong hệ thống nhưng không tham gia trực tiếp vào quy trình nghiệp vụ.
- **Phân quyền**: Người dùng được gán nhóm quyền với Mã chức năng và Mã thao tác như bảng dưới:

| Mã chức năng | Mã thao tác |
| :--- | :--- |
| EVALUATION_PROGRAM_MANAGEMENT | START |

---

### 3.1.4. Bắt đầu đánh giá (Chạy chương trình)

#### 3.1.4.1. Thông tin chung

| Thuộc tính | Mô tả chi tiết |
| :--- | :--- |
| **Tên chức năng** | Bắt đầu đánh giá |
| **Mô tả** | Chức năng cho phép người quản trị kích hoạt bắt đầu một chương trình đánh giá mới. Khi bắt đầu, hệ thống sẽ tự động giao việc thu thập sở cứ thủ công về cho các đơn vị, đồng thời khởi chạy các công cụ quét tự động để đánh giá các hệ thống của đơn vị đó. |
| **Tác nhân** | Người dùng thuộc nhóm Admin hệ thống<br>hoặc<br>Người dùng khác nhóm quyền admin hệ thống nhưng được phân bổ vai trò là Đầu mối điều phối của chương trình đánh giá đó |
| **Điều kiện trước** | Chương trình đánh giá đang ở trạng thái "Chưa đánh giá". |
| **Điều kiện sau** | - Trạng thái của chương trình được chuyển sang "Đang đánh giá".<br>- Hệ thống tự động sinh danh sách các nhiệm vụ nộp sở cứ thủ công (Usecase thủ công) giao cho các Đầu mối đơn vị ở trạng thái "Chưa nộp sở cứ".<br>- Hệ thống tự động khởi tạo các phiên chạy tự động (Usecase tự động) để quét dữ liệu. |
| **Ngoại lệ** | - Trạng thái chương trình đã bị thay đổi, không còn nằm ở trạng thái khởi tạo ("Chưa đánh giá").<br>- Hệ thống gặp lỗi trong quá trình khởi tạo dữ liệu hàng loạt. |
| **Các yêu cầu đặc biệt** | - Khối lượng sinh dữ liệu Usecase là rất lớn đối với các chương trình có nhiều đơn vị. Hệ thống cần đảm bảo tính đồng bộ (Transaction) - một là sinh thành công tất cả, hai là hoàn tác toàn bộ nếu có lỗi để tránh dư thừa rác dữ liệu. |

**Sơ đồ luồng xử lý chức năng:**

```mermaid
graph TD
    Start([Bắt đầu]) --> ClickStart[Người dùng nhấn biểu tượng Bắt đầu đánh giá]
    ClickStart --> CheckConditions{Trạng thái hợp lệ?}
    
    CheckConditions -- Không hợp lệ --> ShowErrorStatus[Hệ thống báo lỗi trạng thái]
    ShowErrorStatus --> End([Kết thúc])
    
    CheckConditions -- Hợp lệ --> ShowPopup[Hệ thống hiển thị Popup Xác nhận Bắt đầu]
    ShowPopup --> ClickConfirm{Người dùng chọn thao tác?}
    
    ClickConfirm -- Chọn Hủy --> ClosePopup[Đóng Popup, hủy thao tác]
    ClosePopup --> End
    
    ClickConfirm -- Chọn Xác nhận --> UpdateStatus[Hệ thống lưu trạng thái Đang đánh giá]
    UpdateStatus --> GenManual[Sinh dữ liệu Usecase thủ công cho các đơn vị]
    GenManual --> GenAuto[Khởi tạo các phiên chạy Usecase tự động]
    GenAuto --> ValidateProcess{Có lỗi xảy ra?}
    
    ValidateProcess -- Có lỗi --> Rollback[Hoàn tác, báo lỗi hệ thống]
    Rollback --> End
    
    ValidateProcess -- Thành công --> ShowSuccess[Thông báo chạy chương trình thành công]
    ShowSuccess --> End
```

#### 3.1.4.2. Màn hình thiết kế (UI Layout)

![Giao diện Xác nhận bắt đầu](../UI/images/Bat_Dau/Popup_Bat_Dau.png)

#### 3.1.4.3. Đặc tả chi tiết các thành phần giao diện

| STT | Thành phần | Kiểu dữ liệu | I/O | Giá trị khởi tạo | Mô tả chi tiết (Mapping CSDL & Thao tác Button) |
| :---: | :--- | :--- | :---: | :--- | :--- |
| **I. Màn hình danh sách (Icon chức năng)** | | | | | |
| 1 | **Biểu tượng Bắt đầu đánh giá** | Icon | Input | Hiển thị/Ẩn | - Chỉ hiển thị/enable khi chương trình ở trạng thái Chưa đánh giá (`status` = 0) và người dùng có quyền thao tác.<br>- Click icon để mở Popup Xác nhận bắt đầu. |
| **II. Popup Xác nhận Bắt đầu** | | | | | |
| 2 | **Nội dung cảnh báo** | Text | Output | N/A | - Tiêu đề: "Xác nhận bắt đầu đánh giá"<br>- Nội dung: "Bạn có chắc chắn muốn bắt đầu đánh giá chương trình này? Hệ thống sẽ giao việc cho các đơn vị và bắt đầu chạy các tác vụ tự động." |
| 3 | **Nút Hủy** | Button | Input | Enable | - Click để đóng popup, hủy bỏ thao tác. |
| 4 | **Nút Xác nhận** | Button | Input | Enable | - Click để thực hiện gửi yêu cầu Bắt đầu chương trình lên máy chủ.<br>- Xử lý CSDL đồng bộ:<br>  + Cập nhật `evaluation_program.status` = 1 (Đang đánh giá).<br>  + Khởi tạo bản ghi vào `usecase_manual_review_mapping` (status = 0: Chưa nộp sở cứ).<br>  + Khởi tạo bản ghi vào `rule_run` (phiên chạy tự động). |

#### 3.1.4.4. Luồng nghiệp vụ
- **Bước 1**: Người dùng đăng nhập và truy cập vào màn hình Danh sách chương trình đánh giá.
- **Bước 2**: Tại dòng dữ liệu của một chương trình ở trạng thái "Chưa đánh giá", người dùng nhấn vào biểu tượng **[Bắt đầu đánh giá]**.
- **Bước 3**: Hệ thống (Frontend) và API gọi kiểm tra tiền điều kiện để xử lý thao tác bắt đầu:
  - **Trường hợp lỗi 1 (Trạng thái chương trình không hợp lệ)**: Nếu chương trình không còn ở trạng thái "Chưa đánh giá" (ví dụ đã bị admin khác chạy trước đó), hệ thống hiển thị thông báo lỗi (Toast đỏ): `"Chương trình không ở trạng thái cho phép bắt đầu. Vui lòng tải lại trang."` và chặn thao tác.
  - **Trường hợp lỗi 2 (Thiếu quyền hạn thao tác)**: Nếu người dùng bị mất phân quyền đột xuất, hệ thống hiển thị lỗi: `"Bạn không có quyền thực hiện thao tác bắt đầu chương trình này."`
  - **Trường hợp Hợp lệ**: Nếu vượt qua kiểm tra, hệ thống hiển thị Popup Xác nhận bắt đầu đánh giá.
- **Bước 4**: Tại Popup Xác nhận:
  - Nếu người dùng chọn nút **[Hủy]**, hệ thống đóng Popup và không làm gì thêm.
  - Nếu người dùng chọn nút **[Xác nhận]**, hệ thống gửi yêu cầu Bắt đầu chương trình lên máy chủ.
- **Bước 5**: Hệ thống (Server) xử lý nghiệp vụ sinh dữ liệu:
  - Hệ thống cập nhật trạng thái của chương trình thành "Đang đánh giá" (`status` = 1).
  - Hệ thống tự động phân bổ và **sinh hàng loạt các bản ghi Usecase thủ công** cho tất cả các đơn vị tham gia. Các bản ghi này được khởi tạo với trạng thái ban đầu là "Chưa nộp sở cứ", mục đích để các Đầu mối đơn vị bắt đầu vào hệ thống để đính kèm minh chứng.
  - Đồng thời, hệ thống tự động **sinh các phiên chạy Usecase tự động** (các lịch chạy quét lỗ hổng/thu thập cấu hình) đẩy vào hàng đợi của hệ thống để bắt đầu thực thi ngầm.
  - **Trường hợp lỗi 3 (Lỗi tạo dữ liệu/Máy chủ)**: Nếu trong quá trình sinh hàng loạt Usecase xảy ra sự cố (timeout, đứt kết nối CSDL), hệ thống sẽ hoàn tác (Rollback) toàn bộ quá trình, giữ nguyên chương trình ở trạng thái "Chưa đánh giá" và hiển thị thông báo lỗi: `"Quá trình khởi tạo dữ liệu đánh giá gặp sự cố. Vui lòng thử lại sau."`
  - **Thành công**: Cập nhật hoàn tất, hệ thống đóng popup, tải lại danh sách chương trình và hiển thị thông báo (Toast xanh): `"Thành công. Chương trình đã bắt đầu đánh giá."`
