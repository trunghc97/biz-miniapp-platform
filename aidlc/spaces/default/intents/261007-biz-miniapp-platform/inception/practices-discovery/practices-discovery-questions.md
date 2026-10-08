# Câu hỏi thống nhất cách làm việc và kiểm thử

Các quyết định đã chốt ở giai đoạn trước được giữ nguyên: backend Java 21/Spring Boot 4; demo local bằng Docker Compose với Redis, PostgreSQL và API mock; chỉ làm quản trị Mini App.

## Q1. Cách làm việc với mã nguồn

Có dùng nhánh ngắn từ `main`, squash về `main`, review bắt buộc và chạy kiểm tra tự động trước khi gộp không? Nếu có, hãy nêu người hoặc vai trò duyệt và nơi chạy CI.

- A. Có; nhánh ngắn, squash về `main`, review bởi người phụ trách, CI chạy kiểm tra trước merge.
- B. Có nhưng quy trình review hoặc CI khác; mô tả cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q2. Lát cắt đầu-cuối

Có xây một lát cắt tối thiểu chạy xuyên suốt trước không? Lát cắt này là phiên bản nhỏ nhất đi từ đăng nhập giả lập qua giao diện tạo cấu hình, API lưu PostgreSQL, đọc lại cấu hình và dùng phiên giả lập trong Redis để chứng minh các phần kết nối được.

- A. Có; hoàn thành và kiểm chứng lát cắt này trước khi mở rộng.
- B. Không; triển khai theo từng lớp hoặc thứ tự khác, mô tả thứ tự.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q3. Phương pháp và thứ tự kiểm thử

Phương pháp nào nhóm muốn dùng cho bản demo, và kiểm thử được viết vào thời điểm nào? Sàn 80% dòng mã của MVP vẫn giữ nguyên; cần xác định phạm vi đo và các lớp kiểm thử.

- A. `test-after`: làm từng lớp rồi viết và chạy kiểm thử cho lớp đó; đo mã backend/frontend thuộc MVP, loại trừ mã sinh tự động.
- B. Dùng TDD, BDD, ATDD hoặc cách tùy chỉnh; mô tả phương pháp, thứ tự và phạm vi đo.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q4. Chạy lại và đặt lại dữ liệu demo

Trong môi trường local đã chốt, nhóm muốn khởi động, chạy lại kịch bản API và reset dữ liệu giả lập như thế nào để buổi trình diễn lặp lại được?

- A. Có lệnh hoặc hướng dẫn có phiên bản để khởi động Compose, nạp dữ liệu mẫu, chạy kịch bản API và reset dữ liệu rõ ràng.
- B. Quy trình khác; mô tả cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Q5. Quy ước mã và kiểm tra chất lượng

Ngoài Java 21/Spring Boot 4, nhóm muốn chốt formatter, linter, kiểm tra dependency và cách tổ chức các lớp API, nghiệp vụ, persistence và phiên giả lập thế nào?

- A. Dùng cấu hình formatter/linter và dependency check được commit cùng dự án; tổ chức theo capability quản trị Mini App với các lớp ranh giới rõ.
- B. Quy ước hoặc công cụ khác; mô tả cụ thể.
- C. Chưa chốt.
- X. Other (please specify)

[Answer]: A

## Assumption Confirmation

- A. Accept assumptions
- B. Convert to follow-up questions

[Answer]: A

## Consolidated Summary Confirmation

- Dùng nhánh ngắn từ `main`, squash về `main`, review và kiểm tra tự động trước merge.
- Xây lát cắt đầu-cuối tối thiểu trước: đăng nhập giả lập → giao diện tạo cấu hình → API/PostgreSQL → đọc lại, dùng Redis cho phiên giả lập.
- Dùng `test-after`, giữ Test Strategy Standard và sàn 80% dòng mã cho mã thuộc MVP, loại trừ mã sinh tự động.
- Có hướng dẫn có phiên bản để khởi động Docker Compose, nạp dữ liệu, chạy kịch bản API và reset dữ liệu demo.
- Dùng cấu hình formatter/linter và dependency check được commit; tổ chức rõ các lớp API, nghiệp vụ, persistence và phiên giả lập.

Does this all look correct before I generate the artifact?

- Looks correct
- Request changes

[Answer]: Looks correct
