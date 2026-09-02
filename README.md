# tianyuan-liu.github.io

Personal academic site of Tianyuan Liu — live at <https://tianyuan-liu.github.io/>.

Six static pages (Home, Research, Publications, Software, Talks & teaching, Elsewhere),
one palette (pine, bone, copper), IBM Plex Sans, no framework, no build step on GitHub's side.

## How it is built

The HTML here is **generated** — do not edit it by hand.

The source of truth is the design canvas in `~/Desktop/website_design/`:

- `build_site.py` writes the six desktop artboards (`*.dc.html`) from one shared block —
  all content (papers, talks, places, news) lives there.
- `build_static.mjs` turns those artboards into this site: it evaluates each page's data,
  renders the templates, replaces placeholder links with real targets (DOIs, GitHub,
  Scholar, ORCID), adds the mobile layout, favicons and metadata, copies the images,
  and writes `references.bib`.

To publish a change:

```sh
cd ~/Desktop/website_design
python3 build_site.py                                  # if the content changed
node build_static.mjs --out ../tianyuan-liu.github.io
cd ../tianyuan-liu.github.io && git add -A && git commit -m "…" && git push
```

GitHub Pages serves the `main` branch root; `.nojekyll` keeps Jekyll out of the way.

## Files

| file | what |
|---|---|
| `index.html`, `research.html`, `publications.html`, `software.html`, `talks.html`, `elsewhere.html` | the pages |
| `favicon/` | icon set (SVG, ICO, PNG sizes, web manifest) |
| `references.bib` | the publication list as BibTeX, generated from the same data |
| `tianyuan_liu_cv.pdf` | curriculum vitae |
| `*.jpg`, `*.svg`, `*.png` | portrait, figure, photographs, project marks |
