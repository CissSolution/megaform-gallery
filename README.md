# MegaForm Online Gallery

Shared portable templates for **DNN, Oqtane and Umbraco**.

The canonical feed is [manifest.json](https://CissSolution.github.io/megaform-gallery/manifest.json).
The [browse page](https://CissSolution.github.io/megaform-gallery/) lists the same catalog.
The 2026-10-20 portable-template release preserves all 82 slugs.

Each template JSON contains its own uniquely scoped pane, CSS and inline styles,
pane-width container queries and namespaced animations. Separate outer page canvases
are transparent; the actual cards retain their authored colors. Templates contain no
demo-site form IDs. Platform adapters map the full relative image path to their own
asset root, avoiding collisions between files such as `hero.webp`.

Every manifest entry pins the exact SHA-256 and size of the JSON, optional artwork ZIP,
and AI knowledge bundle. Guides/facts are regenerated from the same source and carry
the updated shell hashes. Downloads and hash checks happen on the module server.
Keep manifest, templates, assets and KB files from the same generated release.

Authoring source: `Samples/FormTemplates/Premium/GALLERY-PUBLISHED/` in the main solution.
Run the portable-template normalizer and tests, regenerate template facts/guides, then
publish using `tools/gallery/Publish-Gallery.ps1`. Do not edit generated payloads here.
Publishing refuses missing artwork, invalid hashes, unnormalized templates and unintended
removed slugs. The demo catalog retains its locked order across releases.

GitHub Pages serves this repository. There is no jsDelivr purge step. Consumers cache
the manifest for up to 15 minutes; use the module's gallery refresh to fetch it sooner.
Refreshing the catalog does not overwrite existing forms or their submissions.

The module also includes 32 free quick-start templates and four premium starters for
offline discovery. Licensed installations download the remaining premium designs and
their artwork from this feed. Licensing is handled by the module; this repository
contains no production license file or credentials.
