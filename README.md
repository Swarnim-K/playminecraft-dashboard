# playminecraft-dashboard

Public-facing mirror of `docs/progress-dashboard.html` from the main
`PlayMinecraftIN` workspace, published at `docs.playminecraft.in` via
GitHub Pages.

This repo is intentionally separate from the main server workspace so the
plugin source, server docs, and internal infra details never get pushed
to a public repo — only this one dashboard file is public.

## Updating the live site

Whenever `docs/progress-dashboard.html` changes in the main workspace:

```bash
cp "../PlayMinecraftIN/docs/progress-dashboard.html" index.html
git add index.html
git commit -m "Sync dashboard"
git push
```

The site redeploys automatically a few seconds after the push (GitHub
Pages watches the default branch).

## One-time setup (already done locally, GitHub side still pending)

1. Create a new **public** GitHub repo named `playminecraft-dashboard`
   under the `Swarnim-K` account (public is required for free GitHub
   Pages on a personal account).
2. `git remote add origin https://github.com/Swarnim-K/playminecraft-dashboard.git`
3. `git branch -M main`
4. `git push -u origin main`
5. In the repo's **Settings → Pages**: Source = `main` branch, `/ (root)`
   folder. Custom domain = `docs.playminecraft.in`. Wait for the DNS
   check to pass, then enable **Enforce HTTPS**.
6. In your domain registrar's DNS panel, add:
   - Type: `CNAME`
   - Host/Name: `docs`
   - Value/Target: `swarnim-k.github.io`
   (Leave the existing root `playminecraft.in` CNAME to the Minecraft
   server untouched — this only adds the `docs` subdomain.)
