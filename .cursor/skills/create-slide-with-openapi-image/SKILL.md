---
name: Create Slide with OpenAPI Image
description: Generate images using OpenAPI (OpenAI DALL-E) and add them to Slidev slides with proper formatting and layouts.
---

# Create Slide with OpenAPI Image

This skill teaches how to generate images using OpenAPI (OpenAI DALL-E API) and integrate them into Slidev presentation slides.

## When to Use

- Use this skill when you need to create custom images for slides
- When you want to generate illustrations, diagrams, or visual content programmatically
- When creating slides that require unique, AI-generated imagery
- When you need to add images to slides using Slidev's image layouts

## Instructions

### Step 1: Generate Image Using OpenAPI

1. **Obtain API Key**: Ensure you have an OpenAI API key with access to DALL-E image generation
2. **Generate Image**: Use OpenAI's image generation API endpoint:
   - Endpoint: `https://api.openai.com/v1/images/generations`
   - Method: POST
   - Headers: `Authorization: Bearer YOUR_API_KEY`, `Content-Type: application/json`
   - Body: JSON with `model`, `prompt`, `n` (number of images), `size` (e.g., "1024x1024")

3. **Save Image**: Download the generated image URL and save it locally or use the URL directly

### Step 2: Add Image to Slidev Slide

Choose one of these methods based on your slide layout needs:

#### Method A: Using Image Layout (Recommended for side-by-side content)

```markdown
---
layout: image-right
image: https://your-generated-image-url.com/image.png
---

# Slide Title

Your content here appears on the left, image on the right.
```

Available layouts:
- `image-right`: Image on right, content on left
- `image-left`: Image on left, content on right
- `image`: Full-screen image with optional overlay text

#### Method B: Using HTML img Tag (For inline images)

```markdown
---

# Slide Title

Your content here.

<img src="https://your-generated-image-url.com/image.png" alt="Description" class="w-80 mx-auto" />

More content below the image.
```

#### Method C: Using Background Image

```markdown
---
background: https://your-generated-image-url.com/image.png
class: text-center
---

# Slide Title

Content with image as background.
```

### Step 3: Best Practices

1. **Image Sizing**: 
   - Use appropriate sizes (1024x1024 for square, 1024x1792 for portrait, 1792x1024 for landscape)
   - Consider aspect ratio for your slide layout

2. **Image Storage**:
   - For production: Save images to `slidev/public/` directory and reference as `/image.png`
   - For development: Can use external URLs, but prefer local files for reliability

3. **Accessibility**:
   - Always include `alt` text for images
   - Ensure images don't conflict with text readability

4. **Performance**:
   - Optimize images before adding to slides
   - Use appropriate formats (PNG for transparency, JPG for photos)

5. **Speaker Notes**:
   - Add notes about the image in speaker notes section:
   ```markdown
   <!--
   Speaker notes:
   - This image was generated using DALL-E to illustrate...
   - Key points about the visual...
   -->
   ```

## Example: Complete Slide with Generated Image

```markdown
---
layout: image-right
image: https://oaidalleapiprodscus.blob.core.windows.net/private/org-xxx/user-xxx/img-xxx.png
---

# AI-Generated Illustration

This slide demonstrates how to integrate OpenAPI-generated images.

The image on the right was created using DALL-E to visualize our concept.

<!--
Speaker notes:
- Image generated via OpenAI DALL-E API
- Prompt: "Modern tech illustration showing..."
- Key visual elements to highlight
-->
```

## Security Notes

- **Never commit API keys** to the repository
- Use environment variables for API keys
- Store generated images in version control only if they're final assets
- Consider using `.gitignore` for temporary generated images

## Troubleshooting

- **Image not loading**: Check URL accessibility, CORS settings, and network connectivity
- **Layout issues**: Verify Slidev theme supports the layout you're using
- **API errors**: Ensure API key is valid and you have sufficient credits/quota
