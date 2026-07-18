# Shuning Liu — Academic Website

Personal academic website for Shuning Liu, PhD candidate in Microelectronics at HKUST(GZ). The site presents research interests, publications, projects, academic news, talks, and a bilingual profile.

## Technology

- [Hugo](https://gohugo.io/) Extended 0.136.5
- [Hugo Blox Builder](https://hugoblox.com/)
- Hugo Modules
- [Pagefind](https://pagefind.app/) static search
- GitHub Actions and GitHub Pages

## Repository structure

- `config/_default/`: site, language, and navigation configuration
- `content/`: English content
- `content/zh/`: Chinese content
- `content/post/` and `content/zh/post/`: blog and academic-news posts
- `content/publication/`: publications
- `content/event/`: talks and events
- `assets/`: source assets processed by Hugo
- `static/`: files copied directly to the generated site
- `.github/workflows/publish.yaml`: build and deployment workflow

Keep section directory names lowercase. Blog content belongs in `content/post/` and `content/zh/post/`; do not recreate parallel `Blog/` directories.

## Local development

Install Hugo Extended 0.136.5, Go, and Node.js. Then run:

```bash
npm install
hugo server
```

Open the local URL printed by Hugo. Draft content can be included with `hugo server -D`.

## Production build

```bash
npm run build
npm run pagefind
```

The generated website and search index are written to `public/`. Pull requests targeting `main` are built by GitHub Actions; pushes to `main` are built and deployed to GitHub Pages.

## Content maintenance

- Edit the English homepage in `content/_index.md`.
- Edit the Chinese homepage in `content/zh/_index.md`.
- Maintain the English and Chinese profiles in their respective `content/**/authors/admin/_index.md` files.
- Put downloadable files such as the CV in `static/uploads/`.
- Use absolute `https://` URLs for external profile links.
- Preview both language versions before merging content changes.

## License and attribution

The website content belongs to its respective author unless otherwise stated. Hugo, Hugo Blox Builder, Pagefind, and other dependencies remain subject to their own licenses.
