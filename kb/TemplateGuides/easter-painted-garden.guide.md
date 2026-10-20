---
{
  "templateGuideSlug": "tpl-easter-painted-garden",
  "slug": "easter-painted-garden",
  "theme": "system",
  "rootSelector": ".mfp.mfp-easter-painted-garden",
  "tokenStyle": "double",
  "stepMechanism": "single",
  "stepAnchor": null,
  "stepCount": 1,
  "stepFieldKeys": [],
  "chipFields": [],
  "cardFields": [],
  "contentTokens": [],
  "colorVars": {
    "--mf-ink": "#204650",
    "--mf-action-ink": "#ffffff",
    "--mf-surface": "#fbfdfd",
    "--mf-muted": "#52696e",
    "--mf-line": "#a9c2c8",
    "--mf-control": "#ffffff",
    "--mf-action": "#a13e37",
    "--mf-focus": "#237887",
    "--mf-error": "#a82c43",
    "--mf-art": "#daedf1"
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
    "Easter egg hunt",
    "Spring, in full color",
    "Register your family to take part.",
    "Send registration",
    "Your organizer will confirm your place and event details."
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
  "customCssSha256": "f11119a236d03fc163a1303eaf36676a405ead97bddcafc054295a4ecedf7bdd",
  "shellSha256": "5c6a252ca7a03e8ed7df2b509b6ab8fcf042c90c59ec9ea48173da5a9558dd79"
}
---
# AI Edit Guide — Easter Painted Garden

Theme `system` · root `.mfp.mfp-easter-painted-garden` · 5 fields · 1 steps (single).

Embedding: retain the unique `mf-template-easter-painted-garden` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


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
- "Easter egg hunt"
- "Spring, in full color"
- "Register your family to take part."
- "Send registration"
- "Your organizer will confirm your place and event details."

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: none): `{op:"set_field_property", key:"<cardFieldKey>", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - `--mf-ink`: #204650
  - `--mf-action-ink`: #ffffff
  - `--mf-surface`: #fbfdfd
  - `--mf-muted`: #52696e
  - `--mf-line`: #a9c2c8
  - `--mf-control`: #ffffff
  - `--mf-action`: #a13e37
  - `--mf-focus`: #237887
  - `--mf-error`: #a82c43
  - `--mf-art`: #daedf1
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `f11119a236d0…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `f11119a236d03fc1…` · customHtml shell sha256 stays `5c6a252ca7a03e8e…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `system`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
