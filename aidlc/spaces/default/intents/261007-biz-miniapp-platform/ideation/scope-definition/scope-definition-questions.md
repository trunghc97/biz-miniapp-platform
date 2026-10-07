# Câu hỏi xác định phạm vi — BIZ Mini App Platform

Các câu trả lời trước đã xác nhận dùng API giả lập, Docker Compose, dữ liệu giả lập, triển khai phần quản trị Mini App và không tích hợp vào ứng dụng BIZ đang chạy. Các câu hỏi dưới đây chỉ làm rõ ranh giới đầu ra và thứ tự ưu tiên.

## Q1. Đầu ra của bản demo gồm những phần nào?

Để tránh hiểu khác nhau giữa “thiết kế API trước” và “dựng phần quản trị Mini App”, hãy chọn phạm vi đầu ra cần hoàn thành trên máy demo.

- A. Chỉ tài liệu thiết kế API; chưa làm giao diện quản trị hay backend chạy được.
- B. Giao diện quản trị Mini App và backend API giả lập chạy cục bộ; kiểm chứng các luồng quản trị bằng cách gọi API.
- C. Chỉ backend API giả lập chạy cục bộ, chưa làm giao diện quản trị.
- X. Other (please specify)

[Answer]: B

## Q2. Thứ tự ưu tiên khi triển khai phạm vi đã chọn là gì?

Thứ tự này sẽ quyết định cách chia các phần việc và kịch bản demo.

- A. Ưu tiên thiết kế và kiểm chứng hợp đồng API trước, sau đó hoàn thiện giao diện quản trị.
- B. Ưu tiên hoàn tất luồng quản trị Mini App đầu-cuối, gồm giao diện và API.
- C. Ưu tiên hạ tầng Docker Compose và dịch vụ mock trước, rồi mới làm luồng quản trị.
- X. Other (please specify)

[Answer]: B

## Consolidated Summary Confirmation

Tôi đã tổng hợp phạm vi để tạo tài liệu định nghĩa phạm vi và backlog. Hãy kiểm tra câu trả lời và bản tóm tắt sau:

- Bản demo gồm giao diện quản trị Mini App và backend API giả lập chạy cục bộ; kiểm chứng luồng quản trị bằng cách gọi API.
- Ưu tiên hoàn tất luồng quản trị đầu-cuối gồm giao diện và API.
- Dùng Docker Compose để chạy các dịch vụ backend mock dạng microservice, Redis và PostgreSQL; toàn bộ tài khoản và dữ liệu là giả lập.
- Chỉ làm phần quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy. Không xây dựng/tích hợp runtime tải Mini App trong demo này.
- Dùng Java 21 và Spring Boot 4 cho backend mock. Đầu ra trước mắt tập trung vào thiết kế API, sau đó triển khai demo đã chốt ở trên.
- Khi làm thật, phát triển bổ sung trên các dự án hiện có và đối chiếu hợp đồng với API/xác thực/quyền của chúng; việc tương thích chưa được xác minh.

Does this all look correct before I generate the artifact?

- Looks correct
- Request changes

[Answer]: Looks correct
