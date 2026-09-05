# Make IT Work web portal

This repository contains the static content for `makeitwork.cloud` and
`onion.makeitwork.cloud`. There is no application server or site build step;
the source directories are deployed as-is.

## Technology

- **HTML5:** `makeitwork.cloud/index.html` is the public portal and
  `onion.makeitwork.cloud/index.html` is the onion-services directory.
- **CSS:** The public portal uses an embedded stylesheet whose design tokens
  are adapted from the OpenCode web client dark theme: layered grey surfaces
  over a near-black page, white-alpha borders, and a blue accent. It does not
  use W3.CSS or Google Fonts.
- **Fonts:** Inter and JetBrains Mono are external UI/command fonts; the iconic IBM EGA 8x8 title font loads through an immutable jsDelivr URL pinned to the historical `www` revision.
- **Icons:** Font Awesome 7.3.0 is loaded from cdnjs for portal and contact
  icons.
- **Progressive web app:** `makeitwork.cloud/site.webmanifest` provides
  install metadata, and `makeitwork.cloud/sw.js` provides a network-first
  service worker with an offline cache fallback for same-origin assets.
- **Metadata:** The public portal includes standard Open Graph and Twitter
  metadata plus Schema.org JSON-LD.

## References

- [HTML and CSS — MDN Web Docs](https://developer.mozilla.org/docs/Web)
- [Font Awesome](https://fontawesome.com/)
- [Fontsource CDN](https://fontsource.org/docs/getting-started/cdn)
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
