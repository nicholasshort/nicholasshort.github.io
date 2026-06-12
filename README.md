# nicholasshort.com

Personal portfolio site. Plain HTML/CSS — no build step, no framework. Hosted on
GitHub Pages.

## Editing content

Every page is a standalone HTML file. To change copy, open the file and edit the
text between the tags. Don't touch the `<header>` or `<footer>` blocks unless
you want to change the nav on every page.

- `index.html` — home page with project list and contact
- `resume.html` — embedded PDF viewer
- `projects/greenbox.html` — GreenBox detail page
- `projects/digital-guitar-pedal.html` — Digital Guitar Pedal detail page
- `projects/mp3-player.html` — MP3 Player detail page
- `styles.css` — site-wide styles (colors, spacing, fonts)

### Adding an image to a project page

1. Drop the image in `assets/img/`.
2. In the project's HTML, find or add a `<figure>` block:

   ```html
   <figure>
     <img src="../assets/img/my-photo.jpg" alt="Describe the photo">
     <figcaption>Caption text.</figcaption>
   </figure>
   ```

### Adding a video

Self-hosted:

```html
<figure>
  <video controls>
    <source src="../assets/video/demo.mp4" type="video/mp4">
  </video>
  <figcaption>Demo video.</figcaption>
</figure>
```

Or embed YouTube:

```html
<figure>
  <iframe width="100%" height="400"
          src="https://www.youtube.com/embed/VIDEO_ID"
          frameborder="0" allowfullscreen></iframe>
</figure>
```

### Adding a new project

1. Copy one of the existing files in `projects/` to a new file (e.g.
   `projects/new-thing.html`).
2. Update the `<title>` and the content inside `<article>`.
3. Add a new `<li>` to the project list in `index.html`.

### Updating the resume

Replace `assets/NicholasShort_Resume_June2026.pdf` with the new file. If you
rename it, update the two `<a>` tags and the `<embed src>` in `resume.html`.

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploying to nicholasshort.com

1. Push to `main` on `github.com/nicholasshort/nicholasshort.github.io` (or any
   repo with Pages enabled).
2. In repo Settings → Pages, set source to `main` / root. The `CNAME` file in
   this repo already tells GitHub to serve at `nicholasshort.com`.
3. At your DNS registrar, add:
   - Four `A` records on the apex pointing to GitHub's IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - A `CNAME` on `www` pointing to `nicholasshort.github.io`
4. Wait ~10 minutes, then in Settings → Pages tick **Enforce HTTPS**.
