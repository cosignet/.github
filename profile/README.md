<div align="center">

<img src="https://cosignet.com/favicon.svg" width="72" height="72" alt="Cosignet" />

# Cosignet

**Verifiable action authorization for AI agents.**

Cosignet gives agents, automations, and backends a passkey-signed human decision bound to the exact action payload before a payment, production change, deletion, or administrative action proceeds.

[![Website](https://img.shields.io/badge/website-cosignet.com-B4382E)](https://cosignet.com)
[![Docs](https://img.shields.io/badge/docs-read-9B7A45)](https://cosignet.com/docs)
[![Status](https://img.shields.io/badge/status-public-2E7D32)](https://status.cosignet.com)
[![License](https://img.shields.io/badge/SDK-MIT-blue)](https://gitlab.com/cosignet/sdk/-/blob/main/LICENSE)

[Try the live demo](https://cosignet.com/#demo) · [Dashboard demo](https://cosignet.com/app/demo) · [Start free](https://cosignet.com/waitlist?plan=free) · [Docs](https://cosignet.com/docs) · [Security](https://cosignet.com/security)

</div>

---

## Why Cosignet

Platform-native approval can pause a tool call. Cosignet adds a portable authorization and evidence layer for actions that cross systems or organizational boundaries: a specific human signs a decision bound to the exact payload, and the resulting receipt can be verified independently of the agent platform.

```
Critical action  →  passkey approval  →  signed decision  →  verifiable receipt
```

The signature covers `nonce ‖ SHA-256(payload)`. If the command, amount, recipient, endpoint, or payload changes after approval, the signed decision no longer matches. Cosignet complements IAM, policy engines, and audit logs; it does not execute the action or guarantee that an integrator applies the approved payload.

## What you get

- 🔐 **Passkey / WebAuthn approvals**: biometric user verification; the private key never leaves the approver's device.
- 🧾 **Payload-bound signatures and audit evidence**: proof that a specific approver signed a specific payload.
- 🔎 **Independent verification**: open-source verifiers and a public transparency log.
- 🧩 **Integrate in minutes**: MCP tool, REST API, TypeScript/Python clients, or portable recipes.
- 🌐 **Works behind NAT and firewalls**: long-poll over outbound HTTPS; no inbound port or tunnel required.

## Quickstart

```bash
curl -X POST https://cosignet.com/api/confirmations \
  -H "X-Api-Key: $COSIGNET_API_KEY" -H "content-type: application/json" \
  --data '{"username":"alex","action":"Wire transfer to vendor",
    "payload":{"to":"acct_8821","amount_usd":4200}}'
# Returns an approval URL; long-poll ?wait=25 for the signed decision.
```

Or use the TypeScript SDK:

```ts
import { Cosignet } from '@cosignet/sdk';

const cosignet = new Cosignet({ apiKey: process.env.COSIGNET_API_KEY! });
const decision = await cosignet.requestApproval({
  username: 'alex',
  action: 'Wire transfer to vendor',
  payload: { to: 'acct_8821', amount_usd: 4200 },
});

if (decision.status === 'approved') {
  // Verify the decision against the operation, then proceed.
}
```

## Public repositories

| Repository | Purpose |
|------------|---------|
| [**cosignet/sdk on GitLab**](https://gitlab.com/cosignet/sdk) | Canonical SDK, examples, recipes, security documentation, issues, and merge requests. |
| [**cosignet/sdk on GitHub**](https://github.com/cosignet/sdk) | Read-only downstream mirror for discovery and easier consumption. |
| [**cosignet/.github**](https://github.com/cosignet/.github) | GitHub organization profile and community routing. |

> GitLab is the source of truth for public development. Please report bugs, request features, and open merge requests at [gitlab.com/cosignet/sdk](https://gitlab.com/cosignet/sdk). The hosted product remains private; only the SDK, examples, recipes, and verification material are open source.

## Use it before agents or automation

`deploy to production` · `transfer funds` · `issue a large refund` · `delete or export data` · `rotate secrets` · `change access rights` · `run administrative commands`

## Links

- 🌐 Website: https://cosignet.com
- 📚 Documentation: https://cosignet.com/docs
- 🟢 Service status: https://status.cosignet.com
- 🛡️ Security and disclosure: https://cosignet.com/security · `security@cosignet.com`
- 🦊 Canonical SDK and issue tracker: https://gitlab.com/cosignet/sdk
- 🐙 GitHub mirror: https://github.com/cosignet/sdk
- ✉️ Contact: `contact@cosignet.com`
