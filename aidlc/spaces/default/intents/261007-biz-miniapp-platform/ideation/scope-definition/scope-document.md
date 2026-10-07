# Định nghĩa phạm vi — BIZ Mini App Platform

## Mục tiêu

Xây dựng bản demo cục bộ để quản trị Mini App độc lập với ứng dụng BIZ đang chạy. Người vận hành có thể đăng ký và cấu hình Mini App qua giao diện quản trị; các luồng được kiểm chứng bằng API giả lập. Tài liệu này sử dụng [intent-statement.md](../intent-capture/intent-statement.md), [feasibility-assessment.md](../feasibility/feasibility-assessment.md) và [constraint-register.md](../feasibility/constraint-register.md), cùng câu trả lời đã xác nhận trong [scope-definition-questions.md](scope-definition-questions.md).

## Đối tượng và giá trị

- **Người quản trị Mini App**: đăng ký ứng dụng, cập nhật cấu hình, quyền menu và trạng thái phát hành mà không sửa mã nguồn ứng dụng BIZ.
- **Người phát triển demo**: kiểm chứng hợp đồng và luồng API trên máy cá nhân bằng dữ liệu giả lập.
- **Người đánh giá**: có thể quan sát luồng quản trị từ giao diện đến API trong một buổi trình diễn ngắn.

Giá trị MVP là chứng minh khả năng quản lý cấu hình Mini App qua một sản phẩm quản trị chạy được cục bộ. Đây không phải bằng chứng rằng Mini App đã được tải hoặc chạy bên trong BIZ.

## Ranh giới MVP

### Trong phạm vi

- Giao diện quản trị Mini App để đăng ký và xem danh sách Mini App.
- Tạo/cập nhật thông tin: tên, mã, URL truy cập, phiên bản, bật/tắt, quyền menu và cờ forceUpdate.
- Backend API quản trị và hợp đồng API tương ứng; dữ liệu được lưu trong PostgreSQL.
- Các dịch vụ backend mock dạng microservice, Redis và PostgreSQL chạy bằng Docker Compose trên máy demo.
- Mô phỏng SessionId và dữ liệu phiên/quyền giả lập ở mức cần thiết cho kịch bản API; không dùng tài khoản, dữ liệu hoặc endpoint thật.
- Một Mini App mẫu dùng làm dữ liệu cấu hình để minh họa thao tác quản trị.
- Kịch bản kiểm chứng gọi API cho đăng nhập giả lập, tạo/cập nhật cấu hình, quyền menu, trạng thái bật/tắt, phiên bản và forceUpdate.
- Tài liệu thiết kế API là một phần của đầu ra; thứ tự thực hiện ưu tiên hoàn thiện luồng quản trị đầu-cuối.

### Ngoài phạm vi của bản demo

- Tích hợp mã, SDK, WebView hoặc runtime tải Mini App vào ứng dụng BIZ đang chạy.
- Tải động tài nguyên Mini App từ ứng dụng BIZ, cache tài nguyên trên thiết bị và cập nhật khi mở ứng dụng.
- Xác minh hành vi cập nhật phiên bản hoặc cập nhật bắt buộc trên thiết bị thật.
- Kết nối đến API, Redis, PostgreSQL, tài khoản hoặc dữ liệu của hệ thống ngân hàng đang hoạt động.
- Triển khai cloud, phát hành production, tuân thủ vận hành production hoặc chứng nhận bảo mật cho hệ thống thật.
- Xác nhận tính tương thích với các dự án đang chạy; việc này cần thực hiện khi có dự án và hợp đồng API đích.

## Luồng giá trị

~~~mermaid
flowchart LR
    A[Quản trị viên đăng nhập giả lập] --> B[Mở giao diện quản trị Mini App]
    B --> C[Đăng ký hoặc chọn Mini App mẫu]
    C --> D[Cập nhật thông tin và quyền menu]
    D --> E[Gọi API quản trị]
    E --> F[Lưu cấu hình vào PostgreSQL]
    F --> G[Đọc lại cấu hình và kiểm chứng kết quả]
    G --> H[Thay đổi phiên bản hoặc forceUpdate]
    H --> I[Gọi API và xác nhận cấu hình mới]
~~~

Luồng văn bản: đăng nhập giả lập → mở quản trị → tạo/cập nhật Mini App → kiểm tra cấu hình và quyền bằng API → thay đổi phiên bản hoặc forceUpdate → đọc lại và xác nhận dữ liệu mới.

## Tiêu chí thành công

- Người dùng hoàn thành việc đăng ký và cập nhật Mini App mẫu qua giao diện quản trị.
- Tên, mã, URL, phiên bản, trạng thái, quyền menu và forceUpdate được API trả về chính xác sau khi lưu.
- Backend mock, Redis và PostgreSQL khởi động được bằng Docker Compose trên máy demo.
- Kịch bản API có thể chạy lại bằng dữ liệu giả lập và cho kết quả xác định.
- Bản demo không cần thay đổi hoặc phát hành lại ứng dụng BIZ.

## Giả định và phụ thuộc

- Máy demo có Docker và Docker Compose, có thể chạy các container cục bộ.
- Backend mock dùng Java 21 và Spring Boot 4.
- Các dịch vụ và dữ liệu chỉ phục vụ kiểm chứng; chưa đại diện cho dự án đang vận hành.
- Hợp đồng API thật, mô hình quyền chính thức và dự án đích sẽ được khảo sát trước khi tích hợp thực tế.

## Sources

- [intent-statement.md](../intent-capture/intent-statement.md) — vấn đề, mục tiêu ban đầu và các khả năng người dùng đề xuất.
- [feasibility-assessment.md](../feasibility/feasibility-assessment.md) — nền tảng kỹ thuật, giới hạn demo và hướng phát triển trên dự án hiện hữu.
- [constraint-register.md](../feasibility/constraint-register.md) — các ràng buộc đã xác nhận và nội dung cần xác minh khi tích hợp thật.
- [scope-definition-questions.md](scope-definition-questions.md) — lựa chọn đầu ra demo, ưu tiên đầu-cuối và xác nhận bản tóm tắt.

## Assumptions & Open Questions

- Chưa xác định dự án đang chạy nào sẽ nhận phần phát triển bổ sung; phạm vi này chỉ được xem xét khi bắt đầu tích hợp thực tế.
- Hợp đồng API thật, cấu hình SessionId và quy tắc phân quyền chính thức chưa được cung cấp; bản demo dùng mô phỏng.
- Thời hạn và ngân sách cụ thể chưa được đặt; thiết kế cục bộ tránh yêu cầu tài khoản cloud.
