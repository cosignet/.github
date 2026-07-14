# Contributing to Cosignet

Thanks for your interest. The hosted service is private, while the **SDK**, examples, recipes, and verification material are open source.

## Canonical development home

Public development happens on GitLab:

- Source, issues, and merge requests: <https://gitlab.com/cosignet/sdk>
- GitHub is a read-only downstream mirror for discovery.

Please do not open GitHub pull requests or issues; they cannot be merged back into the canonical workflow.

## Ways to help

- Report bugs or rough edges through the GitLab issue templates.
- Propose SDK ergonomics, integrations, examples, recipes, or documentation.
- Build integrations that gate high-risk agent actions behind payload-bound approval.

## Development

```bash
git clone https://gitlab.com/cosignet/sdk.git
cd sdk
npm install
npm run typecheck
npm run build
```

## Merge requests

1. Open a GitLab issue first for anything non-trivial so we can align on approach.
2. Keep merge requests focused and match the existing style.
3. Add or adjust types and update the README when behavior changes.
4. Describe cryptographic binding precisely; never claim the system is "unbreakable".

## Security

Do **not** file security issues publicly. See [SECURITY.md](SECURITY.md) and report privately to `security@cosignet.com`.

By contributing, you agree that your contribution is licensed under the repository's license (MIT for the SDK).
