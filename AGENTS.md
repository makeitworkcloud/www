# Agent Instructions

Static website source for `makeitwork.cloud` and `onion.makeitwork.cloud`.

A successful push to `main` synchronizes both site directories with production using delete semantics and purges Cloudflare cache. Use scoped branches and PR CI for every change; never merge, dispatch, deploy, or purge without explicit confirmation.

Keep public content free of secrets, tokens, private endpoints, and personal data.
