**Collaborator:** aidlc-devsecops-agent

## Contribution

For this mock-only local demo, apply proportionate controls: no real credentials or customer data, secrets supplied through local environment configuration, dependency and vulnerability checks in CI, formatter/linter checks before merge, and static analysis where the selected Java toolchain supports it. API errors should avoid tokens, connection strings and stack traces. A full production DAST or deployment-control requirement is outside the approved scope; the repeatable API script and container configuration should still be reviewed for accidental secret or endpoint leakage.

The interview should confirm the selected formatter/linter, dependency scanning command, and the rule that demo data is reset without using real systems.

## Positions

- AGREE: Keep security controls focused on protecting mock credentials, data and local configuration.
- AGREE: Run dependency and static checks in CI where available.
- OBJECT: Do not add production compliance or cloud deployment obligations to this demo.
