# chandinisushma.com — GitHub Pages site

A fresh, static rebuild of the portfolio (originally on Wix), ready to host
on GitHub Pages under the same custom domain.

## What's here
- `index.html` — Work page
- `about.html` — About page
- `assets/style.css` — all styling
- `CNAME` — tells GitHub Pages which custom domain to serve

## 1. Push it to GitHub
```
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## 2. Turn on GitHub Pages
In the repo: **Settings → Pages**
- Source: `Deploy from a branch`
- Branch: `main`, folder `/ (root)`
- Save. GitHub will build a `https://<your-username>.github.io/<repo-name>/` URL first — that's expected before the custom domain kicks in.

## 3. Point the domain at GitHub Pages
This is the one step that has to happen wherever `chandinisushma.com` is
registered (Wix, GoDaddy, Namecheap, etc.) — it's separate from GitHub.

At your domain's DNS settings, add:

**For the apex domain (`chandinisushma.com`)** — four A records pointing to:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**For `www.chandinisushma.com`** — a CNAME record:
```
www  →  <your-username>.github.io
```

The `CNAME` file in this repo is already set to `www.chandinisushma.com` to
match. If you'd rather serve the bare domain (no `www`), change that file's
contents to `chandinisushma.com` instead and add a redirect from `www` if
you want both to work.

DNS changes can take anywhere from a few minutes to ~24 hours to propagate.
Once it resolves, go back to **Settings → Pages** and check "Enforce HTTPS"
so the domain gets a certificate.

## 4. Swap in the real content
The project thumbnails and exploration tiles are placeholder gradients —
drop in the real images (project covers, the donut render, the hamburger
menu animation still, etc.) and update the `<div class="thumb">` /
`<div class="swatch">` elements to `<img>` tags pointing at them.

## Notes
- If Wix is still the live host while DNS is mid-migration, expect a short
  window where the site might be briefly unreachable — the more common
  approach is to lower the DNS TTL a day ahead of the switch.
- Once GitHub Pages is confirmed working, the old Wix hosting/domain
  connection can be cancelled.
