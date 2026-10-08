# User Stories

## US1 — Đăng nhập phiên giả lập

**Story:** As a Quản trị viên Mini App giả lập, I want to đăng nhập bằng SessionId mock, so that tôi có thể sử dụng các chức năng quản trị local.

**Priority:** Must Have

**Acceptance criteria:**

- AC1.1.1 — Given SessionId mock hợp lệ, When gửi yêu cầu đăng nhập, Then hệ thống tạo phiên Redis và hiển thị trang danh sách.
- AC1.1.2 — Given SessionId không hợp lệ hoặc hết hạn, When gửi yêu cầu, Then hệ thống trả lỗi ổn định và không lộ SessionId.

**Dependencies:** none. **INVEST:** independent entry slice, valuable for access control, estimable, testable.

## US2 — Tạo cấu hình Mini App

**Story:** As a Quản trị viên Mini App giả lập, I want to tạo cấu hình với tên, mã, URL, phiên bản, quyền menu và trạng thái, so that cấu hình được lưu để quản trị.

**Priority:** Must Have

**Acceptance criteria:**

- AC2.1.1 — Given phiên hợp lệ và dữ liệu hợp lệ, When gửi biểu mẫu, Then cấu hình được lưu PostgreSQL và xuất hiện trong danh sách.
- AC2.1.2 — Given mã đã tồn tại hoặc dữ liệu không hợp lệ, When gửi biểu mẫu, Then hệ thống trả lỗi ổn định, giữ dữ liệu đã nhập và không tạo bản ghi mới.
- AC2.1.3 — Given danh sách quyền menu rỗng, When lưu, Then yêu cầu vẫn hợp lệ.

**Dependencies:** US1. **INVEST:** one outcome, valuable, estimable, testable.

## US3 — Xem danh sách và chi tiết

**Story:** As a Quản trị viên Mini App giả lập, I want to xem danh sách và chi tiết cấu hình, so that tôi xác nhận dữ liệu đã lưu.

**Priority:** Must Have

**Acceptance criteria:**

- AC3.1.1 — Given dữ liệu mẫu đã nạp, When mở danh sách, Then ít nhất một Mini App mẫu hiển thị.
- AC3.1.2 — Given chọn một bản ghi, When mở chi tiết, Then các trường đã lưu khớp dữ liệu PostgreSQL.
- AC3.1.3 — Given chưa có bản ghi, When mở vùng danh sách, Then UI hiển thị trạng thái empty.

**Dependencies:** US1, US2. **INVEST:** independent read outcome, valuable, small, testable.

## US4 — Cập nhật cấu hình

**Story:** As a Quản trị viên Mini App giả lập, I want to chỉnh sửa URL, phiên bản, quyền menu, trạng thái và forceUpdate, so that cấu hình phản ánh thay đổi quản trị.

**Priority:** Must Have

**Acceptance criteria:**

- AC4.1.1 — Given bản ghi tồn tại, When lưu thay đổi hợp lệ, Then API cập nhật PostgreSQL và lần đọc sau phản ánh toàn bộ trường mới.
- AC4.1.2 — Given URL hoặc phiên bản không hợp lệ, When lưu, Then hệ thống từ chối và giữ dữ liệu biểu mẫu.

**Dependencies:** US3. **INVEST:** one edit outcome, valuable, estimable, testable.

## US5 — Hiển thị trạng thái UI và phục hồi lỗi

**Story:** As a Quản trị viên Mini App giả lập, I want to thấy loading, success, error và empty rõ ràng, so that tôi biết kết quả thao tác và có thể thử lại.

**Priority:** Should Have

**Acceptance criteria:**

- AC5.1.1 — Given thao tác đang chạy, When chờ phản hồi, Then vùng liên quan hiển thị loading có thể truy cập bằng bàn phím.
- AC5.1.2 — Given thao tác thành công hoặc lỗi, When phản hồi về, Then UI hiển thị trạng thái tương ứng, nhãn trường và thông báo không chỉ dựa vào màu.

**Dependencies:** US1–US4. **INVEST:** testable UI slice.

## US6 — Chạy kịch bản API và reset dữ liệu

**Story:** As a Quản trị viên Mini App giả lập, I want to chạy lại kịch bản login → create → read → update → read và reset dữ liệu, so that tôi có bằng chứng demo xác định.

**Priority:** Must Have

**Acceptance criteria:**

- AC6.1.1 — Given môi trường Compose đã khởi động, When chạy kịch bản với dữ liệu reset, Then các bước login, create, list/detail, update và reread đều cho kết quả dự kiến trong ≤2 giây mỗi request hợp lệ.
- AC6.1.2 — Given chạy lại cùng trạng thái reset, When so sánh kết quả, Then output xác định.
- AC6.1.3 — Given các lỗi SessionId, dữ liệu không hợp lệ và mã trùng, When chạy bước lỗi, Then mã lỗi và phản hồi giữ ổn định.

**Dependencies:** US1–US4. **INVEST:** valuable evidence slice, independently repeatable, testable.

## Priority notes

Could Have: tìm kiếm/lọc. Won't Have: runtime Mini App, WebView, device cache, BIZ integration and cloud deployment.
