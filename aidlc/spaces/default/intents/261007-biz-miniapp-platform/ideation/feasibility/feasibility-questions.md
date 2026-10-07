# Câu hỏi đánh giá tính khả thi và ràng buộc

## Thông tin bổ sung trực tiếp từ người dùng

Nguyên văn: "done, lưu ý máy tính này chỉ demo nên hoàn toàn sử dụng api mock, khi thi thật thì sẽ có sẵn 1 vài project đang chạy rồi và chỉ phát triển thêm"

Áp dụng cho đánh giá: máy hiện tại chỉ chạy demo, toàn bộ API dùng bản giả lập. Theo Q2, demo vẫn sử dụng Redis thật riêng cho demo và mô hình SessionId. Khi triển khai thực tế, phát triển bổ sung trên các dự án đang chạy; không coi bản demo là yêu cầu xây lại toàn bộ hệ thống hiện có.

## Bối cảnh đã xác nhận

Tham chiếu [mục tiêu dự án](../intent-capture/intent-statement.md) và [câu trả lời đã xác nhận](../intent-capture/intent-capture-questions.md). MVP là bản trình diễn độc lập chạy được, cho phép API giả lập; mục tiêu là cập nhật Mini App không cần phát hành lại BIZ. Giữ mô hình SessionId, thông tin phiên và quyền menu trong Redis. Không hỏi lại các quyết định này.

## Hướng dẫn trả lời

Điền chữ cái sau mỗi nhãn `[Answer]:`; với lựa chọn yêu cầu mô tả, ghi thêm thông tin ngay sau chữ cái. Lựa chọn X dùng để trả lời khác.

## Q1. Bản demo cần chạy trên nền tảng nào?

Bạn đã chọn demo độc lập. Nền tảng chạy quyết định khả năng tải và lưu tài nguyên Mini App; đây chưa phải lựa chọn thư viện triển khai.

A. Trình duyệt web trên máy tính; chưa cần ứng dụng di động.
B. Ứng dụng di động hoặc trình giả lập; tôi sẽ nêu Android, iOS hay cả hai.
C. Cần cả web và di động; tôi sẽ nêu nền tảng bắt buộc.
D. Chưa xác định.
X. Other (please specify)

[Answer]: B

## Q2. Demo sẽ sử dụng nguồn xác thực, Redis và API nào?

SessionId và Redis đã là yêu cầu; câu hỏi này làm rõ nguồn có thể truy cập, không thay đổi mô hình xác thực.

A. Tạo đăng nhập giả lập theo mô hình SessionId, dùng Redis thật dành riêng cho demo và API nghiệp vụ giả lập.
B. Có môi trường thử nghiệm của ngân hàng cho xác thực, Redis hoặc API; tôi sẽ nêu phần nào có thể dùng và tài liệu giao tiếp sẵn có.
C. Kết hợp khác; tôi sẽ mô tả thành phần thật và thành phần giả lập.
D. Chưa xác định.
X. Other (please specify)

[Answer]: A


## Q3. Có ràng buộc công nghệ hoặc năng lực đội ngũ nào phải tuân theo không?

Chỉ ghi nhận công nghệ đã bị ràng buộc; việc lựa chọn thiết kế cụ thể thực hiện ở bước sau.

A. Không có công nghệ bắt buộc cho demo; ưu tiên dễ chạy và dễ bàn giao.
B. Có công nghệ bắt buộc hoặc đội ngũ chỉ hỗ trợ một số công nghệ; tôi sẽ cung cấp danh sách và kỹ năng hiện có.
C. Chưa xác định.
X. Other (please specify)

[Answer]: B: Java 21 spring boot 4

## Q4. Demo dùng loại dữ liệu nào và chịu yêu cầu nội bộ nào?

Thông tin này giúp xác định ràng buộc bảo mật và tuân thủ phù hợp, không tự mặc định quy định áp dụng chỉ vì đây là ứng dụng ngân hàng.

A. Chỉ dùng tài khoản và dữ liệu hoàn toàn giả lập; chưa có yêu cầu tuân thủ nội bộ bổ sung được cung cấp.
B. Dùng dữ liệu thử nghiệm đã được ngân hàng cho phép; tôi sẽ mô tả loại dữ liệu và quy định áp dụng, không gửi dữ liệu nhạy cảm.
C. Có dữ liệu khách hàng thật hoặc kết nối hệ thống thật; tôi sẽ nêu phạm vi, nơi xử lý dữ liệu và yêu cầu phê duyệt.
D. Chưa xác định.
X. Other (please specify)

[Answer]: A

## Q5. Môi trường và điều kiện hạ tầng cho demo là gì?

Chưa có yêu cầu dùng AWS. Chỉ cần nêu môi trường thực sự có thể sử dụng và các giới hạn mạng liên quan.

