# Soothing Bots website

The public site for **Soothing Bots**, a mixed-reality music game for Meta Quest 3 and 3S:
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

- `img/`: screenshots and frames from the game's own store screenshots and trailer drafts (WebP, under 300 KB each).

Served by GitHub Pages from the `main` branch root (`.nojekyll` keeps Jekyll out of the way).
