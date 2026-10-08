**Collaborator:** aidlc-quality-agent

## Contribution

The draft's test-after proposal fits a greenfield local demo and the Standard strategy. Keep the 80% line-coverage floor as an explicit target, but define its denominator before implementation: backend production code and any frontend production code included in the MVP, excluding generated sources and test fixtures. Require repeatable API scenarios for login, create/update, permission checks, version and forceUpdate fields, plus Redis/PostgreSQL integration checks. CI should run formatter, unit tests, integration tests, API scenarios and coverage before merge; the local Docker Compose demonstration remains separate from CI deployment.

The interview should confirm whether API scenarios are the repeatable acceptance evidence and how local services are reset between runs. It should not re-open the already approved mock-only scope.

## Positions

- AGREE: Keep test-after as the proposed default; the team has not yet affirmed another methodology.
- AGREE: Preserve the Standard strategy and 80% floor while making the measured code boundary explicit.
- OBJECT: Do not describe a staging deployment as a requirement for this local-only demo.
