# keshav-cse.github.io

Personal site: https://keshav-cse.github.io. A single static page (`index.html`, no build step) with a
fixed sidebar, About / News / Research / Projects / Experience / Skills sections, and a dark-mode toggle.

## Editing

- **Content:** edit `index.html` directly. Each section is a `<section id="...">`. News items marked
  `class="extra"` stay hidden until "Show more" is clicked.
- **Photo:** add `assets/photo.jpg` and replace the `KT` placeholder in `.headshot` with
  `<img src="assets/photo.jpg" alt="Keshav Talwar">`.
- **Colours:** the CSS variables at the top of `<style>` (`--link`, `--heading`, …), with separate light and dark sets.
- Keep the content consistent with the CV's `PROFILE.md` (Overleaf repo `69cad30b575d251a232ee969`).

Pushing to `main` redeploys the site via GitHub Pages in about a minute.
