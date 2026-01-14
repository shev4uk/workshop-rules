# Build Slidev Static Site

Builds the Slidev presentation as a static site for deployment.

## Steps

1. Navigate to the `slidev/` directory
2. Run `npm run build` (or `pnpm build`)
3. The built site will be in `slidev/dist/`

## Usage

Run this command when you want to:
- Prepare the presentation for deployment (Netlify/Vercel)
- Test the production build locally
- Verify static export works correctly

## Notes

- The `dist/` folder contains the static SPA ready for deployment
- Both `netlify.toml` and `vercel.json` are configured for SPA routing
- Make sure all dependencies are installed before building
