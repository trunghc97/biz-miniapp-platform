# Câu hỏi phân tích yêu cầu — BIZ Mini App Platform

Phạm vi đã duyệt là bản demo local cho cổng quản trị Mini App và API mock. Runtime nhúng, tải/cache trên thiết bị và tích hợp BIZ đang chạy vẫn nằm ngoài phạm vi.

## Q1. Vai trò quản trị trong bản demo

Ai được phép thực hiện các thao tác đăng ký, cập nhật và bật/tắt cấu hình Mini App trong kịch bản demo?

- A. Một vai trò quản trị giả lập duy nhất; mọi request hợp lệ dùng cùng vai trò.
- B. Nhiều vai trò giả lập; mô tả quyền khác nhau.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q2. Quy tắc dữ liệu cấu hình

Những trường nào bắt buộc và giới hạn nào cần kiểm tra trước khi lưu: tên, mã, URL truy cập, phiên bản, trạng thái, quyền menu và forceUpdate?

- A. Tên, mã, URL và phiên bản bắt buộc; mã duy nhất; URL hợp lệ; phiên bản theo định dạng có thể so sánh; quyền menu có thể rỗng.
- B. Bộ quy tắc khác; mô tả cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q3. Hợp đồng lỗi và phiên giả lập

API mock nên biểu diễn lỗi xác thực, hết hạn SessionId, thiếu quyền, dữ liệu không hợp lệ và mã Mini App trùng như thế nào để giao diện và kịch bản API kiểm tra được?

- A. Dùng mã lỗi ổn định, thông báo không lộ secret/SessionId, và giữ dữ liệu nhập để thử lại.
- B. Quy ước lỗi khác; mô tả mã và phản hồi mong muốn.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q4. Danh sách và tìm kiếm

Trong MVP, màn hình quản trị cần lọc/tìm kiếm hay chỉ cần danh sách và thao tác với một Mini App mẫu? Backlog hiện xếp lọc là Could Have.

- A. Chỉ cần danh sách, tạo và sửa; không đưa tìm kiếm/lọc thành yêu cầu bắt buộc.
- B. Đưa tìm kiếm/lọc vào MVP; mô tả điều kiện cần kiểm tra.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]:A

## Consolidated Summary Confirmation

- Dùng một vai trò quản trị giả lập duy nhất trong demo.
- Tên, mã, URL và phiên bản bắt buộc; mã duy nhất; URL hợp lệ; phiên bản có thể so sánh; quyền menu có thể rỗng.
- API dùng mã lỗi ổn định, không lộ secret hoặc SessionId và giữ dữ liệu để thử lại.
- MVP chỉ cần danh sách, tạo và sửa; không bắt buộc tìm kiếm hoặc lọc.
- Kịch bản API gồm đăng nhập, tạo, đọc, cập nhật quyền/trạng thái/phiên bản/forceUpdate, đọc lại và kiểm tra lỗi chính.
- Request hợp lệ phản hồi trong 2 giây ở điều kiện demo; kịch bản xác định và dữ liệu reset được.
- Giao diện áp dụng WCAG 2.1 AA cơ bản.

Does this all look correct before I generate the requirements artifact?

- Looks correct
- Request changes

[Answer]: Looks correct

## Q5. Kịch bản kiểm chứng API

Những bước nào phải có trong kịch bản có thể chạy lại để chứng minh bản demo đạt yêu cầu?

- A. Đăng nhập giả lập → tạo cấu hình → đọc danh sách/chi tiết → cập nhật quyền, trạng thái, phiên bản và forceUpdate → đọc lại → kiểm tra lỗi chính.
- B. Kịch bản khác; mô tả các bước và kết quả mong đợi.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]:A

## Q6. Mục tiêu chất lượng cho API mock

Khi chạy local, mục tiêu định lượng nào cần ghi vào yêu cầu cho phản hồi API, khả năng lặp lại và dữ liệu?

- A. Mỗi kịch bản API cho kết quả xác định; request hợp lệ phản hồi trong 2 giây ở điều kiện demo; dữ liệu reset được.
- B. Mục tiêu khác; mô tả ngưỡng cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]:A

## Q7. Khả năng tiếp cận giao diện

Mức hỗ trợ nào cần ghi nhận cho cổng quản trị web ưu tiên máy tính?

- A. WCAG 2.1 AA cơ bản: dùng bàn phím, nhãn trường, thứ bậc tiêu đề, lỗi không chỉ dùng màu và vùng thông báo trạng thái.
- B. Mức hoặc phạm vi khác; mô tả cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]:A
