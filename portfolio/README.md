# Portfolio Project Guidelines

## Required Frontmatter Schema

```yaml
---
title: "Project Title"
subtitle: "Optional brief tagline"
description: "1-2 sentence summary for listing page"
image: "/assets/projects/{project-slug}/{project-slug}.jpg"
category: "NLP | GenAI | Exploratory Data Analysis | Machine Learning"
type: "AI | Deep Learning | Data Analysis | NLP Pipeline | etc."
skills:
  - SkillName  # Use exact names from /_data/skills-glossary.md
featured: 1-4  # Optional: Lower number = higher priority on homepage
---
```

## Asset Organization

- Place all project assets in `/assets/projects/{project-slug}/`
- Main image should match project slug name
- Always use absolute paths starting with `/`

## Code Blocks

- Code is NOT executed during build (`eval: false` in _metadata.yml)
- Use `{python}` for syntax highlighting only
- Include pre-rendered output images below code blocks
- Use `#| code-fold: false` to keep code visible by default
