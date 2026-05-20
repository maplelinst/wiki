# Knowledge Base Setup & Usage Guide

## Folder Structure Overview

```
knowledge_base/
├── docs/                    # Main content organized by category
├── assets/                  # Images, diagrams, and media
├── _config/                 # Configuration and metadata
├── index.md                 # Main entry point
└── README.md                # This file
```

## Content Guidelines

### Naming Conventions
- Documents: `YYYY-MM-DD-topic-title.md` or `topic-title.md`
- Images: `YYYY-MM-DD-descriptive-name.png` (e.g., `2026-05-20-architecture-v2.png`)
- Avoid spaces in filenames; use hyphens instead

### Organizing Content

1. **Getting Started** — Onboarding, setup docs, templates
2. **Work** — Active projects, notes, action items
3. **Learning** — Courses, tutorials, skill development
4. **Reference** — Best practices, standards, reusable content
5. **Archive** — Completed work, historical records

### Linking Images

Use relative paths in markdown:
```markdown
![Description](../assets/images/work/screenshot-name.png)
```

## Image Management

- Place images in `/assets/images/` with subdirectories matching your content category
- Keep original and thumbnail versions
- Update `_config/metadata.json` when uploading important images
- Consider image optimization for web (PNG/JPG, <500KB)

## Metadata & Tagging

- **metadata.json** — Track image sources, licenses, and references
- **tags.json** — Manage content tags for cross-referencing

## Best Practices

✓ Keep documents focused and modular  
✓ Link frequently between related documents  
✓ Archive completed work regularly  
✓ Update metadata when adding images  
✓ Use consistent naming conventions  
✗ Avoid large image files (optimize first)  
✗ Don't duplicate content across folders  

---

**Version:** 1.0  
**Last Updated:** 2026-05-20
