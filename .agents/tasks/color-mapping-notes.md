# Color Mapping Notes — Cream/Beige → Light Blue

Task: convert all cream/beige theme colors to light blue tones (including all buttons),
without changing code structure, markup, or line order. First iteration (no prior
`color-review.json` found).

## Color mapping applied (original → new blue)

| Original (cream/beige/brown) | Role | New light blue |
|---|---|---|
| `#F5EBE0` | body bg gradient start (very light cream) | `#E8F2FB` |
| `#FAF6ED` | body/card bg, button bg (very light cream) | `#EAF4FC` |
| `#EFE3D3` | body bg gradient end (light cream) | `#DCEBFA` |
| `#FAF4EA` | overlay gradient (light cream) | `#E9F3FC` |
| `#F3E7D3` | overlay gradient (light cream) | `#DCEBFA` |
| `#EADBC4` | overlay gradient (mid cream) | `#CBE0F5` |
| `#F7EFE2` | cover section bg gradient start | `#EEF6FD` |
| `#EFE2CC` | cover/footer bg gradient (light tan) | `#DCEBFA` |
| `#E4D4B7` | cover/footer bg gradient end (mid tan) | `#C3DBF0` |
| `#F2E6D4` | event section bg gradient start (light tan) | `#DCEBFA` |
| `#E5DCC5` | border color (used everywhere: cards, inputs, dividers) | `#BFD9EF` |
| `#B8A99A` | muted tan (placeholder text) | `#9CB8D4` |
| `#8C6D53` | mid brown accent (labels, borders, icons, selection) | `#5B8DBF` |
| `#A0796A` | muted brown (radio peer-checked state) | `#6B96BE` |
| `#7A5C43` | brown text/icon | `#46709C` |
| `#6E4F38` | brown button/shadow/text | `#3E6690` |
| `#594433` | brown body text | `#3A5876` |
| `#4A3525` | darkest brown text | `#1F3A5C` |
| `#593E2B` | darkest brown (button gradient end) | `#1A3657` |
| `#F5EBD9` | avatar frame gradient end | `#DCEBFA` |
| `#EFE6D5` | button hover background | `#D3E6F8` |
| `#fff9f0` | flash overlay radial gradient (near-white cream) | `#f0f8ff` |
| `#f5e6cc` | flash overlay radial gradient (light cream) | `#cfe6fb` |
| `4A3525` / `FAF6ED` (no `#`, QR code API params) | QR code foreground/background color | `1F3A5C` / `EAF4FC` |

The mapping is consistent: every occurrence of a given original hex value maps to the
same new blue value everywhere it appears (backgrounds, borders, text, hover states,
gradients, box-shadows, buttons).

## Files touched

- `src/components/CoupleSection.astro`
- `src/components/CoverSection.astro`
- `src/components/EventSection.astro`
- `src/components/FooterSection.astro`
- `src/components/GiftSection.astro`
- `src/components/LocationSection.astro` (also updated QR code `color=`/`bgcolor=` params)
- `src/components/Navbar.astro`
- `src/components/SurahSection.astro`
- `src/layouts/Layout.astro`
- `src/layouts/LayoutPage.astro`
- `src/pages/admin.astro`
- `src/pages/index.astro`
- `src/pages/konfirmasi.astro`

No non-color properties, formatting, line order, class names, or SVG path geometry were
changed. Only hex color values (and the two QR-code color query params) were swapped.

## Files intentionally excluded (not part of the visible cream/beige theme)

- `src/components/Welcome.astro` — Astro's default scaffold boilerplate. Verified with a
  repo-wide search: it is never imported/referenced by any page or component, so it is
  not rendered. Its colors (`#3245ff`, `#bc52ee`, `#d83333`, `#f041ff`, `#111827`,
  `#4b5563`, etc.) are Astro's default branding gradient, unrelated to the wedding theme.
- `src/assets/background.svg` and `src/assets/astro.svg` — Astro scaffold assets used only
  by the unused `Welcome.astro`. Not cream/beige, and not visible on the live site.
- `#003B6D` (Bank Mandiri brand color) and `#005E9E` (Bank BCA brand color) in
  `GiftSection.astro` — these are bank-brand identifiers next to account numbers, not
  theme cream/beige colors, so they were left as-is.
- `#25D366` (WhatsApp green), `#F0F9F4` / `#dcfce7` (success-state green) — unrelated
  brand/status colors, left as-is.
- `astro.config.mjs` — contains no color definitions.
- `src/styles/global.css` — contains no color definitions (only fonts/animations).

## Build verification

Command: `npm run build` (from project root)
Result: **Success** — `astro build` completed, 3 pages generated
(`/admin`, `/konfirmasi`, `/`), no errors or warnings.

## Grep verification (post-edit)

Searched `src/` for the full original cream/beige list (hex codes `#f5f5dc`, `#faf0e6`,
`#fdf5e6`, `#f0ead6`, `#e8dcc8`, `#ead9c3`, `#d2b48c`, `#deb887`, plus all the
project-specific hex values above, and named colors `beige`, `cornsilk`, `wheat`, `tan`,
`antiquewhite`, `blanchedalmond`, `bisque`, `navajowhite`, `moccasin`): **no matches**.

The only hex values remaining in `src/` are: the new blue mapping values, the bank/
WhatsApp/success brand colors noted above as intentionally excluded, and the Astro
scaffold boilerplate colors in the unused `Welcome.astro` / its SVG assets, also
intentionally excluded.
