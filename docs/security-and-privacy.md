# Security and privacy

## Trust boundaries

- Kiosk users are untrusted for administrative operations.
- A client device is authenticated but should not be trusted to authorize server-side actions.
- Administrators receive role-scoped server capabilities.
- Transport security and identity validation are enforced independently.

## Controls represented in the design

- TLS for client/server communications
- Encrypted storage for sensitive local configuration
- PIN-gated, time-bounded local administration
- Role-based access control for central operations
- Audit records for configuration and administrative actions
- Windows kiosk lockdown to limit access outside the application
- Alerting for missed heartbeats and stale backup state

## Privacy approach

Operational monitoring should collect the minimum data needed to identify a managed endpoint and evaluate backup health. Patient or clinical content is not part of the monitoring contract. Logs and audit records should avoid secret values and follow an explicit retention policy.

## Portfolio sanitization

This public repository contains no security configuration that could be replayed against a deployed environment. Certificate procedures, endpoint addresses, bypass utilities, internal diagrams, and operational screenshots remain private.
