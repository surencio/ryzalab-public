# SECURITY.md

Last updated: 2026-03-03

## TL;DR

- Never commit secrets.
- Treat your HA config like infrastructure.
- Assume anything in a public repo will be read by strangers.

## Secrets Handling

- Use config/secrets.yaml for sensitive values.
- Keep secrets.yaml out of Git (see .gitignore).
- If a secret leaks, rotate it immediately.

## Tokens and .storage

Do not commit config/.storage/. It can contain authentication tokens and other sensitive metadata.

## Recommendations

- Use strong passwords and MFA on your Git provider.
- Restrict HA remote access and prefer VPN-based access.
- Keep Home Assistant updated.

## If You Leaked Something

1. Rotate the secret.
2. Rewrite git history if needed (advanced).
3. Assume compromise until proven otherwise.
