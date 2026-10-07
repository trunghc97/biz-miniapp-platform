# BIZ Mini App Platform — Mục tiêu dự án

## Vấn đề cần giải quyết

BIZ hiện đóng gói các tính năng trong một ứng dụng nguyên khối. Việc phát hành tính năng phụ thuộc vào lịch phát hành toàn ứng dụng, làm chậm tiến độ bàn giao của các nhóm BIZ. Mục tiêu chính là phát hành tính năng và bản sửa lỗi mà không cần phát hành lại toàn bộ ứng dụng BIZ. [desc] [Q1] [Q2] [Q4]

## Đối tượng hưởng lợi

Đối tượng hưởng lợi chính là các nhóm phát triển và bàn giao BIZ, hiện phải phát hành tính năng theo các đợt phát hành ứng dụng nguyên khối. MVP sẽ trình diễn khả năng cập nhật Mini App độc lập cho đối tượng này. [Q1] [Q2] [Q8]

## Tiêu chí thành công

MVP thành công khi tất cả kịch bản được yêu cầu đều thực hiện thành công trong một bản trình diễn độc lập, có thể lặp lại. Chưa đặt thêm chỉ tiêu kinh doanh định lượng cho MVP này. [Q3] [Q8]

| Kết quả cần trình diễn | Bằng chứng đạt yêu cầu | Nguồn |
|---|---|---|
| Quản lý Mini App | Đăng ký ứng dụng mẫu; cấu hình tên, mã, URL truy cập, phiên bản, quyền menu, trạng thái bật/tắt và cập nhật bắt buộc. | [desc] [Q3] |
| Tái sử dụng xác thực và phân quyền | Đăng nhập theo mô hình SessionId, với thông tin phiên và quyền menu trong Redis; trình diễn hiển thị menu theo quyền và kiểm tra quyền trước khi mở Mini App. | [desc] [Q3] |
| Chỉ tải khi truy cập | Tài nguyên Mini App được tải xuống và lưu vào bộ nhớ đệm khi truy cập lần đầu, sau đó được tái sử dụng ở các lần truy cập tiếp theo. | [desc] [Q3] |
| Tái sử dụng API backend | Mini App mẫu gọi thành công API backend hiện có hoặc API giả lập. | [desc] [Q3] [Q8] |
| Cập nhật độc lập | Thay đổi phiên bản Mini App và trình diễn việc tải lại; trình diễn cập nhật bắt buộc mà không phát hành lại ứng dụng BIZ. | [desc] [Q3] |

## Lý do triển khai

Sự phụ thuộc giữa các đợt phát hành đang làm chậm việc bàn giao tính năng. Dự án nhằm giải quyết hạn chế này. [Q4]

## Phạm vi ban đầu

Phạm vi quy trình đã chọn là `mvp`. [scope]

Ranh giới sản phẩm được người dùng xác nhận là một bản trình diễn độc lập chạy được, gồm cổng quản lý Mini App, môi trường chạy Mini App, tái sử dụng xác thực và một Mini App mẫu. Cho phép dùng API backend giả lập; việc triển khai thực tế sẽ thực hiện sau. [desc] [Q8]

Cổng quản lý hỗ trợ đăng ký, thông tin định danh và URL truy cập của ứng dụng, phiên bản, bật/tắt, quyền menu và cập nhật bắt buộc. Môi trường chạy hỗ trợ tải động, tải xuống khi truy cập lần đầu, tái sử dụng tài nguyên trong bộ nhớ đệm và tải lại khi phiên bản thay đổi hoặc `forceUpdate=true`. [desc]

Các khả năng được yêu cầu vẫn giữ mô hình xác thực SessionId hiện có cùng thông tin phiên và quyền menu lưu trong Redis. Tái sử dụng API backend hiện có nhiều nhất có thể; bản trình diễn được phép sử dụng API giả lập. [desc] [Q8]

## Nguồn thông tin

Các mã nguồn tham chiếu đến yêu cầu ban đầu và câu trả lời đã xác nhận trong [bộ câu hỏi](intent-capture-questions.md). [desc] [Q1] [Q2] [Q3] [Q4] [Q8]

## Giả định và câu hỏi còn mở

Không có.
