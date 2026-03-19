# CLAUDE.md - AI Context for marcocamilo.com

This document provides context for AI assistants working on this Quarto-based ML portfolio website.

## Project Overview

**Purpose**: Professional portfolio website showcasing ML/AI projects
**Framework**: Quarto 1.9+ static site generator
**Hosting**: GitHub Pages with custom domain (marcocamilo.com)
**Owner**: Marco-Andrés Camilo-Pietri
**Last Major Refactor**: March 2026 (upgraded from 2024 implementation)

## Tech Stack

- **Quarto** - Static site generator with Markdown + YAML frontmatter
- **Custom EJS Templates** - Dynamic project listings (`_templates/listing.ejs`, `_templates/featured.ejs`)
- **CSS/SCSS** - Custom theming with light/dark mode support
- **Shields.io** - Technology skill badges with official logos
- **No Code Execution** - All code blocks are for display only (`execute: enabled: false`)

## Project Structure

```
marcocamilo.com/
├── _quarto.yml              # Main site configuration
├── _includes/               # Reusable HTML components (loop.html)
├── _templates/              # EJS templates for listings
├── _sidebar.qmd             # Reusable sidebar component
├── _data/                   # Reference data
│   └── skills-glossary.md   # Canonical skill names
├── portfolio/               # Project articles (.qmd files)
│   ├── _metadata.yml        # Portfolio-specific settings
│   └── *.qmd               # Individual project pages
├── assets/
│   ├── css/                # Styles (global.css + theme SCSS)
│   ├── img/                # General images
│   └── projects/           # Project-specific assets
├── index.qmd               # Homepage
├── portfolio.qmd           # Portfolio listing page
├── about.qmd               # About page
└── _site/                  # Build output (not in git)
```

## Key Configuration Files

### _quarto.yml
- **Output directory**: `_site/`
- **Code execution**: Disabled globally in portfolio via `_metadata.yml`
- **Image handling**: `default-image-extension: ""` (prevents double extensions like `.png.png`)
- **Resources**: Must include `assets/**` to copy all images to build
- **Themes**:
  - Light: default + `assets/css/light-mods.scss`
  - Dark: cyborg + `assets/css/dark-mods.scss`
  - Global: `/assets/css/global.css`

### portfolio/_metadata.yml
```yaml
execute:
  enabled: false  # Code blocks are for display only
toc: true
toc-expand: true
toc-depth: 4
# Note: number-sections NOT used - conflicts visually with emoji headings
```

## Portfolio Project Schema

Each `.qmd` file in `portfolio/` should follow this frontmatter structure:

```yaml
---
title: "Project Title"
subtitle: "Optional brief tagline"
description: "1-2 sentence summary for listing page"
image: "/assets/projects/{project-slug}/{project-slug}.{ext}"
category: "NLP | GenAI | Exploratory Data Analysis | Machine Learning"
type: "AI | Deep Learning | Data Analysis | NLP Pipeline | etc."
skills:
  - SkillName  # Use exact names from _data/skills-glossary.md
featured: 1-4  # Optional: Lower number = higher priority on homepage
---

![]({{< meta image >}})

## 🔍 Section Title

Content here...

::: {.callout-note}
## Key Finding Title
- Finding 1
- Finding 2
:::
```

### Article Formatting Preferences

**DO:**
- ✅ Use emoji prefixes on headings for visual hierarchy and easier scanning
- ✅ Use Quarto callout blocks for key highlights, findings, and important insights
- ✅ Choose appropriate callout types:
  - `callout-important` - Central findings, actionable insights, critical conclusions
  - `callout-note` - Key findings, summaries, design principles, guidelines
  - `callout-warning` - Critical implications, risks, important caveats
  - `callout-tip` - Strategic insights, best practices, useful observations
- ✅ Give callout blocks descriptive titles using `## Title` syntax inside the block

**DON'T:**
- ❌ Don't use numbered sections (`number-sections: true`) - looks too busy with emojis
- ❌ Don't overuse callouts - only for genuinely important highlights
- ❌ Don't use emojis in body text unless explicitly requested by user

**Emoji Selection Guidelines:**
- Use intuitive, recognizable emojis that match section content
- Examples: 🔍 (analysis/summary), 📖 (story/narrative), 💊 (medical/treatment), 🏥 (healthcare), 🔬 (technical/methodology), 📊 (data/evidence), 🎯 (conclusion/goals)
- Reference existing article emojis for consistency when available

### Important Path Conventions

1. **Always use absolute paths** starting with `/` for assets:
   - ✅ `image: /assets/projects/project-name/image.png`
   - ❌ `image: assets/projects/project-name/image.png`

2. **Always include file extensions** in image paths:
   - The `default-image-extension` is set to `""` to prevent doubling

3. **Project asset organization**:
   - Main image: `/assets/projects/{project-slug}/{project-slug}.{jpg|png|jpeg}`
   - Supporting images: `/assets/projects/{project-slug}/*.png`

## Custom Components

### Homepage Text Animation
- **File**: `_includes/loop.html`
- **Technology**: Vanilla JavaScript (no jQuery)
- **Purpose**: Rotating professional titles on homepage
- **Implementation**: CSS transitions + setInterval

### Sidebar Component
- **File**: `_sidebar.qmd`
- **Usage**: `{{< include _sidebar.qmd >}}`
- **Contains**: Profile image, bio, social links (LinkedIn, GitHub, Email)
- **Note**: Twitter link removed as of March 2026

