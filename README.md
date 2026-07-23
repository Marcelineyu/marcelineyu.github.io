# marcelineyu.github.io

Personal portfolio site for Marceline Yu — a single-page site covering background, experience, side projects, research work, and contact.

**Live:** https://marcelineyu.github.io/

## Screenshots

![Hero section with animated sky](.github/assets/screenshot-hero.png)

<table>
  <tr>
    <td width="50%"><img src=".github/assets/screenshot-experience.png" alt="Selected Experience timeline"></td>
    <td width="50%"><img src=".github/assets/screenshot-globe.png" alt="3D travel globe"></td>
  </tr>
</table>

## Stack

Plain HTML, CSS, and JavaScript. No framework, no build step, no dependencies to install. Libraries are loaded from CDN at runtime.

- Three.js (WebGPU build, via import map) — animated sky in the hero section, with a `lil-gui` control panel for turbidity, Rayleigh scattering, Mie coefficients, sun elevation/azimuth, exposure, and cloud parameters
- Three.js r128 (classic build) — interactive 3D travel globe with rotate, zoom, and per-marker detail on hover
- Formspree — contact form and resume-request form submissions
- Google Fonts (DM Sans)

## Structure

```
index.html    # entire page: all sections, markup, and inline config
styles.css    # all styling
js/
  hero-sky.js                    # ES module — WebGPU sky + cloud rendering and GUI
  site.js                        # main script — globe, lightbox, scroll reveals, section logic
  hero-statement-reveal.js       # hero copy animation
  v78-gift-state-safety.js       # hidden-gift state guard
  v80-navigation-links-form.js   # nav links + form wiring
  v81-smooth-connect-magnetic.js # magnetic hover on connect button
  v82-connect-label-guard.js     # connect label state
  v83-contact-motion.js          # contact section motion
  v87-connect-magnetic-final.js  # final magnetic-hover pass
  v90-contact-formspree.js       # Formspree submission handling
assets/images/                   # portraits, project previews, research and travel photos (.webp)
.nojekyll                        # disables Jekyll processing on GitHub Pages
```

The `v*` scripts are incremental layers added on top of `site.js` rather than edits to it — later files override or refine earlier behavior. Load order in `index.html` matters.

## Page sections

| Section | Contents |
|---|---|
| Hero | Name, positioning line, animated sky background |
| 01 · About Me | Bio, languages, education, technical skills |
| 02 · Selected Experience | Reverse-chronological roles with tags |
| 03 · Things I Build | Linked project cards (Supply Chain Crisis Simulator, AI Reel Maker, Artly, Photography, MarketLens) |
| 04 · Research & Projects | Expandable entries with photo galleries and lightbox |
| 05 · Beyond Work | Personal story, volunteer work, 3D travel globe |
| 06 · Stay Connected | Contact form, resume request, hidden gift easter egg |

## Running locally

Because `index.html` uses ES modules and an import map, opening the file directly with `file://` will not work. Serve it over HTTP:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Any static server works (`npx serve`, VS Code Live Server, etc.).

## Deploying

GitHub Pages serves the `main` branch from the repository root. Push to `main` and the live site updates — no build or workflow step involved.

## Notes for future edits

- Images are `.webp` and live flat in `assets/images/` with descriptive prefixes (`research-`, `beyond-`, `portrait-`).
- Form endpoints are hardcoded in the markup and in `js/v90-contact-formspree.js`; update both if the Formspree form ID changes.
- The WebGPU sky falls back gracefully on browsers without WebGPU support — test hero changes in both Chrome and Safari.
- New project cards go in the `03 · Things I Build` block in `index.html` with a matching preview image in `assets/images/`.
- README screenshots live in `.github/assets/`, kept separate from `assets/images/` so they aren't shipped with the site.

## Contact

marceline.yu@yale.edu · [LinkedIn](https://www.linkedin.com/in/marcelineyu/)

---

Content and images © Marceline Yu. Code is provided as-is for reference.
