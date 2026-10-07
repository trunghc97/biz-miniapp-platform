# Danh sách ràng buộc — BIZ Mini App Platform

## Ràng buộc đã xác nhận

| ID | Ràng buộc | Tác động | Nguồn |
|---|---|---|---|
| CON-1 | Backend demo dùng Java 21 và Spring Boot 4. | Hợp đồng và phần backend giả lập cần tương thích với nền tảng đã chỉ định. | [Q3] |
| CON-2 | Mọi API trên máy demo là API giả lập; không kết nối API thật. | Bản demo chỉ chứng minh luồng và hợp đồng dự kiến, không chứng minh tích hợp hoặc dữ liệu từ hệ thống ngân hàng. | [desc] [Q2] |
| CON-3 | Tài khoản và dữ liệu sử dụng trong demo đều giả lập. | Không dùng thông tin khách hàng thật trong phạm vi demo được xác nhận. | [Q4] |
| CON-4 | Demo mô phỏng mô hình đăng nhập SessionId; Docker Compose dựng backend mock dạng microservice, Redis và PostgreSQL cho demo. | Dịch vụ cục bộ và dữ liệu giả lập chỉ phục vụ demo, tách khỏi dự án đang vận hành. | [desc] [Q2] |
| CON-5 | Dùng Docker Compose trên máy phát triển để dựng backend mock, Redis và PostgreSQL; không cần tài khoản cloud. | Ưu tiên chạy local/container; chưa có yêu cầu hoặc phê duyệt triển khai cloud. | [Q5] |
| CON-6 | Ưu tiên không phát sinh chi phí cloud; chưa có hạn chót cố định. | Không thể dùng giả định về ngân sách hay ngày bàn giao để đánh giá thêm. | [Q6] |
| CON-7 | Việc cần làm trước mắt là thiết kế API; chưa chốt nền tảng di động. | Demo chỉ làm phần quản trị Mini App; chưa chốt Android/iOS và không tích hợp vào ứng dụng BIZ đang chạy. Kiểm chứng bằng luồng gọi API. | [Q8] [Q10] |
| CON-8 | Khi triển khai thực tế sẽ phát triển bổ sung trên các dự án đang chạy và tận dụng hệ thống sẵn có. | Cần đối chiếu API/xác thực/quyền hiện hữu trước khi tích hợp; hiện chưa thể xác nhận tương thích. | [desc] [Q9] [Q10] |
| CON-9 | Bản demo chỉ triển khai phần quản trị Mini App, không tích hợp ứng dụng BIZ đang chạy; kiểm chứng qua luồng gọi API mock. | Kết quả kiểm chứng không chứng minh tương thích với ứng dụng hoặc API thật. | [Q2] [Q10] |

## Chưa có thông tin để kết luận

| ID | Nội dung cần xác minh khi bước vào tích hợp thực tế | Vì sao chưa kết luận được | Nguồn |
|---|---|---|---|
| OPEN-1 | Danh tính, chủ sở hữu và trạng thái các dự án BIZ đang chạy. | Chưa nêu tên hoặc cung cấp tài liệu về các dự án. | [desc] |
| OPEN-2 | Hợp đồng API hiện có, phương thức xác thực và cách cấp quyền menu. | Demo chỉ sử dụng API mock; chưa có tài liệu hoặc endpoint thật. | [Q2] [Q8] |
| OPEN-3 | Yêu cầu tuân thủ, quyền riêng tư, lưu trữ và kiểm toán cho dữ liệu/hệ thống thật. | Demo chỉ dùng dữ liệu giả lập và người dùng chưa cung cấp yêu cầu nội bộ. | [Q4] |
| OPEN-4 | Hệ điều hành và công nghệ ứng dụng BIZ di động, cũng như cách tích hợp API vào dự án đích sau này. | Hiện tại chỉ cần thiết kế API. | [Q8] [Q9] [Q10] |

## Assumptions & Open Questions

- Tải động, cache và cập nhật Mini App trên ứng dụng BIZ không thuộc phần demo hiện được xác nhận; chỉ kiểm chứng luồng gọi API mock. [desc] [Q10]
- Không coi việc dùng API mock trong demo là bằng chứng rằng API thật tương thích. [Q2] [Q8]
- Không suy rộng việc chưa có yêu cầu tuân thủ demo thành việc dự án thực tế không chịu quy định hoặc kiểm soát nội bộ. [Q4]
- OPEN-1 đến OPEN-4 là đầu vào cho giai đoạn tích hợp thực tế; chúng không ngăn việc thiết kế hợp đồng API demo. [Q8] [Q9] [Q10]
