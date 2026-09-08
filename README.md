# zzc-site

Personal site for **Zhongchun Zhou** — computer architecture · GPGPU · AI infrastructure.

Zero dependencies, zero build step. One `index.html` (inline CSS + vanilla JS) plus `assets/`.

```
zzc-site/
├── index.html                       the whole page
└── assets/
    ├── portrait.png                 transparent cutout, 576×720
    └── Zhongchun_Zhou_CV.pdf        linked from the Contact section
```

## Run locally

```sh
cd zzc-site
python3 -m http.server 8787
# → http://localhost:8787
```

## Deploy to GitHub Pages

Copy the contents of this folder into the root of `zzczzc20.github.io`:

```sh
cp -R zzc-site/. /path/to/zzczzc20.github.io/
cd /path/to/zzczzc20.github.io
touch .nojekyll          # keeps Pages from reprocessing the files
git add -A && git commit -m "Personal site" && git push
```

Then the CV download button and every relative asset path work as-is.

## Design notes

- **Palette** — silicon blue-black substrate (`#06080e`) with copper interconnect
  (`#ff8f45`) as the only accent; indigo (`#7c96ff`) for links. Committed dark-only.
- **Type** — Archivo (variable width axis, `wdth` 104–124) for display,
  IBM Plex Sans for body, IBM Plex Mono for every label and figure.
  Loaded from Google Fonts; real fallback stacks are declared.
- **Fig. 1** — the research loop (Benchmark → Trace → Simulate → Architect → back).
  Inline SVG; the copper pulse travels the full racetrack via `animateMotion`.
- **Fig. 2** — managed shared-cache SoC with the TMU. Inline SVG.
- **Hero background** — a `<canvas>` cache-access heatmap: scattered accesses with
  locality, plus left-to-right sweeps standing in for TMA bulk tile copies.
- Wide figures scroll inside their own `overflow-x:auto` container, so the page body
  never scrolls sideways.
- Everything respects `prefers-reduced-motion`.

## Editing

Content lives directly in the markup, grouped by section id:
`#vision`, `#system`, `#arch`, `#pubs`, `#track`, `#kit`, `#contact`.
Design tokens are the CSS custom properties in the `:root` block at the top.
