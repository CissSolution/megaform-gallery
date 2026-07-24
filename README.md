# MegaForm Template Gallery

Static template repository for **MegaForm** (DNN + Oqtane), served from GitHub Pages:

> **https://cissolution.github.io/megaform-gallery/**

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

## Adding or updating a template

1. Drop / edit the template `.json` in the **source** folder of the main solution:
   `Samples/FormTemplates/Premium/DONEE/`
2. Regenerate this repository:
   ```bash
   node tools/gallery/build-gallery.mjs --out <path-to-this-repo>
   ```
3. Commit + push. GitHub Pages republishes automatically.

The publisher will:

- validate every template (must have a valid `slug` and a `fields` array),
- **skip duplicate slugs** loudly rather than silently overwriting a previous template,
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
