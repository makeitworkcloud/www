# www

# About this repo

Serverless web content with GitHub Actions pushing changes to S3.

# Google Fonts

- https://fonts.google.com/

# W3.CSS Tutorial

- https://www.w3schools.com/w3css/

# Font Awesome Introduction

- https://www.w3schools.com/icons/fontawesome_icons_intro.asp

# CI and deployment

Pull requests run static pre-commit checks only. Pushes to `main` deploy the
repository's two source directories directly to their S3 buckets—there is no
site build step—using separate static AWS credentials and `aws s3 sync` with
`--delete --acl public-read --follow-symlinks`. After both syncs succeed, the
workflow purges the Cloudflare zone cache.
