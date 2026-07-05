# Cocktella site (source)

Static pages served by GitHub Pages from the **public** repo
[`peyopeev0206/cocktella-site`](https://github.com/peyopeev0206/cocktella-site)
(this app repo is private, and free Pages requires a public repo).

- `index.html` — landing page; also the Supabase Auth **Site URL** target, so it
  doubles as the "email confirmed" page.
- `privacy.html` — privacy policy (App Store requirement).
- `terms.html` — terms of use incl. the community guidelines / UGC zero-tolerance
  language (Apple guideline 1.2).
- `party.html` — Party Mode menu page opened by QR-code scans and shared links
  (`?code=XXXX`). Fully self-contained (no external assets, no frameworks); fetches
  the party snapshot via the public `get_party_menu` RPC and renders recipe cards
  with a deep-link footer button. **Hard-codes the Supabase anon key** — this is
  intentional; the anon key is public by design (it also ships in the app binary).
  If `SUPABASE_URL` ever changes, update the constant in `party.html` and re-copy
  to the public repo.

**This folder is the source of truth.** After editing, redeploy with:

```sh
git clone --depth 1 https://github.com/peyopeev0206/cocktella-site /tmp/cocktella-site
cp site/*.html site/*.css /tmp/cocktella-site/
cd /tmp/cocktella-site && git add -A && git commit -m "Update site" && git push
```
