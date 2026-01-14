# Add New Page File

Creates a new slide page file and imports it into the main slides.

## Steps

1. Create a new file in `slidev/pages/` (e.g., `slidev/pages/my-topic.md`)
2. Add slide content to the new file
3. Import it in `slidev/slides.md` using the `src:` attribute

## Template

**New file:** `slidev/pages/my-topic.md`
```markdown
# Page Title

Content for this imported slide page.
```

**In `slidev/slides.md`:**
```markdown
---
src: ./pages/my-topic.md
---
```

## Usage

Run this command when you want to:
- Organize slides into separate files by topic
- Split large presentations into manageable chunks
- Reuse slide pages across multiple presentations

## Notes

- Page files are imported using `src:` in frontmatter
- The `hide: false` option can control visibility
- See `slidev/pages/imported-slides.md` for an example
