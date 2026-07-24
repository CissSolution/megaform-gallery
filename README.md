# MegaForm Template Gallery

Static template repository for **MegaForm** (DNN + Oqtane), served through the
**jsDelivr CDN** straight from this repo:

> **https://cdn.jsdelivr.net/gh/CissSolution/megaform-gallery@main/manifest.json**

> **Why jsDelivr and not GitHub Pages?** jsDelivr serves any *public* GitHub repo with a
> correct `application/json` content-type, global caching and no per-repo Pages setup —
> and GitHub Pages was not serving for this organisation. `raw.githubusercontent.com`
> also works and is always fresh, but it is rate-limited and not meant as a distribution
> CDN.
>
> ⚠️ **After pushing new templates, purge the CDN** or the update can lag by hours:
> `https://purge.jsdelivr.net/gh/CissSolution/megaform-gallery@main/manifest.json`
> (plus the changed `templates/...` files).

Licensed MegaForm installs read `manifest.json` from here and download templates on
demand (**Form Wizard → Template Gallery → Browse online**), so premium templates and
their artwork no longer have to ship inside the module package.

## What's in here

| Path | Purpose |
|---|---|
| `manifest.json` | The machine-readable feed the module reads. One entry per template. |
| `templates/<slug>.json` | The template itself. |
| `templates/<slug>-assets.zip` | That template's artwork (hero images), if it has any. |
| `index.html` | Human-friendly browse page. |

Every entry pins a **sha256** for both the template JSON and its assets zip. The module
**refuses** any download whose hash doesn't match the manifest, so the manifest and the
files must always be regenerated together — never hand-edit `manifest.json`.

## What ships in the package vs. what lives here

A fresh MegaForm install opens its Template Gallery with a **bundled shelf** — no network
needed, nothing locked on a trial:

- **31 quick-start starters** (`Samples/FormTemplates/QuickStart/`) — free, flagged
  `premium:false`, contact / booking / application / education / nonprofit / floating-label.
- **4 premium starters on display** — the only cards a trial install shows locked, as the
  upsell. They are chosen for having *no artwork*, so the package stays light.

Everything else — every remaining premium design **and all hero imagery** — is served from
this repo and downloaded on demand by licensed installs. That is what keeps ~14.6 MB of
artwork and ~2.4 MB of template JSON out of the shipped module.

## Adding or updating a template

1. Drop / edit the template `.json` in the **source** folder of the main solution:
   `Samples/FormTemplates/Premium/DONEE/`
2. Regenerate this repository:
   ```bash
   node tools/gallery/build-gallery.mjs --out <path-to-this-repo>
   ```
3. Commit + push, then **purge the jsDelivr cache** for `manifest.json` and every changed
   `templates/...` file (see the note at the top) — otherwise installs keep serving the
   previous version until the CDN expires it on its own.

The publisher will:

- validate every template (must have a valid `slug` and a `fields` array),
- **skip duplicate slugs** loudly rather than silently overwriting a previous template,
- **skip a template whose artwork is missing** from `Assets/img` — publishing it would ship
  a design with a dead hero image,
- bundle each template's referenced artwork into `<slug>-assets.zip`,
- recompute all hashes and **fail the build** if anything doesn't verify.

### Artwork

Templates reference images by absolute, platform-specific URLs:

- DNN — `/DesktopModules/MegaForm/Assets/img/<rel>`
- Oqtane — `/Modules/MegaForm/img/<rel>`

Both normalise to the same repo-relative key, so a single bundle serves both platforms
and the URLs baked into the template keep resolving after install. Put new images under
`Assets/img/` in the main solution and reference them with either URL form.

The zips are written with a fixed timestamp (STORE method), so rebuilding without
changing content produces **byte-identical** files — installs aren't forced to
re-download after every publish.

## Notes

- Downloads are performed **server-side** by the module (the browser never calls this
  repo), and the configured URL is SSRF-guarded.
- The gallery is a **licensed** feature: trial installs get an upgrade prompt instead.
- Repo URL is configurable per install — DNN host setting `MegaForm_GalleryRepoUrl`,
  Oqtane configuration key `MegaForm:GalleryRepoUrl`.
