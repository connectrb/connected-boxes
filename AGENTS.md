# AGENTS.md - Connected Boxes Hugo Site

This document provides guidelines for AI agents working with the Connected Boxes Hugo static site repository.

## Project Overview

This is a Hugo static site using the "hugo-book" theme. The site contains blog posts and content about technology consulting experiences.

**Key Technology Stack:**
- Hugo v0.147.2+ (extended version)
- Hugo Book theme (submodule)
- Markdown content
- TOML configuration

## Build Commands

### Development
```bash
# Start local development server with live reload
hugo server

# Start development server on specific port
hugo server -p 1313

# Start with draft posts visible
hugo server -D
```

### Production Build
```bash
# Build site for production (minified)
hugo --minify

# Build with verbose output and warnings
hugo --minify --printPathWarnings

# Build including draft posts
hugo -D

# Clean build (remove public directory)
rm -rf public && hugo --minify
```

### Theme Management
```bash
# Initialize/update theme submodule
git submodule update --init --recursive

# Update theme to latest
cd themes/hugo-book && git pull origin main
```

## Testing & Quality Assurance

### Content Validation
```bash
# Check for broken links
hugo --minify && htmltest

# Validate site structure
hugo --minify && tree public/

# Check Markdown syntax
# Install markdownlint-cli first: npm install -g markdownlint-cli
markdownlint content/**/*.md
```

### GitHub Actions
The CI/CD pipeline is defined in `.github/workflows/deploy.yml`. It:
1. Checks out repository with submodules
2. Sets up Hugo (latest extended version)
3. Builds site with `hugo --minify --printPathWarnings`
4. Deploys to GitHub Pages

## Code Style Guidelines

### Markdown Content
- **Front Matter:** Use TOML (`+++`) or YAML (`---`) format consistently
- **Headers:** Use sentence case for titles (capitalize first word only)
- **Line Length:** Keep lines under 100 characters where possible
- **Images:** Store in `static/` directory, reference with absolute paths: `/connected-boxes/image-name.ext`
- **File Names:** Use kebab-case: `post-title-here.md`

### Front Matter Standards
```toml
+++
title = 'Post Title'
date = 2026-04-03T13:14:28+11:00
draft = false
description = "Brief description for SEO and previews"
+++
```

### Directory Structure
```
content/
├── _index.md          # Homepage content
├── about.md           # About page
└── posts/
    ├── _index.md      # Posts listing page
    └── post-name.md   # Individual posts

static/                # Images, CSS, JS assets
archetypes/           # Content templates
themes/               # Hugo theme (submodule)
```

### Naming Conventions
- **Directories:** lowercase, kebab-case
- **Markdown files:** kebab-case-with-dashes.md
- **Image files:** descriptive-names-with-dashes.ext
- **Variables:** lowercase-with-hyphens in TOML

### Import/Asset Management
- **CSS/JS:** Place in `themes/hugo-book/assets/` for theme customization
- **Images:** Place in `static/` and reference with absolute paths
- **Custom layouts:** Create in `layouts/` directory to override theme

## Error Handling & Best Practices

### Content Creation
1. **Always include front matter** with at minimum: title, date, draft status
2. **Use descriptive alt text** for images
3. **Test links** before committing
4. **Preview drafts** with `hugo server -D`

### Git Workflow
```bash
# Standard workflow
git add .
git commit -m "feat: add new blog post about [topic]"
git push origin main

# When updating theme
git submodule update --remote themes/hugo-book
git add themes/hugo-book
git commit -m "chore: update hugo-book theme"
```

### Common Issues & Solutions
1. **Missing theme:** Run `git submodule update --init --recursive`
2. **Draft posts not showing:** Use `-D` flag or set `draft = false`
3. **Build errors:** Check Hugo version compatibility with theme
4. **Image not displaying:** Verify path in `static/` directory

## Development Environment

### VS Code Settings
The repository includes `.vscode/settings.json` with:
- Hugo framework identification
- Public folder configuration
- Preview host settings
- Git integration

### Recommended Extensions
- Hugo Language and Syntax Support
- Markdown All in One
- Front Matter CMS

## Agent-Specific Instructions

### When Creating Content
1. Use `archetypes/default.md` as template
2. Follow existing post patterns in `content/posts/`
3. Add relevant images to `static/` directory
4. Update any index pages if adding new sections

### When Modifying Theme
1. Avoid modifying files in `themes/hugo-book/` directly
2. Create overrides in project root `layouts/` directory
3. Document theme customizations in README or comments

### When Running Builds
1. Always test with `hugo server` before committing
2. Run production build locally before pushing
3. Check GitHub Actions workflow for deployment requirements

## Performance Optimization

### Build Optimization
```bash
# Minify output (already in workflow)
hugo --minify

# Enable gzip compression (server-side)
# Configure in hugo.toml or web server
```

### Image Optimization
- Compress images before adding to `static/`
- Use appropriate formats (JPEG for photos, PNG for graphics)
- Consider responsive images for different screen sizes

## Security Considerations

1. **No sensitive data** in repository
2. **GitHub token** managed in Actions secrets
3. **External dependencies** via submodules only
4. **Content validation** before deployment

## Maintenance Tasks

Regular maintenance should include:
- [ ] Update Hugo version in CI/CD workflow
- [ ] Update theme submodule to latest stable
- [ ] Check for broken links
- [ ] Optimize images in static directory
- [ ] Review and update content as needed

## Quick Reference

| Command | Purpose |
|---------|---------|
| `hugo server` | Start dev server |
| `hugo --minify` | Production build |
| `hugo -D` | Include drafts |
| `git submodule update` | Update theme |

**Note:** This is a static site - there are no runtime tests or linting tools configured. Content quality is verified through manual review and build validation.