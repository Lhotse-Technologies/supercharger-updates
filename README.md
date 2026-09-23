# supercharger-updates

Static hosting for the self-signed Lhotse Supercharger extension, used by customers who
force-install it on managed browsers through `ExtensionInstallForcelist`.

Served by Vercel at `https://extension.lhotse.io`.

- `public/index.html` is a short human-readable page with the policy entry.
- `public/update.xml` is the update manifest every managed browser polls.
  Its address never changes and is what customers put into their policy entry.
- `public/supercharger-<version>.crx` are the signed packages, one per version.

Nobody edits this repo by hand. The "Sign CRX for policy install" workflow in
`Lhotse-Technologies/Supercharger` pushes the files here after every production release,
and Vercel deploys the commit. To roll back a version, revert the commit.
