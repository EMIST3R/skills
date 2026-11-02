---
name: local-web-design
description: >-
  Visual and UX standards for local business marketing sites (Next.js). Use when
  scaffolding, redesigning, or polishing client landing pages, or when the user
  says run build, redesign, or improve the look of a local business site.
  Complements emil-design-eng from EMIST3R/skills.
---

# Local web design (marketing sites)

## Also load

Before shipping UI, apply **`emil-design-eng`** (motion, easing, press states, taste) from https://github.com/EMIST3R/skills. For phone feel use **`mobile-native`**. After a pass, optionally **`break-ui`**.

## Composition (landing / marketing pages)

- **One composition** in the first viewport — not a dashboard.
- **Brand first:** business name is a hero-level signal, not only nav text.
- **Hero budget:** brand, one headline, one short supporting sentence, one CTA group, one dominant full-bleed image/background. No stats strips, schedule chips, address blocks, or promo stickers in the first viewport.
- **No hero overlays:** no floating badges, pills, or callout boxes on hero media.
- **Full-bleed hero** by default — not inset cards or side-panel media.
- **Cards:** default no cards. Never in the hero. Cards only when they wrap a real interaction.
- **One job per section:** one purpose, one headline, usually one short supporting sentence.

## Typography and color

- Expressive fonts — avoid Inter, Roboto, Arial, system-ui as the primary brand face.
- Define CSS variables for theme tokens (`trust-blue`, `warm-local`, `minimal-luxury`, `bold-contrast`).
- Avoid AI-default looks: purple-on-white / purple-indigo gradients; warm cream `#F4F1EA` + terracotta + serif; broadsheet hairline newspaper layouts; gratuitous glow; emoji decoration.

## Imagery and CTAs

- Prefer **local** images from intake `localPath` / `public/` — never depend on Facebook CDN alone.
- Primary CTAs: call, LINE (`line-cta`), contact form — not generic “Learn more” only.
- If `social.line` exists, show a clear **Add LINE** button; show QR on contact when `line-qr` is enabled.
- Maps: use `contact.address.mapsUrl` or Maps search on **formatted address** — never `google.com/search?q=Business+Name` as the map CTA.

## Motion

- At least 2–3 intentional motions (hero fade/rise, CTA press scale, section reveal) using **`emil-design-eng`** / **`animate`** — ease-out enter, no animation spam on every scroll block.

## Output

Implement in the client Next.js app. Keep marketing copy tied to intake claims only.
