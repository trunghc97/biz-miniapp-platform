# Wireframe sơ bộ — Cổng quản trị Mini App

## Mục đích và nguồn đầu vào

Wireframe mô tả giao diện quản trị demo được xác định trong [scope-document.md](../scope-definition/scope-document.md) và ưu tiên trong [intent-backlog.md](../scope-definition/intent-backlog.md). Các nhu cầu ban đầu được đối chiếu với [intent-statement.md](../intent-capture/intent-statement.md); lựa chọn phong cách, thiết bị và đăng nhập được ghi tại [rough-mockups-questions.md](rough-mockups-questions.md).

Đây là phác thảo cấu trúc, không phải thiết kế thương hiệu hoặc giao diện hoàn chỉnh. Cổng chạy trên trình duyệt; các trường và trạng thái chỉ thao tác với API mock.

## Kiến trúc thông tin

- **Đăng nhập**: truy cập demo bằng thông tin giả lập để nhận SessionId mock.
- **Quản lý Mini App**: danh sách, tìm kiếm theo tên/mã, lọc trạng thái, tạo mới và mở cấu hình.
- **Cấu hình Mini App**: tên, mã, URL truy cập, phiên bản, quyền menu, trạng thái bật/tắt và cập nhật bắt buộc.
- **Phản hồi thao tác**: trạng thái đang tải, thành công, lỗi nhập liệu, lỗi API và không có dữ liệu.

## Màn hình 1 — Đăng nhập giả lập

| Vùng | Nội dung và hành vi |
|---|---|
| Đầu trang | Tên demo “BIZ Mini App Platform” và nhãn “Môi trường giả lập”. |
| Nội dung chính | Tiêu đề “Đăng nhập quản trị”; trường mã người dùng giả lập; trường mật khẩu giả lập; nút “Đăng nhập”. |
| Gợi ý | Thông báo đây là tài khoản thử nghiệm; không yêu cầu hoặc chấp nhận thông tin đăng nhập thật. |
| Đang gửi | Nút chuyển sang “Đang đăng nhập…” và không nhận gửi lặp. |
| Thành công | Nhận SessionId mock và chuyển tới “Quản lý Mini App”. |
| Lỗi | Hiện mô tả tiếng Việt ngay dưới biểu mẫu; giữ mã người dùng để sửa và cho phép thử lại. Không hiện token hoặc stack trace. |

**Ghi chú trợ năng:** một tiêu đề h1; vùng nội dung chính dùng main; mọi trường có nhãn hiển thị và liên kết với thông báo lỗi; Tab đi theo thứ tự mã người dùng → mật khẩu → Đăng nhập; Enter gửi biểu mẫu; trạng thái kết quả được thông báo bằng vùng live.

## Màn hình 2 — Danh sách Mini App

| Vùng | Nội dung và hành vi |
|---|---|
| Thanh đầu | Tên cổng; người quản trị giả lập; trạng thái “API mock”; nút “Đăng xuất”. |
| Điều hướng bên | Mục “Quản lý Mini App” được đánh dấu đang chọn. Không thêm mục dẫn tới runtime BIZ. |
| Tiêu đề nội dung | h1 “Quản lý Mini App”; mô tả ngắn về các cấu hình trong môi trường demo; nút chính “Đăng ký Mini App”. |
| Tìm và lọc | Ô tìm theo tên/mã; bộ lọc trạng thái “Tất cả / Đang bật / Đang tắt”; nút xóa bộ lọc. |
| Bảng danh sách | Tên, mã, phiên bản, quyền menu, trạng thái, cập nhật bắt buộc và hành động “Sửa”. |
| Rỗng | “Chưa có Mini App”; nút “Đăng ký Mini App” là hành động chính. |
| Đang tải | Hiển thị khung chờ trong vùng bảng và giữ thanh điều hướng ổn định. |
| Lỗi tải | Nêu rằng không lấy được danh sách từ API mock; nút “Thử lại”. |
| Danh sách dài | Phân trang và hiển thị tổng số mục; giữ bộ lọc khi đổi trang. |

