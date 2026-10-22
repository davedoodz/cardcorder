# Cardcorder

```
   ┌──────────────────────┐
   │  ● ● ●  safari-ish    │   rec ●──╮
   │ ┌──────────────────┐ │           │  4s loop
   │ │   ↻  ↻  ↻  ↻      │ │ ───────▶ │  960×710
   │ │  your surface     │ │           │  1.2 MB
   │ └──────────────────┘ │   ╰────────╯
   └──────────────────────┘
```

Record it. Card it. Loop it. Cardcorder turns any self-contained HTML surface into an optimized, silent, looping project-card video — the kind you drop straight into a portfolio grid.

**[Live](https://cardcorder.vercel.app)**

## What it is

Cardcorder is a single-page recorder: load a URL or a local HTML file into a mock Safari window, frame the shot, and capture the browser tab via `getDisplayMedia`, cropping and re-encoding only the window itself. The Pumba gray-white stage (`#ededed` + a white radial wash) and a small Safari-inspector cursor circle are burned into every frame, so every export looks like it came from the same photo shoot.

It defaults to recording from [david-lafond-designs.vercel.app/ascii-hover](https://david-lafond-designs.vercel.app/ascii-hover), but any URL or dropped-in HTML file works.

## Highlights

- **Frame it precisely.** Independent controls for screen zoom, desktop-window scale, X/Y position, cursor-circle size, and four frame styles (Safari light, dark browser, minimal strip, frameless).
- **Card-matched export.** Select a project card from a loaded portfolio preview and Cardcorder matches the output canvas to that card's exact proportions.
- **Tunable export budget.** Duration (3–8s), frame rate (18/24/30 fps), resolution (960×710 card delivery or 1284×950 master), and bitrate (1.6–3.6 Mbps) are all adjustable; the balanced default keeps a 4-second dense-motion loop near 1.2 MB.
- **One-permission capture.** Chrome only asks for a single "This Tab" share; Cardcorder encodes just the output composition, never the surrounding controls.
- **Silent by design.** Audio is never captured — these are loop cards, not video clips.

## Stack

A single `index.html` — vanilla JS, the MediaRecorder and `getDisplayMedia` browser APIs, canvas compositing for the burned-in cursor and frame chrome. No build step. Deployed on Vercel; `vercel.json` rewrites `/ascii-hover(.html)` to the live demo surface it records by default.

## Run locally

Open `index.html` directly in a Chromium-based browser (screen capture needs a secure context, so serve it over `https://` or `localhost` rather than `file://`), or:

```sh
npx serve .
```

## How to use it

1. **Frame** — load a URL or self-contained HTML file, then set screen zoom, desktop-window scale, and frame style.
2. **Perform** — click "Connect mirror," share this tab, and interact inside the window. Only the Pumba card gets cropped into the recording.
3. **Check** — review the looping preview and download if the final frame hands cleanly back to the first.
