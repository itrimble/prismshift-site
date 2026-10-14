# prismshift-site

Marketing, support and privacy site for **Prism Shift**, served by GitHub Pages at
<https://prismshift.remnantsecurity.com/>.

Static HTML — no build step. Edit and push; Pages redeploys in under a minute.

| File | Purpose |
|---|---|
| `index.html` | Marketing page |
| `support.html` | Support / FAQ (App Store support URL) |
| `privacy.html` | Privacy policy (App Store privacy URL) |
| `prismshift.css` | Shared styles, house design tokens |
| `CNAME` | Custom domain — do not delete, Pages needs it |
| `img/` | Key art, icons and the fifteen level screenshots |

Copy is taken from the App Store listing in the app repo at
`release/metadata/en-US/`, and the level names, tempos and world grouping come from
`docs/screenshots/actual-levels/catalog.json` and `PrismShift/App/AppConstants.swift`.
Keep them in step when the game changes.

Images are generated from the app repo:

```sh
SRC=../prismshift
magick "$SRC/artwork/icons/prism-shift-gold-title.png" -resize 1600x -quality 86 img/hero-1600.webp
magick "$SRC/artwork/icons/prism-shift-gold-title.png" -crop 560x560+530+70 +repage -resize 512x512 img/icon-512.png
for f in "$SRC/docs/screenshots/actual-levels"/[0-9][0-9]_*.png; do
  magick "$f" -resize 600x -quality 84 "img/level-$(basename "$f" .png).webp"
done
```
