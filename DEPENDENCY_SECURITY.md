# Dependency security

Previously this repository tracked 11,449 files in backend and frontend `node_modules` directories. These generated artifacts are removed from the new Git tree; lockfiles remain for reproducible installs.

To set up the project after merging:

```sh
cd backend && npm ci
cd ../my-react-frontend && npm ci
```

- Never commit `node_modules`. Let CI install from the committed lockfiles.
- Review and apply dependency updates regularly; removing copied dependency trees does **not** automatically update vulnerable versions inside `package-lock.json`.
- For a full security review, run `npm audit --audit-level=high` separately in both directories and triage fixes (including breaking changes) through tested PRs.
- Historical commits still contain old dependency copies; this cleanup targets the tracked working tree, not Git object history.
