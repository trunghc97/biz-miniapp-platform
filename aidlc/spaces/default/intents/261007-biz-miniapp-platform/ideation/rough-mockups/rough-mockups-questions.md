# Câu hỏi phác thảo giao diện — BIZ Mini App Platform

Phạm vi đã chốt là cổng quản trị Mini App chạy cục bộ; không tích hợp vào ứng dụng BIZ. Các câu hỏi chỉ làm rõ cách trình bày giao diện và kịch bản thao tác.

## Q1. Có quy chuẩn giao diện nào cần áp dụng cho cổng quản trị demo không?

Hiện chưa có bộ nhận diện hoặc hướng dẫn giao diện BIZ trong tài liệu đã cung cấp.

- A. Dùng giao diện quản trị trung tính, rõ ràng, phù hợp bối cảnh ngân hàng; chưa mô phỏng thương hiệu BIZ.
- B. Mô phỏng giao diện BIZ hiện có; tôi sẽ cung cấp màu sắc hoặc quy chuẩn cụ thể.
- C. Dùng phong cách khác; mô tả mong muốn.
- X. Other (please specify)

[Answer]: A

## Q2. Cổng quản trị cần ưu tiên thiết bị nào?

Kích thước màn hình ảnh hưởng đến bố cục danh sách và biểu mẫu cấu hình.

- A. Ưu tiên trình duyệt máy tính; bố cục co giãn cơ bản trên máy tính bảng.
- B. Hỗ trợ đầy đủ máy tính và điện thoại ngay trong demo.
- C. Chỉ cần chạy trên một kích thước màn hình máy tính.
- X. Other (please specify)

[Answer]: A

## Q3. Kịch bản giao diện có cần màn hình đăng nhập giả lập không?

Yêu cầu ban đầu có bước đăng nhập SessionId, còn phạm vi hiện tại không tích hợp BIZ; câu trả lời quyết định điểm bắt đầu của luồng demo trên giao diện.

- A. Có màn hình đăng nhập giả lập, sau đó vào cổng quản trị.
- B. Bỏ màn hình đăng nhập; chỉ kiểm chứng SessionId qua API và mở thẳng giao diện quản trị.
- C. Không cần mô phỏng đăng nhập trong bản demo.
- X. Other (please specify)

[Answer]: A

## Consolidated Summary Confirmation

Tôi đã tổng hợp các quyết định để tạo wireframe và luồng người dùng. Hãy kiểm tra các lựa chọn sau:

- Dùng giao diện quản trị trung tính, rõ ràng, phù hợp bối cảnh ngân hàng; chưa mô phỏng thương hiệu BIZ.
- Ưu tiên trình duyệt máy tính và hỗ trợ bố cục co giãn cơ bản trên máy tính bảng.
- Kịch bản giao diện có màn hình đăng nhập giả lập trước khi vào cổng quản trị.
- Luồng vẫn chỉ thuộc cổng quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy, không có màn hình/runtime để tải và chạy Mini App.

Does this all look correct before I generate the artifact?

- Looks correct
- Request changes

[Answer]: Looks correct
