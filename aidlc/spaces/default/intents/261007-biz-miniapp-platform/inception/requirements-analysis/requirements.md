# Phân tích yêu cầu — BIZ Mini App Platform

## Intent analysis

Mục tiêu của MVP là chứng minh một cổng quản trị Mini App chạy local, có thể đăng ký và cập nhật cấu hình bằng API mock mà không sửa hoặc phát hành lại ứng dụng BIZ. Bản demo ưu tiên lát cắt đầu-cuối có thể lặp lại: đăng nhập giả lập, tạo cấu hình, lưu/đọc PostgreSQL và kiểm tra phiên giả lập trong Redis.

## Functional requirements

### Quản trị cấu hình Mini App

- FR1: Quản trị viên giả lập có thể đăng nhập bằng SessionId mock.
- FR1.1: Hệ thống phải nhận diện một vai trò quản trị giả lập duy nhất cho các thao tác trong demo.
- FR1.2: Hệ thống phải từ chối SessionId không hợp lệ hoặc hết hạn bằng mã lỗi ổn định.
- FR2: Quản trị viên có thể tạo cấu hình Mini App.
- FR2.1: Cấu hình phải có tên, mã, URL truy cập và phiên bản.
- FR2.2: Cấu hình có thể có danh sách quyền menu rỗng, trạng thái bật/tắt và cờ `forceUpdate`.
- FR2.3: Mã Mini App phải duy nhất; hệ thống từ chối mã trùng mà không làm mất dữ liệu đã nhập.
- FR3: Quản trị viên có thể xem danh sách và chi tiết cấu hình Mini App.
- FR3.1: MVP phải hiển thị ít nhất Mini App mẫu sau khi dữ liệu mẫu được nạp.
- FR3.2: Tìm kiếm và lọc là Could Have, không phải điều kiện bắt buộc của MVP.
- FR4: Quản trị viên có thể cập nhật tên, URL, phiên bản, quyền menu, trạng thái và `forceUpdate`.
- FR4.1: URL phải được kiểm tra định dạng trước khi lưu.
- FR4.2: Phiên bản phải theo định dạng có thể so sánh để hỗ trợ kiểm tra thay đổi cấu hình.
- FR5: API phải trả mã lỗi ổn định cho xác thực thất bại, SessionId hết hạn, thiếu quyền, dữ liệu không hợp lệ và mã trùng.
- FR5.1: Phản hồi lỗi phải giữ dữ liệu biểu mẫu để người dùng thử lại.
- FR6: Kịch bản kiểm chứng có thể chạy lại phải thực hiện đăng nhập, tạo, đọc danh sách/chi tiết, cập nhật quyền/trạng thái/phiên bản/`forceUpdate`, đọc lại và kiểm tra lỗi chính.
- FR7: Hệ thống phải lưu cấu hình trong PostgreSQL và đọc lại đúng các trường đã lưu.
- FR8: SessionId mock và quyền menu mock phải được lưu/đọc từ Redis ở mức cần thiết cho kịch bản quản trị.
- FR9: Dữ liệu demo phải có lệnh hoặc hướng dẫn để nạp lại và reset xác định.

### Giao diện quản trị

- FR10: Giao diện phải có màn hình đăng nhập giả lập, danh sách Mini App và biểu mẫu tạo/sửa.
- FR10.1: Giao diện phải hiển thị trạng thái loading, success, error và empty cho các vùng chính.
- FR10.2: Giao diện không được dẫn tới runtime Mini App hoặc tích hợp BIZ.

## Non-functional requirements

- NFR1: Trong điều kiện demo local, request hợp lệ phải có phản hồi trong tối đa 2 giây cho kịch bản API đã định nghĩa.
- NFR2: Mỗi lần chạy kịch bản API phải cho kết quả xác định khi dùng cùng dữ liệu giả lập và trạng thái reset.
- NFR3: Mã lỗi, dữ liệu phản hồi và các bước phục hồi phải được kiểm thử bằng unit, integration và API scenario theo Test Strategy Standard.
- NFR4: Mã backend/frontend thuộc MVP phải đạt tối thiểu 80% line coverage; loại trừ mã sinh tự động và fixture.
- NFR5: Giao diện phải đáp ứng WCAG 2.1 AA cơ bản: thao tác bàn phím, nhãn trường, thứ bậc tiêu đề, lỗi không chỉ dùng màu và vùng thông báo trạng thái.
- NFR6: Không phản hồi hoặc ghi log SessionId, secret, connection string hay stack trace cho người dùng.
- NFR7: Dịch vụ mock, Redis và PostgreSQL phải khởi động được bằng Docker Compose trên máy demo không cần cloud.
- NFR8: Cấu hình formatter, linter và dependency check phải được commit và chạy trước merge.

## Constraints

- Backend bắt buộc dùng Java 21 và Spring Boot 4.
- Demo chỉ dùng tài khoản, dữ liệu, Redis, PostgreSQL và API mock riêng; không kết nối hệ thống ngân hàng thật.
- Phạm vi là quản trị Mini App và kiểm chứng API; không triển khai runtime, WebView, tải/cache tài nguyên trên thiết bị hoặc cập nhật trong BIZ.
- Không triển khai cloud hoặc production trong MVP.
- Làm việc theo nhánh ngắn từ `main`, review và squash merge về `main`.

## Assumptions

- Máy demo có Docker Compose và đủ tài nguyên chạy backend mock, Redis và PostgreSQL.
- Một vai trò quản trị giả lập là đủ cho kịch bản hiện tại.
- Hợp đồng API, quy tắc SessionId và quyền chính thức của các dự án BIZ thật sẽ được khảo sát riêng trước tích hợp.

## Out of scope

- Runtime nhúng, WebView, tải Mini App động, cache trên thiết bị và force update khi mở ứng dụng BIZ.
- Kết nối hoặc tái sử dụng endpoint, tài khoản, dữ liệu hay Redis/PostgreSQL production.
- Tìm kiếm/lọc bắt buộc, audit log giao diện, nhiều Mini App mẫu và triển khai cloud.

## Open questions

- Công cụ formatter, linter và dependency check cụ thể sẽ được chọn khi tạo cấu trúc build.
- Vai trò reviewer và nền tảng CI cụ thể chưa được đặt tên.
- Hợp đồng tích hợp với dự án BIZ thực tế chưa có, nên chưa thể xác nhận tương thích.

## Sources

- [intent-statement.md](../../ideation/intent-capture/intent-statement.md)
- [scope-document.md](../../ideation/scope-definition/scope-document.md)
- [team-practices.md](../practices-discovery/team-practices.md)
- [requirements-analysis-questions.md](requirements-analysis-questions.md)
