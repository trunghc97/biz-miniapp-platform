<!-- INVARIANT: examples are single-line HTML comments so a fresh template parses to total=0 (MEMORY_EMPTY). Do NOT un-comment or split across lines. t100 guards this. -->
> This file is kept up to date automatically while the stage runs. Add observations at the review step, not by editing here directly.

## Interpretations
<!-- example: 2026-05-29T10:14:32Z — chose REST over GraphQL; the consuming team only needs CRUD, revisit if subscriptions land -->
- 2026-10-07T14:55:19Z — Phạm vi được chốt là giao diện quản trị Mini App và backend API mock chạy cục bộ; ưu tiên luồng quản trị đầu-cuối, không gồm runtime hoặc tích hợp BIZ đang chạy.

## Deviations
<!-- example: 2026-05-29T10:14:32Z — skipped the optional caching layer the stage prose suggested; the dataset is small enough that it adds risk -->
- 2026-10-07T14:55:19Z — Thu hẹp yêu cầu Mini App ban đầu: tải động, cache và cập nhật trên runtime BIZ được chuyển ra ngoài phạm vi demo theo xác nhận gần nhất của người dùng.

## Tradeoffs
<!-- example: 2026-05-29T10:14:32Z — picked TDD over BDD this run; the team is unit-first and the domain is well-understood -->

## Open questions
<!-- example: 2026-05-29T10:14:32Z — confirm the retention window with compliance before the next stage hardens the schema -->
