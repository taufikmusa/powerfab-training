# Tekla PowerFab Training

MkDocs Material documentation site for the Tekla PowerFab 5-day training programme and the 18-step implementation workflow. Trimble brand styling.

## Local preview

```bash
pip install -r requirements.txt
mkdocs serve
```

Open `http://127.0.0.1:8000`.

On Windows, if `mkdocs` is not recognized, use:

```bash
python -m mkdocs serve
```

## Build

```bash
mkdocs build --strict
```

## Deploy to GitHub Pages

Two options. Pick one.

### Option A — automatic (recommended)

The workflow in `.github/workflows/deploy.yml` builds and publishes on every push to `main`.

One-time setup: repo **Settings > Pages > Build and deployment > Source** = **GitHub Actions**.

### Option B — manual

```bash
mkdocs gh-deploy
```

One-time setup: repo **Settings > Pages > Source** = **Deploy from a branch**, branch = `gh-pages`, folder = `/(root)`.

Do not use both options on the same repo.

## Add a page

1. Make the `.md` file in the right folder under `docs/`.
2. Add the file to the `nav:` block in `mkdocs.yml`.

A page that is not in `nav:` builds but does not show in the sidebar.

## Add an image

Put the file in `docs/assets/images/`, then:

```markdown
![Alt text](../assets/images/filename.png)
```

Drop the `../` for a page directly in `docs/`. Click-to-zoom works automatically.
