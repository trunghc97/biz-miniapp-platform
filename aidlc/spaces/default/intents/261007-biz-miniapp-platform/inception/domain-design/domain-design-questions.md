# Domain Design Questions

## Component boundaries

Which logical building blocks should own the MVP behavior?

- A. Auth/session, MiniApp configuration, and Admin UI components
- B. One combined Admin component plus an API adapter
- C. Other (please specify)

[Answer]:

## Entity ownership

Which component should own each entity?

- A. AuthSession and MockPermission → AuthSessionComponent; MiniAppConfig → MiniAppConfigComponent
- B. All entities → AdminComponent
- C. Other (please specify)

[Answer]:

## Component responsibilities

Should business validation and stable error behavior live in the owning domain component, with UI limited to presentation and client feedback?

- A. Yes
- B. Put validation primarily in the UI
- C. Other (please specify)

[Answer]:

## Interactions

How should components interact in the MVP?

- A. Admin UI calls AuthSession and MiniAppConfig synchronously through clear interfaces
- B. Components communicate through asynchronous events
- C. Other (please specify)

[Answer]:

## UI structure

Should the UI component own the three refined screens and delegate all persistence/session decisions to domain components?

- A. Yes
- B. Let UI directly access PostgreSQL/Redis adapters
- C. Other (please specify)

[Answer]:
