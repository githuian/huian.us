# huian.us

Static personal site on GitHub Pages (custom domain via `CNAME`). The
homepage `index.html` lists small single-purpose apps under `apps/`, plus
external links (Inventory at inventory.huian.us, the Chess Coach Chrome
extension). `privacy/index.html` is the privacy policy used by the Play
Store, App Store and Chrome Web Store listings.

## Deploy

GitHub Pages serves straight from the `main` branch: pushing to `main` **is**
the deploy and goes live in about 30 seconds. There is no build step. (The
workflows in `.github/workflows/static*.yml` target a `TeslaDisplay` branch
that no longer exists, so they never run.) Pushing is a live, visible
action; confirm before running it unless already asked to.

## Versioning & releases

Same policy as the Inventory apps. **Semver bump policy, effective every
deploy:** a push that ships only fixes or wording tweaks bumps the **patch**
number; one that adds or removes an app, page or feature bumps **minor**
(reset patch to 0); consider **major** for a redesign or other large change.
Bump the version **before** pushing, not after.

The version lives in exactly one place: `<span id="site-version">` in the
homepage footer (`index.html`). Every bump is committed, tagged `vX.Y.Z` and
pushed with the tag (`git push origin main --follow-tags` after
`git tag -a vX.Y.Z -m ...`), then released on GitHub
(`gh release create vX.Y.Z` on `githuian/huian.us`) with curated notes
grouped by app or page, not auto-generated ones. Don't let the footer
version drift ahead of what's tagged.

## Privacy policy

`privacy/index.html` describes what each app actually collects, written from
the code. When an app is added, removed or starts sending data somewhere
new, update its section and the "Effective" date in the same commit.
