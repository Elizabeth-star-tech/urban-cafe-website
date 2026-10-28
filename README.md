# Urban Cafe — Website

A single-page, responsive website for **Urban Cafe**, a family restaurant in Kenya.

Built as one self-contained HTML file with its own image folder — no build step, no
frameworks, no dependencies to install. Upload it to any static host and it works.

---

## What's in this folder

```
urban-cafe-website/
├── index.html          # The entire site (HTML + CSS + JS inline)
├── images/             # 8 photographs used across the page
│   ├── hero.jpg
│   ├── coffee.jpg
│   ├── cappuccino.jpg
│   ├── pilau.jpg
│   ├── nyama.jpg
│   ├── jollof.jpg
│   ├── exterior.jpg
│   └── map.jpg         # Locator map for the Visit section
├── README.md           # This file
├── LICENSE             # Usage terms
└── .gitignore
```

**Sections on the page:** Hero · About · Menu (Mains / Breakfast / Drinks & Coffee tabs) ·
Gallery · Reviews · Visit (hours, contact, map) · Closing CTA · Footer.

---

## Preview it locally

The site runs straight from the filesystem — just open `index.html` in a browser.

**Simplest way:** double-click `index.html`.

**Better way** (a local web server, so paths and fonts behave exactly as they will
online). Run one of these from inside this folder:

```bash
# Python 3 (already installed on macOS and most Linux systems)
python3 -m http.server 8000

# Node.js
npx serve .

# PHP
php -S localhost:8000
```

Then open <http://localhost:8000> in your browser.

To preview the mobile layout, open your browser's developer tools (F12 or
Cmd/Ctrl + Option/Alt + I) and toggle the device toolbar.

---

## Publish on GitHub Pages

GitHub Pages hosts this for free at a public URL. No account upgrade needed.

### Option A — Upload through the website (no command line)

1. **Create the repository.** Go to <https://github.com/new>.
   - *Repository name:* `urban-cafe-website`
   - *Visibility:* **Public** (Pages requires public on free accounts)
   - Leave "Add a README file" **unchecked** — you already have one.
   - Click **Create repository**.

2. **Upload the files.** On the new empty repo page, click
   **uploading an existing file** (or *Add file → Upload files*).
   - Unzip the download on your computer first.
   - Drag in **the contents** of the `urban-cafe-website` folder — that is,
     `index.html`, `README.md`, `LICENSE`, `.gitignore` and the whole `images/` folder.
   - ⚠️ Upload the *contents*, not the outer folder. `index.html` must sit at the
     **top level** of the repo, not inside a subfolder.
   - ⚠️ Make sure `images/` keeps its name and contains all 8 `.jpg` files. If the
     images land in the repo root instead, the page will load with broken pictures.
   - Type a commit message such as `Add Urban Cafe website` and click **Commit changes**.

3. **Turn on Pages.** In the repo, go to **Settings → Pages** (left sidebar).
   - Under *Build and deployment → Source*, choose **Deploy from a branch**.
   - *Branch:* **main**, *Folder:* **/ (root)**. Click **Save**.

4. **Wait, then visit.** The first build takes about 1–2 minutes. Refresh the
   Settings → Pages screen until a banner appears saying *"Your site is live at …"*.

   Your URL will be:

   ```
   https://<your-github-username>.github.io/urban-cafe-website/
   ```

   For example, user `janedoe` gets
   `https://janedoe.github.io/urban-cafe-website/`.

### Option B — Command line (git)

```bash
# from inside the urban-cafe-website folder
git init
git add .
git commit -m "Add Urban Cafe website"
git branch -M main
git remote add origin https://github.com/<your-username>/urban-cafe-website.git
git push -u origin main
```

Then enable Pages exactly as in **Option A, step 3** above.

### Updating the site later

Edit the files, then either upload them again through the GitHub web interface, or:

```bash
git add .
git commit -m "Update menu prices"
git push
```

Pages redeploys automatically within a minute or two. You may need a hard refresh
(Ctrl/Cmd + Shift + R) to bypass your browser cache.

### Using a custom domain (optional)

1. Buy a domain (Namecheap, Cloudflare, Porkbun, etc.).
2. In **Settings → Pages → Custom domain**, enter it and click **Save**.
3. At your domain registrar, add these DNS records:

   | Type  | Name | Value |
   |-------|------|-------|
   | A     | `@`  | `185.199.108.153` |
   | A     | `@`  | `185.199.109.153` |
   | A     | `@`  | `185.199.110.153` |
   | A     | `@`  | `185.199.111.153` |
   | CNAME | `www`| `<your-username>.github.io` |

4. Wait for DNS to propagate (often 10–30 minutes), then tick
   **Enforce HTTPS** on the Pages screen.

---

## Before you go live — replace the placeholders

The business details come from its Google Maps listing. Two fields were **not
published** on that listing, so realistic placeholders are in place. Search
`index.html` for them and swap in the real values:

| Placeholder | Where | Replace with |
|---|---|---|
| `+254700000000` | `tel:` link, hero button, Visit section | The real phone number |
| `hello@urbancafe.co.ke` | `mailto:` link, Visit section | The real email address |

Also worth a review:

- **Menu items and prices** — the listing gives a price range (KES 500–1,000 per
  person) but no itemised menu. The dishes shown are representative Kenyan
  family-restaurant fare at plausible prices; confirm or adjust them.
- **Opening hours** — Mon–Fri 9:00 AM – 9:00 PM, closed weekends, per the listing.
- **Gallery photos** — stock photography chosen to match the category. Swap in real
  photos of the restaurant for the strongest first impression. Keep the same
  filenames (or update the `src` attributes) and the layout stays intact.

---

## Notes on how it's built

- **No dependencies.** Fonts load from Google Fonts (Fraunces for headings, DM Sans
  for body); everything else is inline. The page still renders if fonts fail to load —
  it falls back to system serif/sans.
- **Fully responsive.** Breakpoints for tablet and mobile, with a hamburger menu
  under 900px.
- **Accessible.** Semantic landmarks, visible focus states, descriptive `alt` text,
  and `prefers-reduced-motion` support.
- **The map.** It's a static image with a marker (generated from OpenStreetMap tiles)
  wrapped in a link to Google Maps directions. This is deliberate: Google's embeddable
  map iframe now requires a billed API key and renders blank without one.
- **Menu tabs** and the **mobile menu** use a few lines of vanilla JavaScript. With
  JavaScript disabled, all menu categories remain readable in the page source.

---

## License

See [LICENSE](LICENSE). The site code is yours to use and modify. The photographs are
stock images — if you keep them, confirm the licence terms of the source you obtained
them from, or replace them with your own.
