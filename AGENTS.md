# AGENTS.md

## What this repo is

- Git root is `E:\curso Java` (the parent of the dated folders). Sessions often start in a subfolder like `23-09`.
- Each dated folder (`01-clase-17-09`, `21-09`, `22-09`, `23-09`, …) is an **independent static HTML/CSS exercise** for a web course. There is no build system, package manager, lint, typecheck, test runner, or CI — do not add one or invent commands for them.
- Despite the folder name "curso Java", current content is HTML/CSS only. Some exercises explicitly forbid JavaScript (`No se utilizará JavaScript` in the specs).

## Structure of each exercise folder

```
<fecha>/
  index.html          # entrypoint — open directly in a browser, no dev server
  assets/css/styles.css
  assets/img/…        # required image names are listed in the spec
  instrucciones.md    # 23-09
  ejercicio.md        # 21-09, 22-09
```

- The per-folder markdown (`instrucciones.md` / `ejercicio.md`) is the authoritative spec: required sections, CSS properties, measurements (px/rem/%/vh), folder/image names, and layout percentages. Read it before editing that folder; prefer it over prose in commits or comments.
- Specs often require CSS to stay in a **separate file** from HTML.

## Conventions and gotchas

- Use **relative paths** for assets (`assets/img/foo.jpg`). `23-09/index.html` mixes in an absolute path (`/23-09/assets/img/logo-art-deco.png`) that breaks under `file://` or when the folder is served at the root — do not copy that pattern.
- Images live in `assets/img/` in this repo (older specs may say `img/`); every `<img>` needs an `alt`.
- `styles.css` uses native CSS nesting (e.g. `a {}` inside `header ul li:hover`) — valid modern CSS, not a mistake.
- Known artifact: `23-09/index.html` has a stray `html` line after `</html>`; remove it rather than preserving it.
- A CDN normalize.css link is used in `23-09`; local `styles.css` is loaded first, so normalize can override nothing after it — keep the local sheet second if adding links.
- Student submissions have appeared as zip files and subfolders (e.g. `22-09/daniel molina/`). Do not treat those as app code; avoid committing new zips.

## Git

- No enforced commit style; history messages are short English sentences.
- New dated folders may be untracked — check `git status` from the repo root before assuming the working tree is clean.
