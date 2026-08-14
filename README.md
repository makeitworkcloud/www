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

This static issuer is for Kubernetes ServiceAccount tokens used by AWS STS; it
is not the human kubectl login provider and does not expose the cluster API.
Maintainer kubectl access uses Cloudflare Access plus ArgoCD Dex as documented
in the
[`kustomize-cluster` README](https://github.com/makeitworkcloud/kustomize-cluster#kubectl-access).

# CI and deployment

Pull requests run static pre-commit checks only. Pushes to `main` deploy the
repository's two source directories directly to their S3 buckets—there is no
site build step—using separate static AWS credentials and `aws s3 sync` with
`--delete --acl public-read --follow-symlinks`. After both syncs succeed, the
workflow purges the Cloudflare zone cache.
