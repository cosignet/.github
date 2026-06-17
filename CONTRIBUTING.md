# Contributing to Cosignet

Thanks for your interest! The hosted service is currently closed-source during
early access, but the **SDK** and **recipes** are open and we welcome
contributions there.

## Ways to help

- 🐛 Report bugs or rough edges (use the issue templates).
- 💡 Propose SDK ergonomics, new recipes (LangChain/CrewAI/MCP/CLI), or docs.
- 🔌 Build integrations that gate high-risk agent actions behind approval.

## Development (SDK)

```bash
git clone https://github.com/cosignet/sdk
cd sdk
npm install
npm run typecheck   # or: npm run build
```

## Pull requests

1. Open an issue first for anything non-trivial so we can align on approach.
2. Keep PRs focused; match the existing code style.
3. Add/adjust types and a short note in the README if behavior changes.
4. Be honest in copy and docs — describe cryptographic binding, never claim
   "unbreakable".

## Security

Do **not** file security issues publicly — see [SECURITY.md](SECURITY.md)
(report to `security@cosignet.com`).

By contributing you agree your contributions are licensed under the repository's
license (MIT for the SDK).
