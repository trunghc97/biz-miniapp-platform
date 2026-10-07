# Backlog ưu tiên — BIZ Mini App Platform

Backlog này chuyển ranh giới đã thống nhất trong [scope-document.md](scope-document.md) thành các lát cắt có thể trình diễn. Nội dung dựa trên [intent-statement.md](../intent-capture/intent-statement.md), [feasibility-assessment.md](../feasibility/feasibility-assessment.md), [constraint-register.md](../feasibility/constraint-register.md) và các câu trả lời trong [scope-definition-questions.md](scope-definition-questions.md).

## Cách ưu tiên

Sử dụng MoSCoW cho MVP. Các hạng mục Must được sắp theo phụ thuộc và giá trị đầu-cuối. Hạ tầng local là điều kiện cho API mock, nhưng tiêu chí trình diễn là luồng quản trị Mini App hoàn chỉnh.

## Must Have — MVP

| Thứ tự | ID | Lát cắt | Kết quả có thể kiểm chứng | Phụ thuộc |
|---|---|---|---|---|
| 1 | U1 | Môi trường demo và dịch vụ mock | Docker Compose khởi động backend mock dạng microservice, Redis và PostgreSQL; dữ liệu mẫu có thể khởi tạo lại. | Không |
| 2 | U2 | Hợp đồng API và lưu cấu hình Mini App | API tạo, xem danh sách/chi tiết và cập nhật cấu hình; dữ liệu được lưu và đọc lại từ PostgreSQL. | U1 |
| 3 | U3 | Giao diện quản trị Mini App | Quản trị viên xem danh sách và tạo/cập nhật tên, mã, URL truy cập, phiên bản, trạng thái, quyền menu và forceUpdate. | U2 |
| 4 | U4 | Phiên giả lập và quyền menu | Kịch bản dùng SessionId giả lập; API trả dữ liệu phiên/quyền giả lập từ Redis và kiểm tra quyền cho thao tác quản trị theo hợp đồng đã thiết kế. | U1, U2 |
| 5 | U5 | Kịch bản demo đầu-cuối | Tạo hoặc cập nhật Mini App mẫu từ giao diện, kiểm chứng các trường bằng API, đổi phiên bản và bật forceUpdate; chạy lại được với dữ liệu giả lập. | U3, U4 |

## Should Have — chỉ làm nếu không ảnh hưởng Must Have

| ID | Lát cắt | Giá trị | Phụ thuộc |
|---|---|---|---|
| S1 | Thông báo lỗi API rõ ràng trên giao diện | Giúp người trình diễn nhận biết lỗi nhập liệu hoặc dịch vụ mock không sẵn sàng. | U3 |
| S2 | Tệp yêu cầu/kịch bản gọi API có thể chạy lại | Giúp người khác xác minh hợp đồng mà không cần thao tác thủ công từng request. | U2, U5 |

## Could Have

| ID | Lát cắt | Ghi chú |
|---|---|---|
| C1 | Nhật ký thay đổi cấu hình trong giao diện | Không cần để chứng minh luồng quản trị cơ bản. |
| C2 | Nhiều Mini App mẫu hoặc bộ lọc danh sách | Bản demo chỉ cần một mẫu để kiểm chứng. |

## Won't Have — lần này

| ID | Nội dung loại trừ | Lý do |
|---|---|---|
| W1 | Runtime nhúng trong BIZ để tải và chạy Mini App | Người dùng xác nhận chỉ làm phần quản trị Mini App trên máy demo. |
| W2 | Tải tài nguyên lần đầu, cache trên thiết bị và tải lại theo version/forceUpdate | Cần tích hợp vào runtime ứng dụng; không nằm trong phạm vi demo hiện tại. |
| W3 | Tích hợp API hoặc dữ liệu thật, kết nối Redis/PostgreSQL production | Demo chỉ sử dụng API và dữ liệu giả lập. |
| W4 | Triển khai cloud hoặc phát hành production | Máy demo chạy cục bộ bằng Docker Compose; chưa có yêu cầu triển khai cloud. |
| W5 | Khẳng định tương thích với dự án BIZ hiện có | Chưa có tên dự án, hợp đồng API hoặc môi trường đích để đối chiếu. |

## Bản đồ luồng giá trị

| Bước người dùng | Hạng mục | Ưu tiên | Bằng chứng |
|---|---|---|---|
| Khởi động môi trường local | U1 | Must | Các container cần thiết sẵn sàng và dữ liệu giả lập được nạp. |
| Đăng nhập giả lập | U4 | Must | SessionId giả lập được chấp nhận trong kịch bản API. |
| Truy cập màn hình quản trị | U3 | Must | Giao diện hiển thị và thao tác được Mini App mẫu. |
| Tạo/cập nhật cấu hình | U2, U3 | Must | API và giao diện hiển thị cùng cấu hình đã lưu. |
| Kiểm tra quyền menu | U4 | Must | Kết quả API phản ánh quyền giả lập đã cấu hình. |
| Đổi phiên bản và bật cập nhật bắt buộc | U5 | Must | API trả phiên bản và forceUpdate mới sau thao tác. |

## Trình tự đề xuất

- **Lát cắt nền tảng**: hoàn thành U1, đồng thời xác định hợp đồng API tối thiểu của U2.
- **Lát cắt quản trị**: hoàn thành U2 và U3 để có thao tác đầu-cuối với một Mini App.
- **Lát cắt quyền và trình diễn**: hoàn thành U4, U5; chạy lại toàn bộ kịch bản bằng dữ liệu giả lập.
- Chỉ nhận S1 hoặc S2 nếu chúng hỗ trợ trực tiếp khả năng trình diễn và không làm trễ các hạng mục Must.

## Sources

- [scope-document.md](scope-document.md) — ranh giới, tiêu chí thành công, phụ thuộc và các loại trừ của MVP.
- [intent-statement.md](../intent-capture/intent-statement.md) — yêu cầu chức năng khởi đầu.
- [feasibility-assessment.md](../feasibility/feasibility-assessment.md) — giới hạn demo, công nghệ và phương thức kiểm chứng.
- [constraint-register.md](../feasibility/constraint-register.md) — ràng buộc đã chốt.
- [scope-definition-questions.md](scope-definition-questions.md) — lựa chọn phạm vi đầu ra và ưu tiên.

## Assumptions & Open Questions

- U4 chỉ mô phỏng phiên và quyền bằng dữ liệu giả; quy tắc phân quyền chính thức phải được xác minh khi tích hợp dự án thật.
- API của U2 sẽ được chốt ở giai đoạn thiết kế hợp đồng; backlog hiện chỉ xác định khả năng cần có.
- S1 và S2 không phải điều kiện để hoàn thành MVP nếu thời gian hoặc công sức bị giới hạn.
