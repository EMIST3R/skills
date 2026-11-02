---
name: local-web-design
description: >-
  Visual and UX standards for local business marketing sites (Next.js). Use when
  scaffolding, redesigning, or polishing client landing pages, or when the user
  says run build, redesign, or improve the look of a local business site.
  Complements emil-design-eng from EMIST3R/skills.
---

# Local web design (marketing sites)

Public source of truth: https://github.com/EMIST3R/skills/tree/main/skills/local-web-design  
Also mirrored for a dedicated repo: https://github.com/emist3r/local-web-design-skill (when published).

## Also load

Before shipping UI, apply **`emil-design-eng`** (motion, easing, press states, taste) from https://github.com/EMIST3R/skills. For phone feel use **`mobile-native`**. After a pass, optionally **`break-ui`**.

`local-web-design` = marketing composition, CTAs, channel chrome, visitor copy.  
`emil-design-eng` = motion / polish only. Both required on scaffold; they do not compete.

## Composition (landing / marketing pages)

- **One composition** in the first viewport — not a dashboard.
- **Brand lockup:** header shows the **logo file** (intake logo `localPath`) plus the business name. Do not rely on a logo printed inside a photo, and do not use a text wordmark when a logo file exists.
- **Hero copy is factual, not a slogan.** One line that says place, who it is for, what they do, and since-year when claimed. Examples of forbidden incentive lines: “One teacher. The whole course.”, “Unlock your potential.”, “Your journey starts here.”
- **Hero budget:** logo + name, that one factual line, **one primary CTA**, and one image. No stats strips, schedule chips, address blocks, promo stickers, or floating badges in the hero.
- **Readable type:** do not put the headline on a light gradient over a face or a busy pattern. If the photo has no quiet region, put type on a **solid panel** (split layout or a solid bottom band).
- **First screen:** the hero may be tall, but the next section (what they offer) must begin in or just under the first viewport — not a full empty `100svh` of photo with facts only after scroll.
- **Cards:** default no cards. Never in the hero. Cards only when they wrap a real interaction.
- **One job per section:** one purpose, one headline, usually one short supporting sentence.

## Hero image check

Before using a photo as the hero:

- Reject a centered portrait or a busy pattern that leaves no quiet region for type.
- Prefer classroom, storefront, exterior, or a crop with open space.
- If every candidate fails, use a solid panel for type and a smaller photo beside or below it.
- Always ship the downloaded logo in the header. The photo is not the logo.

## CTA hierarchy (no redundancy)

When phone and/or LINE exist, do **not** stack equal Call + LINE pairs in header + hero + sticky.

| Surface | Rule |
|---------|------|
| **Hero** | **One primary CTA only** — LINE when `social.line` exists, else Call. No second equal-weight button in the hero. |
| **Header** | Logo (if available) + **the same single primary** only. Never a Call in the header when the hero already shows Call as primary. |
| **Sticky bar** (mobile, after scroll) | Call \| LINE dual strip with **app marks** is allowed. Must not duplicate a same-size Call+LINE pair already in the hero. |

Primary CTAs are call / LINE / contact — not generic “Learn more” alone. Show QR on contact when `line-qr` is enabled.

## Channel chrome (LINE / WhatsApp / etc.)

- LINE buttons use classic **LINE green** (`#06C755`) + the **LINE mark** (SVG/icon), not plain text-only “Add LINE” in brand gold/teal.
- WhatsApp (and similar) use the same pattern: official-ish channel color + app mark, confined to that button.
- Channel chrome does **not** replace site theme tokens — brand UI stays on theme CSS variables. No giant logo grids or emoji decoration.

## Typography and color

- Expressive fonts — avoid Inter, Roboto, Arial, system-ui as the primary brand face.
- Define CSS variables for theme tokens (`trust-blue`, `warm-local`, `minimal-luxury`, `bold-contrast`).
- Avoid AI-default looks: purple-on-white / purple-indigo gradients; warm cream `#F4F1EA` + terracotta + serif; broadsheet hairline newspaper layouts; gratuitous glow; emoji decoration.

## Imagery and maps

- Prefer **local** images from intake `localPath` / `public/` — never depend on Facebook CDN alone.
- Maps: use `contact.address.mapsUrl` or Maps search on **formatted address** — never `google.com/search?q=Business+Name` as the map CTA.

## Visitor-voice copy (required)

- Public marketing copy (`site.json`, page prose) is written **for visitors**, not researchers.
- Facts must still be grounded in intake `claims[]` — but **rewrite** into clean marketing voice.
- **Forbidden** in public copy: “Facebook post…”, “a flyer says…”, “Google listing…”, “Posts also say…”, “named on Facebook”, “from the school flyer” as source attribution, or any platform/source provenance.
- Provenance stays in `claims[]`, `client-brief.md`, and client `AGENTS.md` / `conflicts[]` — never in visitor-facing descriptions.
- Hero and section headlines state facts (who, where, what). They are not campaign slogans.

## Locales

- If intake `business.languages` has two or more codes (the source site had a language switch or parallel copy), scaffold a **header language control**.
- Each public string is **one language**. Do not mix Thai and English in the same sentence or button.
- Ship only languages present in intake. Do not invent translations.
- Default locale is the language the source site leads with (often `th` for a Thai business site that also has English).

## Motion

- At least 2–3 intentional motions (hero fade/rise, CTA press scale, section reveal) using **`emil-design-eng`** / **`animate`** — ease-out enter, no animation spam on every scroll block.

## Output

Implement in the client Next.js app under `clients/{slug}/`. Apply this skill + **`emil-design-eng`** on every scaffold.
