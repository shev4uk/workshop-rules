# Add Code Snippet Region

Creates a new code snippet region in the snippets file for use with `<<<` imports.

## Steps

1. Open `slidev/snippets/external.ts` (or create a new snippet file)
2. Add a new region with `#region snippet` and `#endregion snippet` markers
3. Use the snippet in slides with `<<< @/snippets/external.ts#snippet`

## Template

**In `slidev/snippets/external.ts`:**
```typescript
// #region snippet
export function myFunction() {
  // Your code here
}
// #endregion snippet
```

**In `slidev/slides.md`:**
```markdown
<<< @/snippets/external.ts#snippet
```

## Usage

Run this command when you want to:
- Reuse code snippets across multiple slides
- Keep code examples in sync
- Import external TypeScript/JavaScript code into slides

## Notes

- Snippet regions use `#region snippet` and `#endregion snippet` markers
- The `#snippet` anchor in the import path references the region
- Snippets are syntax-highlighted automatically in slides
