# Quy tắc được xác nhận

## Mandated

- ALWAYS dùng dữ liệu, tài khoản và API giả lập trong bản demo local.
- ALWAYS chạy kiểm tra formatter, kiểm thử và dependency check trước merge.
- ALWAYS giữ lát cắt đầu-cuối quản trị Mini App làm bằng chứng đầu tiên trước khi mở rộng.
- ALWAYS che giấu SessionId, secret, connection string và stack trace trong phản hồi lỗi.

## Forbidden

- NEVER kết nối bản demo tới ứng dụng BIZ, Redis, PostgreSQL hoặc API ngân hàng đang vận hành.
- NEVER mở rộng bản demo thành runtime tải/cache Mini App hoặc triển khai cloud/production.
- NEVER hạ sàn 80% line coverage để làm cho bước kiểm tra đạt.
