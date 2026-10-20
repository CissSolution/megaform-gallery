---
{
  "templateGuideSlug": "tpl-halloween-after-dark",
  "slug": "halloween-after-dark",
  "theme": "dark",
  "rootSelector": ".mfp.mfp-halloween-after-dark",
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
    "email",
    "party_size",
    "costume_plans",
    "note"
  ],
  "missingFieldPlaceholders": [],
  "shellTexts": [
    "☾ moonlit",
    "Gatherings with a little magic",
    "An invitation to the unexpected",
    "Halloween",
    "after dark.",
    "A little mystery. A little magic.",
    "Gather your favorite people for a night",
    "that’s anything but ordinary.",
    "October 31 · Come as your alter ego",
    "The more, the eerier",
    "A night worth",
    "dressing up for.",
    "A little make-believe",
    "Go all out or keep it understated. Every alter ego is welcome.",
    "Good company, strange delights",
    "The best kind of gathering starts with the people around you.",
    "The details, in due time",
    "Your organizer will confirm the time, place, and all the little particulars.",
    "Something wickedly wonderful awaits.",
    "Join the guest list",
    "Attendance is subject to confirmation by the organizer.",
    "Send my RSVP",
    "Made for a hauntingly good time. · Moonlit gatherings"
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
  "customCssSha256": "2dc5d7ec22d0ec0dbb448d424a8df22160262b1a94e2fc3f144ed1a5466bdd6f",
  "shellSha256": "aec6091d235628b43efcb4050a164989a9b1c9572c677fad39ff46973a846cbf"
}
---
# AI Edit Guide — Halloween After Dark

Theme `dark` · root `.mfp.mfp-halloween-after-dark` · 5 fields · 1 steps (single).

Embedding: retain the unique `mf-template-halloween-after-dark` pane, its scoped selectors, named container queries and animation names. Never resize body/theme containers or add viewport-width/negative-margin escapes. Keep actual card colors; do not restore the redundant outer page canvas.


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
| costume_plans | Select | choice | - | 4 |
| note | Textarea | input | - |  |

## Content tokens ({{content:*}} — editable text shown in the shell)
_(none — this template has no {{content:*}} tokens)_

## Editable shell text (hardcoded headings/labels — change via set_html_text, NOT customHtml)
Some visible text (hero heading, step labels, section/field captions) is baked into customHtml as plain text, NOT a field.label or token. To rebrand it, emit set_html_text with the EXACT current string (from this list) — it does a text-only swap that keeps the tag tree + CSS byte-identical:
- "☾ moonlit"
- "Gatherings with a little magic"
- "An invitation to the unexpected"
- "Halloween"
- "after dark."
- "A little mystery. A little magic."
- "Gather your favorite people for a night"
- "that’s anything but ordinary."
- "October 31 · Come as your alter ego"
- "The more, the eerier"
- "A night worth"
- "dressing up for."
- "A little make-believe"
- "Go all out or keep it understated. Every alter ego is welcome."
- "Good company, strange delights"
- "The best kind of gathering starts with the people around you."
- "The details, in due time"
- "Your organizer will confirm the time, place, and all the little particulars."
- "Something wickedly wonderful awaits."
- "Join the guest list"
- "Attendance is subject to confirmation by the organizer."
- "Send my RSVP"
- "Made for a hauntingly good time. · Moonlit gatherings"

## Formulas (fill the slots — never change the op shape)
- **C1 Change content/title**: form title `{op:"set_form_meta", title:"New title", designDecision:"preserve"}`; a field's editable label `{op:"set_field_property", key:"<key>", path:"label", value:"New label", designDecision:"preserve"}`; a {{content:*}} token `{op:"set_form_meta", customContent:{"<token>":"New text"}, designDecision:"preserve"}`; **a hardcoded shell heading/caption** `{op:"set_html_text", find:"<exact current text from the list above>", replace:"New text", designDecision:"preserve"}` (text-only swap; never include HTML tags in find/replace).
- **C6 Edit CHIP options** (fields: none): `{op:"set_field_property", key:"<chipFieldKey>", path:"options", value:[{"value":"v1","label":"Label 1"},…], designDecision:"preserve"}`. Keep the field's `optionDisplay:"chips"` — set ONLY options. The chip look (`.mf-option-group--chips`) is in customCss and stays.
- **C7 Edit CARD options** (fields: none): `{op:"set_field_property", key:"<cardFieldKey>", path:"options", value:[{"value":"v1","label":"Title","meta":"Subtitle","description":"…"},…], designDecision:"preserve"}`. Keep `optionDisplay:"cards"`. Card chrome (`.mf-option-group--cards`) stays. ⚠ ICONS — do NOT invent, change, or remove icons: MegaForm's rich-choice catalog/theme owns icon assignment. If an option ALREADY has an `icon`, keep it byte-for-byte; if it has none, OMIT the `icon` field (never emit a plain descriptive word like "city"/"beach" — it renders as literal text). Edit ONLY `label`/`meta`/`description`/`value`.
- **C2 Add field**: `{op:"add_field", type:"Text", key:"new_key", label:"…", step:0, designDecision:"preserve"}` — the dispatcher inserts `{{field:new_key}}` into the matching `panel` block. Pick a snake_case key not already used.
- **C3 Remove field**: `{op:"remove_field", key:"<key>", designDecision:"preserve"}` — removes the field and its token; leaves zero orphan placeholders.
- **C8 Change COLOUR (only if the user explicitly asks)**: `{op:"set_form_meta", themeCssOverrides:{"<scoped-var>":"#hex",…}, designDecision:"preserve"}`. ⚠ This template scopes its palette under TEMPLATE-SPECIFIC vars — target THOSE exact names (the generic `--primary`/`--accent` are INERT here). Available colour vars (current value):
  - _(none detected — fall back to --primary/--accent)_
  NEVER edit customCss for colour — customCss must stay byte-identical (sha256 `2dc5d7ec22d0…`).
- **C4/C5 Add/Remove step** (ADVANCED — single): steps are `panel` blocks in customHtml driven by `the wizard script`. Clone an existing `panel` block via `customHtmlAppend` (NEVER touch customCss), renumber the stepper, and add the new fields with placeholders. Only attempt if the user explicitly asks. If unsure, ask the user instead of guessing.

## Hard invariants (a change that breaks any of these is a FAILURE — refuse the op)
- customCss sha256 stays `2dc5d7ec22d0ec0d…` · customHtml shell sha256 stays `aec6091d235628b4…` (unless C2/C4 legitimately add a node).
- `settings.theme` stays `dark`. Every field keeps a `{{field:key}}` (own or via Row). Zero orphan/zero floating-outside-card fields.
