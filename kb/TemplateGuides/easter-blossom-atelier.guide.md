---
{
  "templateGuideSlug": "tpl-easter-blossom-atelier",
  "slug": "easter-blossom-atelier",
  "theme": "system",
  "rootSelector": ".mfp.mfp-easter-blossom-atelier",
  "tokenStyle": "double",
  "stepMechanism": "single",
  "stepAnchor": null,
  "stepCount": 1,
  "stepFieldKeys": [],
  "chipFields": [],
  "cardFields": [],
  "contentTokens": [],
  "colorVars": {
    "--mf-ink": "#302731",
    "--mf-action-ink": "#ffffff",
    "--mf-surface": "#fffdfd",
    "--mf-muted": "#6e606b",
    "--mf-line": "#d9c9d0",
    "--mf-control": "#ffffff",
    "--mf-action": "#70384d",
    "--mf-focus": "#2c7370",
    "--mf-error": "#ad273d",
    "--mf-tint": "#f7eef2"
  },
  "lockedKeys": [
    "guardian_name",
    "guardian_email",
    "number_of_children",
    "child_age_group",
    "accommodation_note"
  ],
  "missingFieldPlaceholders": [],
  "shellTexts": [
    "Easter registration",
    "A little wonder in bloom",
    "Register your family for the Easter egg hunt.",
    "Your contact details",
    "Your little explorers",
    "Send registration",
    "Your organizer will confirm your place, event date, and location."
  ],
  "allowedOps": [
    "set_form_meta",
    "set_field_property",
    "set_html_text",
    "add_field",
    "remove_field"
  ],
  "forbiddenOps": [
    "replace_form_schema",
    "set customHtml/customCss/theme"
  ],
  "immutable": [
    "customHtml structure (tag tree + classes)",
    "customCss (byte-invariant)",
    "settings.theme",
    "field keys"
  ],
  "customCssSha256": "0ba54d5dd308d0f10af6bde086c8d7baa9d8a08d4a6cf26d561de4ac8dad1c2a",
  "shellSha256": "5dde25cc4720fe2556badd73b4d1da50e520dd52c29167f14fa21e4fb7a4c70c"
}
---
# AI Edit Guide — Easter Blossom Atelier

Theme `system` · root `.mfp.mfp-easter-blossom-atelier` · 5 fields · 1 steps (single).

Embedding: retain the unique `mf-template-easter-blossom-atelier` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


## DETERMINISTIC EDIT PROTOCOL (follow exactly — do NOT improvise structure/CSS)
This is a PREMIUM form. Its look lives in `settings.customHtml` + `settings.customCss` + `settings.theme`, which are **IMMUTABLE**. You may ONLY emit these ops, and ONLY against keys/tokens listed in the frontmatter map:
- `set_form_meta` — title, description, submitButtonText, successMessage, `customContent.<token>`, or `themeCssOverrides` (color only).
- `set_field_property` — label / placeholder / required / options (on an EXISTING key).
- `add_field` — append a new field (the dispatcher injects its `{{field:KEY}}` into the right panel).
- `remove_field` — delete a field + its token.
NEVER emit `customHtml`, `customCss`, `theme`, or `replace_form_schema` for this form. NEVER rename a key in `lockedKeys`. Emit `designDecision:"preserve"` on every op.

## Field map
| key | type | display | step | options |
|-----|------|---------|------|---------|
| guardian_name | Text | input | - |  |
| guardian_email | Email | input | - |  |
| number_of_children | Select | choice | - | 6 |
| child_age_group | Select | choice | - | 5 |
| accommodation_note | Textarea | input | - |  |

## Content tokens ({{content:*}} — editable text shown in the shell)
_(none — this template has no {{content:*}} tokens)_

## Editable shell text (hardcoded headings/labels — change via set_html_text, NOT customHtml)
Some visible text (hero heading, step labels, section/field captions) is baked into customHtml as plain text, NOT a field.label or token. To rebrand it, emit set_html_text with the EXACT current string (from this list) — it does a text-only swap that keeps the tag tree + CSS byte-identical:
- "Easter registration"
- "A little wonder in bloom"
- "Register your family for the Easter egg hunt."
- "Your contact details"
- "Your little explorers"
- "Send registration"
- "Your organizer will confirm your place, event date, and location."

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: none): `{op:"set_field_property", key:"<cardFieldKey>", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - `--mf-ink`: #302731
  - `--mf-action-ink`: #ffffff
  - `--mf-surface`: #fffdfd
  - `--mf-muted`: #6e606b
  - `--mf-line`: #d9c9d0
  - `--mf-control`: #ffffff
  - `--mf-action`: #70384d
  - `--mf-focus`: #2c7370
  - `--mf-error`: #ad273d
  - `--mf-tint`: #f7eef2
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `0ba54d5dd308…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `0ba54d5dd308d0f1…` · customHtml shell sha256 stays `5dde25cc4720fe25…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `system`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
