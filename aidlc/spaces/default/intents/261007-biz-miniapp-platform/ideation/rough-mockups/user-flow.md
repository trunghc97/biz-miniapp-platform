# Luồng người dùng — Demo quản trị Mini App

## Phạm vi và nguồn đầu vào

Luồng này mô tả thao tác trong giao diện quản trị và lời gọi API mock, theo [scope-document.md](../scope-definition/scope-document.md) và các lát cắt U1–U5 trong [intent-backlog.md](../scope-definition/intent-backlog.md). Mục tiêu kinh doanh và yêu cầu ban đầu được đối chiếu với [intent-statement.md](../intent-capture/intent-statement.md); lựa chọn giao diện lấy từ [rough-mockups-questions.md](rough-mockups-questions.md).

## Luồng chính — Đăng nhập, tạo và cập nhật Mini App

~~~text
[Bat dau demo]
      |
      v
[Dang nhap bang tai khoan gia lap]
      |
      +---- loi xac thuc/API ----> [Hien loi va cho thu lai]
      |
      v
[Nhan SessionId mock; mo Quan ly Mini App]
      |
      +---- API loi tai danh sach --> [Hien loi + Thu lai]
      |
      v
[Danh sach rong hoac co Mini App mau]
      |
      +---- Dang ky moi ------------+
      |                              |
      +---- Sua cau hinh mau --------+
                                     |
                                     v
                         [Nhap thong tin va quyen menu]
                                     |
                           [Kiem tra du lieu tren form]
                                     |
                       +-------------+-------------+
                       |                           |
                  [Du lieu loi]              [Du lieu hop le]
                       |                           |
             [Gan loi duoi truong]       [Goi API luu cau hinh]
                       |                           |
                       +---- sua lai               +---- API loi
                                                   |      [Giu du lieu,
                                                   |       bao loi/thu lai]
                                                   v
                                        [Thong bao da luu]
                                                   |
                                                   v
                                    [Kiem tra cau hinh bang API]
                                                   |
                                                   v
                              [Doi version hoac forceUpdate]
                                                   |
                                                   v
                               [Luu, goi API va doc lai cau hinh]
~~~

Luồng văn bản: mở trang đăng nhập giả lập → nhận SessionId mock → xem danh sách Mini App → đăng ký mới hoặc sửa mẫu → nhập thông tin/quyền menu/trạng thái/version/forceUpdate → lưu qua API mock → đọc lại và đối chiếu kết quả.

## Các nhánh và phục hồi lỗi

| Tình huống | Phản hồi giao diện/API | Cách tiếp tục |
|---|---|---|
| SessionId giả lập không hợp lệ hoặc hết hạn | Thông báo phiên không hợp lệ; không lộ giá trị SessionId. | Đăng nhập lại bằng tài khoản giả lập. |
| Dịch vụ danh sách không sẵn sàng | Trạng thái lỗi tại vùng nội dung, có nút thử lại. | Khởi động dịch vụ mock hoặc thử lại lời gọi. |
| Mã Mini App đã tồn tại | Lỗi gắn với trường mã; dữ liệu khác vẫn được giữ. | Sửa mã rồi gửi lại. |
| URL hoặc phiên bản không hợp lệ | Giải thích định dạng cần nhập ngay dưới trường. | Sửa trường được nêu. |
| Lưu cấu hình thất bại | Thông báo thao tác chưa hoàn tất; biểu mẫu giữ nguyên dữ liệu. | Thử gửi lại sau khi API mock sẵn sàng. |
| Người dùng hủy biểu mẫu | Hỏi xác nhận nếu có thay đổi chưa lưu. | Ở lại biểu mẫu hoặc bỏ thay đổi để về danh sách. |

## Ranh giới kiểm chứng

- Kịch bản kiểm tra việc lưu và đọc lại cấu hình từ API mock, gồm quyền menu, trạng thái, phiên bản và forceUpdate.
- Kịch bản không mở Mini App bên trong BIZ và không kiểm tra việc tải tài nguyên, cache hay cập nhật trên thiết bị.
- Kết quả chỉ chứng minh luồng demo cục bộ; không chứng minh tương thích với API hoặc dự án đang vận hành.

## Sources

- [scope-document.md](../scope-definition/scope-document.md) — ranh giới của demo và phương thức kiểm chứng.
- [intent-backlog.md](../scope-definition/intent-backlog.md) — U1–U5 và trình tự phụ thuộc.
- [intent-statement.md](../intent-capture/intent-statement.md) — yêu cầu ban đầu về đăng nhập, quản trị và cập nhật cấu hình.
- [wireframes.md](wireframes.md) — màn hình và trạng thái giao diện.
- [rough-mockups-questions.md](rough-mockups-questions.md) — các lựa chọn đã xác nhận.

## Assumptions & Open Questions

- Thông tin tài khoản giả lập và cách cấp SessionId mock sẽ được xác định trong thiết kế API.
- Demo cần có dữ liệu khởi tạo cho một Mini App mẫu; nội dung cụ thể sẽ được chốt khi thiết kế chức năng.
