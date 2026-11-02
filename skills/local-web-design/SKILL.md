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
- **Brand first:** business name is a hero-level signal, not only nav text. Prefer the **logo** in the header when intake has a logo `localPath`.
- **Hero budget:** brand, one headline, one short supporting sentence, **one primary CTA**, one dominant full-bleed image/background. No stats strips, schedule chips, address blocks, or promo stickers in the first viewport.
- **No hero overlays:** no floating badges, pills, or callout boxes on hero media.
- **Full-bleed hero** by default — not inset cards or side-panel media.
- **Cards:** default no cards. Never in the hero. Cards only when they wrap a real interaction.
- **One job per section:** one purpose, one headline, usually one short supporting sentence.

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

## Motion

- At least 2–3 intentional motions (hero fade/rise, CTA press scale, section reveal) using **`emil-design-eng`** / **`animate`** — ease-out enter, no animation spam on every scroll block.

## Output

Implement in the client Next.js app under `clients/{slug}/`. Apply this skill + **`emil-design-eng`** on every scaffold.
