# Sổ rủi ro, giả định, vấn đề và phụ thuộc (RAID)

## Risks

| ID | Rủi ro | Khả năng / ảnh hưởng | Hướng xử lý | Nguồn |
|---|---|---|---|---|
| R-1 | Hợp đồng API trong demo có thể không khớp với API, xác thực hoặc quyền của các dự án BIZ đang chạy. | Khả năng chưa xác định; ảnh hưởng cao đến tích hợp thực tế. | Trước tích hợp, thu thập hợp đồng API và luồng xác thực của dự án đích; kiểm tra tương thích và ghi nhận thay đổi cần thiết. | [Q2] [Q9] [desc] |
| R-2 | Bản trình diễn với API mock có thể bị hiểu nhầm là đã chứng minh tích hợp với ứng dụng BIZ hoặc hệ thống xác thực thật. | Khả năng trung bình; ảnh hưởng trung bình đến kỳ vọng nghiệm thu. | Ghi rõ mọi API là mock; chỉ làm phần quản trị Mini App và kiểm chứng luồng gọi API, không gắn nhãn là đã tích hợp BIZ thật. | [Q2] [Q4] [Q10] |
| R-3 | Chưa có yêu cầu tuân thủ và xử lý dữ liệu của môi trường ngân hàng thật. | Khả năng chưa xác định; ảnh hưởng cao nếu mở rộng sang dữ liệu hoặc hệ thống thật. | Trước tích hợp thật, xác nhận phân loại dữ liệu, quy định nội bộ, lưu trữ, kiểm soát truy cập và yêu cầu kiểm toán với chủ hệ thống. | [Q4] [Q9] |
| R-4 | Thiết kế API có thể bỏ sót các khác biệt giữa môi trường demo và dự án đang chạy. | Khả năng trung bình; ảnh hưởng trung bình đến cao khi tích hợp. | Ghi rõ các điểm chưa kiểm chứng; đối chiếu với hệ thống mục tiêu trước khi chốt hợp đồng triển khai. | [Q8] [Q9] [Q10] |

## Assumptions

| ID | Giả định | Cách xác nhận hoặc giới hạn | Nguồn |
|---|---|---|---|
| A-1 | Docker Compose có thể dựng Redis và PostgreSQL trên máy demo cùng các backend mock dạng microservice. | Xác nhận điều kiện chung là máy có thể chạy container; phiên bản/cấu hình Redis chưa chốt. | [Q2] [Q5] [Q10] |
| A-2 | Tài khoản và dữ liệu giả lập đủ để minh họa đăng nhập và phân quyền menu. | Chỉ áp dụng cho demo; không đại diện dữ liệu hoặc xác thực thật. | [Q2] [Q4] |
| A-3 | Tài liệu hợp đồng API có thể được thiết kế trước khi chọn công nghệ client di động; demo giới hạn ở phần quản trị Mini App và kiểm chứng luồng gọi API. | Người dùng xác nhận hiện chỉ cần thiết kế API. | [Q8] |

## Issues

| ID | Vấn đề | Trạng thái | Nguồn |
|---|---|---|---|
| I-1 | Chưa có tên dự án BIZ đang chạy hoặc hợp đồng API thật để đối chiếu; demo không tích hợp vào ứng dụng BIZ đang chạy. | Chưa giải quyết; cần trước khi tích hợp thực tế, không chặn API mock/demo. | [Q9] |
| I-2 | Chưa chọn Android hay iOS và chưa xác định công nghệ client hiện hữu. | Chưa giải quyết; demo hiện chỉ làm phần quản trị Mini App và kiểm chứng luồng API. | [Q8] [Q9] [Q10] |

## Dependencies

| ID | Phụ thuộc | Cần cho | Trạng thái | Nguồn |
|---|---|---|---|---|
| D-1 | Docker Compose trên máy phát triển để chạy backend mock, Redis và PostgreSQL. | Mô phỏng dịch vụ backend, lưu phiên SessionId và quyền menu, và lưu dữ liệu demo. | Dựng bằng Docker Compose; không cần tài khoản cloud. | [desc] [Q2] [Q5] [Q10] |
| D-2 | Thông tin về dự án BIZ hiện hữu và hợp đồng API/xác thực của dự án đích. | Xác minh khả năng tương thích khi mở rộng cho môi trường thực tế. | Chưa cung cấp; không thuộc đầu vào demo API mock hiện tại; chỉ kiểm chứng luồng gọi API. | [desc] [Q9] |
| D-3 | Xác nhận yêu cầu tuân thủ và dữ liệu của môi trường thật. | Đánh giá trước khi xử lý dữ liệu hoặc kết nối hệ thống thật. | Chưa cung cấp; demo chỉ dùng dữ liệu giả lập. | [Q4] |

## Assumptions & Open Questions

- Tải Mini App động, cache tài nguyên và tích hợp ứng dụng BIZ đang chạy không thuộc phần demo được xác nhận; kiểm chứng chỉ qua luồng API mock. [desc] [Q10]

Ngoài mục trên, không có mục nào ngoài các giả định, vấn đề và phụ thuộc đã liệt kê ở trên.
