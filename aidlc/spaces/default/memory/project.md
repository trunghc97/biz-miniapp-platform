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

## Mandated

<!-- Populated by practices-discovery affirmation gate. -->
<!-- Format: ALWAYS [behavior] (affirmed [date]) -->
<!-- Example: ALWAYS use Result<T,E> for fallible operations in service layer (affirmed 2026-05-17) -->

## Corrections

<!-- Project-specific corrections from human feedback. -->
<!-- Format: NEVER/ALWAYS [behavior] (learned [date]) -->
- Trên máy demo này, dùng Docker Compose để dựng backend giả lập dạng microservice, Redis và PostgreSQL. Chỉ triển khai phần quản trị Mini App; không tích hợp vào ứng dụng BIZ đang chạy. Kiểm chứng luồng bằng cách gọi API theo kịch bản. Khi triển khai thực tế, phát triển bổ sung trên các dự án hiện có. (learned 2026-10-07) <!-- cid:261007-biz-miniapp-platform:feasibility:e9ab62e1056b56e95da2523dcce67fd5b1e3a06ab92ef0c20d9cffc79996c7cc -->
- Phạm vi được chốt là giao diện quản trị Mini App và backend API mock chạy cục bộ; ưu tiên luồng quản trị đầu-cuối, không gồm runtime hoặc tích hợp BIZ đang chạy. (learned 2026-10-07) <!-- cid:261007-biz-miniapp-platform:scope-definition:b6f9e3d3bc1cd4efbc526eeda3aadb423acc26f0697558ebeba8f7b33f673709 -->