### Technology Badges
- **File**: `_templates/listing.ejs` (lines 16-95)
- **Technology**: Shields.io badges with official logos
- **Coverage**: 50+ technologies including:
  - ML/DL frameworks (PyTorch, TensorFlow, Keras, XGBoost, LightGBM)
  - NLP libraries (NLTK, spaCy, Gensim, LangChain)
  - LLM APIs (OpenAI, Gemini, Anthropic, LiteLLM)
  - Data tools (NumPy, Pandas, Polars)
  - Visualization (Matplotlib, Seaborn, Plotly, Streamlit)
  - Cloud & MLOps (AWS, GCP, Azure, MLflow, W&B)
  - Vector DBs (Pinecone, Weaviate, ChromaDB, FAISS)

### Badge Format
```javascript
"skillname": "https://img.shields.io/badge/{Display}-white?logo={logo}&logoColor={color}"
```

**Adding new badges**: Edit `_templates/listing.ejs`, maintain alphabetical order within categories

## Styling Guidelines

### Dark Mode Consistency
Both light and dark modes should have:
- Matching font weights, sizes, and families
- Consistent link styles and hover effects
- Matching table and code block styling
- Badge images have `border-radius: 4px` for rounded corners

### Theme Files
- **Light**: `assets/css/light-mods.scss` (based on `default` theme)
- **Dark**: `assets/css/dark-mods.scss` (based on `cyborg` theme)
- **Global**: `assets/css/global.css` (shared styles)

### CSS Variables
Not currently using CSS custom properties, but styles are duplicated across theme files for consistency.

## Build Process

### Local Development
```bash
quarto preview  # Live preview with auto-reload
```

### Production Build
```bash
quarto render   # Generates _site/ directory
```

### Deployment
- Push to GitHub repository
- GitHub Pages automatically deploys from configured branch
- Custom domain: marcocamilo.com (via CNAME file)

## Common Issues & Solutions

### Issue: Images not displaying
**Cause**: Assets not included in build resources
**Solution**: Ensure `assets/**` is in `project.resources` in `_quarto.yml`

### Issue: Double file extensions (.png.png)
**Cause**: Quarto's default-image-extension adds extension to paths that already have one
**Solution**: Set `default-image-extension: ""` in `_quarto.yml`

### Issue: Code execution errors during build
**Cause**: Quarto trying to execute code blocks
**Solution**: Use `execute: enabled: false` in `portfolio/_metadata.yml`

### Issue: Dark mode styling inconsistent with light mode
**Cause**: Missing or incomplete style rules in dark-mods.scss
**Solution**: Ensure both theme files have matching structure (fonts, tables, code blocks, links)

## Documentation Files

- **README.md** - Project overview and quick start
- **portfolio/README.md** - Project schema and guidelines
- **_data/skills-glossary.md** - Canonical skill names and capitalization
- **assets/projects/README.md** - Asset organization conventions
- **CLAUDE.md** (this file) - AI assistant context

## Git Workflow

### Commit Strategy

**IMPORTANT**: Commit frequently with granular, focused commits. Each commit should represent a single logical change or task.

**DO:**
- ✅ Commit after completing each individual task or fix
- ✅ One commit per feature/fix/change
- ✅ Commit immediately after making a change, before moving to the next task
- ✅ Use descriptive, imperative commit messages

**DON'T:**
- ❌ Don't cluster multiple unrelated changes into one commit
- ❌ Don't wait to batch multiple edits together
- ❌ Don't combine different types of changes (e.g., styling + content + config)

**Example Good Commits:**
```
Commit 1: Add emoji prefixes to ai-patient-journey headings
Commit 2: Add callout blocks for key findings in ai-patient-journey
Commit 3: Update CLAUDE.md with formatting preferences
```

**Example Bad Commit:**
```
Commit 1: Update article formatting, add emojis, update docs, fix styling
```

### Commit Message Format
```
<Short imperative description>

- Bullet point changes
- More details

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

### Branch Strategy
- **main**: Production branch (deploys to GitHub Pages)
- **Feature branches**: Named descriptively (e.g., `claude-code-refactoring`)

## Design Principles

1. **No Visual Changes**: Refactors should preserve existing look and feel
2. **No Over-Engineering**: Keep solutions simple and focused
3. **Static Portfolio**: No live code execution, pre-rendered outputs only
4. **Maintainability**: Clear documentation, consistent structure
5. **Performance**: Minimize dependencies (removed jQuery in March 2026)

## Current Tooling Versions

- **Quarto**: 1.9+
- **No jQuery**: Removed March 2026 (replaced with vanilla JS)
- **No Python execution**: Code blocks are display-only
- **Shields.io**: External badge service (no local dependencies)

## Future Considerations

- Consider CSS custom properties for theme values
- Potential migration to web components for custom elements
- Image optimization (WebP format consideration)
- Lazy loading for images
- Badge icon SVG optimization

## Contact & Maintenance

**Owner**: Marco-Andrés Camilo-Pietri
**Email**: marco.camilopietri@gmail.com
**LinkedIn**: linkedin.com/in/marcocamilo
**GitHub**: github.com/marcocamilo

---

**Last Updated**: March 21, 2026
**Quarto Version**: 1.9+
**Major Refactor**: March 2026 (2024→2026 best practices upgrade)
