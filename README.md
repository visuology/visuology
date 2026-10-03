# visuology.nl

The personal website of **Jeroen Lavèn**: a one-page link-in-bio site with a short introduction, an "about me" pop-up and links to email, Instagram and LinkedIn.

**Live:** [visuology.nl](https://visuology.nl)

![visuology.nl on desktop](docs/screenshot-desktop.png)

<p>
  <img src="docs/screenshot-mobile-light.png" alt="Home screen on a phone" width="240">
  <img src="docs/screenshot-mobile-about.png" alt="About me pop-up on a phone" width="240">
  <img src="docs/screenshot-mobile-dark.png" alt="Home screen on a phone in dark mode" width="240">
</p>

## Features

- **Tiny and fast:** plain HTML, CSS and a few lines of JavaScript. No frameworks, build step or web fonts. A first visit loads about 25 KB.
- **Works on any screen:** the layout stacks on phones, and the "about me" pop-up always fits the screen with its text scrolling inside.
- **Dark mode** follows the visitor's device setting.
- **Click the photo** to hear a sound and see the wave animation (skipped for visitors who prefer reduced motion).
- **Accessible:** the photo and close buttons are real buttons, the pop-up is announced as a dialog, focus moves into it and back, and <kbd>Esc</kbd> closes it.
- **Good link previews and search results:** a meta description, Open Graph tags for LinkedIn, WhatsApp and Slack, and `Person` structured data for Google.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The page, including its small script |
| `style.css` | All styling, with light and dark colours as CSS variables at the top |
| `jeroen-300.webp` / `jeroen-300.jpg` | The profile photo (WebP, with a JPEG fallback for old browsers) |
| `og-image-800.jpg` | The image used in link previews |
| `sound.mp3` | The sound played when the photo is clicked |
| `favicon*`, `apple-touch-icon.png`, `android-chrome-*`, `mstile-150x150.png`, `site.webmanifest`, `browserconfig.xml` | Browser and home-screen icons |
| `CNAME` | Points GitHub Pages at the `visuology.nl` domain |
| `docs/` | Screenshots for this README |

## Editing

Edit `index.html` or `style.css`, commit, and push to the **`gh-pages`** branch. GitHub Pages publishes it to visuology.nl within a minute or two.

> **After changing `style.css`**, raise the number in `style.css?v=2` in `index.html` (to `?v=3`, and so on). Otherwise visitors' browsers may keep using the old cached stylesheet with the new page.

To preview locally, open `index.html` in a browser, or run a small server:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Replacing the photo

Export a square photo at 300 × 300 px as both `jeroen-300.webp` and `jeroen-300.jpg`, with location and camera data removed. For example, with ImageMagick:

```sh
convert original.jpg -strip -resize 300x300 -quality 80 jeroen-300.webp
convert original.jpg -strip -resize 300x300 -quality 82 jeroen-300.jpg
convert original.jpg -strip -resize 800x800 -quality 80 og-image-800.jpg
```

### After changing the text

If you change your job title or links, update the matching lines in the `<head>` of `index.html` too: the `description`, the `og:` tags and the JSON-LD `Person` block. That keeps link previews and search results in sync.
