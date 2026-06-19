# www

# About this repo

Serverless web content with GitHub Actions pushing changes to S3.

# Google Fonts

- https://fonts.google.com/

# W3.CSS Tutorial

- https://www.w3schools.com/w3css/

# Font Awesome Introduction

- https://www.w3schools.com/icons/fontawesome_icons_intro.asp

# Static OIDC issuer

`makeitwork.cloud/oidc/` hosts public static Kubernetes ServiceAccount OIDC
discovery metadata for future AWS STS web-identity authentication from the k3s
cluster.

- Issuer: `https://makeitwork.cloud/oidc`
- Discovery: `https://makeitwork.cloud/oidc/.well-known/openid-configuration`
- JWKS: `https://makeitwork.cloud/oidc/openid/v1/jwks`

The JWKS file must contain only public key material for the k3s ServiceAccount
token signing key. Never commit the private signing key, AWS credentials, KMS key
IDs, kubeconfigs, or decrypted SOPS values here.
