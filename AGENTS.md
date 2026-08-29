# Repository Guidelines

## Project Structure & Module Organization

This repository publishes a browser-only JupyterLite learning site. All user-facing material lives under `content/`: topic folders such as `numpy/`, `pandas/`, and `sklearn/` contain Japanese tutorial notebooks, while `content/exercises/` contains practice sets. Keep supporting data beside the notebooks that use it, as with `content/jupyterlite/data.csv` and `content/folium/tokai4_prefs.geojson`.

Build dependencies are pinned in `requirements.txt`. `environment.yml` defines the xeus-r kernel environment. GitHub Pages automation is in `.github/workflows/deploy.yml`; generated `dist/` content is not committed.

## Build, Test, and Development Commands

Use Python 3.11 to match CI.

```bash
python -m pip install -r requirements.txt
jupyter lite build --contents content --output-dir dist
jupyter lite serve --contents content
```

The first command installs JupyterLite and its kernels. The build command creates the deployable static site and is the primary repository-wide check. The serve command starts a local preview at `http://localhost:8000`. Building xeus-r content also requires `micromamba`; see the workflow for the CI installation method.

## Coding Style & Naming Conventions

Write notebook Python with four-space indentation and PEP 8-style `snake_case` names. Keep cells focused, place explanatory Markdown before code, and preserve the repository's Japanese instructional tone. Name new files descriptively using lowercase snake case, for example `scipy_stats_beginner_tutorial.ipynb`. Use relative paths for bundled datasets so notebooks work inside JupyterLite. No formatter or linter is configured, so review notebook diffs carefully and avoid unrelated metadata churn.

## Testing Guidelines

There is no automated test suite. Before submitting, restart the relevant kernel and run changed notebooks top to bottom in JupyterLite. Confirm that imports, plots, widgets, and relative data loads work in the browser; desktop-only packages may fail under Pyodide. Test R changes with the xeus-r kernel. Clear transient execution state and unintended outputs, then run the full site build.

## Commit & Pull Request Guidelines

History uses short, imperative, sentence-case subjects such as `Update tutorials repo link...` and `Clear all notebook outputs...`. Keep each commit focused. Pull requests should summarize affected notebooks, explain learner-visible changes, report build and execution checks, and link relevant issues. Include screenshots for visual, widget, or map changes, and call out new dependencies or large data assets.
