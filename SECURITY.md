# Security Policy

Cosignet is a control for high-risk AI-agent actions, so we take reports seriously.

## Reporting a vulnerability

Email **security@cosignet.com** with steps to reproduce and impact. Please do
**not** open a public issue for security reports.

- We aim to acknowledge within a few business days.
- Test only against your own account and data. Do not access other tenants'
  data, run denial-of-service, or send approval requests to real people.
- We won't pursue good-faith research that follows these rules.

A machine-readable policy is published at
<https://cosignet.com/.well-known/security.txt>, and our full security posture
(approval integrity, fail-closed behavior, data handling, retention) is at
<https://cosignet.com/security>.

## Scope

In scope: the hosted service at `cosignet.com`, the public SDK, and recipes.
Especially valuable: human-approval bypass, payload-binding/WYSIWYS issues,
passkey/WebAuthn verification flaws, and tenant-isolation gaps.
