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
- `main` exists only because GitHub needs a default branch and the organisation rule protects
  it, which is why the workflow cannot push there. Nothing deploys from it and nothing needs to be
  kept in sync with it. Changes to the page itself go to `releases`.

To roll back a version, revert the publishing commit on `releases`.
