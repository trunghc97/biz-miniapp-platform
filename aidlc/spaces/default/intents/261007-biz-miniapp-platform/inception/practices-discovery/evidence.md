# Bằng chứng và quyết định

## Sources

- `scope-document.md`, `intent-backlog.md` — local-only, U1–U5 và thứ tự ưu tiên đầu-cuối.
- `feasibility-assessment.md`, `constraint-register.md` — Java 21/Spring Boot 4, Docker Compose, Redis, PostgreSQL và dữ liệu giả lập.
- `rough-mockups/wireframes.md`, `user-flow.md` — giao diện quản trị, đăng nhập giả lập và kịch bản API.
- `org.md`, `project.md`, `inception.md` — mặc định làm việc, kiểm thử, truy nguyên và giới hạn dự án.
- Ba đóng góp trong `contributions/` — quality, developer và devsecops; các góp ý đã được tích hợp vào thực hành nhóm.

## Interview decisions

| Chủ đề | Quyết định |
|---|---|
| Way of Working | Nhánh ngắn, squash về `main`, review và CI trước merge. |
| Walking Skeleton | Xây lát cắt đăng nhập → UI → API/PostgreSQL → đọc lại với Redis trước. |
| Testing Posture | `test-after`, Standard, sàn 80% line coverage cho mã MVP. |
| Deployment | Docker Compose local, có hướng dẫn khởi động/nạp/reset/chạy API lặp lại. |
| Code Style | Formatter/linter/dependency check được commit; ranh giới API/nghiệp vụ/persistence/session rõ. |

## Assumptions & Open Questions

- Công cụ formatter, linter và dependency check cụ thể sẽ được chọn khi tạo cấu trúc build.
- Vai trò review và nền tảng CI cụ thể chưa được đặt tên; quy tắc chỉ yêu cầu review và kiểm tra trước merge.
- Tương thích với các dự án BIZ thực tế vẫn cần đánh giá riêng khi có hợp đồng và môi trường đích.

## Review

Các đóng góp đã được tích hợp; người dùng đã xác nhận bản tổng hợp trước khi tạo tài liệu.
