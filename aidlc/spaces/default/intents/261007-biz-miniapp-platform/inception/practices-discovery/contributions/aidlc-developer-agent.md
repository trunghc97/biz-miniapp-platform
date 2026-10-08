**Collaborator:** aidlc-developer-agent

## Contribution

For Java 21 and Spring Boot 4, organize code by the user-facing Mini App administration capability, with clear controller, application/service, persistence and mock-session boundaries. Keep DTOs at the API boundary, validate input before persistence, and return stable error bodies without leaking stack traces or SessionId values. Use one formatter and linter configuration committed with the project, and keep names idiomatic Java. The interview should confirm the package boundary and error-response convention without changing the approved product scope.

## Positions

- AGREE: Keep the backend technology constraint unchanged.
- AGREE: Use explicit boundaries between API, business logic, persistence and mock session access.
- OBJECT: Avoid selecting a frontend framework or a production integration convention before the API-first scope is designed.
