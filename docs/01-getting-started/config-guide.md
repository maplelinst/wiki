# _config System Examples & Usage Guide

## Overview

The `_config` folder contains two JSON files that organize your knowledge base:
- **metadata.json** — Tracks all images and media files
- **tags.json** — Organizes documents and content by tags

---

## 1. metadata.json — Image Tracking

### Structure of an Image Entry

```json
{
  "filename": "2026-05-20-api-architecture.png",
  "path": "assets/images/work/",
  "uploadDate": "2026-05-20",
  "category": "work",
  "source": "screenshot",
  "license": "proprietary",
  "description": "REST API architecture diagram showing microservices",
  "documentReferences": [
    "docs/02-work/api-design.md",
    "docs/04-reference/architecture-standards.md"
  ],
  "tags": ["work", "important", "architecture"]
}
```

### Field Explanations

| Field | Purpose | Example |
|-------|---------|---------|
| `filename` | Image file name | `2026-05-20-api-architecture.png` |
| `path` | Where it's stored | `assets/images/work/` |
| `uploadDate` | When added (YYYY-MM-DD) | `2026-05-20` |
| `category` | Content category | `work`, `learning`, `reference` |
| `source` | Where it came from | `screenshot`, `hand-drawn`, `tool-generated` |
| `license` | License type | `proprietary`, `cc-by`, `public-domain` |
| `description` | What it shows | Brief explanation |
| `documentReferences` | Docs that use it | Array of paths |
| `tags` | Search tags | Array of tag names |

---

## 2. tags.json — Document Organization

### Structure of a Tag Entry

```json
{
  "work": {
    "description": "Work-related projects and tasks",
    "color": "#0078D4",
    "documents": [
      {
        "path": "docs/02-work/api-design.md",
        "addedDate": "2026-05-20"
      }
    ]
  }
}
```

### Pre-configured Tags

| Tag | Purpose | Use When |
|-----|---------|----------|
| `work` | Active projects | Current assignments |
| `learning` | Educational | Courses, tutorials |
| `reference` | Best practices | Standards, guides |
| `archive` | Completed | Old projects |
| `important` | High priority | Urgent work |
| `todo` | Action items | Pending tasks |
| `python`, `database`, etc. | Topic-specific | Custom tags you create |

---

## 3. Practical Workflow Examples

### Example 1: Adding a New Project Screenshot

**Step 1:** Upload image to `assets/images/work/2026-05-20-dashboard-mockup.png`

**Step 2:** Add entry to `metadata.json`:
```json
{
  "filename": "2026-05-20-dashboard-mockup.png",
  "path": "assets/images/work/",
  "uploadDate": "2026-05-20",
  "category": "work",
  "source": "screenshot",
  "license": "proprietary",
  "description": "UI mockup of new customer dashboard",
  "documentReferences": ["docs/02-work/dashboard-project.md"],
  "tags": ["work", "todo"]
}
```

**Step 3:** Reference in markdown:
```markdown
# Dashboard Project

![Dashboard Mockup](../assets/images/work/2026-05-20-dashboard-mockup.png)
```

**Step 4:** Add document to `tags.json`:
```json
"todo": {
  "documents": [
    {
      "path": "docs/02-work/dashboard-project.md",
      "addedDate": "2026-05-20",
      "status": "in-progress"
    }
  ]
}
```

---

### Example 2: Tracking Multiple Versions

```json
{
  "filename": "database-schema-v3.png",
  "path": "assets/diagrams/",
  "uploadDate": "2026-05-18",
  "category": "reference",
  "description": "Database schema v3 with user and order tables",
  "version": "3.0",
  "previous": "database-schema-v2.png",
  "documentReferences": [
    "docs/04-reference/database-design.md",
    "docs/02-work/migration-plan.md"
  ],
  "tags": ["reference", "database", "important"]
}
```

---

### Example 3: Cross-referenced Learning Content

```json
{
  "filename": "2026-05-19-python-decorators-diagram.png",
  "path": "assets/images/learning/",
  "uploadDate": "2026-05-19",
  "category": "learning",
  "source": "hand-drawn",
  "description": "Visual explanation of Python decorator patterns",
  "documentReferences": [
    "docs/03-learning/python-advanced.md"
  ],
  "tags": ["learning", "python"]
}
```

**In tags.json:**
```json
"python": {
  "description": "Python-related learning and projects",
  "color": "#3776AB",
  "documents": [
    {
      "path": "docs/03-learning/python-advanced.md",
      "addedDate": "2026-05-19"
    }
  ]
}
```

---

## 4. Querying Your Knowledge Base

### Find all images in a category:
```bash
grep -A 10 '"category": "work"' _config/metadata.json
```

### Find all documents with a tag:
```bash
grep -A 20 '"work": {' _config/tags.json
```

### Find high-priority items:
```bash
grep -B 10 '"important"' _config/tags.json
```

---

## 5. Best Practices

✓ Update `metadata.json` when uploading new images  
✓ Use consistent date format: YYYY-MM-DD  
✓ Add `documentReferences` to link images to notes  
✓ Create custom tags for topics you frequently reference  
✓ Archive old content and update tags  
✓ Use descriptive filenames with dates  

✗ Don't leave images untracked  
✗ Don't use spaces in filenames  
✗ Don't create too many custom tags (keep under 15)  

---

## 6. Statistics & Maintenance

`metadata.json` includes statistics:
```json
"statistics": {
  "totalImages": 4,
  "byCategory": {
    "work": 2,
    "learning": 1,
    "reference": 1
  },
  "lastUpdated": "2026-05-20"
}
```

Update these when you add/remove images to track growth.

---

**Ready to populate your knowledge base!**