**Ghi chú trợ năng:** một tiêu đề h1; header, nav, main có cấu trúc rõ; bảng dùng tiêu đề cột; nút có tên mô tả; Tab bắt đầu từ liên kết bỏ qua điều hướng rồi đến nút chính, bộ lọc và các hàng. Trạng thái bật/tắt có chữ đi kèm biểu tượng, không dựa riêng vào màu.

## Màn hình 3 — Đăng ký / chỉnh sửa Mini App

| Nhóm trường | Thành phần và quy tắc hiển thị |
|---|---|
| Thông tin cơ bản | Tên Mini App; mã duy nhất; URL truy cập; phiên bản. |
| Quyền truy cập | Danh sách quyền menu giả lập; nhãn giải thích cấu hình này phục vụ kiểm chứng API mock và chưa quyết định hiển thị menu trong ứng dụng BIZ. |
| Trạng thái | Công tắc “Đang bật”; trạng thái được thể hiện bằng chữ “Bật/Tắt”. |
| Cập nhật | Công tắc “Yêu cầu cập nhật bắt buộc”; giải thích đây là dữ liệu cấu hình, không kích hoạt tải hoặc cập nhật ứng dụng trong demo. |
| Hành động cuối trang | “Lưu cấu hình” là nút chính; “Hủy” quay lại danh sách và bỏ thay đổi chưa lưu. |
| Kiểm tra dữ liệu | Tên, mã, URL và phiên bản bắt buộc; mã được chuẩn hóa và không trùng; URL phải đúng định dạng. Lỗi đặt dưới trường tương ứng. |
| Đang lưu | Khóa gửi lặp, giữ dữ liệu đã nhập và báo trạng thái đang lưu. |
| Thành công | Thông báo “Đã lưu cấu hình”; quay lại danh sách và hiển thị phiên bản/trạng thái mới. |
| Lỗi API | Giữ dữ liệu biểu mẫu; nêu bước có thể thử tiếp theo; không xóa nội dung đã nhập. |

**Ghi chú trợ năng:** một tiêu đề h1 và các tiêu đề h2 cho từng nhóm; header/nav/main/footer có thứ bậc; nhãn hiển thị cho mọi trường, nhóm quyền dùng fieldset/legend, công tắc có tên và trạng thái đọc được; Tab theo thứ tự từ trên xuống, nút Hủy và Lưu ở cuối; lỗi gắn với trường qua mô tả trợ năng.

## Hành vi hiển thị chung

- Giao diện trung tính, độ tương phản rõ, phù hợp môi trường quản trị ngân hàng nhưng không giả lập nhận diện thương hiệu BIZ.
- Ưu tiên bố cục máy tính; ở máy tính bảng, thanh điều hướng có thể thu gọn và biểu mẫu chuyển thành một cột.
- Các thao tác chính dùng văn bản tiếng Việt; tên kỹ thuật như SessionId, URL, API và forceUpdate chỉ xuất hiện khi hữu ích và có giải thích.
- Mọi chức năng thao tác được bằng bàn phím; chỉ dùng phần tử HTML ngữ nghĩa và hiển thị đường viền focus.
- Màu trạng thái luôn đi cùng nhãn chữ; thông báo lỗi chỉ rõ vấn đề và cách khắc phục.
- Nội dung cập nhật bất đồng bộ được thông báo cho trình đọc màn hình; không tự chuyển trang trước khi người dùng đọc được kết quả.

## Sources

- [scope-document.md](../scope-definition/scope-document.md) — đối tượng, ranh giới demo, tiêu chí thành công và phần loại trừ.
- [intent-backlog.md](../scope-definition/intent-backlog.md) — luồng quản trị và các hạng mục Must Have.
- [intent-statement.md](../intent-capture/intent-statement.md) — khả năng quản trị được yêu cầu ban đầu.
- [rough-mockups-questions.md](rough-mockups-questions.md) — lựa chọn giao diện trung tính, thiết bị và đăng nhập mock.

## Assumptions & Open Questions

- Chưa có bộ quy chuẩn giao diện BIZ; wireframe không tuyên bố là bản sao nhận diện BIZ.
- Quy tắc định dạng URL, phiên bản và mã duy nhất cần được chốt trong thiết kế chức năng/API.
- Vai trò và quyền quản trị thật chưa được cung cấp; các quyền hiển thị tại đây là dữ liệu giả lập.
