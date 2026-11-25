# riker.dev

Personal site. Plain HTML/CSS, no build step.

```
index.html              the whole site
colin.jpg               headshot (480px)
favicon.svg             Prairie-glass favicon
ColinRiker_Resume.pdf   linked as "resume"
fonts/                  Inter (variable) + Newsreader 500, self-hosted
docs/                   posters, slides, reports linked from Projects
CNAME                   tells GitHub Pages the custom domain
.nojekyll               tells GitHub Pages to serve files as-is
```

## Editing

- Colors are CSS variables at the top of `<style>` in `index.html`.
- Add a current thing: copy an `<article class="thing">` block.
- Add something to watch/read: copy an `<article class="talk">` block.
- Add a project: copy an `<article class="project">` block; put files in `docs/`.

## Deploy (GitHub Pages + Squarespace DNS)

1. Push this folder to a public repo, e.g. `ColinRiker/riker.dev`.
2. Repo → Settings → Pages → Source: deploy from branch `main`, folder `/ (root)`.
3. Same page → Custom domain: `riker.dev` → Save.
4. Squarespace → Domains → riker.dev → DNS → DNS Settings:
   - Remove the Squarespace Defaults A/CNAME records for `@` and `www` if present.
   - Custom Records → add four A records, host `@`:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Add CNAME, host `www` → `colinriker.github.io`
5. Wait for DNS (minutes to a few hours), then tick **Enforce HTTPS** in Pages settings.
   `.dev` domains only load over HTTPS, so the site won't open until the certificate is issued.

Check with: `dig riker.dev +short`
