<div align="center">

<img src="https://cosignet.com/favicon.svg" width="72" height="72" alt="Cosignet" />

# Cosignet

**Critical Action Control — cryptographically-bound approvals.**

Cosignet pauses high-risk actions before they execute, asks for explicit passkey approval, and returns a signed decision bound to the exact action payload.

[![Website](https://img.shields.io/badge/website-cosignet.com-B4382E)](https://cosignet.com)
[![Docs](https://img.shields.io/badge/docs-read-9B7A45)](https://cosignet.com/docs)
[![Status](https://img.shields.io/badge/stage-early%20access-444)](https://cosignet.com/waitlist)
[![License](https://img.shields.io/badge/SDK-MIT-blue)](https://github.com/cosignet/sdk/blob/main/LICENSE)

[Live demo](https://cosignet.com/#demo) · [Dashboard demo](https://cosignet.com/app/demo) · [Docs](https://cosignet.com/docs) · [Security](https://cosignet.com/security) · [Request access](https://cosignet.com/waitlist)

</div>

---

## Why Cosignet

Automation, agents, and backend services increasingly execute real, irreversible operations — production deploys, fund transfers, data deletion, admin commands. The risky part isn't deciding, it's **executing**. A Slack button or "Are you sure?" only records a click; it isn't bound to what actually runs, and prompt injection can talk an agent or operator past a soft "yes".

Cosignet makes critical actions require an explicit, cryptographically-bound approval:

```
Critical action  →  passkey approval  →  signed decision  →  audit trail
```

The signature covers `nonce ‖ SHA-256(payload)`, so if the command, amount, recipient, endpoint, or payload changes after approval, the signed decision no longer matches. Approval becomes **evidence about a specific operation** — it complements IAM and audit logs, it doesn't replace them. Cosignet is an approval and evidence layer, not an executor or policy engine.

## What you get

- 🔐 **Passkey / WebAuthn approvals** — biometric user verification; the private key never leaves the approver's device.
- 🧾 **Payload-bound signatures + audit trail** — the raw assertion is stored as proof a specific approver signed a specific payload.
- 🧩 **Integrate in minutes** — MCP tool, REST API, or webhooks. No Docker, no rewrite.
- 🌐 **Works behind NAT/firewalls** — your code polls out; no inbound ports, public IP, or tunnels.

## Quickstart

```bash
curl -X POST https://cosignet.com/api/confirmations \
  -H "X-Api-Key: $COSIGNET_API_KEY" -H "content-type: application/json" \
  --data '{"username":"alex","action":"Wire transfer to vendor",
    "payload":{"to":"acct_8821","amount_usd":4200}}'
# → returns an approval URL; long-poll ?wait=25 for the signed decision
```

Or use the TypeScript SDK:

```ts
import { Cosignet } from "@cosignet/sdk";
const cosignet = new Cosignet({ apiKey: process.env.COSIGNET_API_KEY! });
const decision = await cosignet.requestApproval({
  username: "alex", action: "Wire transfer to vendor",
  payload: { to: "acct_8821", amount_usd: 4200 },
});
if (decision.status === "approved") { /* proceed — decision.rawAssertion is the proof */ }
```

## Repositories

| Repo | What |
|------|------|
| [**sdk**](https://github.com/cosignet/sdk) | Thin TypeScript client + CLI-approval recipe (gate `terraform destroy` & co. behind a passkey). |
| [**.github**](https://github.com/cosignet/.github) | This profile + org-wide community health files. |

> The hosted product runs at [cosignet.com](https://cosignet.com). The SDK and recipes are open source; the core service is currently closed during early access.

## Use it before automation or agents…

`deploy to production` · `transfer funds` · `delete or export data` · `rotate secrets` · `run admin commands` · `merge a high-risk PR` · `send customer emails`

## Links

- 🌐 Website — https://cosignet.com
- 📚 Docs — https://cosignet.com/docs
- 🛡️ Security & disclosure — https://cosignet.com/security · `security@cosignet.com`
- ✉️ Contact — `contact@cosignet.com`
<!-- - 💼 LinkedIn — https://www.linkedin.com/company/<add-when-live> -->

<!-- About / team: add founder bios + "who we are" here once ready. -->
