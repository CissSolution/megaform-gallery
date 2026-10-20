---
{
  "templateGuideSlug": "tpl-insurance-enrollment",
  "slug": "insurance-enrollment",
  "theme": "custom",
  "rootSelector": ".mfp-mock11.mfp-insurance-enrollment",
  "tokenStyle": "double",
  "stepMechanism": "single",
  "stepAnchor": null,
  "stepCount": 1,
  "stepFieldKeys": [],
  "chipFields": [],
  "cardFields": [
    "coverage_type"
  ],
  "contentTokens": [],
  "colorVars": {},
  "lockedKeys": [
    "insured_name",
    "birth_date",
    "address",
    "phone_number",
    "email_address",
    "id_number",
    "occupation",
    "gender",
    "status",
    "coverage_type",
    "dependents",
    "annual_premium",
    "units",
    "payment_mode",
    "cash_application",
    "signature"
  ],
  "missingFieldPlaceholders": [],
  "shellTexts": [
    "&larr; Back to forms",
    "Secure Life",
    "Insurance Enrollment",
    "Individual policy application / Page 1 of 1",
    "A. General Questions",
    "Proposed insured's name *",
    "Birth date *",
    "Address",
    "Phone number",
    "Email address *",
    "ID number",
    "Occupation",
    "Gender",
    "Status",
    "B. Type of Health Coverage",
    "Dependents proposed for coverage",
    "C. Policy / Payment / Signature",
    "Annual premium",
    "Units",
    "Payment mode",
    "Cash with application",
    "Signature *",
    "Submit application"
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
  "customCssSha256": "42105100ccb11d5a58bd3d8d651d46eb22bb75d70ebf4412190c833f32766e67",
  "shellSha256": "6098b276d7e5eef399dacd7c490e61114e0a492156e2eb5500f4746ff1662a01"
}
---
# AI Edit Guide — Insurance Enrollment

Theme `custom` · root `.mfp-mock11.mfp-insurance-enrollment` · 16 fields · 1 steps (single).

Embedding: retain the unique `mf-template-insurance-enrollment` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


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
| insured_name | Text | input | - |  |
| birth_date | Date | input | - |  |
| address | Text | input | - |  |
| phone_number | Phone | input | - |  |
| email_address | Email | input | - |  |
| id_number | Text | input | - |  |
| occupation | Text | input | - |  |
| gender | Radio | choice | - | 2 |
| status | Radio | choice | - | 4 |
| coverage_type | Cards | cards | - | 3 |
| dependents | DataGrid | input | - |  |
| annual_premium | Text | input | - |  |
| units | Text | input | - |  |
| payment_mode | Radio | choice | - | 3 |
| cash_application | Text | input | - |  |
| signature | Text | input | - |  |

## Content tokens ({{content:*}} — editable text shown in the shell)
_(none — this template has no {{content:*}} tokens)_

## Editable shell text (hardcoded headings/labels — change via set_html_text, NOT customHtml)
Some visible text (hero heading, step labels, section/field captions) is baked into customHtml as plain text, NOT a field.label or token. To rebrand it, emit set_html_text with the EXACT current string (from this list) — it does a text-only swap that keeps the tag tree + CSS byte-identical:
- "&larr; Back to forms"
- "Secure Life"
- "Insurance Enrollment"
- "Individual policy application / Page 1 of 1"
- "A. General Questions"
- "Proposed insured's name *"
- "Birth date *"
- "Address"
- "Phone number"
- "Email address *"
- "ID number"
- "Occupation"
- "Gender"
- "Status"
- "B. Type of Health Coverage"
- "Dependents proposed for coverage"
- "C. Policy / Payment / Signature"
- "Annual premium"
- "Units"
- "Payment mode"
- "Cash with application"
- "Signature *"
- "Submit application"

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: coverage_type): `{op:"set_field_property", key:"coverage_type", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - _(none detected — fall back to --primary/--accent)_
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `42105100ccb1…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `42105100ccb11d5a…` · customHtml shell sha256 stays `6098b276d7e5eef3…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `custom`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
