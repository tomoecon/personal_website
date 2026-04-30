# Academic Website - Tomoharu Mori

This repository contains the source code for **Tomoharu Mori's** academic website, built with Quarto and hosted on GitHub Pages.

> **AI-Powered Development**: This website is developed with the assistance of AI tools including Claude Code, enabling efficient development and maintenance of academic content.

## About

**Tomoharu Mori**
Associate Professor
College of Comprehensive Psychology, Ritsumeikan University

Research interests: Behavioral Economics, Labor Economics, Public Economics

## Contact

For questions about this website or research inquiries:
- Email: tmr15047 [atmark] fc.ritsumei.ac.jp
- Affiliation: Ritsumeikan University, College of Comprehensive Psychology

## Technology Stack

- **Static Site Generator**: Quarto
- **Development Environment**: RStudio
- **Hosting**: GitHub Pages
- **Version Control**: Git & GitHub

## Project Structure

```
personal_website/
├── _quarto.yml              # Site configuration
├── index.qmd                # Homepage (bilingual: English/Japanese)
├── cv.qmd                   # Short CV page (English)
├── cv-ja.qmd                # Short CV page (Japanese)
├── cv-full.Rmd              # Full CV source (English) — rendered to cv-full.pdf
├── cv-full.pdf              # Full CV (English), linked from cv.qmd
├── cv-full-ja.Rmd           # Full CV source (Japanese) — rendered to cv-full-ja.pdf
├── cv-full-ja.pdf           # Full CV (Japanese), linked from cv-ja.qmd
├── publications.bib         # BibTeX archive of publications (reference only;
│                            # not rendered by Quarto — see "Publications" below)
│
├── files/                   # Downloadable files (PDFs, etc.)
├── images/                  # Image files
│
├── styles.css               # Custom CSS
├── custom.scss              # Custom SCSS styles
├── docs/                    # Generated site (published to GitHub Pages)
│
├── CLAUDE.md                # AI agent operation policy (single source of truth)
├── AGENTS.md                # Pointer to CLAUDE.md for non-Claude agents
├── .gitignore
└── README.md
```

The website is intentionally minimalist, focusing on the homepage and CV pages.

## Local Development

### Prerequisites

- [R](https://www.r-project.org/) (version 4.0 or higher)
- [RStudio](https://posit.co/download/rstudio-desktop/) (recommended)
- [Quarto](https://quarto.org/docs/get-started/)

### Setup

1. Clone this repository:
```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

2. Install Quarto if not already installed

3. Open the project in RStudio (the working directory is the repository root)

### Building the Site

To render the website locally:

```bash
quarto render
```

This will generate the static site in the `docs/` directory.

### Rebuilding the Full CV PDFs

The full CV PDFs (`cv-full.pdf`, `cv-full-ja.pdf`) are produced from R Markdown
sources (`cv-full.Rmd`, `cv-full-ja.Rmd`) and are **not** built by `quarto
render`. Re-render them manually whenever the source changes:

```r
rmarkdown::render("cv-full.Rmd")
rmarkdown::render("cv-full-ja.Rmd")
```

Both files use XeLaTeX. The Japanese version additionally requires the
`Hiragino Mincho ProN` CJK font, which is only available on macOS by default;
on other platforms, edit the `CJKmainfont` field in `cv-full-ja.Rmd` to a
locally installed CJK font before rendering.

The committed PDFs are referenced by `cv.qmd` / `cv-ja.qmd` and are listed
under `resources` in `_quarto.yml` so that they are copied into `docs/`
during `quarto render`.

### Previewing the Site

To preview the site with live reload:

```bash
quarto preview
```

## Deployment to GitHub Pages

### Initial Setup

1. Go to your GitHub repository Settings > Pages
2. Under "Source", select "Deploy from a branch"
3. Select branch: `main` (or `master`)
4. Select folder: `/docs`
5. Click "Save"

### Publishing Updates

1. Make changes to `.qmd` files
2. Render the site: `quarto render`
3. Commit and push to GitHub:

```bash
git add .
git commit -m "Update website content"
git push origin main
```

The site will automatically update on GitHub Pages within a few minutes.

## Customization

### Changing Theme

The site currently uses the Cosmo theme with custom SCSS. Edit `_quarto.yml` to change the theme:

```yaml
format:
  html:
    theme: [cosmo, custom.scss]  # Try: flatly, journal, litera, lumen, etc.
    css: styles.css
```

### Custom Styling

- **`custom.scss`**: SCSS variables and theme customizations
- **`styles.css`**: Additional CSS styling

Edit these files to customize the appearance of your site.

### Adding New Pages

1. Create a new `.qmd` file
2. Add it to the navbar in `_quarto.yml`:

```yaml
website:
  navbar:
    left:
      - text: "New Page"
        href: newpage.qmd
```

3. Render and deploy

## Language Strategy

The website mixes two patterns depending on the page:

- **Homepage (`index.qmd`)** – Bilingual on a single page. English and
  Japanese paragraphs are presented in parallel so that both audiences can
  read the same information without a language switcher.
- **CV** – Split into separate pages. `cv.qmd` (English) and `cv-ja.qmd`
  (Japanese) are linked from the navbar as **CV** and **CV（日本語）**, and
  each links to its own full PDF (`cv-full.pdf` / `cv-full-ja.pdf`). The
  Japanese CV page lists Japanese-language publications that do not appear
  on the English page.

## Content Updates

### Updating the Homepage

Edit `index.qmd` to update:
- Personal introduction (bilingual)
- Research interests
- Recent news and updates

### Adding Publications

Publications are listed in **four** places, all of which are maintained by
hand. When adding or updating an entry, update each location that applies:

1. `cv.qmd` — short English CV page (English-language publications only).
2. `cv-ja.qmd` — short Japanese CV page (English **and** Japanese
   publications).
3. `cv-full.Rmd` / `cv-full-ja.Rmd` — full CV PDFs (English / bilingual).
   Re-render the corresponding PDF after editing (see "Rebuilding the Full
   CV PDFs" above).
4. `publications.bib` — BibTeX archive kept as a personal reference. It is
   **not** consumed by Quarto or by the `.Rmd` sources; the entries on the
   pages are written as plain Markdown text. Keeping the `.bib` in sync is
   optional but recommended so that the file remains usable for citation
   exports.

Follow the existing citation format on each page when adding new entries.

### Updating CV Information

CV content (contact information, education, working experience, research
grants, professional activities, etc.) lives in four files:

- `cv.qmd` — short English CV page
- `cv-ja.qmd` — short Japanese CV page
- `cv-full.Rmd` — full English CV (PDF source)
- `cv-full-ja.Rmd` — full Japanese CV (PDF source)

Edit each file as needed and re-render the PDFs after changing the `.Rmd`
sources.

## Troubleshooting

### Site not updating on GitHub Pages

- Check that `quarto render` was run before committing
- Verify that changes are in the `docs/` directory
- Check GitHub Actions for any build errors

### Images not displaying

- Ensure images are in the `images/` directory
- Check that image paths in `.qmd` files are correct (relative paths)
- Verify image files are committed to Git

## License

This website template is available for academic use. Content copyright belongs to the respective authors.

---

*Last updated: April 2026*
