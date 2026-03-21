# Project Assets Organization

## Directory Structure
```
/assets/projects/{project-slug}/
  - {project-slug}.jpg/png  (main header image)
  - *.png                   (supporting images, diagrams)
  - *_files/                (Quarto-generated outputs)
```

## Path Convention
Always use absolute paths in .qmd frontmatter:
```yaml
image: /assets/projects/{project-slug}/{image}.jpg
```

## Naming Convention
- Use lowercase with hyphens for project slugs
- Match directory name to project file name
- Keep main images descriptively named
