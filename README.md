# Livier Rodriguez — Portfolio

One self-contained page. No build step, no dependencies.

## Assets

| File | Status |
|---|---|
| `assets/hero.jpg` | **In.** Square head-and-shoulders crop of the balcony photo — the circular hero portrait |
| `assets/hero-full.jpg` | The uncropped balcony photo, kept so the crop can be redone |
| `assets/alpfa-poster.jpg` | Unused — the ALPFA poster has text baked into the image, so it can't work as a portrait |
| `assets/about.jpg` | **Missing.** Optional second photo beside the About Me copy |
| `assets/resume.pdf` | **Missing.** Sits behind the `Get Resume` button and the Contact download |

Filenames must match exactly, lowercase. Missing files degrade cleanly: without `about.jpg` the About section reflows to a single column (no empty box), and without `resume.pdf` the two resume links go nowhere.

To recrop the hero from the original:

```bash
python -c "from PIL import Image; im=Image.open('assets/hero-full.jpg'); im.crop((225,420,955,1150)).resize((900,900), Image.LANCZOS).save('assets/hero.jpg', quality=92)"
```

The box is `(left, top, right, bottom)` in source pixels and must stay square.

## Run it

Double-click `index.html`. That's it.

## Deploy to GitHub Pages

```bash
cd portfolio
git init
git add .
git commit -m "Portfolio"
gh repo create livier-portfolio --public --source=. --push
```

Then in the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**. Live at `https://<username>.github.io/livier-portfolio/` in about a minute.

## Editing

Everything is in `index.html`. Section order: nav, hero, about, experience, projects, leadership, education & skills, contact, footer.

Colors live in the `:root` block at the top of the `<style>` tag. All six pass WCAG AA against every background they're used on — if you change `--rose` or `--sage`, re-check the contrast before shipping.

To add an experience entry, copy an `<article class="entry">` block. The number in `<span class="metric">` is the one that shows large in the left rail — keep it to 4 characters or fewer so it doesn't crowd the prose.
