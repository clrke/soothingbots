# Soothing Bots website

The public site for **Soothing Bots**, a mixed-reality music game for Meta Quest:
https://clrke.github.io/soothingbots/

- `index.html`: the homepage. Hand-written HTML and CSS (`style.css`), no build step, no frameworks, no trackers, no
  cookies, no external requests (system fonts only).
- `privacy.html`: the privacy policy, rendered from the app repo's `docs/privacy-policy.md`. To update it after the
  policy changes:

  ```
  SRC=path/to/magna-vocalization/docs/privacy-policy.md
  pandoc -f markdown+autolink_bare_uris+hard_line_breaks-smart -t html5 --standalone \
    --template tools/privacy-template.html --metadata pagetitle="Soothing Bots Privacy Policy" \
    -V updated="$(sed -n 's/^\*\*Effective date:\*\* *//p' "$SRC")" "$SRC" -o privacy.html
  ```

- `img/`: frames from the app's own editor captures (the hype recorder's 1440p airplane take and the `CaptureScreens_Qr`
  share view), in the friendly look (WebP at quality 80, under 300 KB each; `og.jpg` 1200x630 for link previews).

Served by GitHub Pages from the `main` branch root (`.nojekyll` keeps Jekyll out of the way).
