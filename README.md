# jakowetz.nz

Personal site, built as a plain Jekyll site so GitHub Pages builds it
automatically — no build step to run yourself.

## Structure

```
_config.yml            site title, nav links, footer links
_includes/nav.html      header, built from site.nav in _config.yml
_includes/footer.html   footer, built from site.contacts in _config.yml
_layouts/default.html   base HTML shell (fonts, nav, footer)
_layouts/home.html      homepage hero treatment
_layouts/page.html      standard subpage treatment (title + body)
assets/css/style.css    all styling
index.md                homepage content
about.md                About subpage
contact.md              Contact subpage
```

## Adding a new subpage

1. Create a new file in the root, e.g. `writing.md`.
2. Give it front matter:
   ```
   ---
   layout: page
   title: Writing
   permalink: /writing/
   ---
   Your content here, in Markdown.
   ```
3. Add it to the nav so it shows in the header, in `_config.yml`:
   ```yaml
   nav:
     - title: About
       url: /about/
     - title: Contact
       url: /contact/
     - title: Writing
       url: /writing/
   ```
4. Commit and push. That's the whole process — no other file needs touching.

## Editing existing content

- Page text: edit the relevant `.md` file directly (it's just Markdown).
- Nav links and footer links: edit `_config.yml`.
- Design (colours, type, spacing): `assets/css/style.css`.
- Page shell (fonts, structure shared by every page): `_layouts/default.html`.

## Previewing locally (optional)

```
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000`.

## Deploying

1. Push this repo to GitHub.
2. In the repo's Settings → Pages, set the source to the `main` branch, root
   folder. GitHub detects the Jekyll site and builds it — no workflow file
   needed.
3. DNS: point `jakowetz.nz` at GitHub Pages (A records to
   185.199.108.153 / .109.153 / .110.153 / .111.153, or a CNAME record if
   using a subdomain). The `CNAME` file in this repo already tells GitHub
   Pages which custom domain to serve.

## Before going live

- Replace the LinkedIn URL placeholder in `_config.yml` and in `contact.md`.
- Confirm `peter@jakowetz.nz` is the address you want listed.
- Swap the About/Contact copy for whatever you actually want to say — what's
  there now is a starting point, not a final draft.
