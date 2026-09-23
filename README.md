# supercharger-updates

Static hosting for the self-signed Lhotse Supercharger extension, used by customers who
force-install it on managed browsers through `ExtensionInstallForcelist`.

Served by Vercel at `https://extension.lhotse.io`.

- `public/index.html` is a short human-readable page with the policy entry.
- `public/update.xml` is the update manifest every managed browser polls.
  Its address never changes and is what customers put into their policy entry.
- `public/supercharger-<version>.crx` are the signed packages, one per version.

## Branches

- `releases` is the branch Vercel deploys to production. The "Sign CRX for policy install"
  workflow in `Lhotse-Technologies/Supercharger` pushes the signed files to it after every
  production release, using a deploy key. Nobody edits the extension files by hand.
- `main` is protected by the organisation rule that requires pull requests, which is why the
  workflow cannot push to it. Changes to the page itself go to `releases` through a pull request;
  `main` only mirrors the site scaffold.

To roll back a version, revert the publishing commit on `releases`.
