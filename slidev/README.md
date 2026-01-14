# Welcome to [Slidev](https://github.com/slidevjs/slidev)!

To start the slide show:

- `npm install` (or `pnpm install`)
- `npm run dev` (or `pnpm dev`)
- visit <http://localhost:3030>

Edit the [slides.md](./slides.md) to see the changes.

Learn more about Slidev at the [documentation](https://sli.dev/).

## Deployment

### GitHub Pages

This repository includes a GitHub Actions workflow that automatically deploys the slides to GitHub Pages.

**Setup:**

1. Go to your repository **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. Push to `main` or `master` branch to trigger deployment

The workflow (`.github/workflows/deploy-pages.yml`) will:
- Build the slides on every push to `main`/`master`
- Deploy to GitHub Pages automatically

**Manual trigger:** You can also trigger deployment manually via **Actions** → **Deploy to GitHub Pages** → **Run workflow**

### Other Platforms

- **Netlify**: Configured via `netlify.toml`
- **Vercel**: Configured via `vercel.json`
