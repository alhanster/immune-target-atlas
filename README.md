# Immune Target Atlas

A static web portal for browsing machine-learned drug-target candidates for immune disease.
Ranks ~18,700 genes by a PU-learning model score, with per-gene detail pages
(regulator-burden signal, functional-genomics similarity to FDA-drugged targets,
polarization score, and external validation links).

## Run locally

It must be served over HTTP (not opened with `file://`), because the page loads
JavaScript data files. From this folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Host on GitHub Pages

1. Create a new GitHub repository and push the **contents of this folder** to it
   (so that `index.html` sits at the repo root).

   ```bash
   git init
   git add .
   git commit -m "Immune Target Atlas"
   git branch -M main
   git remote add origin https://github.com/<you>/<repo>.git
   git push -u origin main
   ```

2. In the repo, go to **Settings → Pages**, set **Source** to
   *Deploy from a branch*, branch **main**, folder **/ (root)**, and save.

3. Your site will be live at `https://<you>.github.io/<repo>/` within a minute.

The `.nojekyll` file is included so GitHub Pages serves every file as-is.

## Updating the data

Replace the arrays in these files (keep the same column names / structure):

- `target-data.js` — the main scored gene table (title page).
- `cfg-data.js` — kNN functional-genomics similarity, per activation state.
- `polarization-data.js` — polarization scores.

## Technical report

The header's **Read technical report** button links to `assets/technical-report.pdf`.
Add that PDF at that path (create the `assets/` file) and the button will work.

## Files

- `index.html` — entry page.
- `Portal.dc.html` — the app (table, search, gene detail pages).
- `support.js` — runtime.
- `target-data.js`, `cfg-data.js`, `polarization-data.js` — datasets.
- `assets/logo.png` — logo / favicon.
