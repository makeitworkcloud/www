# Agent Instructions

Static website source for `makeitwork.cloud` and `onion.makeitwork.cloud`.

A successful push to `main` synchronizes both site directories with production using delete semantics and purges Cloudflare cache. Use scoped branches and PR CI for every change; never merge, dispatch, deploy, or purge without explicit confirmation.

Use the configured GitHub and documentation MCP integrations. Do not assume a local context-mode plugin, local checkout, shell tooling, or production credentials. Keep public content free of secrets, tokens, private endpoints, and personal data.
