---
{
  "templateGuideSlug": "tpl-event-registration-premium",
  "slug": "event-registration-premium",
  "theme": "custom",
  "rootSelector": ".mfp-mock11.mfp-event-registration-premium",
  "tokenStyle": "double",
  "stepMechanism": "single",
  "stepAnchor": null,
  "stepCount": 1,
  "stepFieldKeys": [],
  "chipFields": [],
  "cardFields": [],
  "contentTokens": [],
  "colorVars": {},
  "lockedKeys": [
    "full_name",
    "date_of_birth",
    "gender",
    "phone_number",
    "email_address",
    "company",
    "heard_from",
    "ticket_count",
    "payment_method",
    "signature",
    "date_signed",
    "consent"
  ],
  "missingFieldPlaceholders": [],
  "shellTexts": [
    "&larr; Back to forms",
    "Event Registration Form",
    "Design Forward Summit / October 15, 2028",
    "About Event",
    "Event Name",
    "Design Forward Summit",
    "Date",
    "October 15, 2028",
    "Venue",
    "Grand Hall, 214 Harbor Avenue",
    "Oct 15, 2028",
    "9:00 AM - 5:00 PM",
    "Grand Hall",
    "Participant Information",
    "Full Name *",
    "Date of Birth",
    "Gender",
    "Phone Number",
    "Email *",
    "Company / Organization",
    "Where did you hear about this event?",
    "Payment and Consent",
    "Number of Tickets *",
    "Payment Method *",
    "Signature *",
    "Date Signed",
    "Complete registration",
    "Webinar Pros LLC / 555-0100 / events@example.com"
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
  "customCssSha256": "19e1aa2782643994c53400bada26cc628c8e3af8076c57cc3251d984469d1b85",
  "shellSha256": "e73e5916ca0c1f9a26970781d0aa0aee850d8fa1228fdb093864f80988f28858"
}
---
# AI Edit Guide — Event Registration Premium

Theme `custom` · root `.mfp-mock11.mfp-event-registration-premium` · 12 fields · 1 steps (single).

Embedding: retain the unique `mf-template-event-registration-premium` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


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
| date_of_birth | Date | input | - |  |
| gender | Select | choice | - | 4 |
| phone_number | Phone | input | - |  |
| email_address | Email | input | - |  |
| company | Text | input | - |  |
| heard_from | Radio | choice | - | 5 |
| ticket_count | Text | input | - |  |
| payment_method | Radio | choice | - | 4 |
| signature | Text | input | - |  |
| date_signed | Date | input | - |  |
| consent | Checkbox | choice | - | 1 |

## Content tokens ({{content:*}} — editable text shown in the shell)
_(none — this template has no {{content:*}} tokens)_

## Editable shell text (hardcoded headings/labels — change via set_html_text, NOT customHtml)
Some visible text (hero heading, step labels, section/field captions) is baked into customHtml as plain text, NOT a field.label or token. To rebrand it, emit set_html_text with the EXACT current string (from this list) — it does a text-only swap that keeps the tag tree + CSS byte-identical:
- "&larr; Back to forms"
- "Event Registration Form"
- "Design Forward Summit / October 15, 2028"
- "About Event"
- "Event Name"
- "Design Forward Summit"
- "Date"
- "October 15, 2028"
- "Venue"
- "Grand Hall, 214 Harbor Avenue"
- "Oct 15, 2028"
- "9:00 AM - 5:00 PM"
- "Grand Hall"
- "Participant Information"
- "Full Name *"
- "Date of Birth"
- "Gender"
- "Phone Number"
- "Email *"
- "Company / Organization"
- "Where did you hear about this event?"
- "Payment and Consent"
- "Number of Tickets *"
- "Payment Method *"
- "Signature *"
- "Date Signed"
- "Complete registration"
- "Webinar Pros LLC / 555-0100 / events@example.com"

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: none): `{op:"set_field_property", key:"<cardFieldKey>", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - _(none detected — fall back to --primary/--accent)_
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `19e1aa278264…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `19e1aa2782643994…` · customHtml shell sha256 stays `e73e5916ca0c1f9a…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `custom`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
