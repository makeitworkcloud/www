# Make IT Work web portal

This repository contains the static content for `makeitwork.cloud` and
`onion.makeitwork.cloud`. There is no application server or site build step;
the source directories are deployed as-is.

## Technology

- **HTML5:** `makeitwork.cloud/index.html` is the public portal and
  `onion.makeitwork.cloud/index.html` is the onion-services directory.
- **CSS:** The public portal uses an embedded stylesheet and locally hosted
  Web437 bitmap fonts. It does not use W3.CSS or Google Fonts.
- **Icons:** Font Awesome 7.3.0 is loaded from cdnjs for portal and contact
  icons.
- **Progressive web app:** `makeitwork.cloud/site.webmanifest` provides
  install metadata, and `makeitwork.cloud/sw.js` provides a network-first
  service worker with an offline cache fallback for same-origin assets.
- **Metadata:** The public portal includes standard Open Graph and Twitter
  metadata plus Schema.org JSON-LD.
- **Feed:** `makeitwork.cloud/feed.xml` is a hand-maintained Atom feed of
  site updates, advertised from the portal head for feed-reader discovery.
  Entry ids are permanent tag URIs and must not be reused or changed.

## References

- [HTML and CSS — MDN Web Docs](https://developer.mozilla.org/docs/Web)
- [Font Awesome](https://fontawesome.com/)
- [Web app manifests — MDN Web Docs](https://developer.mozilla.org/docs/Web/Progressive_web_apps/Manifest)
- [Service Worker API — MDN Web Docs](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)
- [Schema.org](https://schema.org/)

## CI and deployment

Pull requests run static pre-commit checks only. A push to `main` deploys both
source directories directly to their S3 buckets using `aws s3 sync` with
`--delete --acl public-read --follow-symlinks`. After both syncs succeed, the
workflow purges the Cloudflare zone cache. Deployment uses separate GitHub
Actions secrets for the public and onion buckets.

## Local validation

```sh
pre-commit run --all-files
node --check makeitwork.cloud/sw.js
```
