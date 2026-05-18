# Thomas Felton — Portfolio Site

A static personal site for Thomas Felton, built for GitHub Pages.

## Files

```
index.html      # All page content
styles.css      # Visual design
main.js         # Tiny JS (just sets footer year)
resume.pdf      # Downloadable résumé
README.md       # This file
```

No build step, no dependencies, no JavaScript framework. Open `index.html` directly in any browser to preview.

## Deploying to GitHub Pages

1. **Create a new repository on GitHub** named exactly `tdfelton.github.io` (this special name makes it your root user site, served at `https://tdfelton.github.io/`).
2. **Initialize and push these files** from a terminal in this directory:

   ```bash
   git init
   git add .
   git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin https://github.com/TDFelton/tdfelton.github.io.git
   git push -u origin main
   ```

3. **Enable Pages**: On GitHub, go to the repo → **Settings** → **Pages** → under "Build and deployment" set **Source** to **Deploy from a branch**, **Branch** = `main`, folder = `/ (root)`. Save.
4. Wait 30–60 seconds. The site will be live at `https://tdfelton.github.io/`.

**Alternative:** If you'd rather keep the repo named something else (e.g., `portfolio`), the site will live at `https://tdfelton.github.io/portfolio/` instead. Same setup steps; just rename the repo.

### Custom domain (optional, later)

If you ever buy a domain (e.g., `thomasfelton.com`):
1. Add a file named `CNAME` (no extension) containing just the domain: `thomasfelton.com`
2. In your domain registrar's DNS, add A records pointing to GitHub Pages IPs (see GitHub's [docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)).
3. In repo Settings → Pages, enter the custom domain and enable HTTPS.

## How to update content

Everything is in **`index.html`**. Search for the text you want to change and edit in place. The sections are clearly marked with HTML comments (`<!-- About -->`, `<!-- Projects -->`, etc.).

### Adding a new project

In `index.html`, find the `<!-- Projects -->` section. Copy this template inside the `<div class="col-body">`:

```html
<article class="project">
  <div class="project-head">
    <h3 class="project-title">YOUR PROJECT TITLE</h3>
    <span class="badge badge-active">In progress</span>  <!-- or remove this span -->
  </div>
  <p class="project-tagline">One-line tagline in italic red.</p>
  <p class="prose">
    Longer description paragraph.
  </p>
  <ul class="tag-row">
    <li>Python</li><li>Tool</li><li>Tool</li>
  </ul>
  <p class="project-links">
    <a href="https://github.com/TDFelton/repo" target="_blank" rel="noopener">GitHub →</a>
  </p>
</article>
```

### Adding a new experience entry

In the `<!-- Experience -->` section:

```html
<article class="entry">
  <header class="entry-head">
    <h3 class="entry-title">ROLE TITLE</h3>
    <p class="entry-org">Organization · Location</p>
    <p class="entry-meta">Month YYYY — Month YYYY</p>
  </header>
  <ul class="entry-bullets">
    <li>Bullet about what you did and the impact.</li>
    <li>Another bullet.</li>
  </ul>
</article>
```

### Adding a new skill block

In the `<!-- Skills -->` section:

```html
<div class="skill-block">
  <h3 class="skill-heading">Category Name</h3>
  <p class="skill-list">Item · Item · Item</p>
</div>
```

### Adding a course

In the `<!-- Coursework -->` section, copy a `<div class="course">...</div>` block and edit.

### Adding your photo

Replace the `.photo-placeholder` block in the hero with:

```html
<img src="photo.jpg" alt="Thomas Felton" class="photo" />
```

Then add this CSS to `styles.css`:

```css
.photo {
  width: 100%;
  aspect-ratio: 4 / 5;
  object-fit: cover;
  margin-bottom: 1.25rem;
  border: 1px solid var(--ink-muted);
}
```

Save the photo as `photo.jpg` in the same folder as `index.html`.

### Updating the résumé

Just replace `resume.pdf` with a new file of the same name. The site's link will continue to work.

## Design notes

- **Fonts**: Fraunces (serif display) + IBM Plex Sans (body) + IBM Plex Mono (small caps / metadata). Loaded from Google Fonts.
- **Color tokens** are defined in `:root` at the top of `styles.css`. Change `--accent` (currently brick red `#a8331f`) to recolor the site's highlight.
- **Two-column layout** breaks to single-column below 880px.
- **Sticky nav** with smooth-scroll anchors.
- **Accessible**: skip link, semantic HTML, focus-visible outlines, keyboard navigable, `prefers-reduced-motion` respected, decent contrast ratios.
- **Print styles** included — the page prints cleanly without nav/footer.

## Future improvements to consider

- Replace the photo placeholder with a real headshot.
- Add a `/projects/stuff-plus/` subpage with charts, methodology writeups, and leaderboard tables once your model is refined.
- When you have a conservation project, add a "Conservation" section in the same pattern as Projects.
- Once the NMR paper is published, link the DOI from the project entry.
