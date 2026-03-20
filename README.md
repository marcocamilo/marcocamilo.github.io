# marcocamilo.com - ML Portfolio Website

Professional portfolio showcasing ML/AI projects, built with Quarto and hosted on GitHub Pages.

## Tech Stack

- **Quarto** 1.9+ - Static site generator
- **Custom EJS Templates** - Dynamic project listings with technology badges
- **CSS/SCSS** - Custom theming with light/dark mode support
- **GitHub Pages** - Hosting with custom domain

## Quick Start

```bash
# Preview locally
quarto preview

# Build site
quarto render

# Output directory
_site/
```

## Project Structure

```
├── portfolio/           # Project articles (.qmd files)
├── assets/
│   ├── css/            # Styles (global.css + theme SCSS)
│   ├── img/            # General images
│   └── projects/       # Project-specific assets
├── _templates/         # EJS templates for listings
├── _includes/          # Reusable components
└── _quarto.yml        # Main configuration
```

## Adding New Projects

See `portfolio/README.md` for schema and guidelines.

## Customization

- **Themes:** Modify `assets/css/light-mods.scss` and `dark-mods.scss`
- **Badges:** Update badge definitions in `_templates/listing.ejs`
- **Categories:** Add categories in `_templates/listing.ejs`

## Build Configuration

- Code execution is disabled (`eval: false`)
- All code outputs are pre-rendered static images
- Build uses freeze mode for faster rebuilds
