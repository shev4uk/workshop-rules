# Add New Slide Template

Inserts a new slide template with title and speaker notes section.

## Steps

1. Open `slidev/slides.md`
2. Add a new slide separator (`---`)
3. Insert the slide template with:
   - Frontmatter (optional: theme, layout, transition)
   - Slide title (H1)
   - Content area
   - Speaker notes section (HTML comment)

## Template

```markdown
---

# Slide Title

Slide content goes here.

<!--
Speaker notes:
- Point 1
- Point 2
- Demo: show X
-->
```

## Usage

Run this command when you want to:
- Add a new slide to the presentation
- Ensure consistent slide structure
- Include speaker notes from the start

## Notes

- Use `---` to separate slides
- Speaker notes in HTML comments are visible in Presenter Mode
- Frontmatter can override global theme settings per slide
