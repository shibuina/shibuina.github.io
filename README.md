# shibuina.github.io

Personal site of Do Duc Anh, built with [al-folio](https://github.com/alshedivat/al-folio) v1.2 (Jekyll). The Arena 5.0
project page that used to live at the root is in `arena5/` and is served at <https://shibuina.github.io/arena5/>.

## Editing

| What | Where |
| --- | --- |
| Bio, photo | `_pages/about.md`, `assets/img/prof_pic.jpg` |
| Publications | `_bibliography/papers.bib` (`selected = {true}` puts a paper on the home page, `preview` names an image in `assets/img/publication_preview/`) |
| News | one file per item in `_news/` |
| Projects | one file per card in `_projects/` (`redirect:` sends the card to an external page) |
| Social links | `_data/socials.yml` |
| Site settings | `_config.yml` |

## Local preview

The host toolchain cannot compile the native gems, so build in Docker:

```bash
docker build -t shibuina-site .
docker run --rm -u $(id -u):$(id -g) -e HOME=/tmp -v $PWD:/srv/jekyll -p 8080:8080 shibuina-site \
  bundle exec jekyll serve --host 0.0.0.0 --port 8080 --destination /tmp/_site
```

Then open <http://localhost:8080>.

## Deploy

Pushing to `main` runs `.github/workflows/deploy.yml`, which builds the site and pushes it to the `gh-pages` branch.
GitHub Pages serves `gh-pages`.
