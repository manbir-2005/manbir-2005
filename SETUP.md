# manbir-2005 — Premium GitHub Profile · Setup & Maintenance

A complete asset kit for a custom, animated GitHub profile:

- `README.md` — the profile page
- `assets/` — 6 hand-crafted SVGs (all animations are native SMIL, no JavaScript → fully compatible with GitHub's image proxy)
- `.github/workflows/snake.yml` — contribution-snake generator

---

## 1. Installation (one-time, ~5 minutes)

1. **Create the profile repo** (skip if it already exists):
   - Repo name **must** be exactly `manbir-2005` → [github.com/new](https://github.com/new)
   - Public, with a `README.md` initialized.

2. **Copy the files into the repo root** so the structure looks like:

   ```text
   manbir-2005/
   ├── README.md
   ├── assets/
   │   ├── hero-banner.svg
   │   ├── divider.svg
   │   ├── wave-art.svg
   │   ├── forge-art.svg
   │   ├── team-net.svg
   │   └── signature.svg
   └── .github/
       └── workflows/
           └── snake.yml
   ```

   (If working locally: create a git repo in this folder, add a remote `git remote add origin https://github.com/manbir-2005/manbir-2005.git`, then `git push -f origin main`.)

3. **Activate the snake** (needs one manual run for the first render):
   - Repo → **Actions** tab → *Contribution Snake* → **Run workflow** → Run.
   - Wait ~1 minute. The action creates an `output` branch with two SVGs.
     The README's `<picture>` element picks them up automatically (dark mode + light mode).
   - From then on it refreshes automatically (cron: daily at 00:00 IST) and on every push to `main`.
   - *No secrets needed — the workflow uses the built-in `GITHUB_TOKEN`.*

4. **Verify locally before committing** — open the SVGs in a browser and, to preview the
   README exactly as GitHub renders it, use the repo page itself (GitHub applies its
   restrictive avatar-friendly SVG rendering to profile READMEs, matching production).

---

## 2. What runs where (honest dependency map)

| Element | Source | Needs setup? | Failure behaviour |
|---|---|---|---|
| Hero banner, divider, wave art, forge art, team network, signature | local `assets/*.svg` | none | always render (no external calls) |
| Typing roles line | `readme-typing-svg.demolab.com` | none | if offline, image simply doesn't load |
| GitHub statistics / top languages | `github-readme-stats.vercel.app` | none | if offline, image doesn't load |
| Contribution streak | `streak-stats.demolab.com` | none | if offline, image doesn't load |
| Contribution snake | `Platane/snk` GitHub Action → `output` branch | **run the workflow once** | blank until first run |
| Activity graph | *intentionally disabled* — `github-readme-activity-graph.vercel.app` returned HTTP 402 "Payment Required / DEPLOYMENT_DISABLED" on 2026-10-24 | see README HTML comment for the exact embed line to re-enable when the service (or a self-deploy) is healthy | — |
| View counter (optional) | `komarev.com/ghpvc` | uncomment in README | commented out by default |

External stat widgets are standard, widely mirrored, self-serve services.
They report **real GitHub data** for `manbir-2005` — nothing is fabricated. The custom
SVGs are decoration and never claim to be live data.

## 3. Honesty policy baked into the design

- Skills are split into **working knowledge** (solid icons) and **active learning** (violet tags & the AI/ML, GenAI rows) — mirroring what you actually stated.
- Stats/labels come from real services; placeholders in *Project Log* are clearly marked as reserved slots and invent nothing.
- No certifications, awards, or metrics were added beyond what you provided.

## 4. Maintaining

| Change | Do this |
|---|---|
| Add a project | duplicate one of the two real `<td>` cards in *Project Log* and replace a reserved slot |
| Update roles typed in the hero area | edit the `lines=` parameter in the `readme-typing-svg.demolab.com` URL (use `%20` for spaces, `%2C` for commas, `;` to separate lines) |
| Change the palette | edit the SVG gradient stops (`#22d3ee` cyan → `#818cf8`/`#a78bfa` violet) and the `title_color/color_*` params in the widget URLs |
| New tech icon | append its id (comma-separated) to any `https://skillicons.dev/icons?i=...` URL — ids verified working: python, cpp, js, mysql, numpy, pandas, tensorflow, keras, pytorch, opencv, git, github, docker, vscode, html, css |
| Slow down the hero typing | change `dur="5.2s"` on both the `<rect>` width animate and the cursor `x` animate in `assets/hero-banner.svg` (keep the two `values` lists in step) |

## 5. Files created

```text
manbir-2005-profile/
├── README.md                        ← replace the repo's README.md
├── SETUP.md                         ← this guide
├── assets/
│   ├── hero-banner.svg              ← animated hero (neural lattice, streams, typing line)
│   ├── divider.svg                  ← animated section divider
│   ├── wave-art.svg                 ← Ocean Bed card art (seamless wave loop)
│   ├── forge-art.svg                ← Forge AI card art (analysis lattice + scan sweep)
│   ├── team-net.svg                 ← UpToSkills leadership network
│   └── signature.svg                ← footer signature
└── .github/workflows/snake.yml      ← contribution snake (Platane/snk@v3)
```

Nothing in your original repo values was discarded: the Forge AI project, Kaggle
account (kaggle.com/manbirr) and contact email from your previous template README
were folded into the new design (email intentionally omitted from the page itself;
it stays out of this kit until you choose to publish it — the old README had it, so
re-add `singhmanbir101@gmail.com` only if you're comfortable keeping it public).
