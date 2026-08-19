# Build assets

Sources for generated assets. Not part of the deployed page.

- `og-card.html` — source for the 1200×630 social preview card
- `favicon.svg` — source for the inlined favicon (embedded in `index.html` as a base64 data URI)

Regenerate `og-image.png`:

```sh
BRAVE="/Applications/Brave Browser.app/Contents/MacOS/Brave Browser"
"$BRAVE" --headless --disable-gpu --hide-scrollbars \
  --force-device-scale-factor=2 --window-size=1200,630 \
  --screenshot=build/og-2x.png "file://$PWD/build/og-card.html"
sips -z 630 1200 build/og-2x.png --out og-image.png
```
