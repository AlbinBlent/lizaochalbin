# Multilingual Wedding Site — Design Spec

**Date:** 2026-05-06
**Project:** lizaochalbin.se

---

## Overview

Extend the existing Swedish wedding website to support English and Arabic, and add a contact section with phone numbers to all three versions.

---

## File Structure

```
lizaochalbin/
  style.css          # Extracted shared stylesheet (new)
  index.html         # Swedish (existing, updated)
  en.html            # English (new)
  ar.html            # Arabic (new)
  images/
  favicon.svg
  ...
```

All three HTML files link to the shared `style.css`. Arabic-specific overrides (RTL, font) are scoped inline in `ar.html`.

---

## Language Switcher

A small nav rendered at the top of every page, above the hero. Three links: `Svenska`, `English`, `العربية`. The active language is visually distinguished (e.g. slightly darker color). Styled in small caps to match the site's existing typographic language.

---

## Contact Section (all three versions)

- Placed above the OSA/RSVP section
- Heading: "Kontakt" / "Contact" / "التواصل"
- Three entries, each with name and a `tel:` hyperlink:
  - Albin — +46 70 499 05 38
  - Liza — +46 73 718 81 95
  - Seham — +46 76 223 68 65
- Same visual style as the existing "greeting" sections (centered, Fraunces serif)

---

## Section Matrix

| Section             | Swedish (`index.html`) | English (`en.html`) | Arabic (`ar.html`) |
|---------------------|:---:|:---:|:---:|
| Hero                | ✅  | ✅  | ✅  |
| Photo               | ✅  | ✅  | ✅  |
| Greeting            | ✅  | ✅  | ✅  |
| Details             | ✅  | ✅  | ✅  |
| Schedule            | ✅  | ✅  | ✅  |
| Children            | ✅  | ✅  | ✅  |
| Gifts (GÅVOR)       | ✅  | ❌  | ❌  |
| Contact             | ✅  | ✅  | ✅  |
| RSVP (OSA)          | ✅  | ✅  | ✅  |
| Footer              | ✅  | ✅  | ✅  |

---

## Arabic Version Specifics

- `<html lang="ar" dir="rtl">` for right-to-left layout
- Google Font **Cairo** added for Arabic text (alongside Fraunces and DM Sans which cover Latin)
- Schedule time column switches sides naturally via RTL grid flow
- Language switcher link order remains LTR internally (lang codes) but text renders RTL

---

## Content Translations (key strings)

| Swedish            | English                        | Arabic                          |
|--------------------|--------------------------------|---------------------------------|
| vi gifter oss      | we're getting married          | نحن نتزوج                       |
| Datum              | Date                           | التاريخ                         |
| Vigsel             | Ceremony                       | حفل الزواج                      |
| Middag & fest      | Dinner & reception             | العشاء والاحتفال                 |
| Klädsel            | Dress code                     | قواعد اللباس                    |
| OSA senast         | RSVP by                        | تأكيد الحضور بحلول               |
| Mörk kostym        | Dark suit                      | بدلة داكنة                      |
| Dagen              | The Day                        | يوم الزفاف                      |
| Barn               | Children                       | الأطفال                         |
| Kontakt            | Contact                        | التواصل                         |
| OSA                | RSVP                           | تأكيد الحضور                    |
| Svara här          | Respond here                   | الرد هنا                        |

---

## Changes to Existing `index.html`

- Remove inline `<style>` block, replace with `<link rel="stylesheet" href="style.css">`
- Add language switcher nav above hero
- Add contact section above OSA section
- No content changes to Swedish copy
