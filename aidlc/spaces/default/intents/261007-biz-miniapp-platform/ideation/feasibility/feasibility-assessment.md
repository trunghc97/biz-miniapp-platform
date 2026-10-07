# Đánh giá tính khả thi — BIZ Mini App Platform

## Kết luận

Thiết kế API cho bản demo là khả thi trong điều kiện đã xác nhận: backend dùng Java 21 và Spring Boot 4; Docker Compose dựng các dịch vụ backend mock dạng microservice, Redis và PostgreSQL; tài khoản và dữ liệu đều giả lập. Không cần tài khoản cloud; chưa có hạn chót cố định và ưu tiên không phát sinh chi phí cloud. [Q2] [Q3] [Q4] [Q5] [Q6] [Q10]

Đầu ra trước mắt là thiết kế API. Phần demo được giới hạn ở quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy. Kiểm chứng bằng cách gọi API theo luồng. Chưa cần chốt nền tảng di động hoặc xác minh ứng dụng BIZ thật. [Q8] [Q10]

Khi đưa vào sử dụng thực tế, công việc dự kiến là phát triển bổ sung trên một số dự án đang chạy và tận dụng hệ thống hiện có. Chưa có dự án cụ thể, đặc tả API, hợp đồng tích hợp hoặc quyền truy cập môi trường để đánh giá khả năng tương thích. Đây là hướng triển khai đã nêu, chưa phải tích hợp đã được xác minh. [intent-statement] [Q9] [Q10] [desc]

## Cơ sở đánh giá

- Nền tảng dịch vụ đã được chỉ định là Java 21 và Spring Boot 4. [Q3]
- Demo dùng đăng nhập giả lập theo mô hình SessionId, Docker Compose dựng Redis, PostgreSQL và backend mock dạng microservice; các API trên máy này đều là mock. [Q2] [Q10] [desc]
- Tài khoản và dữ liệu trong demo hoàn toàn giả lập; chưa có yêu cầu tuân thủ nội bộ bổ sung nào được cung cấp. Không suy ra rằng hệ thống ngân hàng thực tế không có nghĩa vụ tuân thủ. [Q4]
- Môi trường dự kiến là máy phát triển chạy Docker Compose cho backend mock, Redis và PostgreSQL, không cần tài khoản cloud. Người dùng ưu tiên tránh chi phí cloud. [Q5] [Q6] [Q10]
- Phạm vi việc làm trước mắt là thiết kế API. Yêu cầu này chưa xác định hệ điều hành di động hay hợp đồng tích hợp với ứng dụng BIZ đang có. [Q8] [Q9]

## Khả năng và giới hạn

| Nội dung | Đánh giá | Điều kiện hoặc giới hạn | Nguồn |
|---|---|---|---|
| Thiết kế hợp đồng API cho quản lý Mini App, kiểm tra quyền, phiên bản và tải cấu hình | Khả thi trong phạm vi demo | Chốt luồng và dữ liệu trao đổi; API mock được gọi theo kịch bản để kiểm chứng. | [desc] [Q2] [Q8] [Q10] |
| Mô phỏng đăng nhập SessionId và quyền menu | Khả thi cho trình diễn | Dùng tài khoản giả lập; chỉ kiểm chứng qua luồng API, không tích hợp app BIZ đang chạy. | [desc] [Q2] [Q4] [Q10] |
| Redis cho thông tin phiên và quyền demo | Khả thi | Docker Compose dựng Redis và PostgreSQL cùng backend mock dạng microservice trên máy demo. | [desc] [Q2] [Q5] [Q10] |
| Cập nhật Mini App bằng version và force update | Có thể mô tả trong hợp đồng API | Phần demo hiện chỉ làm quản trị Mini App; không tích hợp vào BIZ đang chạy. Kiểm chứng luồng bằng các API mock; tải động/cache trên ứng dụng BIZ chưa được triển khai hay xác minh. | [desc] [Q8] [Q10] |
| Phát triển bổ sung vào các dự án đang chạy | Chưa thể xác minh | Cần biết dự án, hợp đồng API, cơ chế xác thực và các giới hạn tích hợp thực tế. | [intent-statement] [Q9] [Q10] |
| Tuân thủ cho sản phẩm ngân hàng thật | Chưa thể kết luận từ demo | Chỉ có dữ liệu giả lập và chưa có yêu cầu nội bộ hay phạm vi xử lý dữ liệu thật được cung cấp. | [Q4] [intent-statement] |

## Phương án đánh giá

Trong thiết kế API, giữ rõ ranh giới giữa hợp đồng dịch vụ dự kiến và các adapter giả lập của demo. Dùng dữ liệu giả lập xuyên suốt; không đưa thông tin xác thực thật, dữ liệu khách hàng thật hay khóa truy cập vào demo. Đây là biện pháp giới hạn phạm vi do người dùng chọn dữ liệu hoàn toàn giả lập, không phải tuyên bố rằng hệ thống thực tế không cần kiểm soát bảo mật. [Q2] [Q4] [Q8]

Trước khi tích hợp vào các dự án hiện hữu, cần đối chiếu hợp đồng đã thiết kế với API, xác thực, quyền menu, Redis, PostgreSQL và quy trình phát hành thực tế của những dự án đó. Hiện chưa có đủ thông tin để xác nhận tính tương thích hoặc yêu cầu tuân thủ của môi trường thật. [intent-statement] [Q9]

## Assumptions & Open Questions

- Chức năng tải động Mini App, cache tài nguyên và cập nhật trên ứng dụng BIZ không nằm trong phần demo hiện được xác nhận; chỉ có thể mô tả luồng API trong thiết kế. [desc] [Q8] [Q10]
- Docker Compose dựng các dịch vụ backend mock dạng microservice, Redis và PostgreSQL. Tài khoản và dữ liệu đều giả lập. Chi tiết cấu hình dịch vụ sẽ được xác định khi triển khai demo. [Q2] [Q4] [Q5] [Q10]
- Q1 chọn ứng dụng di động hoặc trình giả lập, nhưng Q8 và Q10 giới hạn đầu ra trước mắt ở thiết kế API và demo phần quản trị Mini App. Hệ điều hành di động và tích hợp vào ứng dụng BIZ đang chạy chưa xác định, không thuộc phần demo hiện tại. [Q1] [Q8] [Q10]
- Các dự án thực tế sẽ tiếp tục được phát triển thêm, nhưng danh tính dự án và hợp đồng tích hợp chưa được cung cấp. Khả năng tích hợp cần đánh giá lại khi có thông tin đó. [intent-statement] [Q9]
- Không có ngày hoàn thành hoặc ngân sách cloud cụ thể; hiện chỉ có ưu tiên tránh chi phí cloud. [Q6]
