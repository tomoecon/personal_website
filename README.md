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
website_test/
├── _quarto.yml              # Site configuration
├── index.qmd                # Homepage (bilingual: English/Japanese)
├── cv.qmd                   # Curriculum Vitae (bilingual)
│
├── files/                   # Downloadable files (PDFs, etc.)
├── images/                  # Image files
│
├── styles.css               # Custom CSS
├── custom.scss              # Custom SCSS styles
├── docs/                    # Generated site (published to GitHub Pages)
├── .gitignore
├── website_test.Rproj       # RStudio project file
└── README.md
```

The website has been simplified to focus on essential content with a clean, minimalist design.

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

3. Open the project in RStudio (double-click `website_test.Rproj`)

### Building the Site

To render the website locally:

```bash
quarto render
```

This will generate the static site in the `docs/` directory.

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

The website uses a **bilingual approach** where English and Japanese content coexist on the same pages:
- Both `index.qmd` and `cv.qmd` contain parallel sections in English and Japanese
- This design provides accessibility to both domestic and international audiences
- No language switcher needed - all content is visible in both languages

## Content Updates

### Updating the Homepage

Edit `index.qmd` to update:
- Personal introduction (bilingual)
- Research interests
- Recent news and updates

### Adding Publications

Edit `cv.qmd` and add new entries under the Publications section. The file includes sections for:
- Peer-Reviewed Journal Articles
- Journal Articles (Not Peer-Reviewed)
- Working Papers

Follow the existing citation format when adding new publications.

### Updating CV Information

Edit `cv.qmd` to update:
- Contact information
- Education history
- Working experience
- Research grants
- Publications

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

*Last updated: January 2026*
