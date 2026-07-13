# Immune Target Atlas

### 📖 Technical report **https://github.com/alhanster/immune-target-atlas-technical-report**

A static web portal for browsing machine-learned drug-target candidates for immune
disease. It ranks ~18,700 genes by a PU-learning model score and provides a per-gene
detail page for each: regulator-burden signal, functional-genomics similarity to
FDA-drugged targets, polarization score, and external validation links.

**Live site:** https://alhanster.github.io/immune-target-atlas/

## Run locally

The page loads its data from JavaScript files, so it must be served over HTTP —
opening `index.html` directly with `file://` will not work. From this folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

The site is hosted on GitHub Pages from the `main` branch (root folder). To publish
changes, just commit and push:

```bash
git add .
git commit -m "Update atlas"
git push
```

Pages rebuilds automatically and the live site updates within a minute. The included
`.nojekyll` file tells Pages to serve every file as-is.

## Updating the data

Replace the arrays in these files, keeping the same column names and structure:

- `target-data.js` — the main scored gene table (title page).
- `cfg-data.js` — kNN functional-genomics similarity, per activation state.
- `polarization-data.js` — polarization scores.

## Technical report

The header's **Read technical report** button links to `assets/technical-report.pdf`.
Add a PDF at that path and commit it, and the button will work.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Entry page. |
| `Portal.dc.html` | The app — table, search, and gene detail pages. |
| `support.js` | Runtime. |
| `target-data.js`, `cfg-data.js`, `polarization-data.js` | Datasets. |
| `assets/logo.png` | Logo / favicon. |
