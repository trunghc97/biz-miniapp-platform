# Thực hành nhóm — BIZ Mini App Platform

## Way of Working

- Làm việc trên các nhánh ngắn từ `main`, review bởi người phụ trách và squash về `main`.
- CI chạy formatter, kiểm thử và các kiểm tra chất lượng trước merge.
- Mỗi thay đổi giữ phạm vi nhỏ, có thể truy nguyên tới một lát cắt hoặc yêu cầu.

## Walking Skeleton

- Bắt đầu bằng lát cắt đầu-cuối tối thiểu: đăng nhập giả lập → giao diện tạo cấu hình Mini App → API lưu PostgreSQL → đọc lại cấu hình, với phiên giả lập trong Redis.
- Chỉ mở rộng sau khi lát cắt này chạy được bằng Docker Compose và có bằng chứng API lặp lại được.
- Không đưa runtime Mini App hoặc tích hợp BIZ vào bản demo hiện tại.

## Testing Posture

- **Methodology**: test-after
- **Ordering**: Triển khai từng lớp có thể kiểm thử, sau đó viết và chạy kiểm thử cho lớp đó.
- Giữ Test Strategy Standard và sàn 80% line coverage cho mã backend/frontend thuộc MVP; loại trừ mã sinh tự động và fixture.
- Bao gồm unit test, tích hợp Redis/PostgreSQL và kịch bản API quản trị có kết quả xác định.
- CI chạy kiểm tra trước merge; phạm vi CI không bao gồm triển khai staging/cloud cho bản demo.

## Deployment

- Demo chạy local bằng Docker Compose với backend mock dạng microservice, Redis và PostgreSQL.
- Dự án có hướng dẫn hoặc lệnh có phiên bản để khởi động Compose, nạp dữ liệu mẫu, chạy kịch bản API và reset dữ liệu.
- Không kết nối hệ thống ngân hàng thật, không dùng tài khoản thật và không tạo nghĩa vụ triển khai production.

## Code Style

- Backend dùng Java 21 và Spring Boot 4.
- Cấu hình formatter, linter và dependency check được commit cùng dự án và chạy trong CI.
- Tổ chức theo capability quản trị Mini App, với ranh giới rõ giữa API, nghiệp vụ, persistence và truy cập phiên giả lập.
- DTO nằm ở biên API; lỗi trả về ổn định, không lộ SessionId, secret hay stack trace.
