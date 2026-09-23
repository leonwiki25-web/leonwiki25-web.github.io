# Taishi Huang

Personal site for UBC MDS DSCI 521. Milestone 3 adds two computational posts (R and Python), one bonus post that passes an object between R and Python with reticulate, and locked environments so the site can be rebuilt from a clean clone.

## Prerequisites

Install these first, then clone the repository.

- Quarto 1.10 (or later)
- uv (0.12.7)
- R 4.6.1 (or later)
- Git

`renv` is restored from the lockfile; you do not install it separately.

## Build

```bash
git clone git@github.com:leonwiki25-web/leonwiki25-web.github.io.git
cd leonwiki25-web.github.io
```


Python environment:

```bash
uv sync
```

R environment, from an R session started in the repository root:

```r
renv::restore()
```

Render the site from the repository root so R reads `.Rprofile` and Quarto uses the project `.venv`:

```bash
uv run quarto render
```

## View locally

The built site is in `docs/`. Open `docs/index.html` in a browser. The computational posts are:

- `docs/posts/penguins-r/index.html`
- `docs/posts/penguins-python/index.html`
- `docs/posts/r-and-python/index.html` (R and Python in one document)

## Data

Both posts use the [Palmer Penguins](https://allisonhorst.github.io/palmerpenguins/) data that ships with the `palmerpenguins` package (CC0). No data files are committed. `uv sync` and `renv::restore()` need the network to download packages. After that, rendering does not fetch the dataset. The Python Altair chart loads Vega from a CDN, so the figure needs a network connection when you open the HTML.