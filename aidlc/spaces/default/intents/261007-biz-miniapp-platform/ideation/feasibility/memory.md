<!-- INVARIANT: examples are single-line HTML comments so a fresh template parses to total=0 (MEMORY_EMPTY). Do NOT un-comment or split across lines. t100 guards this. -->
> This file is kept up to date automatically while the stage runs. Add observations at the review step, not by editing here directly.

## Interpretations
<!-- example: 2026-05-29T10:14:32Z — chose REST over GraphQL; the consuming team only needs CRUD, revisit if subscriptions land -->

## Deviations
<!-- example: 2026-05-29T10:14:32Z — skipped the optional caching layer the stage prose suggested; the dataset is small enough that it adds risk -->

## Tradeoffs
<!-- example: 2026-05-29T10:14:32Z — picked TDD over BDD this run; the team is unit-first and the domain is well-understood -->

## Open questions
<!-- example: 2026-05-29T10:14:32Z — confirm the retention window with compliance before the next stage hardens the schema -->

## Interpretations
- 2026-10-07T14:10:20Z — Q8 limits the immediate work to API design; retain mobile platform selection as an open item for later runtime planning. The user clarified that all APIs on this machine are mocked, Redis may be real for the demo, and the real deployment extends existing projects.

- 2026-10-07T14:18:21Z — Cập nhật ranh giới demo theo Q10. Dùng Docker Compose cho backend mock dạng microservice, Redis và PostgreSQL; phần demo chỉ làm quản trị Mini App và kiểm chứng luồng API, không tích hợp ứng dụng BIZ đang chạy.
