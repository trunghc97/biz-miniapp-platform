# Project-Level Rules

> Project-specific specialisation and corrections. Loaded after `org.md` and
> `team.md` as strict-additive guidance; contradictions with broader policy
> are rejected. Populated by practices-discovery and the self-learning loop.
>
> Use sparingly: most teams don't need a project layer. Reach for it
> only when this specific project needs stable, durable guidance beyond the
> team practice (for example, package-specific release checks or an additional
> regression suite for a legacy component).

## Way of Working

<!-- Project-specific specialisation. Example: -->
<!-- This monorepo requires package-scoped branch names and a package owner -->
<!-- review in addition to the team's normal merge policy. -->

## Walking Skeleton

<!-- Project-specific specialisation. Example: -->
<!-- The walking skeleton must exercise the legacy service adapter as well -->
<!-- as the new service boundary. -->

## Testing Posture

<!-- Project-specific specialisation. -->

## Guard Policy

<!-- Project-specific. Mode: strict, relaxed, or off. Strict here holds for every intent and cannot be changed from chat. A section under the retired Change Control heading, written by an earlier release, is still read. -->

## Deployment

<!-- Project-specific specialisation. -->

## Code Style

<!-- Project-specific specialisation. -->

## Tech Stack

<!-- Technology choices locked for this project. -->

## Decided

<!-- Decisions made in earlier stages that should not be re-asked. -->
<!-- Format: DECIDED: [decision] (Stage [slug], [date]) -->

## Scope Overrides

<!-- Custom scope rules for this project. -->

## Forbidden

<!-- Populated by practices-discovery affirmation gate. -->
<!-- Format: NEVER [behavior] (affirmed [date]) -->
<!-- Example: NEVER throw exceptions across service layer boundaries (affirmed 2026-05-17) -->

- NEVER kết nối bản demo tới ứng dụng BIZ, Redis, PostgreSQL hoặc API ngân hàng đang vận hành. (affirmed 2026-10-08)

- NEVER mở rộng bản demo thành runtime tải/cache Mini App hoặc triển khai cloud/production. (affirmed 2026-10-08)

- NEVER hạ sàn 80% line coverage để làm cho bước kiểm tra đạt. (affirmed 2026-10-08)

## Mandated

<!-- Populated by practices-discovery affirmation gate. -->
<!-- Format: ALWAYS [behavior] (affirmed [date]) -->
<!-- Example: ALWAYS use Result<T,E> for fallible operations in service layer (affirmed 2026-05-17) -->

- ALWAYS dùng dữ liệu, tài khoản và API giả lập trong bản demo local. (affirmed 2026-10-08)

- ALWAYS chạy kiểm tra formatter, kiểm thử và dependency check trước merge. (affirmed 2026-10-08)

- ALWAYS giữ lát cắt đầu-cuối quản trị Mini App làm bằng chứng đầu tiên trước khi mở rộng. (affirmed 2026-10-08)

- ALWAYS che giấu SessionId, secret, connection string và stack trace trong phản hồi lỗi. (affirmed 2026-10-08)

## Corrections

<!-- Project-specific corrections from human feedback. -->
<!-- Format: NEVER/ALWAYS [behavior] (learned [date]) -->
- Trên máy demo này, dùng Docker Compose để dựng backend giả lập dạng microservice, Redis và PostgreSQL. Chỉ triển khai phần quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy. Kiểm chứng luồng bằng cách gọi API theo kịch bản. Khi triển khai thực tế, phát triển bổ sung trên các dự án hiện có. (learned 2026-10-07) <!-- cid:261007-biz-miniapp-platform:feasibility:e9ab62e1056b56e95da2523dcce67fd5b1e3a06ab92ef0c20d9cffc79996c7cc -->
- Phạm vi được chốt là giao diện quản trị Mini App và backend API mock chạy cục bộ; ưu tiên luồng quản trị đầu-cuối, không gồm runtime hoặc tích hợp BIZ đang chạy. (learned 2026-10-07) <!-- cid:261007-biz-miniapp-platform:scope-definition:b6f9e3d3bc1cd4efbc526eeda3aadb423acc26f0697558ebeba8f7b33f673709 -->
- Phác thảo là cổng quản trị web trung tính, ưu tiên máy tính và có đăng nhập giả lập. Người dùng xác nhận không tích hợp vào ứng dụng BIZ nên giao diện chỉ quản lý cấu hình và kiểm chứng API mock. (learned 2026-10-07) <!-- cid:261007-biz-miniapp-platform:rough-mockups:0f79733efa45488201b957b95cf66c84aafdb71b9f5a18f9cab39b6f4dead8fa -->

## Interpretations
- one mock admin is sufficient; stories are sliced by workflow and use standard Given/When/Then criteria. (learned 2026-10-08) <!-- cid:261007-biz-miniapp-platform:user-stories:0cf0c62a3c85b453b1e5b06843129c7f863dc3c0bd52e009ac1fb2901b0eada4 -->

- represented the workflow with three primary screens and supporting API notes because the MVP has one persona and a compact admin path. (learned 2026-10-08) <!-- cid:261007-biz-miniapp-platform:refined-mockups:91eef11e458d4d6258732a05987fde878f7b9b018b5d56da2c67b985d7fd456a -->

## Tradeoffs
- kept UI-state recovery as Should Have while the login-to-API verification path remains Must Have. (learned 2026-10-08) <!-- cid:261007-biz-miniapp-platform:user-stories:cde363f9e03e2236b7712242f8cf77b3c4d052aa7a09432a9444c6e409d6a009 -->
