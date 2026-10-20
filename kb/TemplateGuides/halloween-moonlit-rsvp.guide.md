---
{
  "templateGuideSlug": "tpl-halloween-moonlit-rsvp",
  "slug": "halloween-moonlit-rsvp",
  "theme": "system",
  "rootSelector": ".mfp.mfp-halloween-moonlit-rsvp",
  "tokenStyle": "double",
  "stepMechanism": "single",
  "stepAnchor": null,
  "stepCount": 1,
  "stepFieldKeys": [],
  "chipFields": [],
  "cardFields": [],
  "contentTokens": [],
  "colorVars": {
    "--mf-ink": "#f3f4ef",
    "--mf-action-ink": "#25251f",
    "--mf-surface": "#142922",
    "--mf-muted": "#bbc8c0",
    "--mf-line": "#4a6155",
    "--mf-control": "#20382d",
    "--mf-action": "#ffc08b",
    "--mf-focus": "#d4c4f5",
    "--mf-error": "#ffb4b4"
  },
  "lockedKeys": [
    "full_name",
    "email",
    "party_size",
    "costume_plan",
    "access_note"
  ],
  "missingFieldPlaceholders": [],
  "shellTexts": [
    "October 31 · Halloween",
    "Join the moonlit gathering",
    "A little mystery, a little magic. Share your RSVP below.",
    "Send my RSVP",
    "Your organizer will confirm attendance, time, and location."
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
  "customCssSha256": "1084aebf9d07bfaa149e31cee19cd40c4045af4ddc9ce904c6a4f99880f8f827",
  "shellSha256": "6677c8176c1dfcb91838e809572676adb64159448cb36391f6be4ee0098c9176"
}
---
# AI Edit Guide — Halloween Moonlit RSVP

Theme `system` · root `.mfp.mfp-halloween-moonlit-rsvp` · 5 fields · 1 steps (single).

Embedding: retain the unique `mf-template-halloween-moonlit-rsvp` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


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
| full_name | Text | input | - |  |
| email | Email | input | - |  |
| party_size | Select | choice | - | 6 |
| costume_plan | Select | choice | - | 4 |
| access_note | Textarea | input | - |  |

## Content tokens ({{content:*}} — editable text shown in the shell)
_(none — this template has no {{content:*}} tokens)_

## Editable shell text (hardcoded headings/labels — change via set_html_text, NOT customHtml)
Some visible text (hero heading, step labels, section/field captions) is baked into customHtml as plain text, NOT a field.label or token. To rebrand it, emit set_html_text with the EXACT current string (from this list) — it does a text-only swap that keeps the tag tree + CSS byte-identical:
- "October 31 · Halloween"
- "Join the moonlit gathering"
- "A little mystery, a little magic. Share your RSVP below."
- "Send my RSVP"
- "Your organizer will confirm attendance, time, and location."

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: none): `{op:"set_field_property", key:"<cardFieldKey>", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - `--mf-ink`: #f3f4ef
  - `--mf-action-ink`: #25251f
  - `--mf-surface`: #142922
  - `--mf-muted`: #bbc8c0
  - `--mf-line`: #4a6155
  - `--mf-control`: #20382d
  - `--mf-action`: #ffc08b
  - `--mf-focus`: #d4c4f5
  - `--mf-error`: #ffb4b4
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `1084aebf9d07…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `1084aebf9d07bfaa…` · customHtml shell sha256 stays `6677c8176c1dfcb9…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `system`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
