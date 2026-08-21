# HeyBrand brand kit

Everything needed to use the HeyBrand logo. Open `index.html` in a browser for a visual
version of this document.

---

## 1. The logo

The mark is a speech bubble with a lowercase **h** knocked out of it, plus a four-point
sparkle at the top right. The wordmark is **HeyBrand**, with "Hey" in violet and "Brand"
in black.

| Asset | Use it for |
|---|---|
| **Lockup** (symbol + wordmark) | The default. Website header, decks, email signatures, docs |
| **Symbol** (bubble alone, with sparkle) | Social avatars, app icon, anywhere the name is already present |
| **Favicon** (bubble alone, no sparkle) | Browser tabs and any use below 32px |

### Why the favicon has no sparkle

At 16px the sparkle collapses into one or two pixels and reads as dirt, and because it sits
outside the bubble it forces the bubble to render about 11% smaller in the same square,
which costs legibility on the **h**. So the favicon files deliberately drop it. This is normal
practice, not a compromise: the bubble and the **h** carry the identity, the sparkle is garnish.

Use the sparkle at 32px and above. Drop it below that.

---

## 2. Colours

| Name | Hex | Use |
|---|---|---|
| Brand violet | `#6d3bff` | The symbol, and "Hey" in the wordmark |
| Ink | `#0e0e12` | "Brand" in the wordmark, and the all-black variant |
| White | `#ffffff` | The knocked-out **h**, and the reversed variant |

These match the app's CSS variables in `app/src/index.css` (`--color-brand`, `--color-ink`).
Two supporting colours already in the app, not part of the logo: `--color-brand-soft`
`#f0ebff` and `--color-canvas` `#fafafb`.

**The logo uses three colours only.** No gradients, no accent colours.

---

## 3. Typography

| Element | Typeface | Weight |
|---|---|---|
| The **h** in the symbol | Archivo | 900 |
| The wordmark | Figtree | 800, letter-spacing -0.025em |

Both are Google Fonts under the SIL Open Font License, which permits commercial use
including logos. The original TTFs are kept in `source/` for reference.

**You do not need either font installed.** Every glyph has been converted to vector outlines,
so the files render identically everywhere with no font dependency.

---

## 4. Files

```
brand/
├── logo/            the full lockup, symbol + wordmark
│   ├── svg/         6 variants
│   └── png/         transparent, 2048 / 1024 / 512 / 256 px wide
├── symbol/          the bubble on its own
│   ├── svg/         with sparkle, without sparkle, and square
│   └── png/         transparent, 1024 / 512 / 256 px
├── favicon/         square, no sparkle, plus favicon.ico and apple-touch-icon.png
├── source/          the original Archivo and Figtree font files
├── explorations/    the three HTML pages used to choose the design
└── archive/         earlier attempts, kept for reference only. Do not use these
```

### Variants

| Suffix | Symbol | "Hey" | "Brand" | Where |
|---|---|---|---|---|
| `-primary` | violet | violet | black | Default, on light backgrounds |
| `-violet` | violet | violet | violet | One-colour violet |
| `-black` | black | black | black | Print, faxes, single-colour |
| `-white` | white | white | white | On dark or photographic backgrounds |
| `-stacked-*` | above the wordmark | | | Square placements, avatars, merch |

---

## 5. Using it

### Clear space
Keep clear space around the logo equal to the height of the bubble's tail, roughly 10% of
the logo height. Nothing should intrude into it.

### Minimum sizes
- Lockup: **120px** wide on screen. Below that the wordmark stops being legible.
- Symbol: **24px**.
- Favicon variant: **16px**.

### Don't
- Recolour it outside the three colours above
- Add gradients, shadows, outlines or effects
- Stretch, skew or rotate it
- Re-typeset the wordmark in a different font
- Place the violet version on a dark background; use the white variant instead
- Use anything from `archive/`

---

## 6. Favicon setup

Copy the contents of `favicon/` into `app/public/`, then add this to `<head>` in
`app/index.html`:

```html
<link rel="icon" href="/favicon.ico" sizes="32x32">
<link rel="icon" href="/heybrand-favicon-violet-512.png" type="image/png" sizes="512x512">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">
```

`favicon.ico` contains 16, 32 and 48px versions in one file.

---

## 7. Technical notes

Each SVG is a **single `<path>` using `fill-rule="evenodd"`**. The bubble is the filled shape,
the **h** is a hole punched through it, and the sparkle is a separate island. There are no
`<mask>` elements and no `<text>`, which means the files survive Figma, Illustrator, Inkscape,
PDF export and older SVG renderers without surprises. The primary symbol SVG is under 1 KB.

The viewBox of every file is the tight bounding box of its artwork, so the logo has no baked-in
padding and aligns predictably in layouts.

---

## 8. Provenance and licensing

- The speech bubble outline came from **SVG Repo**. Check its licence terms before commercial
  use, and note that a stock shape cannot be trademarked, so if HeyBrand becomes valuable,
  commission an original bubble drawing to replace it.
- The **h** and the wordmark are outlined from Archivo and Figtree, both SIL OFL, which
  permits logo use.
- The sparkle is original geometry.