A. Chạy trên máy phát triển, có thể cài công cụ và chạy container; không cần tài khoản cloud.
B. Chạy trên máy phát triển nhưng không được dùng container; tôi sẽ nêu hệ điều hành và hạn chế cài đặt.
C. Chạy trên máy chủ nội bộ hoặc cloud đã có; tôi sẽ nêu môi trường, dịch vụ và giới hạn mạng, không cung cấp khóa truy cập.
D. Chưa xác định.
X. Other (please specify)

[Answer]: A

## Q6. Có thời hạn hoặc giới hạn ngân sách nào cho MVP không?

Cần biết giới hạn thực tế trước khi đưa ra nhận định khả thi; không tự đặt ngày giao hoặc chi phí.

A. Chưa có hạn chót cố định; ưu tiên demo chạy được và không phát sinh chi phí cloud.
B. Có hạn chót hoặc ngân sách; tôi sẽ nêu ngày, mức ngân sách và giới hạn liên quan.
C. Chưa xác định.
X. Other (please specify)

[Answer]: A

## Q7. Có trở ngại tổ chức hoặc phụ thuộc phê duyệt nào đã biết không?

Ví dụ: không được cài công cụ, chờ cấp môi trường, hạn chế tải mã động, lịch đóng băng thay đổi hoặc đội liên quan chưa sẵn sàng.

A. Chưa có trở ngại hoặc phụ thuộc phê duyệt nào được xác định cho demo độc lập.
B. Có; tôi sẽ mô tả trở ngại, bên cần phối hợp và thời điểm dự kiến giải quyết nếu biết.
C. Chưa xác định.
X. Other (please specify)

[Answer]: A

## Q8. Demo di động ở Q1 cần chạy trên nền tảng nào?

Bạn đã chọn ứng dụng di động hoặc trình giả lập, nhưng chưa nêu hệ điều hành. Cần xác định nền tảng bắt buộc để đánh giá điều kiện chạy demo trên máy này.

A. Android; trình giả lập Android là đủ cho demo.
B. iOS; trình giả lập iOS là đủ cho demo.
C. Cả Android và iOS; cần trình diễn trên cả hai.
X. Other (please specify)

[Answer]: X hiện tại chỉ cần thiết kế api trước

## Q9. Ngoài Java 21 và Spring Boot 4, ứng dụng BIZ di động có ràng buộc công nghệ nào cần theo không?

Bạn đã nêu công nghệ ở Q3 và cho biết sau này sẽ mở rộng các dự án đang chạy. Cần phân biệt ràng buộc backend với công nghệ ứng dụng di động, để demo có giá trị tham khảo khi tích hợp thực tế.

A. Java 21 và Spring Boot 4 áp dụng cho backend; demo di động chưa bị ràng buộc công nghệ.
B. Java 21 và Spring Boot 4 áp dụng cho backend; ứng dụng di động phải theo công nghệ hiện có, tôi sẽ nêu tên công nghệ và phiên bản nếu biết.
C. Java 21 và Spring Boot 4 áp dụng cho backend; công nghệ di động hiện có chưa rõ và cần xác minh trước khi chốt lựa chọn.
X. Other (please specify)

[Answer]: A

## Q10. Ranh giới triển khai và kiểm chứng của bản demo là gì?

Bạn đã xác nhận đầu ra trước mắt là thiết kế API. Ghi chú bổ sung làm rõ thành phần nào sẽ được dựng cho demo trên máy này và luồng nào được kiểm chứng.

A. Dùng Docker Compose để dựng backend mock dạng microservice, Redis và PostgreSQL; chỉ làm phần quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy; chỉ gọi API theo luồng để kiểm chứng.
B. Tôi sẽ mô tả ranh giới khác.
X. Other (please specify)

[Answer]: A

## Consolidated Summary Confirmation

- Đầu ra trước mắt là thiết kế API; chưa cần chốt nền tảng di động. [Q8]
- Backend demo dùng Java 21 và Spring Boot 4; chưa có công nghệ di động bắt buộc. [Q3] [Q9]
- Bản demo dùng Docker Compose để dựng backend mock dạng microservice, Redis và PostgreSQL. Tài khoản và dữ liệu đều giả lập. [Q2] [Q4] [Q5] [Q10]
- Phạm vi demo chỉ làm phần quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy. Kiểm chứng bằng cách gọi API theo luồng. [Q10]
- Khi triển khai thực tế, phát triển bổ sung trên các dự án đang chạy và tái sử dụng hệ thống hiện có; khả năng tương thích chưa được xác minh. [desc] [Q9] [Q10]
- Chưa có hạn chót cố định; chưa có trở ngại tổ chức nào được xác định. [Q6] [Q7]
- Chưa có yêu cầu tuân thủ nội bộ được cung cấp cho demo; điều đó không kết luận yêu cầu của môi trường thật. [Q4]

Bản tổng hợp này đã đúng để tôi cập nhật tài liệu đánh giá tính khả thi và các ràng buộc chưa?

- Looks correct
- Request changes

[Answer]: Looks correct
